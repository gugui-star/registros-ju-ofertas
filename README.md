# Registros Ju

App simples (PWA, funciona offline no iPhone) para a mãe do Gustavo:
- **Supermercado**: lista de compras, registro de compras e **Promoções** da semana (Lages-SC).
- **Pagamentos**: contas a pagar (empresa, valor, vencimento) e registro de pagos.

## Como é organizado
- `promocoes.json` (raiz): ofertas da semana. O app lê este arquivo direto daqui
  (`https://raw.githubusercontent.com/gugui-star/registros-ju-ofertas/main/promocoes.json`).
  Atualizar este arquivo atualiza o app sem publicar nada.
- `app/`: código do app (index.html com todo o CSS/JS, sw.js, manifest, ícones).
  `app/promocoes.json` é só uma cópia de reserva; a que vale é a da raiz.
- Os dados da usuária (lista, compras, contas) ficam só no navegador do celular dela (localStorage). Nada é enviado para cá.

## Hospedagem do app
O app é publicado como site estático no Netlify (pasta `app/`). Para mudar o código: editar `app/` e publicar a pasta de novo no mesmo site, para manter o endereço e os dados.

## Formato do promocoes.json
`{atualizado, mercados:[{id,nome,link,nota}], itens:[{produto,mercado,preco,precoAntes?,desconto?,validade?,fonte,obs?,variantes?}]}`
Ofertas com `validade` vencida são escondidas pelo app. Atualizar o campo `atualizado` com a data de hoje.
