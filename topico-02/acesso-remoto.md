# Acesso remoto por SSH

## Estado do serviço SSH
O serviço SSH está: active (verificado com systemctl status ssh).

## Endereço identificado
10.0.2.15 fd17:625c:f037:2:a00:27ff:feeb:bde1  (rede NAT do VirtualBox, apenas visível dentro da VM).

## Comando de ligação
    ssh -p 2222 kelby@127.0.0.1

A ligação usa o reencaminhamento de portas do VirtualBox: porta 2222 do Windows para a porta 22 da VM.

## Resultado obtido
Ligação efetuada com sucesso a partir do PowerShell do Windows, com autenticação por palavra-passe.

## Limitações encontradas
O IP 10.0.2.15 é privado (modo NAT), por isso não é possível ligar diretamente a esse endereço a partir do Windows; foi necessário configurar o reencaminhamento de portas.
