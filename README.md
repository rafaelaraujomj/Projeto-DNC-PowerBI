# Desafio 1 - Preveja os resultados de um e-commerce utilizando o Power BI

## Contexto

Neste desafio, você deverá construir um painel gerencial para um e-commerce que almeja estudar as suas vendas e assim, traçar a melhor estratégia para alavancar seus resultados. Você receberá duas bases de dados, uma com dados das vendas e outra com informações dos clientes. Com isso, crie duas páginas para que os analistas possam visualizar as métricas. Crie as determinadas métricas: Quantidade total e valor total de vendas, contagem e valor total de vendas por data, quantidade e valor total por categoria e crie os filtros necessários para fornecer ao usuário a melhor experiência. Lembrem-se do storytelling e de um bom layout para ser atrativo.

## Detalhamento das tabelas

| Coluna            | Descrição                                      | Base         |
| ----------------- | ---------------------------------------------- | ------------ |
| idcompra          | numero de identificação da compra              | base compra  |
| idcanalvenda      | Canal de venda                                 | base compra  |
| bandeira          | Qual foi a bandeira que a compra foi realizada | base compra  |
| Data              | Data da compra                                 | base compra  |
| Preço             | Preço da compra                                | base compra  |
| Preço_com_frete   | Preço da compra + frete                        | base compra  |
| Nome_Departamento | Departamento do produto                        | base compra  |
| estado            | Estado da compra                               | base compra  |
| cliente_Log       | Identificação do cliente                       | base compra  |
| cliente_Log       | Identificação do cliente                       | Base cliente |
| Idade             | Idade do cliente                               | Base cliente |
| uf_nascimento     | Cidade de nascimento                           | Base cliente |
| Renda             | renda do cliente                               | Base cliente |

## Etapas de Desenvolvimento

Etapa 01: Cartões
Análise das tabelas recebidas, identificando colunas e valores.
Criação de indicadores para quantidade de vendas, valores totais com e sem frete, quantidade de clientes e média de renda.

Etapa 02: Gráficos de Linhas
Contagem de vendas por mês.
Valor total de vendas por mês.

Etapa 03: Gráficos de Barras
Quantidade de vendas e valor total por categoria.
Distribuição de idades e rendas dos clientes.

Etapa 04: Filtros
Filtros baseados em bandeira, estado, canal de venda, departamento, idade, faixa de renda e estado de nascimento.

----------------
![Report de Vendas](https://raw.githubusercontent.com/rafaelaraujomj/Projeto-DNC-PowerBI/refs/heads/main/Pasted%20image%2020250319180205.png?token=GHSAT0AAAAAADALMHN3BVHSZGQGWGJAUBS4Z63IBNA)
-----------------
![Perfil do Cliente](https://raw.githubusercontent.com/rafaelaraujomj/Projeto-DNC-PowerBI/refs/heads/main/Pasted%20image%2020250319180101.png?token=GHSAT0AAAAAADALMHN3CPQCPW5LL3ZKC374Z63IAAQ)
-------------------
# Fórmula DAX

Foram utilizadas as seguintes fórmulas para melhor análise dos dados.
~~~
Faixa Etária = 
SWITCH(
    TRUE(),
    'Base cliente'[idade] < 18, "Menor de 18",
    'Base cliente'[idade] >= 18 && 'Base cliente'[idade] <= 25, "18 a 25",
    'Base cliente'[idade] >= 26 && 'Base cliente'[idade] <= 35, "26 a 35",
    'Base cliente'[idade] >= 36 && 'Base cliente'[idade] <= 45, "36 a 45",
    'Base cliente'[idade] >= 46 && 'Base cliente'[idade] <= 55, "46 a 55",
    'Base cliente'[idade] >= 56 && 'Base cliente'[idade] <= 65, "56 a 65",
    'Base cliente'[idade] >= 66 && 'Base cliente'[idade] <= 75, "66 a 75",
    'Base cliente'[idade] >= 76 && 'Base cliente'[idade] <= 85, "76 a 85",
    'Base cliente'[idade] > 85, "Acima de 85",
    "Sem Idade"
)

faixa_renda = 
SWITCH(
    TRUE(),
    'Base cliente'[renda] <= 1000, "Até R$1000",
    'Base cliente'[renda] <= 1750, "Até R$1750",
    'Base cliente'[renda] <= 2500, "Até R$2500",
    'Base cliente'[renda] <= 5000, "Até R$5000",
    'Base cliente'[renda] <= 7500, "Até R$7500",
    'Base cliente'[renda] <= 10000, "Até R$10000",
    "Maior que R$10000"
)
~~~
# Conclusão

### Tendência de Vendas

- Há uma oscilação no volume de vendas ao longo do tempo, com picos nos dias 6 e 7 de abril, e uma queda acentuada após o dia 9 de abril.
- A tendência geral parece ser de declínio após o pico, o que pode indicar sazonalidade ou outros fatores de influência.

### Departamentos Mais Lucrativos

- Telefonia e Celulares é o departamento com maior faturamento, totalizando R$ 22,1 milhões.
- Eletrodomésticos (R$ 13,6 milhões) e TVs e Acessórios (R$ 13,1 milhões) também se destacam em receita.
- Esses três departamentos juntos representam a maior parte das vendas.

### Quantidade de Vendas por Departamento

- Telefonia e Celulares lidera também em número de unidades vendidas, com 16 mil vendas.
- Eletroportáteis e Eletrodomésticos também têm volume alto, indicando forte demanda por esses produtos.
- Departamentos como Perfumes e Games têm volumes muito baixos, sugerindo menor interesse ou menor disponibilidade.

## Possíveis Ações

- Investigar a queda de vendas após o pico de abril para entender se há fatores sazonais, concorrência ou problemas internos.
- Focar em promoções e estratégias para os departamentos de menor venda para aumentar a atratividade.
- Analisar o impacto do frete sobre as vendas, já que a diferença entre os valores com e sem frete é baixa.
- Segmentar campanhas de marketing para fortalecer ainda mais os produtos mais vendidos e aumentar a conversão dos produtos com baixo desempenho.


