# Configure a protocol

> TODO: This page is a work in progress.

This example demonstrates how to install a protocol and write messages to it.

Alice installs a protocol that allows anyone using it to take any action on her DWN.

```rust
use std::io::Cursor;

use credibil_dwn::client::protocols::{ConfigureBuilder, Definition};
use credibil_dwn::client::records::{Data, ProtocolBuilder, WriteBuilder};
use credibil_dwn::{Method, StatusCode, endpoint};

use test_node::keystore::{self, Keyring};
use test_node::provider::ProviderImpl;

static ALICE: LazyLock<Keyring> = LazyLock::new(|| keystore::new_keyring());
static BOB: LazyLock<Keyring> = LazyLock::new(|| keystore::new_keyring());

fn main() {
    let provider = ProviderImpl::new().await.expect("should create provider");

    // Alice configures a protocol to allow anyone to do anything on her DWN.
    let ffa = include_bytes!("protocols/free-for-all.json");
    let definition = serde_json::from_slice(ffa).expect("should deserialize");

    let configure = ConfigureBuilder::new()
        .definition(definition.clone())
        .sign(&*ALICE)
        .build()
        .await
        .expect("should build");

    // Alice installs the protocol on her DWN.
    let reply = endpoint::handle(&ALICE.did, configure, &provider)
        .await
        .expect("should configure protocol");
    assert_eq!(reply.status.code, StatusCode::ACCEPTED);

    // Alice writes a message to the Records `free-for-all` interface.
    let data = br#"{"message": "test record write"}"#;
    let reader = Cursor::new(data.to_vec());

    let write_any = WriteBuilder::new()
        .protocol(ProtocolBuilder {
            protocol: &definition.protocol,
            protocol_path: "post",
            parent_context_id: None,
        })
        .schema(definition.types["post"].schema)
        .data(Data::Stream(reader))
        .sign(&*ALICE)
        .build()
        .await
        .expect("should create write");

    let reply =
        endpoint::handle(&ALICE.did, write_any.clone(), &provider).await.expect("should write");
    assert_eq!(reply.status.code, StatusCode::ACCEPTED);
}
```