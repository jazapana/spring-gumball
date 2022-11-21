# Lab 10

CI Workflow:


First, I put all of the Professor's starter code in my new public repository. Then I set up a new workflow (gradle.yml):
<img width="1440" alt="Screen Shot 2022-11-20 at 4 12 20 PM" src="https://user-images.githubusercontent.com/89716705/202969129-cf23419d-db62-46d2-9e2c-929c44dff0ca.png">
Unfortunately, I had forgotten to change the contents of this gradle.yml to what Canvas said. So I updated it:
<img width="1440" alt="Screen Shot 2022-11-20 at 7 46 34 PM" src="https://user-images.githubusercontent.com/89716705/202969166-a100045f-9519-40b0-8b82-0d38026ee879.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 7 46 40 PM" src="https://user-images.githubusercontent.com/89716705/202969215-a95e065f-3d99-4d20-bde2-23d7eec3a146.png">
After updating, I went into the deployment.yaml file and changed the number of pods matching the template from 4 to 2:
<img width="1440" alt="Screen Shot 2022-11-20 at 4 49 13 PM" src="https://user-images.githubusercontent.com/89716705/202969254-8fd95588-ca17-4164-98ec-13af954fd214.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 4 49 34 PM" src="https://user-images.githubusercontent.com/89716705/202969288-0618ff58-db3e-440b-b0e6-f71fe60e45fb.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 4 49 40 PM" src="https://user-images.githubusercontent.com/89716705/202969310-99468bd1-e4a5-40f1-9ba0-febf21bcf3a0.png">
After commiting the change, a new workflow had begun, called "Update deployment.yaml":
<img width="1440" alt="Screen Shot 2022-11-20 at 4 50 02 PM" src="https://user-images.githubusercontent.com/89716705/202969380-f5b7469c-f57d-4edb-9b96-0798f18a6514.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 4 50 44 PM" src="https://user-images.githubusercontent.com/89716705/202969402-6191c3ac-9062-448f-bb7b-df0cb68ae82a.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 4 51 03 PM" src="https://user-images.githubusercontent.com/89716705/202969430-d10277f1-a236-4b21-aece-5dd255252faa.png">

CD Workflow:


Using GKE, I created a Kubernetes cluster with the name as cmpe172 and the zone as us-central1-c, all within a project called cmpe172:
<img width="1440" alt="Screen Shot 2022-11-20 at 5 18 17 PM" src="https://user-images.githubusercontent.com/89716705/202969944-82d1bd07-cd88-4e00-a0e8-f98478151d45.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 5 27 49 PM" src="https://user-images.githubusercontent.com/89716705/202969973-6cd10370-ba44-421d-8944-2d39c2a684ae.png">
Then I went to APIs & Services, went to the library page, and clicked on Private APIS. Since I saw the API listed, this means I was given access to enable APIs:
<img width="1440" alt="Screen Shot 2022-11-20 at 5 30 08 PM" src="https://user-images.githubusercontent.com/89716705/202970072-5c6bdabd-77ea-4eff-ae89-0595d280684f.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 5 31 02 PM" src="https://user-images.githubusercontent.com/89716705/202970100-cc0e6acc-8687-423b-a45b-4b5149c77b6a.png">
Using a link on Canvas, I enabled the Container Registry and Kubernetes Engine API:
<img width="1440" alt="Screen Shot 2022-11-20 at 6 24 03 PM" src="https://user-images.githubusercontent.com/89716705/202970132-6def6a0b-068b-4c69-87f3-88d5d4a0bfbc.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 24 09 PM" src="https://user-images.githubusercontent.com/89716705/202970166-7711cb25-ad79-45ae-bb93-44f99e1b7a9b.png">
Then, to see my project's ID, I went on to Cloud Overview / Dashboard:
<img width="1440" alt="Screen Shot 2022-11-20 at 6 27 02 PM" src="https://user-images.githubusercontent.com/89716705/202970313-748a623b-8d4e-49fe-9019-11797fec41b8.png">
To create a service account for Github Access, first I needed to enable the IAM API:
<img width="1440" alt="Screen Shot 2022-11-20 at 6 35 48 PM" src="https://user-images.githubusercontent.com/89716705/202970545-8f6dda62-a22e-4b60-9a16-cdaef72ae82d.png">
Then I went on to IAM & Admin / Service Accounts, and created a service account with the name "spring-gumball":
<img width="1440" alt="Screen Shot 2022-11-20 at 6 38 14 PM" src="https://user-images.githubusercontent.com/89716705/202970696-671c3fa3-c1e5-42fa-a1b1-03af23cc4449.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 38 24 PM" src="https://user-images.githubusercontent.com/89716705/202970726-0e79e2a7-aef1-4cb1-8fb9-23b03cc47d52.png">
I went onto IAM & Admin / IAM and clicked "Grant Access". Then I put the email of the newly created service account as a new principal, and assigned the Kubernetes Engine Developer and Storage Admin roles to the new principal:
<img width="1440" alt="Screen Shot 2022-11-20 at 6 43 17 PM" src="https://user-images.githubusercontent.com/89716705/202972217-e0b7ed90-df36-4a18-aa76-a84017144fbc.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 45 08 PM" src="https://user-images.githubusercontent.com/89716705/202972234-3743a99c-f059-4431-877a-f4bb40636a50.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 45 17 PM" src="https://user-images.githubusercontent.com/89716705/202972257-7c2e695e-0a91-4e29-bfad-7699a0e2e4bc.png">
To create a JSON service account key, first I went to IAM & Admin / Service Accounts and clicked the "Manage keys" Action for the service account "spring-gumball". Then I clicked Add Key / Create new key and chose the JSON key type. Once it was created, it was saved to my computer and was active:
<img width="1440" alt="Screen Shot 2022-11-20 at 6 47 16 PM" src="https://user-images.githubusercontent.com/89716705/202972906-4684334c-99ee-4c40-a312-ff797853fc72.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 47 29 PM" src="https://user-images.githubusercontent.com/89716705/202972942-f97f1f7e-aeca-46db-9c03-387e223c6d7c.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 47 45 PM" src="https://user-images.githubusercontent.com/89716705/202972970-b1368c14-f424-45ec-9546-f8145805e3b0.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 48 05 PM" src="https://user-images.githubusercontent.com/89716705/202972994-5ede7373-b0fa-4448-a5fc-c2b6efef88e4.png">
<img width="1440" alt="Screen Shot 2022-11-20 at 6 48 52 PM" src="https://user-images.githubusercontent.com/89716705/202973014-ed97ee95-baa0-45e8-8c44-90510ab2f432.png">
