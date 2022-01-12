# DotNetAPP

Infer.NET and probabilistic programming


## Template for Full .Net Framework:
Action [Tab] -> Configure new .yml file (named NetFxCI.yml)

### change the branches and runs-on to the coressponded OS:

runs-on: [macos-11]
(see https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions for more information)

### setup msbuild:
search for msbuild in the right hand side menu 

copy 
      - name: setup-msbuild
        uses: microsoft/setup-msbuild@v1.1
        
into .yml file just after 
    runs-on: [macos-11]

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2
      
and remove the rest of codes in the .yml file.

Then you will search for NuGet and choose Setup NuGet.exe for use with actions
copy 


So you will have:


