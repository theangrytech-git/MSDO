*******************************************************************************<br>
<br>
<b>PROJECT NAME:&emsp;&emsp;&emsp;&emsp;&nbsp;MSDO Central Repo<br>
CREATED BY:&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;THEANGRYTECH-GIT<br>
REPO:&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;[([link to repo](https://github.com/theangrytech-git/MSDO))]<br><br>
DESCRIPTION:</b>&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;This repo will be used as a central repo for <bR>setting up security scanning in other repos<br>
<br>
*******************************************************************************<br>
<br>
<br>

*******************************************************************************
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;GETTING STARTED GUIDE
*******************************************************************************
<b>Use this section to clone or fork this repo and configure GitHub Security <br>
DevOps scanning tools (MSDO) in your own environment.</b><br>
<br>
-Built with no external GitHub Actions — works in restricted org environments <br>
-Includes secret scanning, SARIF upload, and Defender for Cloud integration<br>
<br>
---<br>
<br>
<b>WHAT'S INCLUDED:</b><br>
- Microsoft Security DevOps scanning (`credscan`, `binskim`, `checkov`, etc.)<br>
- Secret scanning using `credscan`<br>
- Self-hosted SARIF uploader (composite GitHub Action)<br>
- Manual .NET 6 install (no external dependencies)<br>
- Fully functional SARIF upload to GitHub Code Scanning<br>
<br>
---<br>
<br>
<b>HOW TO SET UP:</b><br>
<br>
<b>1. Fork the repository</b>  <br>
> [Click here to fork](https://github.com/theangrytech-git/MSDO/fork)<br>
<br>
<b>2. Add a `GH_TOKEN` secret:</b>  <br>
Go to **Settings → Secrets and variables → Actions**, then add:<br>
<br>
| Name      | Description                        |<br>
|-----------|------------------------------------|<br>
| GH_TOKEN  | GitHub PAT with `repo` permissions (optional, usually not needed if using `${{ secrets.GITHUB_TOKEN }}`) |<br>
<br>
---<br>
<br>
<b>INCLUDED WORKFLOWS:</b><br>
<br>
| Workflow Name           | Purpose                                       |<br>
|-------------------------|-----------------------------------------------|<br>
| `msdo-main-pipeline.yml`    | Orchestrates all security scans + uploads   |<br>
| `msdo-reusable.yml`         | Performs MSDO scans on infra/code/containers |<br>
| `msdo-secret-scanning.yml`  | Runs `credscan` for secret detection         |<br>
| `.github/actions/upload-sarif/` | Composite action to upload SARIF locally |<br>
<br>
---<br>
<br>
<b>HOW TO RUN:</b><br>
<br>
- Trigger automatically on push to `main`<br>
- Or manually from the **Actions** tab → Select **workflow** → Click **Run workflow**<br>
<br>
---<br>
<br>
<b>SYSTEM REQUIREMENTS:</b><br>
<br>
- Runner: `ubuntu-latest`<br>
- .NET 6 SDK is installed via script in workflow<br>
- `gh` CLI is already available on GitHub-hosted runners<br>
<br>
---<br>
<br>
<b>OUTPUT:</b><br>
<br>
- Results are uploaded to **GitHub Code Scanning Alerts**<br>
- Optionally ingested into **Microsoft Defender for Cloud**<br>
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

