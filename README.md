> [!IMPORTANT]
> This project is in the process of being created.
> See it as version 0.1 currently.

# AI Research

This neat repository creates and analyzes an AI system architecture.
The goal is to learn capabilities of different AI architectural setups.

To be able to see differences in testing the setups, the architecture will
follow a modular structure with artefacts that can be exchanged easily and
parameterized where feasible - see below for a more detailed explanation.


## The artefacts

* **The intended task** of the AI system.
  Examples: Categorizing mail, searching for specific news in a domain,
  handling software development etc.
* **The prompt**. Changing the prompt is the most obvious way of testing
  the behaviour (output, time to process, ...) of an AI system.
  We will keep prompts in a collection that showed significant results in
  testing and give insight to the capabilities of an AI architecture.
* **The type of architecture**.
  Is it a local-only setup, do we have a setup with Google Vertex AI, do
  we use a hosted solution with an LLM like ChatGPT at OpenAI, do we choose
  to test a ready-to-use framework like Claude Flow etc.
* **The used AI components**, e.g. a dedicated LLM, ML models, ...
* **The used process**.
  How does the exact processing of information / data work?
  This artefact is strongly related to the intended task.
  E.g. when building an automated software development pipeline (the
  intended task), the used process will describe all steps in the software
  development pipeline that are automated by the AI system.
* **The behaviour**.
  This is the only resulting artefact - all the others will be created to
  build / define the AI system.
  The behaviour will be the artefact to be analyzed after the AI system has
  done a test run.
  Behaviours are output of the AI components, time needed to process a test
  run etc.
  The output itself can be categorized in additional levels, e.g. if the
  output is source code, you could have additional levels like which
  programming language has been used, which build system is used, which
  classes have been created, which technology is used for internal
  communication of software components, which libraries have been used etc.
