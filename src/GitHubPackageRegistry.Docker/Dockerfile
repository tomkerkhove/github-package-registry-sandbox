FROM mcr.microsoft.com/dotnet/core/runtime:3.0.0-preview7-alpine3.9 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/core/sdk:3.0.100-preview7-alpine3.9 AS build
WORKDIR /src
COPY ["GitHubPackageRegistry.Docker/GitHubPackageRegistry.Docker.csproj", "GitHubPackageRegistry.Docker/"]
RUN dotnet restore "GitHubPackageRegistry.Docker/GitHubPackageRegistry.Docker.csproj"
COPY . .
WORKDIR "/src/GitHubPackageRegistry.Docker"
RUN dotnet build "GitHubPackageRegistry.Docker.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "GitHubPackageRegistry.Docker.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "GitHubPackageRegistry.Docker.dll"]