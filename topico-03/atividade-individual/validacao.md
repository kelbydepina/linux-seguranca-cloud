# Validação

## URLs testados
- http://localhost/topico-03/ (dentro da VM, com curl)
- http://localhost/topico-03/sobre.html (dentro da VM, com curl)
- http://localhost/topico-03/style.css (dentro da VM, com curl)
- http://localhost:8080/topico-03/ (navegador do Windows, via reencaminhamento de portas)

## Resultados dos testes
- Página inicial: resposta HTTP 200 OK.
- Página sobre.html: resposta HTTP 200 OK.
- style.css: resposta HTTP 200 OK com o tipo text/css; o estilo é aplicado no navegador.
- Ligações entre páginas: index.html liga a sobre.html e sobre.html liga de volta a index.html.

## Evidências
- evidencias/validacao-curl.txt (output dos testes com curl)
- Prints do navegador da página inicial e da página sobre (pasta evidencias)

## Observações
O teste no navegador foi feito a partir do Windows, através da porta 8080 do anfitrião reencaminhada para a porta 80 da VM.
