# create-ecr-buildkite-plugin

A [Buildkite plugin](https://buildkite.com/docs/agent/v3/plugins) to create and configure AWS ECR.

# Example

## Basic Usage

```yml
steps:
  - label: 'Main'
    plugins:
      seek-oss/create-ecr:
        name: 'my-repo-name'
        repository-policy: 'path/to/repository-policy.json'
        lifecycle-policy: 'path/to/lifecycle-policy.json'
    command:
      - echo hi
```

Params:

- name (required) - name of the ECR.
- repository-policy (optional) - path in local repository to the repository policy file.
- lifecycle-policy (optional) - path in local repository to the lifecycle policy file.

# License

MIT (see [LICENSE](LICENSE))
