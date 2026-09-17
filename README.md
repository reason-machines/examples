# Reason Machines examples

Run Reason on [DeepSWE](https://github.com/datacurve-ai/deep-swe) coding tasks in Docker.

## Setup

On macOS or Linux, install [Docker](https://docs.docker.com/get-started/get-docker/)
and [uv](https://docs.astral.sh/uv/getting-started/installation/), and start Docker.
You also need Git and curl. Run these commands in the same terminal:

```bash
git clone https://github.com/reason-machines/examples.git
cd examples
uv venv --python 3.12 .venv
uv pip install --python .venv/bin/python \
  https://github.com/reason-machines/examples/releases/download/v0.3.6/reason_machines_pier.tar.gz

mkdir -p deep-swe
curl -LsSf https://github.com/datacurve-ai/deep-swe/archive/0b9fabbb63b9104d678fe965e1632f2dd9eaa2ea.tar.gz \
  | tar -xz --strip-components=1 -C deep-swe
```

This installs Pier. The adapter installs the Reason CLI inside Docker automatically.

## Run

Get a [Reason API key](https://reasonmachines.ai/customize?tab=api) and enable
`openai/gpt-5.6-luna` in your workspace's
[Models settings](https://reasonmachines.ai/customize?tab=models).
Replace the placeholder with your key, then run:

```bash
export REASON_API_KEY="YOUR_REASON_API_KEY"
DOCKER_DEFAULT_PLATFORM=linux/amd64 .venv/bin/pier run \
  --path deep-swe/tasks/csstree-shorthand-expansion-compression \
  --agent-import-path reasonmachines_pier:ReasonAgent \
  --model openai/gpt-5.6-luna \
  --jobs-dir outputs/pier
```

This runs **one task** in Docker, including on Apple Silicon. Model/API charges may apply.

Allow **up to 3 hours for the agent, plus 30 minutes for verification**.
It can finish sooner. The first run also downloads several GB of Docker images.
Keep your terminal and Docker running, and your computer awake.

Results and logs are saved in `outputs/pier/`. A completed run can still fail tests.

[More tasks and API-key permissions](pier-deepswe/README.md).
