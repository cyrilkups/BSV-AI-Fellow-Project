# BAML Lightweight Diligence

## 1. Why I Chose BAML
"Most production AI failures are not only model failures. They are interface reliability failures between probabilistic LLM outputs and deterministic software systems."

That is why BAML stood out to me. It gives developers a structured way to define, call, and test LLM functions. It makes AI workflows feel closer to typed software interfaces, which matters because production AI systems need reliability, not just impressive demos.

## 2. Product Overview
BAML is a developer tool by BoundaryML. It is designed to help teams build more reliable LLM applications through structured outputs, prompt definitions, testing, and typed interfaces. The product is attractive because it tries to turn "prompt engineering" into something closer to normal engineering discipline.

The current Boundary documentation emphasizes a flow where developers define BAML functions, generate a typed `baml_client`, and test functions directly in the tooling. The docs also present testing as a first-class concept, which is a strong signal for a serious developer product.

## 3. Hands-On Testing
I built a small prototype called `Startup Signal Extractor`.

### Purpose
The prototype tests whether a typed extraction workflow can turn messy startup descriptions into structured diligence fields:
- company name
- website
- category
- target customer
- product summary
- AI-native score
- developer-tool relevance
- adoption friction
- likely buyer
- key risk
- diligence notes

### What I built
Inside `prototype/` I created:
- `main.py` to run the extraction pipeline
- `evaluator.py` to audit the outputs
- `core.py` for typed validation, extraction logic, and a raw baseline simulation
- labeled clean, messy, and adversarial input sets
- generated JSON outputs and an evaluation summary
- a draft `baml_src/startup_signal_extractor.baml` file showing how the task maps into real BAML syntax

### Setup and execution
I could not fully run live BAML in this workspace because `baml-py`, a generated `baml_client`, and live API credentials were not available locally. So I took the fallback path the assignment allowed: I implemented a BAML-inspired typed extraction flow that is fully runnable offline and documented the limitation clearly.

I then ran:

```bash
python3 main.py
python3 evaluator.py
python3 -m unittest discover -s tests
```

### What I tested
I used three test sets:
1. Clean inputs with well-formed blurbs
2. Messy inputs with vague or noisy descriptions
3. Adversarial inputs with conflicts, hype, or missing clarity

### What the outputs looked like
The structured path produced valid, schema-complete outputs on all 9 samples across repeated runs. The offline evaluator showed:
- `3/3` valid outputs on clean inputs
- `3/3` valid outputs on messy inputs
- `3/3` valid outputs on adversarial inputs

The simulated raw-output baseline was much weaker:
- clean inputs still showed parse and type drift
- messy inputs frequently lost required fields or broke types
- adversarial inputs regularly broke JSON shape or score ranges

That is not a real benchmark against a live model, but it is directionally useful. It gave me a concrete harness for thinking about what BAML is trying to solve.

### Screenshots to include
- terminal setup
- successful extraction output
- failure case from the raw baseline or adversarial set
- final evaluation summary

## 4. Technical Evaluation

### Ease of setup
Conceptually, BAML's setup is straightforward. The official docs clearly describe installing `baml-py`, running `baml-cli init`, generating a typed client, and then calling BAML functions from Python. That is a clean mental model.

The real question is less "can I install it?" and more "does this abstraction stay pleasant once a team has many prompts, schemas, and regressions to manage?" My prototype could not answer that fully because I did not run the live toolchain here.

### Documentation clarity
The docs are one of the product's strengths. They make the product legible quickly: define a function, generate a client, test it, switch models if needed. I especially liked that testing is treated as part of the normal workflow rather than an afterthought.

### Developer experience
The strongest part of the product story is that it reframes LLM calls as something closer to typed interfaces than raw prompt strings. That is a useful abstraction. It reduces prompt chaos and gives teams a cleaner surface for shared ownership.

### Schema reliability
This is where the product thesis is strongest. In my offline harness, the typed path stayed stable across clean, messy, and adversarial cases, while the simulated raw path drifted. That result came from my own structured validation layer, not BAML's runtime, but it still reflects why the category matters.

### Failure handling
BAML's value proposition is not "the model is now correct." It is "the interface is easier to constrain, inspect, and recover." That is the right framing. Even then, teams still need strong evals around hallucination, ambiguous inputs, and silent semantic errors.

### Testing experience
I like that BAML makes tests a first-class concept. That matters because prompt regressions are real, and teams need a way to save known cases and rerun them. For a serious AI developer tool, this is table stakes.

### Portability across models
The docs suggest a nice model-switching story, which is strategically valuable. If teams can keep their interface stable while changing models, that reduces lock-in and makes BAML more useful as an orchestration layer.

### Scalability considerations
The upside is that BAML can become a shared interface layer for AI application development. The risk is that abstraction layers can become harder to debug once prompts, schemas, retries, and model routing all interact. Prompt versioning, schema versioning, and surrounding evaluation infrastructure still matter a lot.

## 5. Strategic Insights

### Why now
AI applications are moving from demos to production systems. Once teams have real users and real workflows, they need reliability, structured outputs, and testability. That timing makes BAML more interesting today than it would have been in the earlier prompt-hacking phase.

### Target customers
The clearest customers are AI engineers, product engineers, infra teams, and developer tool teams shipping LLM-backed features. Startups building production AI workflows are the natural early adopter set.

### Differentiation
BAML is not just another prompt wrapper. The more interesting positioning is as an interface layer for LLM systems: define functions, enforce schemas, generate typed clients, and test the system in one place.

### Risks
- Model providers may improve native structured outputs enough to collapse part of the wedge.
- Open-source frameworks and SDKs will compete aggressively around developer mindshare.
- Some developers may resist learning a new syntax or toolchain layer.
- Reliability expectations are high, so failures will be judged harshly.

## 6. What I Would Do Next
- test the same datasets against live BAML and at least one raw-prompt baseline
- benchmark latency and cost, not just output shape
- add regression tests with more edge cases and harder labels
- compare against raw prompting, Instructor, LangChain, DSPy, and OpenAI structured outputs
- run the extractor on real customer support tickets, call notes, or founder blurbs
- understand whether teams adopt BAML for one narrow use case or across the whole AI workflow

## 7. Final Take
BAML is promising because it sits close to a painful and growing problem: making LLM behavior usable inside normal software systems. I would prioritize deeper diligence because the product is technical, timely, and has a credible path to becoming part of the AI application development workflow.

My current view is positive but not naive. The product makes sense, the documentation is thoughtful, and the category is real. The real diligence question is whether BAML becomes a durable interface layer teams standardize around, or whether some of its value gets absorbed by model vendors and adjacent frameworks over time.
