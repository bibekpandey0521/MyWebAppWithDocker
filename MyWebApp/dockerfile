FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY ./MyWebApp.csproj ./
RUN dotnet restore "MyWebApp.csproj"
COPY . . 
RUN dotnet publish ./MyWebApp.csproj -c Release -o /app/

FROM mcr.microsoft.com/dotnet/sdk:9.0 AS final
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet","MyWebApp.dll"]