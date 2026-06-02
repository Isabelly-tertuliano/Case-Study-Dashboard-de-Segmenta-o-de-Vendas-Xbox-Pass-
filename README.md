# 📊 Case Study: Dashboard de Segmentação de Vendas (Xbox Pass)

Este repositório apresenta o desenvolvimento completo de um painel analítico construído no **Microsoft Excel**, desenhado para consolidar dados transacionais de assinaturas de games (Xbox Game Pass, EA Play e Minecraft) e transformá-los em inteligência de negócio orientada para retenção e receita recorrente.

---

## 🎯 O Desafio de Negócio (As Perguntas)

O objetivo principal foi criar uma ferramenta visual e dinâmica que respondesse centralizadamente a quatro perguntas estratégicas de faturamento e comportamento de consumo:

1. **Qual o faturamento total de vendas anuais** (contendo todas as assinaturas agregadas)?
2. **Qual o faturamento total dos planos anuais**, divididos estritamente entre assinaturas com **auto-renovação** e **não auto-renovação**?
3. **Qual o total de vendas** específico da assinatura **EA Play Season Pass**?
4. **Qual o total de vendas** específico da assinatura **Minecraft Season Pass**?

---

## 🛠️ Como o Dashboard foi Construído (Metodologia)

Para garantir performance, organização e uma interface limpa (conforme demonstrado em `image_c4cb63.png`), o projeto foi executado em três camadas lógicas de desenvolvimento:

### 1. Arquitetura e Organização das Abas
Em vez de misturar dados e gráficos na mesma tela, o arquivo foi modelado seguindo as melhores práticas de Business Intelligence, dividindo-se em:
* **`Bases`:** Onde ficam guardados os dados brutos e históricos de transações.
* **`Cálculos`:** A área técnica ("o motor") onde os dados foram limpos e processados utilizando tabelas dinâmicas e fórmulas de soma e contagem.
* **`Annual / Monthly / Quarterly`:** Abas de suporte para organizar as segmentações temporais.
* **`Assets`:** Centralização dos elementos visuais (logos e paleta de cores) para manter o arquivo leve e organizado.
* **`Dashboard`:** A camada visual de interação final do usuário.

### 2. Design de Interface (UI/UX)
Com os números validados, a interface foi desenhada focando na experiência do usuário final (*User Experience*):
* **Identidade Visual:** Uso da paleta de cores oficial da marca (tons de verde, cinza escuro e branco) para gerar conexão visual imediata com o tema (Xbox).
* **Cards de KPI de Alto Impacto:** Posicionamento estratégico no topo da tela com logos oficiais para leitura instantânea do faturamento de cada ecossistema.
* **Filtros Dinâmicos (Segmentadores):** Inserção de uma barra lateral para alternar instantaneamente entre visões anuais, mensais ou trimestrais, atualizando todo o painel com um clique.

---

## 📖 Instruções para Reprodução Passo a Passo

Caso queira replicar este projeto do zero ou atualizar a base de dados existente, siga as instruções abaixo:

### Passo 1: Preparação da Base de Dados (`Bases`)
1. Insira os novos dados transacionais na aba `Bases`.
2. Certifique-se de que a tabela possui as colunas estruturadas corretamente: `Data da Venda`, `Produto (Assinatura)`, `Valor (R$)`, `Tipo de Plano (Anual/Mensal)` e `Auto-Renovação (Yes/No)`.

### Passo 2: Construção do Motor de Cálculos (`Cálculos`)
Para responder às perguntas de negócio sem pesar o painel visual, acesse a aba `Cálculos` e aplique as seguintes fórmulas:

* **Para o Faturamento Total de Xbox (Pergunta 1):**
  Use a fórmula de soma total da coluna de receita para consolidar o montante geral:
  ```excel
  =SOMA(Bases!C:C) 
Para as Vendas de EA Play e Minecraft (Perguntas 3 e 4):
Aplique a função SOMASE para filtrar o faturamento exato pelo nome do produto: ``` excel
=SOMASE(Bases!B:B; "EA Play Season Pass"; Bases!C:C)
=SOMASE(Bases!B:B; "Minecraft Season Pass"; Bases!C:C)

** Para a Segmentação de Auto-Renovação dos Planos Anuais (Pergunta 2):
Crie uma Tabela Dinâmica apontando para a sua base de dados. Colete o campo Auto-Renovação para as Linhas (Yes e No), filtre o Tipo de Plano para conter apenas "Anual" e adicione o campo de Valor em Valores (configurado como Soma).

## Passo 3: Montagem dos Gráficos e Vínculos no Dashboard
Na aba Dashboard, crie as formas geométricas (retângulos com cantos arredondados) para servirem de fundo para os cartões (Cards) e para o gráfico.

Vinculando os KPIs: Clique em cima do texto descritivo do valor do Card, vá até a barra de fórmulas do Excel, digite = e clique na célula correspondente lá na aba de Cálculos. Isso garante que o valor seja dinâmico.

Inserindo o Gráfico: Selecione a tabela dinâmica de Auto-Renovação que você criou no Passo 2, vá em Inserir > Gráficos > Gráfico de Barras Horizontais. Recorte o gráfico gerado e cole-o na aba Dashboard.

Adicionando a Segmentação de Dados (Slicer): Clique no seu gráfico, vá na guia Análise de Gráfico Dinâmico > Inserir Segmentação de Dados e escolha o campo de período desejado. Posicione-o na barra lateral esquerda (área verde do layout).

## 📈 Análise do Relatório (Insights de Negócio obtidos)
Abaixo está o diagnóstico gerencial extraído a partir da leitura dos dados consolidados no painel:

Concentração de Receita (Market Share interno): O ecossistema Minecraft Season Pass demonstrou uma força expressiva de vendas (R$ 3.880,00), superando isoladamente a receita gerada pela EA Play (R$ 2.940,00). Isso indica uma alta aderência do produto e uma base de usuários muito activa no período apurado.

O Gargalo da Retenção (Comportamento de Renovação): O gráfico de barras horizontais "Total de Vendas XBOX GAME PASS – COM E SEM PLANOS ANUAIS" revela um equilíbrio perigoso: o faturamento de planos sem renovação automática (No: R$ 3.847,00) é ligeiramente maior do que os com renovação ativa (Yes: R$ 3.786,00).

Recomendação Estratégica de CRM: Como quase 50% do faturamento anual está concentrado em usuários que não possuem renovação automática ativa, há um risco latente de churn (cancelamento). A recomendação acionável baseada neste relatório é disparar réguas de relacionamento automatizadas focadas em incentivar a mudança para o modelo de auto-renovação antes do término do ciclo anual desses clientes.

💻 Competências Demonstradas neste Projeto
-Data Analytics & Business Intelligence: Transformação de dados brutos em decisões de negócios.

-Advanced Excel: Fórmulas lógicas, condicionais (SOMASE), tabelas dinâmicas e segmentadores de dados.

-Data Visualization & UI/UX: Construção de layouts corporativos fluidos, escaneáveis e temáticos.

👩‍💻 Autora
Isabelly - Profissional de CRM - Linkedin: www.linkedin.com/in/
isabellytertuliano


