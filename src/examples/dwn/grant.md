# Grant access

> TODO: This page is a work in progress.

This example demonstrates how to create a grant for and use it to query for messages.

Grants are used to grant a user permission to access a specific method on a DWN.

Alice grants Bob permission to query messages (`MessagesQuery`). The grant is persisted to Alice's
DWN so all Bob needs to do is sign his message and specify the `record_id` of the grant in order
to make use of it.

```rust
use credibil_dwn::client::grants::{GrantBuilder, Scope};
use credibil_dwn::{Method, StatusCode, endpoint};

use test_node::keystore::{self, Keyring};
use test_node::provider::ProviderImpl;

static ALICE: LazyLock<Keyring> = LazyLock::new(|| keystore::new_keyring());
static BOB: LazyLock<Keyring> = LazyLock::new(|| keystore::new_keyring());

fn main() {
    let provider = ProviderImpl::new().await.expect("should create provider");

    // Alice creates a grant scoped to `MessagesQuery` for Bob.
    let bob_grant = GrantBuilder::new()
        .granted_to(&BOB.did)
        .scope(Scope::Messages {
            method: Method::Query,
            protocol: None,
        })
        .sign(&*ALICE)
        .build()
        .await
        .expect("should create grant");

    // Alice persists the grant on her DWN.
    let reply =
        endpoint::handle(&ALICE.did, bob_grant.clone(), &provider).await.expect("should write");
    assert_eq!(reply.status.code, StatusCode::ACCEPTED);

    // Bob uses the grant to query for the messages.
    let query = QueryBuilder::new()
        .permission_grant_id(&bob_grant.record_id)
        .sign(&*BOB)
        .build()
        .await
        .expect("should create write");
    let reply = endpoint::handle(&ALICE.did, query, &provider).await.expect("should write");
    assert_eq!(reply.status.code, StatusCode::OK);
}
```