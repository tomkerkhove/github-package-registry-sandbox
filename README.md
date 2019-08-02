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