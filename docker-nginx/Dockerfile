# Define a imagem base como a versão mais recente do Nginx.
FROM nginx:latest

# Atualiza a lista de pacotes do sistema.
# Instala ferramentas úteis para testes e diagnóstico de rede.
# Remove o cache do apt para reduzir o tamanho final da imagem.
RUN apt-get update && \
    apt-get install -y iputils-ping curl && \
    rm -rf /var/lib/apt/lists/*

# Copia o arquivo de configuração customizado do Nginx.
COPY nginx.conf /etc/nginx/nginx.conf

# Expõe a porta 8080 do container.
EXPOSE 8080

