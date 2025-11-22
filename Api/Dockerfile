# Estágio 1: Build da Aplicação
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["mininal-api.csproj", "."]
RUN dotnet restore

# Copia o restante dos arquivos e publica (Build)
COPY . .
RUN dotnet publish -c Release -o /app/publish

# Estágio 2: Criação da Imagem Final (SDK Leve)
# Usamos o SDK porque ele contém o 'dotnet tool' para a migração
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS final
WORKDIR /app

# Instala a ferramenta 'dotnet-ef' AGORA, pois o SDK está presente
RUN dotnet tool install --global dotnet-ef --version 8.0.0
ENV PATH="$PATH:/root/.dotnet/tools"

# Copia os binários e define o ponto de entrada
COPY --from=build /app/publish .

COPY ./ /app/
# Muda o ENTRYPOINT para usar o modo 'run' se o arquivo for .dll
ENTRYPOINT ["dotnet", "mininal-api.dll"]