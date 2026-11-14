# Firewall (UFW)

## Estado inicial
O UFW estava inativo antes das alterações (sudo ufw status verbose):

    Status: inactive

## Regras aplicadas
| Porta | Protocolo | Serviço | Decisão | Justificação |
|---|---|---|---|---|
| 22 | TCP | SSH | Permitir | Necessária para a administração remota; foi permitida antes de ativar o UFW para não perder o acesso. |
| 80 | TCP | HTTP (Nginx) | Permitir | Necessária para o site publicado no Tópico 3. |
| 443 | TCP | HTTPS | Não aberta | O HTTPS não está configurado, por isso a porta não é aberta. |

Política por omissão: deny incoming (o que não é permitido é bloqueado) e allow outgoing.

## Comandos utilizados
    sudo ufw status verbose
    sudo ufw allow 22/tcp comment 'SSH'
    sudo ufw allow 80/tcp comment 'HTTP'
    sudo ufw show added
    sudo ufw enable
    sudo ufw status numbered

## Estado final
O UFW ficou ativo com as regras seguintes (sudo ufw status verbose):

    Status: active
    Logging: on (low)
    Default: deny (incoming), allow (outgoing), disabled (routed)
    New profiles: skip
    
    To                         Action      From
    --                         ------      ----
    22/tcp                     ALLOW IN    Anywhere                   # SSH
    80/tcp                     ALLOW IN    Anywhere                   # HTTP
    22/tcp (v6)                ALLOW IN    Anywhere (v6)              # SSH
    80/tcp (v6)                ALLOW IN    Anywhere (v6)              # HTTP
    

## Cuidado com o SSH
O acesso SSH foi permitido antes de ativar a firewall. Num servidor remoto, ativar o UFW sem esta regra cortaria a ligação e deixaria o servidor inacessível.
