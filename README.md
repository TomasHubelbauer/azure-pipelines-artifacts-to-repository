# Azure Pipelines Artifacts to Repository

- [ ] Set up an Azure build Pipeline and see if there is a task/way to collect the artifacts and push them back to the repository

This way Azure Pipelines could be abused as a free build server.
We need to take care though not to trigger another Pipeline on the Pipeline to GitHub push.
That would cause an endless loop and most likely get my personal account banned in VSTS.
