# GitHub Action for `mix test`

This Action makes it easy to run `mix test` with no additional args or environment variables necessary.

## Usage

An example workflow to run `mix test` is as follows:

```hcl
workflow "Run Tests on Push" {
    on = "push"
    resolves = "Run Tests"
}

action "Run Tests" {
    uses = "jclem/action-mix/test@v1.2.0"
}
```