.github/workflows/build.yml

name: Build DLL

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: windows-latest

    steps:
    - uses: actions/checkout@v3

    - name: Setup .NET
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: '4.7.2'

    - name: Build
      run: dotnet build --configuration Release

    - name: Upload DLL
      uses: actions/upload-artifact@v3
      with:
        name: SpeedrunTimer
        path: bin/Release/
