# AngularNginxDockerTemplate


Configuration template project for Angular VPS using Nginx and Docker. Created by @EmesDev.


<div align="center">
<img alt="Static Badge" src="https://img.shields.io/badge/Angular-v18-blue?style=plastic&logo=angular&logoColor=%23ff2e2e&logoSize=auto&labelColor=%23303030">
<img alt="Static Badge" src="https://img.shields.io/badge/Nginx-v1.25.5-blue?style=plastic&logo=nginx&logoColor=%2302f71b&logoSize=auto&labelColor=%23303030">
<img alt="Static Badge" src="https://img.shields.io/badge/Docker-latest-blue?style=plastic&logo=docker&logoColor=%2300d0ff&logoSize=auto&labelColor=%23303030">
<img alt="Static Badge" src="https://img.shields.io/badge/NPM-v21-blue?style=plastic&logo=NPM&logoColor=red&logoSize=auto&labelColor=%23303030">


</div>


## Configurando Dominios e SSL


Na pasta ./nginx/http.d é onde você pode configurar seus dominios e certificados SSL.


### Configurando dominio


Crie uma copia de um arquivo [ 02.exemple1.conf ] altere seu nome para [ 02.meudominio.conf ].


> Os numeros no inicio do path do arquivo são improtantes para a compilação do projeto, lebre sempre de organizar na ordem de prioridade sendo o "default" sempre [ 01.default.conf ]


Altere o server name para seu domínio


```nginx
    server_name meudominio.lvh.me;
```


### Configurando SSL


Para configurar o SSL do seu domínio é bastante simples. Basta entrar na pasta ./nginx/cert e colar os respectivos conteúdos em cada arquivo.


|     Arquivo     |     Conteúdo      |
| :-------------: | :---------------: |
| certificate.key | BEGIN CERTIFICATE |
| certificate.key | BEGIN PRIVATE KEY |


#### Onde os arquivos são importados


```nginx
server {
    # SSL configuration
    listen 443 ssl;
    listen [::]:443 ssl;
    http2 on;
    ssl_certificate /etc/nginx/ssl/certificate.crt;
    ssl_certificate_key /etc/nginx/ssl/certificate.key;


    server_name meudominio.lvh.me;
    access_log /var/log/nginx/meudominio.lvh.me.access.log main;


    root /usr/share/nginx/html/angular_exemple_1;
    index index.html;


    include /usr/share/nginx/html/errors/*.conf;


    location / {
        try_files $uri $uri/ /index.html;
    }
}
```


## Iniciando projeto Docker


Vamos iniciar o projeto para produção


### Build das aplicações


Execute o comando no seu terminal.


```bash
docker-compose up angular_example_1 angular_example_2


```


apos o fim do build, vamos iniciar o nginx


```bash
docker-compose up nginx


```


seu projeto será iniciado no <a href='http://meudominio.lvh.me'>http://meudominio.lvh.me</a>



