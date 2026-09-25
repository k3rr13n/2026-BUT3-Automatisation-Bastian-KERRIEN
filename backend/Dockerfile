# ==== build ====
FROM mcr.microsoft.com/dotnet/sdk:10.0 as build

WORKDIR /app

COPY src/TaskList.Api/TaskList.Api.csproj src/TaskList.Api/

RUN dotnet restore src/TaskList.Api/TaskList.Api.csproj

COPY src/TaskList.Api/ src/TaskList.Api/

RUN dotnet publish src/TaskList.Api/TaskList.Api.csproj -c Release -o /dossier_de_sortie 

# ==== finale ====
FROM mcr.microsoft.com/dotnet/aspnet:10.0

EXPOSE 8080

ENV ASPNETCORE_URLS=http://+:8080

WORKDIR /dossier_de_sortie

COPY --from=build /dossier_de_sortie .

HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1

CMD dotnet TaskList.Api.dll 

USER $APP_UID
