# Create-CI-CD-pipeline-Using-GitHub-Action-Automate-Terraform
Modifying  previously  deployed AWS instances in Github repository via CI/CD pipeline by using GitHub Actions and Terraform automation 

![Screenshot 2023-03-15 at 9 49 25 PM](https://user-images.githubusercontent.com/121365233/225489030-06a3e0c6-855e-4e50-9f9e-bc09c5380bb2.png)

# OBJECTIVES:

-Terraform Cloud Setup

-GitHub Repository Setup

-Actions Workflow

-Creating and Merging Pull Requests

-Verifying a Provisioned Instance

1) Go to Terraform cloud and create an Organization as well as workspace.

-- Choose your setup workflow

<img width="661" alt="Screenshot 2023-03-15 at 10 03 35 PM" src="https://user-images.githubusercontent.com/121365233/225490775-b06868c6-ded5-4f94-9baf-5043ea24b9b6.png">

<img width="622" alt="Screenshot 2023-03-15 at 10 04 57 PM" src="https://user-images.githubusercontent.com/121365233/225491142-055ff63a-3bc2-46ba-9a1e-0b183dbdf1b6.png">


<img width="570" alt="Screenshot 2023-03-15 at 10 07 00 PM" src="https://user-images.githubusercontent.com/121365233/225491279-6656cc1c-86af-4e40-83db-d1ed68e2dfb8.png">

<img width="591" alt="Screenshot 2023-03-15 at 10 08 25 PM" src="https://user-images.githubusercontent.com/121365233/225491420-31a18a67-568e-46d2-9213-9eb92b3b1fab.png">

--Now we have created organization and workspace!

<img width="599" alt="Screenshot 2023-03-15 at 10 09 45 PM" src="https://user-images.githubusercontent.com/121365233/225491540-44991839-217a-4610-a2e1-7349472f16b3.png">

--Let’s add some access variables! To do so first we need to go AWS console and create access key first!

2) Open AWS console.

--Create a user

<img width="1105" alt="Screenshot 2023-03-15 at 10 16 29 PM" src="https://user-images.githubusercontent.com/121365233/225492951-bdcd31c8-dfc4-4802-be87-e607b39e46f1.png">

<img width="894" alt="Screenshot 2023-03-15 at 10 17 37 PM" src="https://user-images.githubusercontent.com/121365233/225492969-1d93ff4a-609e-4a7a-b13c-3efb8ddaa9e0.png">

<img width="868" alt="Screenshot 2023-03-15 at 10 18 24 PM" src="https://user-images.githubusercontent.com/121365233/225492979-8d616a83-1caf-44ff-b460-801f527d3383.png">

<img width="862" alt="Screenshot 2023-03-15 at 10 18 56 PM" src="https://user-images.githubusercontent.com/121365233/225493004-0751244e-a67a-4d79-9897-2ce4ede3b526.png">

<img width="863" alt="Screenshot 2023-03-15 at 10 19 24 PM" src="https://user-images.githubusercontent.com/121365233/225493012-1c0103b2-7b1c-49e2-940d-48de4d04002c.png">

--Click on the user button

<img width="892" alt="Screenshot 2023-03-15 at 10 21 19 PM" src="https://user-images.githubusercontent.com/121365233/225493199-775ea47f-5e97-4016-889b-de0065385d2f.png">

--select security credentials 

<img width="1064" alt="Screenshot 2023-03-15 at 10 22 53 PM" src="https://user-images.githubusercontent.com/121365233/225493510-7fbb0e73-cf01-4e67-9a20-3895ade4e768.png">

--scroll down and click on create access key

<img width="917" alt="Screenshot 2023-03-15 at 10 24 58 PM" src="https://user-images.githubusercontent.com/121365233/225493724-bc27dffb-e257-4a2d-90d8-291d8d52f979.png">

<img width="685" alt="Screenshot 2023-03-15 at 10 25 46 PM" src="https://user-images.githubusercontent.com/121365233/225493948-ce47d246-4c0e-4114-a575-2162cfef535e.png">

<img width="689" alt="Screenshot 2023-03-15 at 10 27 03 PM" src="https://user-images.githubusercontent.com/121365233/225494085-a6e3cf9a-6f7d-4db3-ac03-0b25d933d3c4.png">

--Copy your keys to use them in variables, or download .csv file

<img width="686" alt="Screenshot 2023-03-15 at 10 27 59 PM" src="https://user-images.githubusercontent.com/121365233/225494784-10a14575-75c6-4126-9fd9-6484015a061e.png">

3) Here we go back to terraform cloud to add variables

<img width="1237" alt="Screenshot 2023-03-15 at 10 33 10 PM" src="https://user-images.githubusercontent.com/121365233/225495579-4eec5914-338f-4c46-8cf5-03bdd2208c4c.png">

--Add second variable

<img width="1253" alt="Screenshot 2023-03-15 at 10 37 33 PM" src="https://user-images.githubusercontent.com/121365233/225495922-321093b5-15f6-4c9d-9995-3980ac3c47ff.png">

--To connect our local terminal to the pipeline we need an <API token>. To generate API token click on your avatar on the left top corner and select user settings.

<img width="1279" alt="Screenshot 2023-03-15 at 10 40 36 PM" src="https://user-images.githubusercontent.com/121365233/225496641-a631ff4b-4834-4d79-ba67-402bcd2ce212.png">

<img width="1260" alt="Screenshot 2023-03-15 at 10 43 59 PM" src="https://user-images.githubusercontent.com/121365233/225496886-b93bc07b-0120-466c-8cbe-f549edb7d64d.png">

***After generating your token DO NOT FORGET to copy it before you press done!!! Save securely to use it in section 4.

4) Now let`s jump into Github repository that we want to make changes in. 

--select the target repository --click on the settings --Secrets and variables --actions --New repository secret.

<img width="915" alt="Screenshot 2023-03-15 at 11 03 38 PM" src="https://user-images.githubusercontent.com/121365233/225501134-d6457b19-881d-4e37-bebb-15034c2645f8.png">

<img width="1212" alt="Screenshot 2023-03-15 at 11 05 37 PM" src="https://user-images.githubusercontent.com/121365233/225501836-ebf2d6ae-15fa-4927-967c-970f3cb5f4dc.png">

--paste your generated token and click on the add secret. If you have lost it, no worries while connecting your terminal to terraform cloud there be the second chance to generate new on.

![Screenshot 2023-03-15 at 11 11 14 PM](https://user-images.githubusercontent.com/121365233/225504365-437cd67d-3b5b-45f0-84f9-05fca5a1ca9e.png)

<img width="793" alt="Screenshot 2023-03-15 at 11 11 52 PM" src="https://user-images.githubusercontent.com/121365233/225504380-d5cd0216-ca7f-4a9a-9f62-44d0e4a2f277.png">

![Screenshot 2023-03-15 at 11 13 50 PM](https://user-images.githubusercontent.com/121365233/225504396-1dd08a61-19a1-4314-a3ee-3d81469f1121.png)

5) To start actions workflow first we need to clone target repo to our local machine!

<img width="878" alt="Screenshot 2023-03-15 at 11 15 58 PM" src="https://user-images.githubusercontent.com/121365233/225504857-94af569a-f53c-48cc-a0e3-60af98bc7c79.png">

--Change directory to downloaded repo folder name by using "cd" command. --To see existing files use "ls" command. -- To open any file and make edits use "vim" command

<img width="799" alt="Screenshot 2023-03-15 at 11 25 35 PM" src="https://user-images.githubusercontent.com/121365233/225506263-2bb3dceb-bcaf-485b-bc35-cb58fc6d6415.png">

--Run "terraform fmt" command->it updates the formatting of Terraform configuration files in the current directory and its subdirectories.
--"terraform init" command-> it initializes the backend. --"terraform validate"->to check whether configuration is valid or not. --"terraform plan"->helps you to preview changes before applying them, reducing the risk of unexpected changes or downtime. --"terraform apply"->creates or modifies resources to match the desired state described in the configuration files.

<img width="1138" alt="Screenshot 2023-03-15 at 11 38 09 PM" src="https://user-images.githubusercontent.com/121365233/225509277-9b022932-67fd-4aa0-b799-0585d9fa7f10.png">

<img width="1138" alt="Screenshot 2023-03-15 at 11 40 25 PM" src="https://user-images.githubusercontent.com/121365233/225509296-ea71e6cb-1a8a-490a-9dcf-f5bbfa7a59ef.png">

--Successfully deployed our EC2 instance in us-east-1 region.

<img width="1431" alt="Screenshot 2023-03-15 at 11 50 25 PM" src="https://user-images.githubusercontent.com/121365233/225510002-7f566fb5-0c19-4465-96dd-e4cc8486b898.png">

6) Creating and merging pull requests.

--Create a new branch, then update our main.tf file.
--Commit the changes.
--Push the updates to the file to our repository.
--Review and merge the pull request.

<img width="1436" alt="Screenshot 2023-03-16 at 12 01 09 AM" src="https://user-images.githubusercontent.com/121365233/225511371-8db993e6-06c5-4823-898e-1acba88b09e4.png">

7) Verifying a provisioned instance

--Check GitHub and terraform cloud to make sure actions did as they were intended to do. 

--If you notice we have a message here, it says compare & pull request.

<img width="942" alt="Screenshot 2023-03-16 at 12 06 35 AM" src="https://user-images.githubusercontent.com/121365233/225517140-2b030d81-8d61-4047-aa12-ebfd4dbdac95.png">

<img width="1225" alt="Screenshot 2023-03-16 at 12 52 44 AM" src="https://user-images.githubusercontent.com/121365233/225517765-58bdb387-a323-4533-939c-001d39df1d0c.png">

--Click on the "Create pull request" and then merge pull request finally confirm merge.

<img width="939" alt="Screenshot 2023-03-16 at 12 55 10 AM" src="https://user-images.githubusercontent.com/121365233/225518115-ab722d36-60f6-4d9a-b0e8-91a2b5cac003.png">

<img width="932" alt="Screenshot 2023-03-16 at 12 55 22 AM" src="https://user-images.githubusercontent.com/121365233/225518134-940d2a28-c279-43ac-ac55-8ebbc3d52ecf.png">

8) Finally, let’s do some clean up and destroyments to avoid extra charges.

--Use "terraform destroy"

<img width="1004" alt="Screenshot 2023-03-16 at 12 58 20 AM" src="https://user-images.githubusercontent.com/121365233/225518645-f161015b-b13d-4e23-9f2c-93f6e8ebffd8.png">

8) Finally, let’s do some clean up and destroyments to avoid extra charges.

--Go to terraform cloude console --sellect created organization, --settings, --destruction and deletion.

Congratulations!




