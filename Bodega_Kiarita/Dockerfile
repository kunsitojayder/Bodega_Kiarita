FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["TuProyecto.csproj", "./"]
RUN dotnet restore "./TuProyecto.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "TuProyecto.csproj" -c Release -o /app/build
RUN dotnet publish "TuProyecto.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "TuProyecto.dll"]
