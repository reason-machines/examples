# DeepSWE with Reason on Pier

Use the installable `reason-machines-pier` adapter with the Reason Machines API.
See the [main README](../README.md) for CLI and package installation.

## Dataset

Download the official DeepSWE v1.1 tasks:

```bash
mkdir -p deep-swe
curl -LsSf https://github.com/datacurve-ai/deep-swe/archive/0b9fabbb63b9104d678fe965e1632f2dd9eaa2ea.tar.gz \
  | tar -xz --strip-components=1 -C deep-swe
```

## Run

With Docker running:

```bash
export REASON_API_KEY="<your-reason-api-key>"
pier run --path deep-swe/tasks \
  --agent-import-path reasonmachines_pier:ReasonAgent \
  --model openai/gpt-5.6-luna
```

Docker is the default. Results are saved to `jobs/`.
Pier currently requires a local dataset path; named datasets such as `--dataset deep-swe@1.1` are not supported.

The adapter installs and verifies its pinned Linux x64/glibc CLI inside the task container.
Your host CLI is the same product, but is not copied into Docker. No YAML or
wrapper script is needed. Defaults are production Reason Machines, isolated mode and medium
reasoning effort. Pier defaults to one attempt and no retries.

Configure model access and provider credentials in Reason Machines. The API key must be able
to access or create its organization's resource-free `Pier Benchmarks` project.
An inaccessible existing project with that slug blocks startup.

## References

- [Pier](https://github.com/datacurve-ai/pier)
- [DeepSWE](https://github.com/datacurve-ai/deep-swe)
- [Reason Machines API](https://docs.reasonmachines.ai/api-reference/)
- [Latest adapter](https://github.com/reason-machines/examples/releases/tag/latest)
