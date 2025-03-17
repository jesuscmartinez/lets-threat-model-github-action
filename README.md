# 🚀 Lets Threat Model Core GitHub Action

<!-- [![GitHub Marketplace](https://img.shields.io/badge/GitHub-Marketplace-blue?logo=github)](https://github.com/jesuscmartinez/lets-threat-model-core-action)
[![License](https://img.shields.io/github/license/jesuscmartinez/lets-threat-model-demo)](LICENSE) -->

Generate **Threat Models** from YAML configurations using the `lets-threat-model-core` Docker container.  
This GitHub Action helps automate the process of generating Markdown and optional JSON reports for your applications' threat models.

---

## ✨ Features

- 📦 Runs the [`lets-threat-model-core`](https://github.com/jesuscmartinez/lets-threat-model-core) Docker container.
- ✅ Generates **Markdown reports** of your threat models.
- 📝 Optionally outputs **JSON** versions of your threat models.
- 🔐 Securely integrates with GitHub and OpenAI using environment variables.

---

## 📂 Inputs

| Name               | Description                                                    | Required | Default                   |
|--------------------|----------------------------------------------------------------|----------|---------------------------|
| `config`           | Path to your YAML config file (must be checked out in the repo). | ✅ Yes    |                           |
| `output-markdown`  | Output path for the Markdown report.                           | ❌ No     | `threat_model_report.md`  |
| `output-json`      | Output path for the JSON report.                               | ❌ No     | `threat_model_report.json`|
| `github-username`  | GitHub username for authenticated operations.                  | ❌ No     |                           |
| `github-pat`       | GitHub Personal Access Token (keep secret!).                   | ❌ No     |                           |
| `openai-api-key`   | OpenAI API Key (keep secret!).                                 | ✅ Yes    |                           |
| `log-level`        | Log level (`DEBUG`, `INFO`, etc.).                             | ❌ No     | `INFO`                   |

---

## 🔧 Usage

### Basic Example (Minimal Inputs)
```yaml
name: Generate Threat Model

on:
  workflow_dispatch:

jobs:
  generate-threat-model:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Generate Threat Model
        uses: jesuscmartinez/lets-threat-model-core-action@v1
        with:
          config: config/my-config.yaml
          openai-api-key: ${{ secrets.OPENAI_API_KEY }}