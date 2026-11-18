# Monitorização do sistema

## Ambiente
VM local (VirtualBox) com Ubuntu Server 26.04.1 LTS e Nginx.

## Tempo de atividade e carga (uptime)
Mostra há quanto tempo o sistema está ligado e a carga média (últimos 1, 5 e 15 minutos):

     03:11:54 up 5 min,  2 users,  load average: 0.02, 0.12, 0.08

## Memória (free -h)

                   total        used        free      shared  buff/cache   available
    Mem:           1.6Gi       377Mi       1.0Gi       1.1Mi       380Mi       1.2Gi
    Swap:             0B          0B          0B

## Espaço em disco (df -h /)

    Filesystem      Size  Used Avail Use% Mounted on
    /dev/sda2        25G  3.2G   21G  14% /

## Serviço web (Nginx)
Estado (systemctl is-active nginx):

    active

Detalhe (systemctl status nginx):

    ● nginx.service - A high performance web server and a reverse proxy server
         Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
         Active: active (running) since Wed 2026-11-18 03:06:53 UTC; 5min ago
     Invocation: 63487caa55c4407db3dd25c6df1158fd
           Docs: man:nginx(8)

## Interpretação
No momento da recolha não foram observados sinais de sobrecarga: a carga média, a memória disponível e o espaço livre em disco estão em valores normais para esta VM, e o Nginx está ativo. Estes comandos devem ser repetidos com regularidade, para detetar tendências como o disco a encher ou o aumento da carga.
