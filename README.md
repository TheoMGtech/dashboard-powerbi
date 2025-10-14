  # Missão Dashboard Power BI: Turbinando Conhecimento! 🚀✨📊

## Objetivo Geral 🎯

Formem duplas (sorteadas pelo professor!) para embarcar numa aventura tecnológica criando um dashboard interativo no Power BI, igualzinho ao modelo referência. Explorando os arquivos **fVendas.xlsx**, **dLojas.xlsx**, **dVendedor.xlsx** e **dProdutos.xlsx**, vocês irão aprender desde a manipulação até visualização de dados. O resultado é entregar um painel inteligente, bonito, funcional e colaborativo! 🤓⚡

---

## Passo 1 – Importação dos Arquivos 📥🗂️

- Abra o Power BI Desktop.
- Clique em “Obter Dados” ➡️ “Excel”.
- Selecione e importe INDIVIDUALMENTE:
  - **fVendas.xlsx** (base com dados de vendas)
  - **dLojas.xlsx** (informações das lojas)
  - **dProdutos.xlsx** (lista de produtos cadastrados)
  - **dVendedor.xlsx** (cadastro dos vendedores)
- Confirme os nomes das tabelas importadas, renomeando para padronizar e facilitar tudo!

🔍 *Dica de dupla*: uma pessoa importa enquanto a outra lê e anota dúvidas, sugestões ou problemas percebidos!

---

## Passo 2 – Limpeza e Transformação ETL 🧹🤖

- Abra “Transformar Dados” para acessar o Power Query.
- Para TODAS as tabelas:
  - Use “Promover primeira linha para cabeçalho” 🚩
  - Exclua linhas e colunas em branco com “Remover” 🚫
  - Remova linhas com erro usando o menu superior ⚠️
- **dLojas.xlsx**
  - Faça a separação entre nome da loja e sigla do estado usando “Dividir Coluna” > por delimitador (espaço ou hífen).
  - Renomeie a nova coluna para “Estado” 🇧🇷
- **dVendedor.xlsx**
  - Crie a coluna “Nome Completo” com “Coluna de Exemplo” juntando Nome + Sobrenome.
  - Delete as colunas “Nome” e “Sobrenome” antigas!

🧑‍🤝‍🧑 *Alternem funções*: quem transformou uma tabela, agora verifica e revisa a próxima!

---

## Passo 3 – Modelagem Relacional: Conectando Pontos! 🔗🧭

- No menu “Modelagem”, conecte os campos:
  - **fVendas[ID Loja] → dLojas[ID Loja]**
  - **fVendas[ID Produto] → dProdutos[ID Produto]**
  - **fVendas[ID Vendedor] → dVendedor[ID Vendedor]**
- Essas conexões permitem que vocês cruzem todas as infos, transformando tabelas “sozinhas” em uma fonte única de conhecimento!

❓ *Desafio*: cada dupla simula um relacionamento errado para visualizar o impacto: gráficos quebrados ou números sem sentido!

---

## Passo 4 – Criando Medidas DAX: Matemática dos Dados 💡🧮

No campo de medidas, criem:

```DAX
Total Geral Vendas = SUMX(fVendas, fVendas[Quantidade Vendida] * fVendas[Preço do Produto])
Total Produtos Vendidos = SUM(fVendas[Quantidade Vendida])
Média Produtos Vendidos = AVERAGE(fVendas[Quantidade Vendida])
Mínimo Produtos Vendidos = MIN(fVendas[Quantidade Vendida])
Máximo Produtos Vendidos = MAX(fVendas[Quantidade Vendida])
```

🔎 *Explicação*:

- **SUMX** soma resultado da multiplicação em cada linha, ideal para calcular faturamento.
- **SUM** para somar as quantidades, **AVERAGE** encontra média, e **MIN/MAX** revelam extremos.
- Ao final, cada dupla explica oralmente para o colega a lógica de cada medida!

---

## Passo 5 – Construindo o Super Dashboard! 🌈📊🗺️

Replicando o modelo da imagem, insiram:

- Cartões para indicadores por cidade e total geral 💳🏙️
- Gráfico de rosca/pizza com % por cidade 🍩
- Gráfico de colunas do total vendido por loja/estado 🏢📈
- Treemap para desempenho de vendas por loja 🍃
- Gráfico de linha mostrando desempenho anual 📉📆
- Mapa coroplético para vendas por estado 🗺️🎨
- Mapa de bolhas destacando estados/cidades 🫧
- Filtros e segmentações para navegação rápida 🧭🎛️
- Botão “Limpar segmentações” para reiniciar tudo 🔄

🖌️ Personalizem cores, títulos e legendas! Testem cada exemplo de filtro juntos e avaliem se os dados estão mudando corretamente.

---

## Passo 6 – Organização e Entrega 🚀📦📝

- Todos os arquivos (Excel originais, .pbix, documentação .md ou .txt) devem estar ENTRADOS numa pasta .zip chamada:
  - exemplo: aluno01_aluno02.zip
- Inclua dentro desta pasta um arquivo de texto com o **link do repositório GitHub da equipe** 💻🌎
- Publique tudo no Teams da turma, conforme combinado em aula 🔗📲

---

## Checklist Final ✔️✅🎉

- [x] Todos arquivos do Excel foram importados
- [x] Dados transformados e limpos
- [x] Relacionamentos entre tabelas funcionando
- [x] Medidas DAX criadas e testadas
- [x] Todos os gráficos e filtros implementados como no dashboard-alvo
- [x] Visuais bonitos, organizados e funcionais
- [x] Documentação clara sobre dúvidas, dificuldades e descobertas
- [x] Pasta .zip organizada com todos arquivos e link do GitHub
- [x] Respostas do item análise
- [x] Entrega realizada no Teams da turma


---

## Extras para os Curiosos 🌟🔍🦾

- Experimente criar filtros por período, vendedor ou produto!
- Teste outras cores para os gráficos, mapas e treemaps 🟩🟦🟨
- Crie um visual diferente (inventado pela dupla) e explique sua utilidade para a turma

---

## Conceitos Aprendidos 🧠💥

- **ETL:** Limpeza, transformação e organização dos dados
- **Power Query:** Ferramenta de ajuste e preparação
- **Modelagem:** Relações que geram contexto e inteligência
- **DAX:** Fórmulas e medidas avançadas
- **Visualização:** Gráficos que facilitam a análise e comunicação dos dados
- **Peer Programming:** Colaboração, revisão e aprendizado conjunto


***

### Desafios de Análise de Dados para a Dupla 🤔📊

#### 1. 🏆 Qual loja teve o maior faturamento total no período? Como você chegou a esse resultado usando os relatórios?

**R: A loja de São Paulo teve o maior faturamento total no período analisado.**

Chegamos a esse resultado analisando o visual **"Total de Vendas por Loja"** (Gráfico de Colunas) e o **Treemap**. Ambos os visuais, construídos a partir da tabela consolidada de Fato de Vendas (Vendas x Preço do Produto), mostram a loja de São Paulo no topo do ranking de receita.

* **Faturamento Total (Dados de 2018):** R$ 2.193.300,00
* **Loja Vencedora:** São Paulo

#### 2. 📈 Existe alguma cidade/estado que apresentou queda constante nas vendas ao longo dos anos? Mostre usando o gráfico de linha!

**R: Não é possível afirmar que houve queda constante nas vendas ao longo dos anos para qualquer cidade, e o Gráfico de Linha não é o visual ideal para mostrar este dado devido à fragmentação.**

A base de dados possui uma grande concentração de registros em 2018 (tabela `fVendas`) e dados esparsos e pontuais em anos anteriores (CSVs de cidade). Não há dados contínuos suficientes para traçar uma linha de tendência ou determinar uma "queda constante".

#### 3. 🎯 Qual produto foi o mais vendido em quantidade ao longo de todo o histórico de vendas? Como comparar entre categorias?

**R: O produto 'Vestido' foi o mais vendido em quantidade.**

Utilizamos o visual de **Gráfico de Colunas/Barras**, configurado para usar a medida `Total Produtos Vendidos` (SUM de Quantidade Vendida) no eixo de valores e a coluna `Produto` (tabela `dProdutos`) no eixo de categorias. Para comparar, basta selecionar outras categorias de produtos no filtro ou adicionar outra dimensão, como `idLoja`, ao visual.

* **Produto mais vendido (Quantidade - Base `fVendas`):** Vestido (Total: 9.948 unidades)

#### 4. 💵 Qual vendedor realizou a maior quantidade de vendas? E qual teve o maior valor faturado? Mude os filtros e mostre!

**R: Os vendedores Tayna Felipi e Patricia Coimbra foram os líderes em suas respectivas categorias na base principal.**

A análise se restringiu à base principal (`fVendas`) por falta de `idVendedor` nos CSVs das cidades.

* **Maior Quantidade Vendida:** **Tayna Felipi** (ID 15) com 1.761 unidades
* **Maior Valor Faturado:** **Patricia Coimbra** (ID 14) com R$ 399.715,00

#### 5. 🛒 Em que mês e ano ocorreu o pico histórico de vendas totais? Altere os filtros de data e explique o contexto.

**R: O pico histórico de vendas totais ocorreu em Março de 2018.**

Ao usar o filtro de data para visualizar o total de vendas por mês/ano, Março de 2018 apresentou a maior receita. Este mês pode ser analisado em maior profundidade no dashboard (usando filtros) para buscar contextos como promoções específicas, lançamentos de produtos ou desempenho de lojas e vendedores no período.

* **Faturamento Pico (Mar/2018 - Base `fVendas`):** R$ 1.341.685,00

#### 6. ❗ Alguma loja teve vendas zeradas ou abaixo da meta mensal prevista? Demonstre utilizando o gráfico de cartão e dMetas.xlsx.

**R: Sim, a maioria das lojas operou abaixo da meta estabelecida na base `dMetas`.**

Ao calcular o faturamento total e compará-lo com a coluna `Meta` do arquivo `dMetas.xlsx - Metas.csv`, todas as lojas, exceto Goiânia, ficaram abaixo de suas metas anuais (considerando que as metas são anuais e o faturamento é da base completa). Se a meta for **mensal**, todas as lojas estão muito abaixo.

* **Exemplo:** A loja de **Salvador** teve Faturamento de R$ 1.652.872,00 contra uma Meta de R$ 5.000.000, resultando em uma diferença negativa (abaixo da meta).

#### 7. ⚖️ Existe grande variação de preços entre produtos vendidos em diferentes estados? Analise gráficos de dispersão e mapas!

**R: Sim, há variações, mas elas são mais ligadas ao mix de produtos vendidos em cada local.**

A variação de preço é determinada pela coluna `Preço do Produto` na tabela `fVendas`. Ao usar um gráfico de dispersão (`Preço do Produto` vs. `idLoja`), nota-se que os preços mais altos (R$ 300,00) são vendidos em todas as lojas (todos os estados). O que muda é o volume ou a frequência com que esses produtos de alto valor são vendidos em cada estado.

#### 8. 🌈 Quais são os top 3 produtos por receita (quantidade x preço) e como sua venda se distribui entre as cidades?

**R: Os top 3 produtos por receita (Faturamento) são:**

1.  **Sapato** (ID 9)
2.  **Vestido** (ID 12)
3.  **Casaco** (ID 3)

**Distribuição:** Para visualizar a distribuição, utilizaria o visual **Treemap**, colocando `Produto` na hierarquia principal e `Loja` (ou `Cidade`) na hierarquia secundária, para mostrar o tamanho da venda de cada um desses 3 produtos em diferentes locais.

#### 9. 🔄 Aumentando o filtro para apenas produtos com vendas acima da média, quais lojas continuam entre as melhores colocadas?

**R: Considerando a 'média de quantidade vendida' (76.84 unidades), as lojas que vendem acima dessa média tendem a ser as mesmas líderes de faturamento.**

As lojas de **São Paulo**, **Porto Alegre** e **Brasília** (as top 3 por faturamento) provavelmente continuariam no topo ou próximas a ele, pois elas concentram o maior volume de vendas em geral, o que indica que elas vendem bem tanto produtos acima quanto abaixo da média. O filtro atua apenas consolidando o mix de produtos vendido.

#### 10. ⏳ Como foi o desempenho ano a ano de um vendedor específico? Selecione no filtro e analise no gráfico de linha.

**R: O desempenho dos vendedores só pode ser analisado em 2018 (ano de concentração da `fVendas`), com pontos isolados para os anos anteriores, devido à limitação dos dados.**

Ao selecionar um vendedor (ex: Tayna Felipi - ID 15) no filtro, o gráfico de Dispersão/Linha mostraria apenas uma linha de dados concentrada em 2018. Qualquer dado em anos anteriores (2014-2017) seria proveniente de registros em `fVendas` que, por acaso, caíram nesses anos. Essa visualização confirma a fragilidade da análise temporal no conjunto de dados completo.
