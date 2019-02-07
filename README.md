# create-ecr-buildkite-plugin

A [Buildkite plugin](https://buildkite.com/docs/agent/v3/plugins) to create and configure AWS ECR.

# Example

## Basic Usage

```yml
steps:
  - label: 'Main'
    plugins:
      seek-oss/create-ecr#v1.0.10:
        name: "my-repo-name"
        policy: "path/to/ecr-policy.json"
    command:
      - echo hi
```

Params:

- name (required) - name of the ECR.
- policy (optional) - path in local repository to the policy file.

# License

MIT (see [LICENSE](LICENSE))
