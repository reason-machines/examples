# Reason Machines examples

Run the Reason agent through the Reason Machines API.

## Installation

Install the Reason CLI:

```bash
curl -LsSf https://reasonmachines.com/install.sh | bash
```

Install the Pier adapter with Python 3.12+:

```bash
pip install --upgrade https://github.com/reason-machines/examples/releases/download/latest/reason_machines_pier.tar.gz
```

<!--
This installs Pier too. The adapter automatically installs the Linux x64/glibc Reason CLI
inside each Docker task; it does not copy your host CLI into the container.
-->

## Example: running DeepSWE

Download the [DeepSWE tasks](pier-deepswe/#dataset) and get your `REASON_API_KEY` from the [Reason Machines dashboard](https://reasonmachines.ai/customize?tab=api).

```bash
export REASON_API_KEY="<your-reason-api-key>"
pier run --path deep-swe/tasks \
  --agent-import-path reasonmachines_pier:ReasonAgent \
  --model openai/gpt-5.6-luna
```

`--agent-import-path reasonmachines_pier:ReasonAgent` loads the Reason adapter. Everything else uses standard [Pier options](https://github.com/datacurve-ai/pier#readme).

## Citation

Cite the upstream [DeepSWE](https://github.com/datacurve-ai/deep-swe) and
[Pier](https://github.com/datacurve-ai/pier) repositories alongside this example.

```bibtex
@misc{reasonmachines_examples,
  author = {{Reason Machines}},
  title = {Reason Machines Examples},
  year = {2026},
  howpublished = {\url{https://github.com/reason-machines/examples}}
}
```
