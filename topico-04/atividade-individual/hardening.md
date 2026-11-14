# Hardening inicial (proposta)

## Serviço publicado
Nginx, a servir um site estático.

## Riscos específicos
- Versão do Nginx visível nas respostas HTTP.
- Tráfego HTTP sem cifragem.
- Risco de ficheiros sensíveis ficarem na pasta publicada.
- Permissões demasiado abertas nos ficheiros do site.

## Medidas que podem ser aplicadas agora
- Atualizar os pacotes do sistema (sudo apt update e sudo apt upgrade).
- Manter só as portas 22 e 80 abertas no UFW.
- Rever as permissões da pasta /var/www/html/topico-03 (ficheiros 644, pastas 755).
- Não colocar ficheiros sensíveis na pasta publicada.

## Medidas para os tópicos seguintes
- Configurar HTTPS com certificado.
- Esconder a versão do Nginx (server_tokens off).
- SSH apenas com chave e sem palavra-passe.
- Proteção contra força bruta (fail2ban).
- Logs, monitorização e cópias de segurança.
