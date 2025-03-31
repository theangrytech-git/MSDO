*******************************************************************************<br>
<br>
<b>PROJECT NAME:&emsp;&emsp;&emsp;&emsp;&nbsp;MSDO Central Repo<br>
CREATED BY:&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;THEANGRYTECH-GIT<br>
REPO:&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;[([MSDO Repo](https://github.com/theangrytech-git/MSDO))]<br><br>
DESCRIPTION:</b>&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;This repository centrally <br>manages reusable GitHub Action workflows for secure DevOps pipelines <br>using Microsoft Security DevOps (MSDO), Gitleaks, Trufflehog,<br>
Credscan, and SARIF reporting.

It is designed for organizations with restricted environments and **does not <br>rely on any external GitHub Actions**.<br>
<br>
*******************************************************************************<br>
<br>
<b>FEATURES</b><br>
<br>
- 🔍 Microsoft Security DevOps (MSDO) scanning  <br>
- Tools like `ESLint`, `Bandit`, `Binskim`, `Checkov`, `Credscan`, `Templateanalyzer`, `Terrascan`, `Trivvy`, etc<br>
- 🔐 Secret scanning<br>
  - `Credscan` for code-level secrets<br>
  - `Trufflehog` for detecting API keys, passwords, and other sensitive data in source code using entropy and regex-based rules<br>
  - `Gitleaks` for Git history, tokens, config, and sensitive patterns<br>
- 📦 Custom SARIF uploader (no marketplace action)<br>
- 🌐 Defender for Cloud integration supported<br>
- 🚫 No external marketplace dependencies — fully self-contained<br>
<br>

*******************************************************************************
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;GETTING STARTED GUIDE
*******************************************************************************
<b>Use this section to clone or fork this repo and configure GitHub Security <br>
DevOps scanning tools (MSDO) in your own environment.</b><br>
<br>
<b>HOW TO SET UP:</b><br>
<br>
<ol>
  <li><strong>Create a Central MSDO Security Repo:</strong><br>
    Create a new repository in your org called <code>MSDO-Security</code> (or a name of your choosing),<br>and copy these files from this repository:
    <ul>
      <li><code>.github/workflows/msdo-main-pipeline.yml</code></li>
      <li><code>.github/workflows/msdo-dynamic-scanning.yml</code></li>
      <li><code>.github/workflows/msdo-credscan.yml</code></li>
      <li><code>.github/workflows/msdo-gitleaks.yml</code></li>
      <li><code>.github/workflows/msdo-trufflehog.yml</code></li>
      <li><code>.github/actions/upload-sarif/ ← composite action for native SARIF upload</code></li>
      <li><code>gitleaks.toml ← centralized scanning config </code></li>
    </ul>
  </li><br>
  <li><strong>Add a GH_TOKEN secret (if needed):</strong><br>
    Navigate to <em>Settings → Secrets and variables → Actions</em> in the central repo and add:
    <table border="1" cellpadding="5">
      <tr><th>Name</th><th>Description</th></tr>
      <tr><td>GH_TOKEN</td><td>GitHub PAT with <code>repo</code> permissions (optional; usually <code>${{ secrets.GITHUB_TOKEN }}</code> is sufficient)</td></tr>
    </table>
  </li><br>
  <li><strong>In each repo you want to scan:</strong>
    <ul>
      <li>Create a new file: <code>.github/workflows/msdo-repo-pipeline.yml</code></li>
      <li>Create a Workflow Action called <code>msdo-repo-pipeline.yml</code></li>
      <li>Copy and paste the <code>msdo-repo-pipeline.yml</code> into your newly created workflow</li>
      <li>This should trigger and run - review pipeline to confirm that it runs and completes</li>
    </ul>

---<br>
<br>
<b>INCLUDED WORKFLOWS:</b><br>
<table border="1" cellpadding="5">
  <tr><th>Workflow Name</th><th>Purpose</th></tr>
  <tr><td><code>msdo-main-pipeline.yml</code></td><td>Orchestrates all security scans + uploads</td></tr>
  <tr><td><code>msdo-dynamic-scanning.yml</code></td><td>Performs MSDO scans on infra/code/containers</td></tr>
  <tr><td><code>msdo-credscan.yml</code></td><td>Runs <code>credscan</code> with <code>.gdnsettings</code> config for secret detection</td></tr>
  <tr><td><code>msdo-trufflehog.yml</code></td><td>Runs <code>Trufflehog</code> to detect passwords and secrets using entropy and regex-based rules</td></tr>
  <tr><td><code>msdo-gitleaks.yml</code></td><td>Git-aware secret scanning using Gitleaks</td></tr>
  <tr><td><code>upload-sarif action</code></td><td>Composite action to upload SARIF locally</td></tr>
  <tr><td><code>gitleaks.toml</code></td><td>Custom rule config for Gitleaks</td></tr>
  <tr><td><code>msdo-repo-pipeline.yml</code></td><td>To be added into each Repo you want to scan as a Workflow Action</td></tr>
</table>
---<br>
<br>
<b>HOW TO RUN:</b><br>
<br>
- Triggers automatically on push/commit to <code>main</code> within the Repo<br>
- Or run manually via <strong>Actions</strong> tab → Select workflow → Click <strong>Run workflow</strong><br>
<br>
---<br>
<br>
<b>SYSTEM REQUIREMENTS:</b><br>
<br>
- Runner: <code>ubuntu-latest</code><br>
- .NET 6 SDK is installed via script in workflow<br>
- <code>gh</code> CLI is available by default on GitHub-hosted runners<br>
- Gitleaks downloaded and run as part of pipeline<br>
- No GitHub Marketplace dependencies required
<br>
---<br>
<br>
<b>OUTPUT:</b><br>
<br>
- Results are uploaded to <strong>GitHub Code Scanning Alerts</strong><br>
- Optionally ingested into <strong>Microsoft Defender for Cloud if configured</strong><br>
<br>
---<br>
<br>
<b>NEED HELP?</b><br>
<br>
Open an issue or contact [@theangrytech-git](https://github.com/theangrytech-git)<br><br>
*******************************************************************************<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;RESOURCE VISUALISATION<br>
*******************************************************************************<br>
*******************************************************************************<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;HIGH LEVEL DESIGN<br>
*******************************************************************************<br>
This section will be used to insert a High-Level Design to give an<br>
impression of how this solution is made up.<br>
*******************************************************************************<br>
<br>
![Screenshot of HLD Design.](insert the link here)<br>
<br>
*******************************************************************************<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;LOWER LEVEL DESIGN<br>
********************************************************************************<br>
Notes: This section will be used to insert Low-Level Design to give a detailed<br>
map of how this solution is made up.<br>
*******************************************************************************<br>
<br>
![Screenshot of HLD Design.](insert the link here)<br>
<br>
*******************************************************************************<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;ESTIMATE COSTS (£)<br>
*******************************************************************************<br>
Daily: £0.00<br>
Weekly: £0.00<br>
Monthly: £0.00<br>
Yearly: £0.00<br>
<br>
*******************************************************************************<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Roadmap (Planned)<br>
*******************************************************************************<br>
<br>
Add Slack/MS Teams alerting<br>
<br>
Upload SARIF as downloadable artifacts<br>
<br>
Add cloud cost scanning support<br>
<br>
Add GitHub Enterprise integration templates<br>
<br>

