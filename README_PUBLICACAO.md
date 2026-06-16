# Publicação do Painel BI CABW na internet

Este pacote está pronto para hospedagem estática. O site principal é `index.html` e já contém CSS, JavaScript e dados embutidos.

## Atenção antes de publicar

O `index.html` contém dados extraídos das planilhas Excel. Ao publicar em GitHub Pages, Netlify, Vercel, Cloudflare Pages ou outro serviço público, qualquer pessoa com o link poderá acessar esses dados. Use uma hospedagem com autenticação, firewall, VPN ou controle de acesso caso os dados sejam internos ou sensíveis.

O arquivo `robots.txt` foi incluído com `Disallow: /` para reduzir indexação por buscadores, mas isso não protege o conteúdo contra acesso direto ao link.

## Opção 1 — Netlify Drop, método mais rápido

1. Acesse sua conta Netlify.
2. Abra a área Netlify Drop.
3. Arraste a pasta `cabw-bi-publicacao` inteira para a área de upload.
4. Ao final do deploy, a Netlify exibirá uma URL pública terminada em `.netlify.app`.
5. Teste a URL abrindo as abas e conferindo se KPIs, gráficos e tabelas aparecem preenchidos.

## Opção 2 — Cloudflare Pages, upload direto

1. Acesse Cloudflare Dashboard > Workers & Pages.
2. Crie uma aplicação usando a opção de upload/drag and drop.
3. Informe o nome do projeto e envie a pasta `cabw-bi-publicacao`.
4. O site ficará disponível em uma URL `pages.dev`.

## Opção 3 — GitHub Pages

1. Crie um repositório no GitHub, por exemplo `cabw-bi`.
2. Envie todo o conteúdo desta pasta para a branch `main`.
3. No repositório, acesse Settings > Pages.
4. Configure a publicação por GitHub Actions, usando o workflow já incluído em `.github/workflows/pages.yml`, ou configure Deploy from branch usando `main` e `/root`.
5. Aguarde a execução do workflow ou publicação da branch.
6. O endereço ficará no formato `https://USUARIO.github.io/cabw-bi/`, salvo se você configurar domínio próprio.

## Opção 4 — Vercel

1. Crie um projeto na Vercel.
2. Importe um repositório Git contendo estes arquivos ou use a CLI a partir da raiz desta pasta.
3. Não há comando de build; a pasta raiz já é o diretório publicável.
4. A Vercel gerará uma URL de deploy automaticamente.

## Validação pós-publicação

- A página deve carregar sem erro de console.
- As abas devem alternar entre Visão geral, Requisições, Ordens de compra, Financeiro, Logística, NL & pagamentos, Compatibilização entre Créditos e Mapas e Transparência & dados.
- Os indicadores devem refletir os 61.166 registros analíticos embutidos.
- Os filtros por ano, projeto, status e busca textual devem alterar gráficos e tabelas.

## Arquivos incluídos

- `index.html`: site completo e autocontido.
- `README.md`: descrição técnica do painel.
- `README_PUBLICACAO.md`: este guia de publicação.
- `.nojekyll`: evita processamento Jekyll no GitHub Pages.
- `robots.txt`: solicita não indexação por buscadores.
- `netlify.toml`: configuração opcional para Netlify.
- `vercel.json`: configuração opcional para Vercel.
- `.github/workflows/pages.yml`: workflow opcional de GitHub Pages.


## Atualização 3.1.0

- Filtros de ano e projeto ajustados para exibir apenas valores com dados efetivos de requisições/planilhas operacionais.
- Filtro de projeto removendo opções artificiais 01-99 sem requisições.
- Inclusão de aba dedicada Contratos, com separação em administrativos (GC=CW), FMS (CAGE W2525) e finalísticos.
- Inclusão de filtro de unidade requisitante e vigência.
- Gráficos e tabelas de unidade usam sigla operacional conforme descricao_OM.xlsx.

Observação: o pacote standalone recebido não contém a coluna analítica DATA ASSINATURA nos registros compactados de contratos; o filtro de ano dos contratos usa a data final/vigência disponível no HTML embutido.


## Atualização 3.2.0

- Visão Geral: indicador de contratos ajustado para contar contratos assinados no período quando a coluna DATA ASSINATURA estiver embutida; no pacote atual, sem essa coluna compactada, usa a data final disponível.
- Visão Geral: valor total dos contratos apresentado no formato US$ com vírgula para milhar e ponto decimal.
- Visão Geral: gráfico de requisições por status exibe quantidade e percentual.
- Visão Geral: volumes estratificados por sigla da unidade requisitante.
- Visão Geral: PO por mês com rótulos de quantidade e valor total.
- Visão Geral: execução financeira por ano para saldo de PO e NL pago.
- Visão Geral: adicionados Controle de RP geral e Controle de RP de Contratos.
- Financeiro: removido o indicador Cobertura NL/PO.


## Atualização v3.3

Pacote regenerado a partir das planilhas originais reencaminhadas, incluindo DATA ASSINATURA e COTAÇÃO para contratos e controles de RP.


## Atualização v3.4
- Filtros globais com múltipla seleção.
- Visão Geral: volumes por OM via dois primeiros caracteres da requisição do volume.
- Execução financeira: valor total de PO criadas e saldo de PO não faturado por ano.
- RP Requisições: saldo de POs com PAG não cadastrado como contrato, por projeto, unidade e ano.
- RP de Contratos: agrupamento por número do contrato, empresa e ano, com objeto resumo no tooltip.

## Atualização v3.5
- Filtros globais convertidos para dropdown com checkboxes, mantendo múltipla seleção sem exibir a lista permanentemente.
- RP Requisições: tooltip passa a mostrar número da requisição e até os primeiros 30 caracteres da descrição do objeto associado.

## Atualização v3.6
- Visão Geral: gráfico alterado para Volumes por destino, usando a OM requisitante identificada pela requisição real em `volumes.xlsx` x `requisicoes.xlsx`, com fallback por `PAG` x `COTAÇÃO` quando aplicável e sem classificar códigos logísticos não requisitantes como OM.
- Visão Geral: tooltip do RP Requisições ampliado para até 100 caracteres da descrição do objeto.
- Financeiro/NL & pagamentos: gráfico Top POs pagos substituído por Top Fornecedores, agrupado pelo fornecedor da PO vinculada.
- NL & pagamentos: incluído card de tempo médio entre `DATA REC` do volume e `DATA` da NL de pagamento.
- NL & pagamentos: gráfico Quantidade comprada x ref. fatura substituído pela evolução mensal do tempo médio até pagamento, do mês mais recente para o mais antigo.


## Atualização v3.8
- Aba Dígitos reposicionada com gráficos de crédito disponível e mapa aprovado logo abaixo dos cards.
- Incluídas ferramentas para exportar PDFs de solicitação de empenho e sugestão de realocação de saldos.

## Atualização v3.12
- Corrigido o sublinhado do nome completo da UG Requisitante nos PDFs gerados pela aba Compatibilização entre Créditos e Mapas.
- Acrescentada visão gerencial no painel, junto às ferramentas de geração dos relatórios, com potencial de empenho imediato e potencial de realocação.
- A compatibilidade das sugestões considera UG Requisitante, natureza de despesa, projeto e valor.

## Atualização v3.13

- Corrigido o filtro **Tipo do processo** para separar corretamente requisições, POs, volumes e NLs de **Contrato** e **Varejo**.
- Registros de contrato são identificados por correspondência entre `PAG`/`COTAÇÃO` e `CONTRATO`, com relacionamento intermediário por requisição e ordem de compra quando necessário.
## Atualização v3.14

- Aba orçamentária renomeada para Compatibilização entre Créditos e Mapas.
- Gráficos de dotação ajustados para exibir saldo disponível.
- Gráfico por Unidade Requisitante passa a empilhar valor de PO empenhada e crédito disponível, com tooltips de requisições/objetos e dígitos/objetivos.
