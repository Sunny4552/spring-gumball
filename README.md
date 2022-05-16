# spring-gumball

---------------------------------------
## ---- CI Workflow (Part 1) -------
---------------------------------------

1. Make a spring-gumball repository, go to the Actions tab, and then Create a New Workflow

2. Add starter code provided for the lab and also the GitHub Actions file

<img width="1512" alt="Screen Shot 2022-05-15 at 11 22 04 PM" src="https://user-images.githubusercontent.com/54876893/168531401-9678c442-a0c7-493a-91c1-1584e9f3e2f0.png">

3. After doing commits, see the Github Actions tab to see the status.

<img width="1512" alt="Screen Shot 2022-05-11 at 11 06 10 PM" src="https://user-images.githubusercontent.com/54876893/168509208-41a9f2f7-79ed-4dbb-9d46-b296af9f4de7.png">

### Errors I ran into in the Actions Tab:
> Error - `./gradlew: Permission denied`
> 
> Solution - add 
> **'- name: Change wrapper permissions
     run: chmod +x ./gradlew'**
>
> Resource - https://stackoverflow.com/questions/58282791/why-when-i-use-github-actions-ci-for-a-gradle-project-i-face-gradlew-permiss
     

---------------------------------------
## ---- CI Workflow (Part 2) -------
---------------------------------------

1. Create kustomization.yaml, deployment.yaml, and service.yaml files 

2. Go to IAM & Admin/Service Accounts, and make a new one called spring-gumball and set it as an Owner. Then select 'Add Key' > 'Create New Key' > 'JSON'. The json file will be downloaded.

<img width="1512" alt="Screen Shot 2022-05-15 at 11 01 06 PM" src="https://user-images.githubusercontent.com/54876893/168528838-953c3f6a-5a70-4217-9290-1b0145135364.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 7 32 06 PM" src="https://user-images.githubusercontent.com/54876893/168528860-b60d44f6-6c61-438e-88dd-57531d5b9344.png">


3. In the spring-gumball repository, Go to Settings > Secrets, and add secrets GKE_PROJECT with the project ID found in GCP Dashboard page and GKE_SA_KEY with the generated json file for creating the key.

<img width="1512" alt="Screen Shot 2022-05-15 at 11 08 35 PM" src="https://user-images.githubusercontent.com/54876893/168529655-dfe8237b-9fa9-42a4-83f1-29bbaeb51984.png">

4. In GCP, make a kubernetes cluster called cmpe172. 

<img width="1512" alt="Screen Shot 2022-05-15 at 11 10 10 PM" src="https://user-images.githubusercontent.com/54876893/168529819-8ae4e180-724e-4a7b-ae91-fb87bda91828.png">

5. In Github, add the provided file google.yml action to the spring-gumball repository Actions. 

<img width="1512" alt="Screen Shot 2022-05-15 at 11 25 48 PM" src="https://user-images.githubusercontent.com/54876893/168531843-f82ce1a4-ca08-47a3-aed4-614527b2ee3f.png">

6. After, go to the Code tab and make a new release to trigger a CD Deployment.

### Errors I ran into in the Actions Tab:
> Error - `Error: Required "container.clusters.get" permission(s) for "projects/***/zones/us-central1-c/clusters/cmpe172".`
> 
> Solution - check to see if your Service Account is set as Owner.
> 
> Error - `Error: No method for authentication. Set credentials in this action or export credentials from the setup-gcloud action`
> 
> Solution - Make sure secrets are added to the actions tab of secrets instead of dependabot

<img width="1512" alt="Screen Shot 2022-05-15 at 10 42 38 PM" src="https://user-images.githubusercontent.com/54876893/168530679-6690b5af-9cee-4683-9a0e-bc2f9ae7adfc.png">

7. When the Github Action is completed, in GCP, go to Services & Ingress, select on the service, and then select Create Ingress. For 'Host and path' rules, add the spring-gumball-service. After this the gumball app is now deployed.

<img width="1512" alt="Screen Shot 2022-05-15 at 10 41 20 PM" src="https://user-images.githubusercontent.com/54876893/168530854-caf5216b-3f13-490c-9af4-b117904cb4a4.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 10 44 05 PM" src="https://user-images.githubusercontent.com/54876893/168530875-17c5ff86-78f4-4360-8792-eb58a1823960.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 10 44 42 PM" src="https://user-images.githubusercontent.com/54876893/168530907-b80d1a2d-7202-4239-ba5e-831aca2e9ea5.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 10 45 26 PM" src="https://user-images.githubusercontent.com/54876893/168531020-7ceaaa21-58da-4b58-a201-394c1dec30e9.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 10 47 25 PM" src="https://user-images.githubusercontent.com/54876893/168531053-7295cd3d-42b1-45f0-895d-c7631d8b9c59.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 10 52 36 PM" src="https://user-images.githubusercontent.com/54876893/168531071-ef958eaf-e0a2-419f-b111-5d4c25ce77b5.png">

<img width="1512" alt="Screen Shot 2022-05-15 at 10 52 53 PM" src="https://user-images.githubusercontent.com/54876893/168531090-1d17381b-c3f8-42b7-85b3-4652553b817c.png">

