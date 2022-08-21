FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build

WORKDIR /app
COPY ["Testapp/Testapp.csproj", "./"]
RUN dotnet restore "Testapp/Testapp.csproj"
COPY . .

RUN dotnet publish "Testapp.csproj" -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:3.1
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "Testapp.dll"]
