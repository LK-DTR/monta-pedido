# Montador de Pedidos

Utilizando planilha no formato xlsx para o banco de dados do catálogo.

Site de página única para montar pedidos de clientes a partir de um catálogo de produtos, com conversão automática entre caixa e unidade e entre preço sem ST e com ST. Roda direto no navegador, sem servidor, e pode ser hospedado gratuitamente no GitHub Pages.

## Funcionalidades

- **Busca de produtos** por REF, nome ou categoria, sem diferenciar acentos ou maiúsculas, com filtro por categoria e navegação pelo teclado.
- **Quantidade em caixa ou unidade**, escolhida no cabeçalho da coluna. O site mostra sempre as duas medidas.
- **Preço por caixa ou por unidade, sem ST ou com ST**, também escolhido no cabeçalho da coluna. O site calcula o preço unitário e o da caixa nos dois formatos, além do total de cada item.
- **ST por categoria**, vinda do catálogo. Produtos sem ST cadastrada aparecem como "sem ST" e ficam sem preço com ST.
- **Totais do pedido**: unidades, caixas, total sem ST e total com ST.
- **Exportar planilha (.xlsx)** com as fórmulas de preço, que recalculam no Excel se você alterar quantidades, preços ou os modos de digitação.
- **Importar pedido** exportado pelo próprio site, para continuar ou ajustar um pedido depois.
- O pedido em andamento fica salvo no navegador de quem está usando.

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `index.html` | O site inteiro (não precisa ser editado). |
| `catalogo.xlsx` | O banco de dados do catálogo. É este arquivo que você atualiza. |
| `README.md` | Este documento. |

## O banco de dados: `catalogo.xlsx`

O site lê o `catalogo.xlsx` toda vez que abre. Os dados ficam na aba **BD** (ou na primeira aba da planilha), com o cabeçalho na primeira linha:

| Coluna | Descrição |
|---|---|
| `REF` | Código do produto (número, não pode repetir). |
| `Descrição` | Nome do produto. |
| `Un/Cx` | Unidades por caixa. |
| `EAN13` | Código de barras (opcional, o site não usa). |
| `ST` | ST do produto em porcentagem, por exemplo `12,5`. Se ficar vazia, o site mostra "sem ST". |
| `Categoria` | Categoria do produto. Categorias novas aparecem sozinhas no filtro. |

Se o `catalogo.xlsx` não puder ser lido, o site usa uma cópia reserva do catálogo que vai embutida no `index.html` e avisa no rodapé da página.
