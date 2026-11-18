# Plano de continuidade (proposta)

## Serviço crítico
Nginx a servir o site em /var/www/html/topico-03/.

## Ficheiros e configurações críticas
- /var/www/html/topico-03/ (conteúdo do site)
- /etc/nginx/ (configuração do Nginx)
- /etc/ufw/ (regras da firewall)

## Logs importantes
- /var/log/nginx/access.log e /var/log/nginx/error.log
- Registos do SSH e do sistema (journalctl)

## Periodicidade do backup
- Site: semanal e antes de cada alteração.
- Configuração do Nginx e do UFW: depois de cada alteração.
- Manter as últimas 4 cópias e guardar uma cópia fora da VM.

## Procedimento de recuperação
    1. Extrair o backup para uma pasta temporária: tar -xzvf ~/backups/backup-site-topico03.tar.gz -C /tmp
    2. Copiar para a pasta do site: sudo cp -r /tmp/topico-03/. /var/www/html/topico-03/
    3. Corrigir as permissões: sudo chmod -R a+rX /var/www/html/topico-03
    4. Testar a configuração e recarregar: sudo nginx -t && sudo systemctl reload nginx

## Critérios de validação após recuperação
- systemctl is-active nginx devolve active.
- curl -sI http://localhost/topico-03/ devolve HTTP/1.1 200 OK.
- As páginas abrem no navegador com o estilo aplicado.
- O UFW continua ativo com as regras 22/tcp e 80/tcp.
