> [!IMPORTANT]
> This project is in the process of being created.
> See it as version 0.1 currently.

# AI Research

This neat repository creates and analyzes an AI system architecture.
The goal is to learn capabilities of different AI architectural setups.

To be able to see differences in testing the setups, the architecture will
follow a modular structure with artefacts that can be exchanged easily and
parameterized where feasible - see below for a more detailed explanation.


## High-level goals

In **short-term**, we will have a repository that explains the differences when
using dedicated artefacts (AI components, prompts etc) for chosen tasks.
This way, you can get an idea about which artefacts to use in which use cases.

In **middle-term**, we should get a system that allows you to
configure a complex system of AI components and software-architectural
artefacts that can be used to get early information about the suitability of
architectural choices for your dedicated project.

In **long-term**, this can be extended to a deployment machine based on your
architectural configuration.


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


## The notation of information

How can we best represent the different options and alternatives of artefact
combinations in this repository?
How can we give a nice overview about our findings when comparing dedicated
architectural choices? Here are a few complementary approaches.

As we have a rather complex and more-dimensional combination of potential
choices, this could get overwhelming.
A combination of structured data, clear organization and effective
visualization is the best way to manage this complexity.


### 1. Structured notation and organization

* **YAML for configuration**: Each experimental run can be defined in a structured `YAML` file. This makes the setup explicit, version-controllable, and machine-readable.
* **Directory structure**: Organize results in a logical folder hierarchy based on the artefacts. For example: `/results/<task>/<architecture>/<components>/results.md`.
* **Markdown tables for summaries**: Use tables in result files for a quick, high-level comparison of key outcomes.

| Task                  | Architecture | LLM         | Prompt    | Avg. Time (s) | Accuracy |
| --------------------- | ------------ | ----------- | --------- | ------------- | -------- |
| Email Categorization  | Vertex AI    | Gemini 1.0  | `prompt1` | 1.2           | 98%      |
| Email Categorization  | Local        | Llama 3 8B  | `prompt1` | 3.5           | 95%      |
| ...                   | ...          | ...         | ...       | ...           | ...      |

#### Folder example

/experiments
|
└───/email_categorization
|   |
|   └───/vertex_ai_gemini_pro
|   |   |   prompt_v1.txt
|   |   |   results.md  <-- Contains detailed analysis and tables
|   |   |   run_data.json
|   |
|   └───/local_llama3
|       |   prompt_v1.txt
|       |   prompt_v2.txt
|       |   results.md
|       |   run_data.json
|
└───/code_generation
    |
    └───/...

#### YAML example

experiment_id: 001
task: "Categorizing support emails"
architecture: "Local-only with Ollama"
components:
  - name: "LLM"
    type: "Llama3-8B-Instruct"
prompt: "prompt_categorize_v1.txt"
process: "Single-pass classification"
# --- Results ---
behavior:
  output_quality: "High accuracy on test set (95%)"
  metrics:
    processing_time_seconds: 2.5
    cost: 0.0


### 2. Visualization techniques

Visuals are crucial for understanding trade-offs and patterns across many dimensions.

* **Radar charts**: To compare multiple quantitative metrics (e.g., cost, speed, output quality) across different setups. This gives a fast visual summary of the strengths and weaknesses of each architectural choice.
* **Heatmaps**: Useful for visualizing the performance of two-dimensional combinations (e.g., `Model` vs. `Prompt`) against a single metric (like accuracy). This can quickly reveal "hotspots" of high performance.
* **Parallel coordinates plots**: A more advanced method for visualizing high-dimensional data. Each experiment is represented as a line weaving through parallel axes that represent artefacts and metrics. This can help identify correlations and clusters in the results.

### 3. Interactive exploration

As the number of experiments grows, static reports can become insufficient.
An interactive dashboard could the way to go.

Users could:

*   **Filter** results based on artefacts (e.g., show only local models).
*   **Sort** by performance metrics.
*   **Dynamically generate** visualizations for the selected data.

This approach then turns this repository from static reporting into dynamic
architectural exploration.