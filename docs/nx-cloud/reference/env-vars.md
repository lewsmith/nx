# Environment Variables

### NX_BRANCH

The `@nrwl/nx-cloud` requires the `NX_BRANCH` environment variables to be set. For many CI providers (e.g., GitHub Actions), the runner is able to set it automatically. For others, the variable will have to be set manually. If you set it manually, note that `NX_BRANCH` has to be set to a PR number for the GitHub integration to work.

### NX_CLOUD_ACCESS_TOKEN

You can also configure the access token by setting the `NX_CLOUD_ACCESS_TOKEN` environment variable. `NX_CLOUD_ACCESS_TOKEN` takes precedence over the `accessToken` property. It's common to have a read-only token stored in `nx.json` and a read-write token set via `NX_CLOUD_ACCESS_TOKEN` in CI. If you are using this environment variable with Distributed Task Execution, the value on the main and agent jobs must match.

### NX_CLOUD_DISTRIBUTED_EXECUTION_AGENT_COUNT

The Nx Cloud plans distributed task execution based on the available information from the running agents. Due to asynchronous nature of CI jobs, an agent might not have been created or started at the moment when DTE is initiated. Setting `NX_CLOUD_DISTRIBUTED_EXECUTION_AGENT_COUNT` to say 8 will inform Nx Cloud to assume that there will be 8 agents running. This can have an impact on better distribution of the tasks and allocation of the agents.

### NX_CLOUD_DISTRIBUTED_EXECUTION_STOP_AGENTS_ON_FAILURE

Setting `NX_CLOUD_DISTRIBUTED_EXECUTION_STOP_AGENTS_ON_FAILURE` to `true` will tell Nx Cloud to stop agents if a command fails. When set to false (default value), you need to make sure to invoke `nx-cloud stop-all-agents` even if CI fails.

### NX_CLOUD_DISTRIBUTED_EXECUTION

Setting `NX_CLOUD_DISTRIBUTED_EXECUTION` to `true` enables distributed task execution.

### NX_CLOUD_ENCRYPTION_KEY

You can set the `encryptionKey` property in `nx.json` or set the `NX_CLOUD_ENCRYPTION_KEY` environment variable to enable the e2e encryption of your artifacts. In this case, the artifacts will be encrypted/decrypted on your machine.

### NX_CLOUD_ENV_NAME

Setting `NX_CLOUD_ENV_NAME` will prefix all your commands so you can easily distinguish them in the UI and in GitHub comments. For instance, if you run the same set of commands on Windows and Linux machines, you can set `NX_CLOUD_ENV_NAME` to `win` on the Windows agent, and `linux` on Linux agents.

### NX_CLOUD_NO_TIMEOUTS

By default, Nx Cloud requests will time out after 10 seconds. `NX_CLOUD_NO_TIMEOUTS` disables the timeout.

### NX_RUN_GROUP

- The `@nrwl/nx-cloud` requires the `NX_RUN_GROUP` environment variables to be set. For many CI providers (e.g., GitHub
  Actions), the runner is able to set it automatically. For others, the variable will have to be set manually. If you set
  it manually, note that `NX_RUN_GROUP` has to be a unique value associated with a CI run.

### NX_VERBOSE_LOGGING

Setting `NX_VERBOSE_LOGGING` to true will output the debug information about agents communicating with the main job. This can be useful for debugging unexpected cache misses and issues with on-prem setups.
