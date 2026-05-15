You are helping me complete the BSV AI Fellow Written Project.

The assignment asks for:
1. A prioritization framework ranking a list of early-stage startups.
2. Lightweight diligence and hands-on testing for one selected company.
3. A shared LLM conversation showing how I explored, tested, critiqued, and reasoned through the product.

I want to choose Track 1: Developer Tools.
My top company is BAML by BoundaryML.

Core thesis:
“Most production AI failures are not only model failures. They are interface reliability failures between probabilistic LLM outputs and deterministic software systems. BAML is interesting because it tries to make LLM calls feel more like strongly typed software interfaces.”

Your job is to help me create a complete submission package with code, written reports, screenshots, diagrams, and a README.

Create this folder structure:

Cyril_BSV_AI_Fellow_Project/
├── README.md
├── 1_Prioritization_Framework.md
├── 2_BAML_Lightweight_Diligence.md
├── 3_LLM_Conversation_Transcript.md
├── prototype/
│   ├── README.md
│   ├── requirements.txt
│   ├── .env.example
│   ├── input_examples/
│   │   ├── clean_startup_descriptions.json
│   │   ├── messy_startup_descriptions.json
│   │   └── adversarial_startup_descriptions.json
│   ├── outputs/
│   │   ├── clean_run_output.json
│   │   ├── messy_run_output.json
│   │   ├── adversarial_run_output.json
│   │   └── evaluation_summary.md
│   ├── screenshots/
│   │   ├── setup_terminal.png
│   │   ├── successful_extraction.png
│   │   ├── failure_case.png
│   │   └── final_output.png
│   ├── diagrams/
│   │   ├── architecture_diagram.md
│   │   └── workflow_diagram.md
│   ├── main.py
│   ├── evaluator.py
│   └── notes.md
└── final_exports/
    ├── Prioritization_Framework.pdf
    ├── BAML_Lightweight_Diligence.pdf
    └── LLM_Conversation.pdf

Build a small prototype called “Startup Signal Extractor.”

Prototype goal:
Use BAML or a BAML-inspired structured extraction workflow to parse messy startup descriptions and return structured JSON with:
- company_name
- website
- category
- target_customer
- product_summary
- ai_native_score from 1 to 5
- developer_tool_relevance from 1 to 5
- adoption_friction from 1 to 5
- likely_buyer
- key_risk
- diligence_notes

The prototype should test whether structured LLM interfaces improve reliability when extracting investment-relevant startup data from messy text.

Use Python unless BAML requires another setup.
If actual BAML setup is possible, use real BAML.
If setup is blocked by environment/API limitations, clearly document that and implement a BAML-inspired typed extraction flow using Pydantic models and an LLM API placeholder.

The prototype should include three test sets:
1. Clean inputs:
   Well-written startup blurbs.
2. Messy inputs:
   Incomplete, vague, noisy, poorly formatted startup descriptions.
3. Adversarial inputs:
   Conflicting claims, missing company names, exaggerated AI language, malformed formatting.

The evaluator should check:
- valid JSON returned
- required fields present
- type correctness
- hallucinated fields
- consistency across repeated runs
- usefulness of diligence notes

Create an evaluation_summary.md with a small table:
| Test Type | Inputs Tested | Valid Outputs | Common Failures | Notes |
|---|---:|---:|---|---|

Also include qualitative observations:
- What worked well
- What broke
- What surprised me
- What I would improve with more time

Now create the written deliverables.

Deliverable 1: 1_Prioritization_Framework.md

Use this structure:

Title: Prioritization Framework

Opening paragraph:
Explain that I ranked the companies based on where I saw the strongest combination of painful developer workflow, AI-native timing, infrastructure potential, adoption path, and defensibility.

Criteria:
1. Severity of pain
2. AI-native urgency
3. Technical leverage
4. Workflow embedding
5. Adoption friction
6. Defensibility
7. Fit with BSV’s thesis around AI improving productivity

Ranked list:
1. BAML
2. Mem0
3. Tigris Data
4. Parasail
5. Atuin
6. Primitive
7. Rasa
8. Entire

For each company, write 2 to 4 sentences explaining the ranking.

Tone:
Concise, sharp, human, investor-like.
Avoid generic AI buzzwords.
Do not sound like a Wikipedia summary.
Show judgment.

BAML rationale:
Emphasize typed LLM interfaces, reliability, schema enforcement, and production AI workflows.

Mem0 rationale:
Memory infrastructure is important as agents become more persistent, but the space could become crowded and platform-dependent.

Tigris rationale:
Object storage and data infra are useful, especially for AI workloads, but may face strong incumbent pressure.

Parasail rationale:
Interesting AI infrastructure angle, especially around compute, but diligence would depend on adoption, margins, and differentiation.

Atuin rationale:
Strong developer love and workflow embedding, but may be narrower or harder to scale into a venture-scale platform.

Primitive rationale:
Potentially interesting if it changes how developers understand codebases, but needs proof of repeated workflow use.

Rasa rationale:
Known conversational AI platform with enterprise relevance, but may feel less early and less aligned with the newest AI-native developer workflow shift.

Entire rationale:
Rank lower if product clarity or developer-tool relevance is less obvious from public materials.

Deliverable 2: 2_BAML_Lightweight_Diligence.md

Use this structure:

Title: BAML Lightweight Diligence

Sections:

1. Why I Chose BAML
Include my thesis:
“Most production AI failures are not only model failures. They are interface reliability failures between probabilistic LLM outputs and deterministic software systems.”

Explain why BAML is interesting:
- It gives developers a structured way to define, call, and test LLM functions.
- It makes AI workflows feel closer to typed software interfaces.
- It is useful because production AI systems need reliability, not just impressive demos.

2. Product Overview
Briefly describe BAML:
- Developer tool by BoundaryML.
- Helps teams build more reliable LLM applications.
- Focuses on structured outputs, prompts, testing, and typed interfaces.

3. Hands-On Testing
Explain the prototype I built:
“Startup Signal Extractor”
Purpose:
Use BAML or BAML-inspired typed extraction to turn messy startup descriptions into structured diligence fields.

Include:
- setup steps
- what files were created
- how inputs were tested
- what outputs looked like
- screenshots to include
- mention clean, messy, and adversarial inputs

4. Technical Evaluation
Evaluate:
- ease of setup
- documentation clarity
- developer experience
- schema reliability
- failure handling
- testing experience
- portability across models
- scalability considerations

Include balanced critique:
- Strong abstraction for typed LLM calls
- Useful for reducing prompt chaos
- Still needs strong evals around hallucination and edge cases
- Debugging abstraction layers can become challenging
- Versioning prompts and schemas is important
- Reliability depends on surrounding evaluation infrastructure

5. Strategic Insights
Discuss:
- Why now:
  AI apps are moving from demos to production.
  Teams need reliability, structured outputs, and testability.
- Target customers:
  AI engineers, product engineers, infra teams, developer tool teams, startups building LLM features.
- Differentiation:
  BAML is not just another prompt wrapper. It is closer to an interface layer for LLM systems.
- Risks:
  model providers may add better native structured outputs
  open-source frameworks may compete
  developers may resist new syntax/tooling
  reliability expectations are high

6. What I Would Do Next
Include:
- test against more models
- benchmark latency and cost
- add regression tests
- compare against raw prompting, instructor, LangChain, DSPy, and OpenAI structured outputs
- test with real customer support tickets or sales call notes
- evaluate team workflow fit

7. Final Take
Write a strong but balanced conclusion:
BAML is promising because it sits close to a painful and growing problem: making LLM behavior usable inside normal software systems. I would prioritize deeper diligence because the product is technical, timely, and has potential to become part of the AI application development workflow.

Deliverable 3: 3_LLM_Conversation_Transcript.md

Create a realistic transcript showing my process with an AI assistant.

Important:
Do NOT make it look like I asked the AI to simply write the project.
The transcript should show thinking, testing, and iteration.

Structure:
- Initial hypothesis
- Choosing between BAML, Mem0, and Tigris
- Designing the prototype
- Asking the AI to challenge the thesis
- Asking for failure modes
- Debugging schema issues
- Improving the evaluator
- Reflecting on what broke
- Final synthesis

Example prompts from me:
1. “I am evaluating BAML as a developer tool. What would make this company venture-scale versus just a useful open-source utility?”
2. “Challenge my thesis that typed LLM interfaces will matter long term.”
3. “Design a small hands-on test that reveals whether BAML improves reliability over raw prompting.”
4. “Here is a malformed startup description. What failure modes should I expect?”
5. “How should I evaluate structured output quality beyond just valid JSON?”
6. “What would a skeptical investor ask about this product?”
7. “Rewrite my conclusion so it sounds like my judgment, not a generic company summary.”

The transcript should include places where I push back on the AI.
Make it clear I am making decisions, not outsourcing judgment.

README.md

Create a clean README explaining:
- what the project is
- why I chose BAML
- how the prototype works
- how to run it
- what files matter
- what artifacts are included

README structure:
# BSV AI Fellow Written Project — Cyril Ofori Kupualor

## Overview
This submission includes:
1. Prioritization framework
2. Lightweight diligence on BAML
3. LLM conversation transcript
4. Hands-on prototype artifacts

## Why BAML
Brief thesis.

## Prototype
Explain Startup Signal Extractor.

## How to Run
Use:
pip install -r requirements.txt
python main.py
python evaluator.py

## Outputs
Explain where outputs are stored.

## Notes
Mention that the goal is not production-grade software. The goal is to test developer experience, structured output reliability, and product intuition.

Diagrams:

Create two Mermaid diagrams in markdown.

1. Architecture diagram:
Input startup descriptions → BAML/typed extraction layer → LLM call → structured JSON → evaluator → diligence summary

2. Workflow diagram:
Select company → form thesis → build prototype → test clean inputs → test messy inputs → test adversarial inputs → evaluate failures → write diligence

Screenshots:
Since you cannot generate screenshots directly unless code is run, add placeholders in the screenshots folder and write a note telling me exactly what screenshots I should capture:
- terminal setup
- successful extraction output
- failed or messy extraction case
- evaluation summary
- code structure in VS Code

Writing style:
- Human
- Sharp
- Specific
- No fluff
- No generic AI hype
- No em dashes
- Avoid phrases like “AI is revolutionizing”
- Use confident but balanced judgment
- Make it sound like a technical builder with investor instincts

Final instruction:
After creating files, tell me:
1. What has been created
2. What I still need to manually run
3. What screenshots I need to capture
4. What PDFs I need to export
5. What to submit finally