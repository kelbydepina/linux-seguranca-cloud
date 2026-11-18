# Backup e recuperação

## Ficheiro crítico identificado
A pasta /var/www/html/topico-03, que contém o site publicado (index.html, sobre.html e style.css).

## Criação do backup
Comando: tar -czvf ~/backups/backup-site-topico03.tar.gz -C /var/www/html topico-03

O backup é guardado em ~/backups, fora do repositório Git. Resultado:

    == Backup criado ==
    total 4.0K
    -rw-rw-r-- 1 kelby kelby 1.1K Nov 18 03:17 backup-site-topico03.tar.gz
    
    == Conteudo do backup ==
    drwxr-xr-x root/root         0 2026-11-14 04:05 topico-03/
    -rw-r--r-- root/root       617 2026-11-14 04:05 topico-03/sobre.html
    -rw-r--r-- root/root      1016 2026-11-14 04:05 topico-03/index.html
    -rw-r--r-- root/root       385 2026-11-14 04:05 topico-03/style.css

Checksum do backup (sha256sum):

    6288948b825251bbceb1deea62e883f98a09be9a0ad458acd3b2196091dbc0c4  /home/kelby/backups/backup-site-topico03.tar.gz

## Restauro numa pasta de teste
Comando: tar -xzvf ~/backups/backup-site-topico03.tar.gz -C ~/teste-restauro

O restauro foi feito numa pasta de teste (~/teste-restauro) e não sobre o site em produção, para não arriscar o serviço. Resultado:

    == Ficheiros restaurados ==
    total 12
    -rw-r--r-- 1 kelby kelby 1016 Nov 14 04:05 index.html
    -rw-r--r-- 1 kelby kelby  617 Nov 14 04:05 sobre.html
    -rw-r--r-- 1 kelby kelby  385 Nov 14 04:05 style.css
    
    == Comparacao com o original ==
    Identico ao original

## Conclusão
Os três ficheiros do site foram recuperados e a comparação com o original (diff -r) confirma que o conteúdo é idêntico. O backup é válido e a recuperação funciona.
