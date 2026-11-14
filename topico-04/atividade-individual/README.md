# Atividade prática individual - Tópico 4

## Nível realizado
Nível 2 - Intermédio (inclui a identificação de serviços e portas do Nível 1 e uma proposta de hardening)

## Objetivo
Aplicar medidas iniciais de segurança ao serviço publicado no Tópico 3: identificar portas e serviços, configurar a firewall UFW e validar o serviço.

## Ambiente utilizado
VM local (VirtualBox) com Ubuntu Server 26.04.1 LTS e Nginx

## Ficheiros criados
- superficie-ataque.md
- firewall.md
- hardening.md
- validacao.md
- comandos.txt
- evidencias/

## Evidências produzidas
Outputs do ss, do UFW (antes e depois) e do curl, e prints do UFW ativo, da segunda ligação SSH e do site no navegador.

## Dificuldades encontradas
Garantir que o acesso SSH não era cortado ao ativar o UFW, permitindo a porta 22 antes de ativar a firewall.

## Link do repositório GitHub
https://github.com/kelbydepina/linux-seguranca-cloud/tree/main/topico-04/atividade-individual

## Próximos passos
Configurar HTTPS, reforçar o SSH (chaves e proteção contra força bruta), ativar logs e monitorização e criar cópias de segurança.
