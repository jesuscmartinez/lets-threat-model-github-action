# 🚀 Lets Threat Model Core GitHub Action

<!-- [![GitHub Marketplace](https://img.shields.io/badge/GitHub-Marketplace-blue?logo=github)](https://github.com/jesuscmartinez/lets-threat-model-core-action)
[![License](https://img.shields.io/github/license/jesuscmartinez/lets-threat-model-demo)](LICENSE) -->

Agentic AI threat modeling using the lets-threat-model-core Docker container. This action produces Markdown, optional JSON, and SARIF reports—seamlessly integrating security assessments into your CI/CD pipeline and supporting GitHub Code Scanning.

---

## ✨ Features

- 📦 Runs the [`lets-threat-model-core`](https://github.com/jesuscmartinez/lets-threat-model-core) Docker container.
- ✅ Generates **Markdown reports** of your threat models.
- 📝 Optionally outputs **JSON or SARIF** versions of your threat models.
- 🔐 Securely integrates with GitHub and OpenAI using environment variables.

---

## 📂 Inputs

| Name               | Description                                                    | Required | Default                     |
|--------------------|----------------------------------------------------------------|----------|-----------------------------|
| `config`           | Path to your YAML config file (must be checked out in the repo). | ✅ Yes  |                            |
| `markdown-output`  | Output path for the Markdown report.                           | ❌ No     | `threat_model_report.md`   |
| `json-output`      | Output path for the JSON report.                               | ❌ No     | `threat_model_report.json` |
| `sarif-output`     | Output path for the SARIF report.                              | ❌ No     | `threat_model_report.sarif`|
| `github-username`  | GitHub username for authenticated operations. (Required for remote repos) | ❌ No     |                 |
| `github-pat`       | GitHub Personal Access Token (keep secret!). (Required for remote repos)  | ❌ No     |                 |
| `openai-api-key`   | OpenAI API Key (keep secret!).                                 | ✅ Yes    |                            |
| `log-level`        | Log level (`DEBUG`, `INFO`, etc.).                             | ❌ No     | `INFO`                     |

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
        uses: jesuscmartinez/lets-threat-model-github-action@main
        with:
          config: config/my-config.yaml
          openai-api-key: ${{ secrets.OPENAI_API_KEY }}
          markdown-output: threat_model_report.md
          json-output: threat_model_report.json
          sarif-output: threat_model_report.sarif
```

### 📌 Demo Workflow Example

A working demo is available in the [`lets-threat-model-demo`](https://github.com/jesuscmartinez/lets-threat-model-demo) repository.

You can see it in action via the [GitHub Actions workflow](https://github.com/jesuscmartinez/lets-threat-model-demo/actions/workflows/lets_threat_model.yml):

