# Credibil Documentation

Documentation for the Credibil open source components.

## Getting Started

This is built with [mdBook](https://github.com/rust-lang/mdBook). If you want to
change the docs, follow the [installation](https://rust-lang.github.io/mdBook/guide/installation.html) 
and [getting started guide](https://rust-lang.github.io/mdBook/guide/creating.html).

TLDR: to view this book locally, install mdBook 

```sh
cargo install mdbook
```

and run

```sh
mdbook serve --open
```

## Plugins

To get the full styling, install the following plugins:

```sh
cargo install mdbook-admonish
```

We also use the [linkcheck](https://github.com/Michael-F-Bryan/mdbook-linkcheck)
plugin to check for broken links:

```sh
cargo install mdbook-linkcheck
```

## Publishing

The documentation is published directly to GitHub pages on commit to `main` using GitHub actions.
