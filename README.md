# trivy-repo-scan-pipeline (Repository Scanning)

This repository contains a task that uses [trivy](https://github.com/aquasecurity/trivy) tool for detecting vulnerabilities present in an Repository. With this task we can scan a repository that has application dependencies and OS Packages for vulnerabilities.

#### Set up a cluster using minikube by doing a `minikube start`

# Set up Tekton
Install tekton with the foloowing command after setting up the cluster

`kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml`

This will install all the necessary tekton components to get started

# Installing the Task
`kubectl apply -f https://raw.githubusercontent.com/mbharatk/trivy-repo-scan-pipeline/main/repo-scan-task.yaml`

# Applying the Pipeline and PipelineRun
`kubectl apply -f https://raw.githubusercontent.com/mbharatk/trivy-repo-scan-pipeline/main/repo-pipeline.yaml`

`kubectl apply -f https://raw.githubusercontent.com/mbharatk/trivy-repo-scan-pipeline/main/repo-pipelinerun.yaml`

##### After applying all the above mentioned, follow the below steps:
`tkn pipeline start <name-of-your-pipeline>` 

Enter the url of the repository to scan in the below given format when prompted after the above mentioned pipeline start step

    Example format: https://github.com/mbharatk/test-repo1
    
and all the other values are same as mentioned in the pipeline.

Once done, check the logs using the following command:

`tkn pipelinerun logs <name-of-the-pipelinerun>`
