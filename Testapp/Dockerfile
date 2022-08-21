

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:3.1
WORKDIR /app
COPY --from=publish /app/out .
ENTRYPOINT ["dotnet", "Testapp.dll"]

