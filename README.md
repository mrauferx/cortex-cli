# Cortex CLI image scan

### Steps: 
* Clone this repository.
* Add the Dockerfile of the image that needs to be built and scanned.
* Create a basic Github Actions workflow. (already created in this repository, the comments added in the blank.yml file explain the structure of the file)
* Add the required steps in the **.github/workflows/blank.yml** file in order to orchestrate GitHub Actions workflow:
  * **actions/checkout@v4** step checks out the repository under $GITHUB_WORKSPACE, so the job can access it.
  * Build the Docker image using the Dockerfile
  * Download [Cortex CLI dependencies](https://docs-cortex.paloaltonetworks.com/r/Cortex-Cloud-Posture-Management/Code-Security/Connect-Cortex-CLI) based on the OS of the machine (The current job **runs-on** `ubuntu:latest`)
  * Ensure the **URL**, **API key**, **API ID** are added as environment variables post storing them as Secrets (**Settings > Secrets and variables > Actions > New repository secret**)
  * The **image name** should be set before defining **steps** as best practice
  * Add the **Cortex CLI install** command as a step (Copy it from the Cortex Console data sources page)
  * Add the **Cortex CLI image scan** as another step
 
Once the above steps are completed, the output under the Actions tab for the **Cortex CLI execution** to find the results of the scan displayed as a table.

<img width="914" height="256" alt="Screenshot 2025-11-22 at 12 12 55 AM" src="https://github.com/user-attachments/assets/2d72242a-f53f-4640-9d2f-fe5468f2b18d" />



The same setup can be used for [Cortex CLI SBOM](https://docs-cortex.paloaltonetworks.com/r/Cortex-CLOUD/Cortex-Cloud-Runtime-Security-Documentation/Cortex-CLI-for-Cloud-Workload-Protection) scan too with slight modification/updating the deployment YAML file. (blank.yml)
