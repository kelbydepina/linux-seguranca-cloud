# Análise de logs

## Logs consultados
- Registos do sistema (journalctl): evidencias/journal-recente.txt e evidencias/journal-avisos.txt
- Registos do serviço SSH (journalctl -u ssh)
- Log de acessos do Nginx (/var/log/nginx/access.log)

## Registos do SSH (acessos ao servidor)

    Nov 13 18:25:12 Ubuntu-Server-Lab sshd-session[2014]: Accepted password for kelby from 10.0.2.2 port 59237 ssh2
    Nov 14 17:08:07 Ubuntu-Server-Lab sshd-session[1318]: Accepted password for kelby from 10.0.2.2 port 53466 ssh2
    Nov 14 17:40:12 Ubuntu-Server-Lab sshd-session[2844]: Accepted password for kelby from 10.0.2.2 port 50285 ssh2
    Nov 18 03:08:42 Ubuntu-Server-Lab sshd-session[1432]: Accepted password for kelby from 10.0.2.2 port 52064 ssh2

## Registos de acesso do Nginx (últimos pedidos ao site)

    10.0.2.2 - - [14/Nov/2026:04:32:22 +0000] "GET /topico-03/ HTTP/1.1" 200 618 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    10.0.2.2 - - [14/Nov/2026:04:32:22 +0000] "GET /topico-03/style.css HTTP/1.1" 304 0 "http://localhost:8080/topico-03/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    10.0.2.2 - - [14/Nov/2026:04:32:25 +0000] "GET /topico-03/sobre.html HTTP/1.1" 304 0 "http://localhost:8080/topico-03/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    10.0.2.2 - - [14/Nov/2026:04:32:27 +0000] "GET /topico-03/index.html HTTP/1.1" 200 618 "http://localhost:8080/topico-03/sobre.html" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    ::1 - - [14/Nov/2026:17:24:45 +0000] "HEAD /topico-03/ HTTP/1.1" 200 0 "-" "curl/8.18.0"
    10.0.2.2 - - [14/Nov/2026:17:44:23 +0000] "GET /topico-03/ HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    10.0.2.2 - - [14/Nov/2026:17:44:23 +0000] "GET /topico-03/style.css HTTP/1.1" 304 0 "http://localhost:8080/topico-03/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    10.0.2.2 - - [14/Nov/2026:17:45:09 +0000] "GET /topico-03/sobre.html HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    10.0.2.2 - - [14/Nov/2026:17:45:37 +0000] "GET /topico-03/index.html HTTP/1.1" 304 0 "http://localhost:8080/topico-03/sobre.html" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36"
    ::1 - - [14/Nov/2026:17:49:11 +0000] "HEAD /topico-03/ HTTP/1.1" 200 0 "-" "curl/8.18.0"

## Eventos relevantes identificados
1. Autenticações SSH bem-sucedidas do utilizador kelby: mostram quem entrou no servidor e quando. Uma entrada inesperada seria um sinal de acesso indevido.
2. Pedidos HTTP ao site (GET /topico-03/ e recursos associados) registados no access.log do Nginx: mostram que o serviço está a responder e que endereço o acedeu.

## Importância dos logs
Os logs permitem auditar acessos, diagnosticar falhas e detetar comportamentos anómalos, como muitas tentativas de login falhadas ou pedidos a páginas inexistentes. Por isso devem ser consultados com regularidade e preservados.
