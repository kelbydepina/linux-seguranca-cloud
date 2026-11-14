# Publicação do site

## Nível escolhido
Nível 2 - Intermédio

## Rota escolhida
Nginx

## Ficheiros criados
- index.html
- sobre.html
- style.css

## Local de publicação
/var/www/html/topico-03/ (URL: http://localhost/topico-03/)

## Comandos principais utilizados
    sudo apt update
    sudo apt install -y nginx
    systemctl status nginx
    sudo mkdir -p /var/www/html/topico-03
    sudo cp index.html sobre.html style.css /var/www/html/topico-03/
    sudo chmod -R a+rX /var/www/html/topico-03

## Resultado obtido
O Nginx ficou ativo e o site ficou acessível em /topico-03/, com as duas páginas e o CSS aplicado.

## Limitações encontradas
A VM usa rede NAT, pelo que foi necessário um reencaminhamento de portas (8080 para 80) para abrir o site no navegador do Windows. A segurança do servidor (firewall, HTTPS, hardening) não foi tratada nesta atividade e fica para o Tópico 4.
