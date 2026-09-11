FROM mcr.microsoft.com/dotnet/sdk:10.0

WORKDIR /tp

COPY . .

RUN dotnet restore api.slnx

RUN dotnet publish src/TaskList.Api/TaskList.Api.csproj -c Release -o /dossier_de_sortie 

EXPOSE 8080

ENV ASPNETCORE_URLS=http://+:8080

WORKDIR /dossier_de_sortie

CMD dotnet TaskList.Api.dll 