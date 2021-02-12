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
  - command: echo 'use your new ECR repo here'
    label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          name: my-repo
```

A custom lifecycle policy and repository policy may be specified:

```yaml
steps:
  - command: echo 'use your new ECR repo here'
    label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          lifecycle-policy: path/to/lifecycle-policy.json
          name: my-repo
          repository-policy: path/to/repository-policy.json
```

A custom ECR repository tags file may be specified:

```yaml
steps:
  - command: echo 'use your new ECR repo here'
    label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          name: my-repo
          repository-tags-file: path/to/repository-tags-file.json

```

Multiple regions can be specified:

```yaml
steps:
  - command: echo 'use your new ECR repo here'
    label: ecr
    plugins:
      - seek-oss/create-ecr#v1.3.0:
          name: my-repo
          regions: 
            - us-west-2
            - ap-southeast-2
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

- `regions` (optional, array of strings)

  Regions to push the images to. If not mentioned, current region is pulled from runtime config.

## Troubleshooting

### 🚨 Error: No command has been provided

This plugin runs on a [`pre-command` hook] to allow it to be chained with other commands and plugins, like the [`docker-ecr-publish` plugin].
You will need to specify a `command` for the step, even if it is just a simple `echo` like in the examples above.

[`docker-ecr-publish` plugin]: https://github.com/seek-oss/docker-ecr-publish-buildkite-plugin
[`pre-command` hook]: https://buildkite.com/docs/agent/v3/hooks#available-hooks

## License

MIT (see [LICENSE](LICENSE))
