# Manutenção

## Atualizações pendentes
Número de pacotes com atualização disponível (apt list --upgradable):

    50

## Rotina de manutenção proposta
- Semanal: verificar o espaço em disco, a memória e o estado do Nginx.
- Semanal: rever os logs de SSH e de Nginx à procura de acessos anormais.
- Mensal: aplicar as atualizações pendentes (sudo apt update e sudo apt upgrade) e reiniciar se for necessário.
- Antes de cada alteração importante: criar um backup do site.

## Nota
As atualizações não foram aplicadas nesta atividade, para não alterar o ambiente durante a avaliação; ficam como tarefa de manutenção planeada.
