<h1>
Pipeline-trivy

</h1>
This repository demonstrates Trivy, a vulnerability management tool for images and containers. It uses Tekton pipeline under the hood.  



The repo contains a single task, **scan-repo**, for scanning a repository through Trivy. After running the pipeline, user is first asked to enter a repo to be scanned. Try [this](https://github.com/knqyf263/trivy-ci-test) repo. Further working of Trivy can be understood [here](https://rastogee-ayushi.medium.com/trivy-keep-your-artifacts-vulnerability-free-6dce292134e5). 

## Setting up cluster
Set up a cluster using minikube by doing a minikube start.

## Setting up Tekton
Install tekton with the following command after setting up the cluster

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

This will install all the necessary Tekton components to get started.

## Applying the Tasks and Pipeline yamls
Apply all the mentioned tasks in the repositorry above. Example format:

kubectl apply -f https://raw.githubusercontent.com/ayushi-24git/pipeline-trivy-tekton/main/tasks/scan-repo.yaml

Apply the pipeline yamls as:

kubectl apply -f https://raw.githubusercontent.com/ayushi-24git/pipeline-trivy-tekton/scan-pipeline-repo.yaml

kubectl apply -f https://raw.githubusercontent.com/ayushi-24git/pipeline-trivy-tekton/scan-pipelinerun-repo.yaml

Now, start the pipeline by: `tkn pipeline start scan-pipeline-repo`


Check logs
Now, the pipeline has successfully started. You can check the logs using the following command:

`tkn pipelinerun logs <name-of-the-pipelinerun>`

  



  

  
