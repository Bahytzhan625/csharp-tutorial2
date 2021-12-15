FROM mcr.microsoft.com/dotnet/runtime:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["csharp-tutorial2/csharp-tutorial2.csproj", "csharp-tutorial2/"]
RUN dotnet restore "csharp-tutorial2/csharp-tutorial2.csproj"
COPY . .
WORKDIR "/src/csharp-tutorial2"
RUN dotnet build "csharp-tutorial2.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "csharp-tutorial2.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "csharp-tutorial2.dll"]
