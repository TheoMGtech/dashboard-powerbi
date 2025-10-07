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

- [ ] Todos arquivos do Excel foram importados
- [ ] Dados transformados e limpos
- [ ] Relacionamentos entre tabelas funcionando
- [ ] Medidas DAX criadas e testadas
- [ ] Todos os gráficos e filtros implementados como no dashboard-alvo
- [ ] Visuais bonitos, organizados e funcionais
- [ ] Documentação clara sobre dúvidas, dificuldades e descobertas
- [ ] Pasta .zip organizada com todos arquivos e link do GitHub
- [ ] Respostas do item análise
- [ ] Entrega realizada no Teams da turma


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

1. 🏆 **Qual loja teve o maior faturamento total no período? Como você chegou a esse resultado usando os relatórios?**
R: 

2. 📈 **Existe alguma cidade/estado que apresentou queda constante nas vendas ao longo dos anos? Mostre usando o gráfico de linha!**
R: 

3. 🎯 **Qual produto foi o mais vendido em quantidade ao longo de todo o histórico de vendas? Como comparar entre categorias?**
R: 

4. 💵 **Qual vendedor realizou a maior quantidade de vendas? E qual teve o maior valor faturado? Mude os filtros e mostre!**
R:

5. 🛒 **Em que mês e ano ocorreu o pico histórico de vendas totais? Altere os filtros de data e explique o contexto.**
R:

6. ❗ **Alguma loja teve vendas zeradas ou abaixo da meta mensal prevista? Demonstre utilizando o gráfico de cartão e dMetas.xlsx.**
R:

7. ⚖️ **Existe grande variação de preços entre produtos vendidos em diferentes estados? Analise gráficos de dispersão e mapas!**
R:

8. 🌈 **Quais são os top 3 produtos por receita (quantidade x preço) e como sua venda se distribui entre as cidades?**
R:

9. 🔄 **Aumentando o filtro para apenas produtos com vendas acima da média, quais lojas continuam entre as melhores colocadas?**
R:

10. ⏳ **Como foi o desempenho ano a ano de um vendedor específico? Selecione no filtro e analise no gráfico de linha.**
R:
