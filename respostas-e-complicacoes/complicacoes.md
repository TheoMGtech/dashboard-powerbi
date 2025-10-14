## Dúvidas, Dificuldades e Descobertas (Missão Dashboard Power BI)

**1. Complicações Iniciais com Acesso e Repositório (Setup)**

* **Problema de Caminho Absoluto (File or Folder Error):** A principal dificuldade inicial foi o erro de não conseguir encontrar os arquivos de dados (`fVendas.xlsx`, etc.) após clonar o repositório Git. O arquivo `.pbix` original utilizava caminhos absolutos do criador (`C:\Users\giovannavicentin-ieg\...`) que não existiam em nossa máquina.
    * **Solução Aplicada:** Implementação de um **Parâmetro de Caminho (`RootFolder`)** no Power Query. Isso permitiu que o projeto buscasse os arquivos na nova estrutura de pastas local (`\dados\`) de forma genérica, solucionando a portabilidade do projeto.
* **Ajuste da Função Auxiliar de Carga (Binary to Text):** Foi necessário corrigir a consulta auxiliar gerada automaticamente (`Transformar Arquivo`), alterando o tipo do parâmetro de entrada de `text` para **`binary`** (`(CaminhoDados as binary)`) para que a função `Csv.Document` pudesse processar o conteúdo binário dos arquivos corretamente.

**2. Dificuldades de Qualidade e Granularidade de Dados**

* **Inconsistência de IDs de Loja (O Grande Desafio):** As vendas por cidade (CSVs) apresentavam `LojaID` internos (ex: 980, 1520) que **não correspondiam** aos IDs de dimensão (`idLoja` de 1 a 7) da tabela `dLojas`. A única ponte possível era o nome da Cidade/Estado.
    * **Solução Aplicada:** Realizamos a **Mesclagem (Merge)** dos CSVs de vendas com `dLojas` utilizando a coluna **`Cidade/Nome da Loja`** como chave, para injetar o `idLoja` correto (1 a 7) antes da anexação.
* **Fragmentação Temporal (Análise de Linha):** O conjunto de dados completo possui dados concentrados em 2018 (`fVendas`) e dados muito esparsos (pontos isolados) em 2014, 2015, 2016 e 2017 (CSVs por cidade).
    * **Implicação:** Isso inviabilizou a criação de um "Gráfico de Linha mostrando desempenho anual" (conforme o Passo 5), pois os vazios temporais tornariam a linha enganosa. Optamos por usar um Gráfico de Dispersão, que representa de forma mais honesta apenas os pontos de dados anuais registrados.
* **Chaves de Dimensão Faltantes:** Os CSVs de cidade não continham as colunas cruciais **`idProduto`** e **`idVendedor`**.
    * **Solução Aplicada:** Inserção de colunas com valor **`null`** para `idProduto` e `idVendedor` nos CSVs por cidade, permitindo o Anexamento (Append) vertical das tabelas. No entanto, as vendas nessas linhas permaneceram sem contexto de Produto e Vendedor.

**3. Solução Alternativa Pensada (Mas Não Aplicada)**

A dupla considerou uma alternativa mais complexa de modelagem para lidar com a diferença de granularidade das lojas, mas não a aplicou devido a dúvidas sobre a sua necessidade e complexidade no escopo do exercício:

* **Plano Alternativo:**
    1.  **Mesclar e Anexar Incial:** Consolidar a tabela principal (`fVendas`) com os CSVs de cidade, criando uma única tabela de vendas gerais (`Fato_Vendas_Total`).
    2.  **Tratamento do `dLojas`:** Criar novos registros na tabela `dLojas` para incluir todos os nomes das cidades dos CSVs (se não existissem), usando o `idLoja` de 1 a 7.
    3.  **Agrupamento para Simular Nível Alto (O Ponto de Dúvida):** Fazer um **Agrupamento (Group By)** nos CSVs de cidade por `Data` e `Cidade`, **somando a `Quantidade` e o `Valor`** de todas as vendas das filiais (os `LojaID` internos).
    4.  **Objetivo do Agrupamento:** Isso agregaria as vendas de todas as filiais (ex: 980, 981, 982) de Curitiba para uma única linha de Curitiba/Dia, simulando o nível da dimensão `dLojas` (cidade/estado), assumindo que os `LojaID` internos representam filiais que precisam ser totalizadas.
* **Motivo da Não Aplicação:** O agrupamento introduziria perdas de detalhes de transação e simplificaria demais a base de Fato, o que não parecia o caminho mais direto. Optamos manter o uso de fVendas, para atingir maior quantidade de requisitos, principalmente porque não conseguimos tirar essa dúvida.