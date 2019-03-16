# GitHub Action for `mix deps.get`

This Action makes it easy to run `mix deps.get` with no additional args or
environment variables necessary.

## Usage

An example workflow to run `mix deps.get` is as follows:

```hcl
workflow "Run Tests on Push" {
    on = "push"
    resolves = "Run Tests"
}

action "Get Deps" {
    uses = "jclem/action-mix/deps.get@v1.3.2"
}

action "Run Tests" {
    uses = "jclem/action-mix/test@v1.3.2"
    needs = "Get Deps"
}
```