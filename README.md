# create-ecr-buildkite-plugin

A [Buildkite plugin](https://buildkite.com/docs/agent/v3/plugins) to create and configure AWS ECR.

# Example

## Basic Usage

```yml
steps:
  - label: 'Main'
    plugins:
      seek-oss/create-ecr#v1.0.11:
        name: 'my-repo-name'
        permissionspolicy: 'path/to/permissions-policy.json'
        lifecyclepolicy: 'path/to/lifecycle-policy.json'
    command:
      - echo hi
```

Params:

- name (required) - name of the ECR.
- permissionspolicy (optional) - path in local repository to the permissions policy file.
- lifecyclepolicy (optional) - path in local repository to the lifecycle policy file.

# License

MIT (see [LICENSE](LICENSE))
