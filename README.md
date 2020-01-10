# Create ECR Buildkite Plugin

[![GitHub Release](https://img.shields.io/github/release/seek-oss/create-ecr-buildkite-plugin.svg)](https://github.com/seek-oss/create-ecr-buildkite-plugin/releases)

A [Buildkite plugin](https://buildkite.com/docs/agent/v3/plugins) to create and
manage an Amazon ECR repository.

## Example

The following pipeline creates an ECR repository `my-repo` if it does not
already exist, and sets the lifecycle policy to the default
[policies/default-lifecycle-policy.json](policies/default-lifecycle-policy.json):

```yaml
steps:
  - label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          name: my-repo
```

A custom lifecycle policy and repository policy may be specified:

```yaml
steps:
  - label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          lifecycle-policy: path/to/lifecycle-policy.json
          name: my-repo
          repository-policy: path/to/repository-policy.json
```

A custom ECR repository tags file may be specified:

```yaml
steps:
  - label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          name: my-repo
          repository-tags-file: path/to/repository-tags-file.json
```

## Configuration

- `name` (required, string)

  Name of the ECR repository.

- `scan-on-push` (optional, boolean)

  Whether to [automatically scan images](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-scanning.html#scanning-repository) pushed to the ECR repository for vulnerabilities.
  Omitting this option will leave the existing image scanning configuration untouched.

- `repository-policy` (optional, string)

  Path in local repository to the repository policy file.

- `lifecycle-policy` (optional, string)

  Path in local repository to the lifecycle policy file.

- `repository-tags-file` (optional, string)

  Path in local repository to the ecr repository tags file.

## License

MIT (see [LICENSE](LICENSE))
