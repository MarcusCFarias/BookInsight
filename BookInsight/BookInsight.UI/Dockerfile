# Etapa 1: Construir a aplica��o Blazor WebAssembly
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copie os arquivos do projeto para o cont�iner
COPY . ./

# Restaurar depend�ncias e construir o projeto
RUN dotnet restore
RUN dotnet publish -c Release -o /app/publish

# Etapa 2: Configurar o servidor Nginx
FROM nginx:alpine
COPY --from=build /app/publish/wwwroot /usr/share/nginx/html

# Expor a porta padr�o do Nginx
EXPOSE 80

# Iniciar o Nginx
CMD ["nginx", "-g", "daemon off;"]