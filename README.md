# submodule-checkout-buildkite-plugin

This plugin enables you to specify which submodules of a repo you would like to checkout, on top of your base repo.

If no submodules are supplied, this will still override the default checkout buildkite provides, and do a shallow checkout of your base repo.

Given the submodule arguments supplied are just used inline for a checkout command like so: `git submodule checkout --init ${submodule}`, this means you can also provide additional flags like `--recursive` to the submodule arg you provide, if required.

## Using the plugin

```yaml
steps:
  - label: "My pipeline step"
    plugins:
      - https://github.com/viviedu/submodule-checkout-buildkite-plugin.git#1.0.0:
          checkouts:
            - git submodule update --init my-submodule
            - git -C my-submodule submodule update --init my-nested-submodule
            - git submodule update --init --recursive my-other-submodule
```
