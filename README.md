# GitHub Action for Mix

This Action for [Mix](https://hexdocs.pm/mix/Mix.html) enables arbitrary actions with this `mix` command-line client.

The default `MIX_ENV` is `"dev"`, so override it as needed.

## Usage

An example workflow to run `mix test` and `mix format --check-formatted` is as follows:

```hcl
workflow "Tests & Formatting" {
    on = "push"
    resolves = ["Test", "Check Formatting"]
}

# Convenience workflow for `mix test`
action "Test" {
    uses = "jclem/action-mix/test@v1.2.0"
}

action "Check Formatting" {
    uses = "jclem/action-mix@v1.2.0"
    args = "format --check-formatted"
}
```