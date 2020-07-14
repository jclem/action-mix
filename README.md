**🚨 [Archived] This action worked for an early iteration of the GitHub Actions beta. Now, check out [actions/setup-elixir](https://github.com/actions/setup-elixir)! 🚨**

---

# GitHub Action for Mix

This Action for [Mix](https://hexdocs.pm/mix/Mix.html) enables arbitrary actions with this `mix` command-line client.

The default `MIX_ENV` is `"dev"`, so override it as needed.

## Usage

An example workflow to run `mix test` and `mix format --check-formatted` is as follows:

```hcl
workflow "Tests & Formatting" {
    on = "push"
    resolves = ["Run Tests", "Check Formatting"]
}

# Convenience workflow for `mix deps.get`
action "Get Deps" {
    uses = "jclem/action-mix/deps.get@v1.3.3"
}

# Convenience workflow for `mix test`
action "Run Tests" {
    uses = "jclem/action-mix/test@v1.3.3"
    needs = "Get Deps"
}

action "Check Formatting" {
    uses = "jclem/action-mix@v1.3.3"
    needs = "Get Deps"
    args = "format --check-formatted"
}
```
