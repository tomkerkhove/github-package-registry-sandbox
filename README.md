# GitHub Package Registry Sandbox
Playing around with GitHub Package Registry.

## Docker
POC based on [Docker docs for GitHub Package Registry](https://help.github.com/en/articles/configuring-docker-for-use-with-github-package-registry).

Login to GitHub Package Registry on this repo
```cli
docker login docker.pkg.github.com -u tomkerkhove -p <pat-token>
```

Build & tag the image for GitHub Package Registry on this repo:
```cli
cd src/
docker build . --file .\GitHubPackageRegistry.Docker\Dockerfile --tag docker.pkg.github.com/tomkerkhove/github-package-registry-sandbox/myimage:cli
```

Push the image to GitHub Package Registry for this repo:
```cli
docker push docker.pkg.github.com/tomkerkhove/github-package-registry-sandbox/myimage:cli
```


Image is published to GitHub Package Registry - [Have a look](https://github.com/tomkerkhove/github-package-registry-sandbox/packages/14409).

## NuGet
POC based on [NuGet docs for GitHub Package Registry](https://help.github.com/en/articles/configuring-nuget-for-use-with-github-package-registry).

Add a new NuGet source:
```cli
nuget source Add -Name "GitHub NuGet Registry" -Source "https://nuget.pkg.github.com/tomkerkhove/index.json" -UserName tomkerkhove -Password <pat-token>
```

Publish the NuGet package:
```cli
dotnet build .\src\GitHubPackageRegistry.Library\GitHubPackageRegistry.Library.csproj --configuration release
```

Push the package to GitHub Package Registry for this repo:
```cli
nuget push .\src\GitHubPackageRegistry.Library\bin\release\GitHubPackageRegistry.Library.1.0.0.nupkg -Source "GitHub nuget registry"
```

NuGet Package is published to GitHub Package Registry - [Have a look](https://github.com/tomkerkhove/github-package-registry-sandbox/packages/14412).