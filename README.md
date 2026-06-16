# Painel BI CABW — V3 Standalone

Esta versão corrige o problema de abertura do HTML isolado: todo o CSS, JavaScript e os dados extraídos das planilhas estão embutidos em `index.html`.

## Como abrir

Abra diretamente `index.html` no navegador. Não é necessário servidor local, bibliotecas externas ou arquivos auxiliares.

## Fontes processadas

- requisicoes.xlsx: 21,823 registros analíticos
- ordem_de_compra.xlsx: 7,372 registros analíticos
- volumes.xlsx: 16,153 registros analíticos
- nl_requisicao.xlsx: 15,414 registros analíticos
- controle_financeiro_contratos.xlsx: 136 registros analíticos
- digitos.xlsx: 268 registros analíticos; a linha TOTAIS foi ignorada para evitar duplicidade de leitura

## Conteúdo

Abas: Visão geral, Requisições, Ordens de compra, Financeiro, Logística, NL & pagamentos, Compatibilização entre Créditos e Mapas e Transparência & dados.

Recursos: filtros globais por ano/projeto/status, busca textual, gráficos em HTML/CSS, tabelas detalhadas, exportação CSV por tabela, exportação JSON da base filtrada, modo alto contraste e impressão/PDF.


Correção: o snapshot operacional exibido no painel foi ajustado para 2026-06-08; os vencimentos futuros dos contratos seguem preservados na aba Financeiro.


## Atualização v3.8
- Aba Dígitos reposicionada com gráficos de crédito disponível e mapa aprovado logo abaixo dos cards.
- Incluídas ferramentas para exportar PDFs de solicitação de empenho e sugestão de realocação de saldos.

## Atualização v3.12
- Corrigido o sublinhado integral do nome por extenso da UG Requisitante nos PDFs de solicitação de empenho e realocação de saldos.
- Incluída visão gerencial diretamente no painel de Compatibilização entre Créditos e Mapas, abaixo dos gráficos comparativos e acima das ferramentas de geração de relatórios.
- Sugestões de empenho imediato agora exigem compatibilidade simultânea de UG Requisitante, natureza de despesa, projeto e valor disponível.

## Atualização v3.13

- Corrigido o filtro **Tipo do processo**.
- A classificação **Contrato** considera registros cujo `PAG` ou `COTAÇÃO` coincide com a coluna `CONTRATO` da base de contratos.
- Quando a base filtrada não possui o campo direto, o vínculo é inferido por PO ou requisição associada.
## Atualização v3.14

- Aba orçamentária renomeada para Compatibilização entre Créditos e Mapas.
- Gráficos de dotação ajustados para exibir saldo disponível.
- Gráfico por Unidade Requisitante passa a empilhar valor de PO empenhada e crédito disponível, com tooltips de requisições/objetos e dígitos/objetivos.
