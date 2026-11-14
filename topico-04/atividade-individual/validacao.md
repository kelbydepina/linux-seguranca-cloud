# Validação

## Estado da firewall
UFW ativo, com as regras 22/tcp e 80/tcp (ver firewall.md e evidencias/ufw-depois.txt).

## Testes realizados
1. SSH: foi aberta uma segunda ligação SSH ao servidor depois de ativar o UFW e funcionou.
2. Site no navegador do Windows: http://localhost:8080/topico-03/ e http://localhost:8080/topico-03/sobre.html abriram corretamente, com o CSS aplicado. Este teste passa pela firewall.
3. curl dentro da VM: http://localhost/topico-03/ devolveu o resultado seguinte.

    HTTP/1.1 200 OK

## Evidências
- evidencias/ufw-antes.txt e evidencias/ufw-depois.txt
- evidencias/portas-antes.txt
- evidencias/curl-antes.txt e evidencias/curl-depois.txt
- Prints do UFW, da segunda ligação SSH e do site no navegador

## Observações
O curl dentro da VM usa a interface de loopback, que o UFW permite por omissão; por isso o teste no navegador do Windows é o que confirma que a porta 80 está realmente permitida. A porta 443 não foi aberta, porque o HTTPS não está configurado.
