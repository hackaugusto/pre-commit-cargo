# Cargo hook for pre-commit

Hooks have to be defined in a repository to be easily used with `pre-commit`.
This is a very simple hook that allows `pre-commit` to call `cargo`. Your
configuration file has to provide the required flags to use it properly.

The main goal of this hook is to allow one to configure the target
channel/toolchain, for example to run `check` with `stable` and `clippy` with
`nigthly`.

## Why not `doublify/pre-commit-rust`?

The repo seems dead, there are multiple PRs spaning multiple years that are not
reviewed/merged.

# Usage

```yaml
- repo: https://github.com/hackaugusto/pre-commit-cargo
  rev: v1.0.0
  hooks:
    - id: cargo
      name: cargo +nigthly fmt
      args: [+nightly, fmt, --all, --, --check]
    - id: cargo
      name: cargo +nigthly clippy
      args: [+nightly, clippy, --all, --, -D, clippy::all, -D, warnings]
    - id: cargo +stable check
      name: cargo check
      args: [+stable, check, --all-target]
```

# License

MIT-0
