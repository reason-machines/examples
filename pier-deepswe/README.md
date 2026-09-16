# More DeepSWE tasks

Complete the [setup in the main README](../README.md) first.

To run a different task, replace the task directory in `--path`.
Use `ls deep-swe/tasks` to see the available tasks.

To run the **whole dataset**, one task at a time:

```bash
DOCKER_DEFAULT_PLATFORM=linux/amd64 .venv/bin/pier run \
  --path deep-swe/tasks \
  --agent-import-path reasonmachines_pier:ReasonAgent \
  --model openai/gpt-5.6-luna \
  --n-concurrent 1 \
  --jobs-dir outputs/pier
```

A full run can take many hours or days and costs more than a single task.
Pier uses each task's default time limits, one attempt, and no retries.

## API-key permissions

Your key needs `run`, `sessions:read`, `deployment:read`, `devices:read`,
`devices:write`, and `devices:use`. Its owner must be able to create or access a
workspace-visible `Pier Benchmarks` project. The adapter manages this project automatically.

For model errors, check your workspace's [Models settings](https://reasonmachines.ai/customize?tab=models).
For command options, run `.venv/bin/pier run --help` or see [Pier](https://github.com/datacurve-ai/pier).
