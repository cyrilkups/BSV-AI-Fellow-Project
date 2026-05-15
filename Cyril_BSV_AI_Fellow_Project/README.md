# BSV AI Fellow Written Project - Cyril Ofori Kupualor

## Overview
This submission includes:
1. Prioritization framework
2. Lightweight diligence on BAML
3. LLM conversation transcript
4. Hands-on prototype artifacts

## Why BAML
I chose BAML because it sits on a painful part of the production AI stack. The interesting question is not whether models can sometimes answer correctly. It is whether developers can make probabilistic model behavior dependable inside deterministic software systems. BAML is compelling because it treats that problem like an interface and tooling problem, not just a prompting problem.

## Prototype
The prototype is called `Startup Signal Extractor`. It tests a BAML-inspired typed extraction workflow against clean, messy, and adversarial startup descriptions and returns structured diligence fields.

Because this workspace did not have live API credentials or `baml-py` installed, I implemented a fully runnable offline version with:
- typed schema validation
- repeated-run consistency checks
- a simulated raw-output baseline that intentionally drifts
- evaluation artifacts written to `prototype/outputs/`

I also included an optional real BAML sketch in `prototype/baml_src/` based on the current Boundary documentation.

## How to Run
From `prototype/`:

```bash
pip install -r requirements.txt
python3 main.py
python3 evaluator.py
python3 -m unittest discover -s tests
```

From the project root, you can generate the export PDFs with:

```bash
python3 export_pdfs.py
```

## Outputs
The main artifacts live here:
- `1_Prioritization_Framework.md`
- `2_BAML_Lightweight_Diligence.md`
- `3_LLM_Conversation_Transcript.md`
- `prototype/outputs/clean_run_output.json`
- `prototype/outputs/messy_run_output.json`
- `prototype/outputs/adversarial_run_output.json`
- `prototype/outputs/evaluation_summary.md`
- `final_exports/`

## Notes
The goal here is not production-grade extraction software. The goal is to test developer experience, structured output reliability, and product judgment under mild ambiguity.
