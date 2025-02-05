# Paperless-ngx

## Sobre

O Paperless-ngx é  um sistema de gerenciamento de documentos de código aberto que transforma seus documentos físicos em um arquivo on-line pesquisável

### Features

Principais features:

- Organizar e indexar os documentos escaneados com tags, correspondentes, tipos e muitos outros
- Os dados são armazenados num servidor local
- Executa OCR nos documentos
- Reconhece mais de 100 idiomas
- Os documentos são salvos em PDF juntos dos arquivos originais inalterados
- Suporta vários tipos de arquivo (desde PDFs ou imagens até documentos Office)

## Instalação

### Clonagem

É necessário ter o **Docker** instalado e configurar o compose.

```bash
git clone https://github.com/paperless-ngx/paperless-ngx.git
```

### Configuração do *docler-compose.yml*

O compose (*docker-compose.yml*), porém ele não vai vir com este nome. Para Configurar este arquivo, é necessário seguir até a o diretório *docker/compose* do repositório recém clonado e atualizar o nome de *docker-compose.sqlite-tika.yml* para *docker-compose.yml*. Após esse processo, é necessário setar alguns valores em *volumes* dentro de *webserver*

Antes:

```yml
volumes:
    - data:/usr/src/paperless/data
    - media:/usr/src/paperless/media
    - ./export:/usr/src/paperless/export
    - ./consume:/usr/src/paperless/consume
```

Depois:

```yml
volumes:
    - <Pasta salva do usuário>/data:usr/src/paperless/data
    - <Pasta salva do usuário>/media:/usr/src/paperless/media
    - <Pasta salva do usuário>/export:/usr/src/paperless/export
    - <Pasta salva do usuário>/consume:/usr/src/paperless/consume
```

### Baixando as imagens com o Docker

Script para baixar as imagens do Paperless no diretório em que se encontra o compose.

```bash
docker-compose pull
```

### Configuração de servidor web

Script para configurar o usuário e a senha para o servidor web.

```bash
docker-compose run --rm webserver createsuperuser
```

## Execução do serviço

Script para inicializar o serviço.

```bash
docker-compose up -d
```

Para acessar o serviço, é necessário acessar atráves da porta *8000*: [localhost:8000/dashboard](https://localhost:8000/dashboard)

# Referências
1. [Setup - Paperless-ngx | Paperless-ngx](https://docs.paperless-ngx.com/setup/)
2. [DMS Paperless NGX with Docker in Windows Installation, Instructions & Tips [EN] | YouTube
](https://www.youtube.com/watch?v=kRH0nPRcRMY)