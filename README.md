# DotNetAPP

## Infer.NET and probabilistic programming
https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/matchup-app-infer-net

https://github.com/dotnet/infer



## Template for Full .Net Framework:
Action [Tab] -> Configure new .yml file (named NetFxCI.yml)

### change the branches and runs-on to the coressponded OS:

runs-on: [windows-latest]
(see https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions for more information)

### setup msbuild:
search for msbuild in the right hand side menu 

copy 
      - name: setup-msbuild
        uses: microsoft/setup-msbuild@v1.1
        
into .yml file just after 
    runs-on: [windows-latest]

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2
      
and remove the rest of codes in the .yml file.

Then you will search for NuGet and choose Setup NuGet.exe for use with actions
copy 
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1
    
    - name: Setup NuGet
      uses: NuGet/setup-nuget@v1.0.5
      
So you will have:

# This is a basic workflow to help you get started with Actions

name: CI

# Controls when the action will run. Triggers the workflow on push or pull request 
# events but only for the master branch
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: [windows-latest]

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
    # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
    - uses: actions/checkout@v2
      
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1
    
    - name: Setup NuGet
      uses: NuGet/setup-nuget@v1.0.5
    
    - name: Restore NuGet packages
      run: nuget restore DotNetAPP.sln
    
    - name: Build the Solution
      run: msbuild DotNetAPP.sln /p:Configuration=Release
      
