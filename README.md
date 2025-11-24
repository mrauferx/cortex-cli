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
  * On every commit to the **main branch**, **Actions** will run the pipeline
  * Please make sure an active **Prevention** policy is present at **Cortex Cloud > Posture Management > Rules & Policies > Vulnerability     Management > Vulnerability Policies - Prevention**

  <img width="893" height="640" alt="Screenshot 2025-11-24 at 3 26 17 PM" src="https://github.com/user-attachments/assets/525f8717-08b1-4b57-bae7-baa72ed70f11" />

  <img width="924" height="569" alt="Screenshot 2025-11-24 at 3 26 28 PM" src="https://github.com/user-attachments/assets/fd1109a4-53d7-4a52-ace6-3df2e0ae825a" />

  <img width="916" height="786" alt="Screenshot 2025-11-24 at 3 26 38 PM" src="https://github.com/user-attachments/assets/9f7ac4d4-375a-4b8a-bd4c-702e101d8063" />

  
Once the above steps are completed, the output under the Actions tab for the **Cortex CLI execution** to find the results of the scan displayed as a table.

<img width="1048" height="352" alt="Screenshot 2025-11-24 at 3 21 56 PM" src="https://github.com/user-attachments/assets/b83d54fd-80d0-4025-9f36-90f139294ae0" />

The results can be found under All Assets > Container Images (filter by image name or image id):

<img width="897" height="447" alt="Screenshot 2025-11-24 at 4 23 29 PM" src="https://github.com/user-attachments/assets/831ac189-e5ed-4a5f-bcc6-e35d2485ce5c" />



The same setup can be used for [Cortex CLI SBOM](https://docs-cortex.paloaltonetworks.com/r/Cortex-CLOUD/Cortex-Cloud-Runtime-Security-Documentation/Cortex-CLI-for-Cloud-Workload-Protection) scan too with slight modification/updating the deployment YAML file. (blank.yml)
