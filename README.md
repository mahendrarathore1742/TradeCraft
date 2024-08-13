# TradeCraft Stock application


For Run and build Dotnet Application
~~~

dotnet build

dotnet run

~~~

## DockerFile doc For Dotnet Application

~~~

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT [ "dotnet", "(Your Application Name)".dll" ]

~~~

## DockerFile doc For MS SQL :-

~~~
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=abcDEF123#" \
-p 1433:1433 --name sqlsv \
-d mcr.microsoft.com/mssql/server:2017-latest

~~~


### Follow this blog for deeper understanding

~~~
[Basic] Docker image 🐳 Dockerfile — SQL Server with custom prefill DB scripts

https://medium.com/bright-days/basic-docker-image-dockerfile-sql-server-with-custom-prefill-db-script-8f12f197867a

~~~

~~~
How to Dockerize a .Net application: All You Need To Know

https://medium.com/@vndpal/how-to-dockerize-a-net-application-all-you-need-to-know-9b7d62cf5793
~~~






