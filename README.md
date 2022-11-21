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


