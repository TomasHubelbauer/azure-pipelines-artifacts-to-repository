# Azure Pipelines Artifacts to Repository

**This repository is archived.** I've completely migrated to using GitHub Actions for my open source and personal projects.

To use Azure Pipelines to compile repository sources and place artifacts in `docs` for GitHub Pages or to run reports on the data
tracked in the repository, Azure Pipelines can be set up in a way which allows the Git client to remain authenticated with GitHub
after the source code checkout so that it can be used to also push to GitHub, allowing us to store any artifacts in the source
repository.

To achieve it:

- Have a continuously triggered pipeline and expose the Git credentials in it
  
  https://docs.microsoft.com/en-us/azure/devops/pipelines/scripts/git-commands?view=azure-devops&tabs=yaml#allow-scripts-to-access-the-system-token

- Run whatever script on the checked out repository and put the artifacts anywhere in the checked out sources

- Run `git config`, `git add`, `git commit` and `git push` and find your changes in the repository

  - Make sure to tag the commit with `**NO_CI**` to prevent an endless loop
    
    https://docs.microsoft.com/en-us/azure/devops/pipelines/build/triggers?view=azure-devops&tabs=yaml#skipping-ci-for-individual-commits
    
  - Consider checking out again just before the commit so that the push works out if it can be fast forwarded

- Use scheduled pipeline trigger in case of recurring recomputation (hourly, daily etc.)
