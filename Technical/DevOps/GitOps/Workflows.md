![[GitOps workflow.png]]

1. Create a Git repository to serve as an SSOT and to hold both the IaC and application code.
    
2. Create pull/merge requests to make changes and collaborate before pushing back to the main branch of the repository.
    
3. Run a CI pipeline to integrate changes, validate configuration files, and perform automated tests.
    
4. Review and approve the changes to ensure that the changes are well tested before being applied in an environment.
    
5. Run a CD pipeline for the continuous deployment of the infrastructure.