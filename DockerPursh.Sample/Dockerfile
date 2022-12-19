#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see https://aka.ms/containercompat


#FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
 #WORKDIR /app
  #EXPOSE 80
 #FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
#
##FROM  maven2.it.volvo.net:18443/nvs-dotnet-60-runtime-mq9-ubi8:latest AS publish
#
#ENV DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=false
#
#WORKDIR /app
#ARG dotnet_cli_home_arg=/tmp/
#ENV DOTNET_CLI_HOME=$dotnet_cli_home_arg
#
#EXPOSE 4000
#
#ARG dotnet_cli_home_arg=/tmp/
#ENV DOTNET_CLI_HOME=$dotnet_cli_home_arg
#
#ENV ASPNETCORE_ENVIRONMENT=Development
#ENV BRANCH=master
#ENV ASPNETCORE_URLS=http://+:4000
#
#COPY --from=build /app/publish /app
#
#USER 1000
#
#ENTRYPOINT ["dotnet", "DockerPursh.Sample.dll.dll"]
#

#FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
 #WORKDIR /app
 #EXPOSE 80
#FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
 #WORKDIR /src
 #COPY ["DockerPursh.Sample.csproj", ""]
 #RUN dotnet restore --interactive
 #COPY . .
 #WORKDIR "/src/."
 #RUN dotnet build "DockerPursh.Sample.csproj" -c Release -o /app/build
 #FROM build AS publish
 #RUN dotnet publish "DockerPursh.Sample.csproj" -c Release -o /app/publish
 #FROM base AS final
 #WORKDIR /app
 #COPY --from=publish /app/publish .
 #ENTRYPOINT ["dotnet", "DockerPursh.Sample.dll"]


FROM mcr.microsoft.com/dotnet/sdk:6.0  as build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore "DockerPursh.Sample.csproj"

COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app

COPY --from=build-env /app/out .
ENTRYPOINT [ "dotnet", "DockerPursh.Sample.dll" ]


#FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
#WORKDIR /app
#EXPOSE 80
#
#FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
#WORKDIR /src
#COPY ["DockerPursh.Sample.csproj", "DockerPursh.Sample/"]
#RUN dotnet restore "DockerPursh.Sample/DockerPursh.Sample.csproj"
#COPY . .
#WORKDIR "/src/DockerPursh.Sample"
#RUN dotnet build "DockerPursh.Sample.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "DockerPursh.Sample.csproj" -c Release -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "DockerPursh.Sample.dll"]