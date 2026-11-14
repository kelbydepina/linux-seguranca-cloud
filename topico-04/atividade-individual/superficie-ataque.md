# Superfície de ataque

## Serviço web usado no Tópico 3
Nginx, a publicar o site estático em /var/www/html/topico-03/ (porta 80).

## Serviços ativos
Estado dos serviços principais (systemctl is-active):

    == nginx ==
    active
    
    == ssh ==
    active

A lista completa de serviços em execução está em evidencias/servicos-ativos.txt.

## Portas em escuta (antes da firewall)
Output de sudo ss -tulpn:

    Netid State  Recv-Q Send-Q    Local Address:Port Peer Address:PortProcess                                                                         
    udp   UNCONN 0      0            127.0.0.54:53        0.0.0.0:*    users:(("systemd-resolve",pid=495,fd=18))                                      
    udp   UNCONN 0      0         127.0.0.53%lo:53        0.0.0.0:*    users:(("systemd-resolve",pid=495,fd=16))                                      
    udp   UNCONN 0      0      10.0.2.15%enp0s3:68        0.0.0.0:*    users:(("systemd-network",pid=685,fd=34))                                      
    udp   UNCONN 0      0             127.0.0.1:323       0.0.0.0:*    users:(("chronyd",pid=990,fd=4))                                               
    udp   UNCONN 0      0                 [::1]:323          [::]:*    users:(("chronyd",pid=990,fd=5))                                               
    tcp   LISTEN 0      511             0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1054,fd=5),("nginx",pid=1052,fd=5),("nginx",pid=1051,fd=5))
    tcp   LISTEN 0      4096      127.0.0.53%lo:53        0.0.0.0:*    users:(("systemd-resolve",pid=495,fd=17))                                      
    tcp   LISTEN 0      4096            0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=1315,fd=3),("systemd",pid=1,fd=104))                        
    tcp   LISTEN 0      4096         127.0.0.54:53        0.0.0.0:*    users:(("systemd-resolve",pid=495,fd=19))                                      
    tcp   LISTEN 0      511                [::]:80           [::]:*    users:(("nginx",pid=1054,fd=6),("nginx",pid=1052,fd=6),("nginx",pid=1051,fd=6))
    tcp   LISTEN 0      4096               [::]:22           [::]:*    users:(("sshd",pid=1315,fd=4),("systemd",pid=1,fd=105))                        

## Portas necessárias
- 22/TCP (SSH): necessária para a administração remota da VM.
- 80/TCP (HTTP): necessária para o site do Tópico 3.
- Portas em escuta apenas em 127.0.0.x (loopback) não são acessíveis a partir do exterior.
- A porta 443 (HTTPS) não é necessária, porque o HTTPS não está configurado.

## Riscos iniciais identificados
1. Firewall inativa: sem UFW, qualquer serviço que passe a escutar numa porta fica exposto sem controlo.
2. SSH exposto com autenticação por palavra-passe: sujeito a ataques de força bruta e de adivinhação de credenciais.
3. HTTP sem cifragem: o tráfego do site circula em texto claro e pode ser intercetado ou alterado.
4. Pacotes por atualizar: o sistema indicou dezenas de atualizações pendentes, o que pode deixar vulnerabilidades conhecidas por corrigir.
5. Informação do servidor visível: o Nginx pode revelar a versão nas respostas, o que ajuda um atacante a escolher exploits.

## Análise das portas observadas
- 22/TCP (sshd) e 80/TCP (nginx): escutam em 0.0.0.0 e em [::], ou seja, estão acessíveis a partir da rede. São as duas portas necessárias e as que ficam permitidas na firewall.
- 53 (systemd-resolved) em 127.0.0.53 e 127.0.0.54: serviço de resolução de nomes, apenas local (loopback), não acessível do exterior.
- 323/UDP (chronyd) em 127.0.0.1 e [::1]: sincronização da hora, apenas local (loopback).
- 68/UDP (systemd-network) na interface enp0s3: cliente DHCP, usado para obter o endereço IP, não é um serviço exposto.
