# Xbox Game Pass - Análise de Assinaturas e Dashboard de Vendas

## Visão geral

Este projeto utiliza o Microsoft Excel para organizar, analisar e visualizar dados de assinaturas do Xbox Game Pass. O objetivo é transformar uma base de dados de assinantes em informações úteis para responder a perguntas de negócio relacionadas ao faturamento, à renovação automática e à adesão a serviços adicionais.

O arquivo reúne a base de dados, tabelas dinâmicas, cálculos de apoio e um dashboard com identidade visual inspirada no ecossistema Xbox. A análise considera os registros do período de **1º de janeiro a 31 de dezembro de 2024**, conforme indicado no painel.

> **Objetivo do projeto:** praticar análise de dados e construção de dashboards no Excel, demonstrando como perguntas de negócio podem orientar a organização dos dados, a criação de indicadores e a comunicação de insights.

## Objetivos

- Consolidar informações de assinaturas em uma base estruturada.
- Utilizar tabelas dinâmicas para agrupar e resumir os dados.
- Investigar o faturamento de assinaturas anuais.
- Comparar o faturamento de assinantes com e sem renovação automática.
- Analisar a receita associada aos complementos EA Play Season Pass e Minecraft Season Pass.
- Calcular e comparar a receita média por assinatura entre os planos.
- Apresentar os resultados em um dashboard de leitura rápida.

## Ferramentas e recursos utilizados

- **Microsoft Excel**
  - Base de dados tabular.
  - Tabelas dinâmicas.
  - Gráficos.
  - Filtros.
  - Fórmulas e cálculos auxiliares.
  - Formatação condicional e recursos visuais para organização do dashboard.

O projeto foi desenvolvido em Excel, sem necessidade de ferramentas externas para visualizar o arquivo.

## Estrutura do arquivo

O arquivo principal é `projDashboardXbox.xlsx` e está organizado nas seguintes planilhas:

| Planilha | Finalidade |
|---|---|
| `Bases` | Base principal com informações dos assinantes, planos, datas, renovação, preços e complementos. |
| `Cálculos` | Área de apoio com tabelas dinâmicas e resultados utilizados para responder às perguntas de negócio. |
| `Detalhes1` | Registros detalhados relacionados a uma análise filtrada, úteis para consultar os dados que compõem um resultado. |
| `Dashboard` | Painel visual que reúne os principais resultados e gráficos. |
| `Assets` | Referências visuais, como paleta de cores e recursos de identidade visual. |

Os nomes das planilhas podem conter caracteres estilizados no arquivo original.

## Dados utilizados

A base contém informações relacionadas aos assinantes e às características de suas assinaturas. Entre os campos presentes estão:

| Campo | Descrição |
|---|---|
| `Subscriber ID` | Identificador do assinante. |
| `Name` | Nome associado ao registro. |
| `Plan` | Plano contratado, como Core, Standard ou Ultimate. |
| `Start Date` | Data de início da assinatura. |
| `Auto Renewal` | Indica se a renovação automática está habilitada. |
| `Subscription Price` | Preço informado para a assinatura. |
| `Subscription Type` | Periodicidade da assinatura, como Monthly, Quarterly ou Annual. |
| `EA Play Season Pass` | Indica a adesão ao complemento EA Play Season Pass. |
| `EA Play Season Pass Price` | Valor associado ao complemento EA Play Season Pass. |
| `Minecraft Season Pass` | Indica a adesão ao complemento Minecraft Season Pass. |
| `Minecraft Season Pass Price` | Valor associado ao complemento Minecraft Season Pass. |
| `Total Value` | Valor total da assinatura após a aplicação do desconto, conforme a estrutura utilizada no projeto. |

A base contém campos de diferentes tipos. Para evitar erros, campos numéricos devem ser tratados como números, datas como datas e categorias como texto. Valores como `Yes` e `No` representam categorias, enquanto o hífen pode indicar ausência de um preço aplicável.

## Perguntas de negócio analisadas

### 1. Qual é o faturamento total das assinaturas anuais?

**Objetivo:** identificar o faturamento agregado dos registros classificados como anuais.

**Abordagem:** filtrar `Subscription Type` para `Annual` e somar `Total Value`.

**Resultado registrado no projeto:** **R$ 1.754,00**.

Esse indicador oferece uma visão consolidada do valor total associado às assinaturas anuais no conjunto de dados analisado.

### 2. Qual é o faturamento das assinaturas anuais com e sem renovação automática?

**Objetivo:** comparar o faturamento entre assinaturas com renovação automática habilitada e aquelas sem essa configuração.

**Abordagem:** manter o filtro `Subscription Type = Annual`, agrupar por `Auto Renewal` e somar `Total Value`.

| Renovação automática | Faturamento |
|---|---:|
| `Yes` | R$ 1.537,00 |
| `No` | R$ 217,00 |
| **Total** | **R$ 1.754,00** |

**Interpretação:** dentro do recorte analisado, a maior parte do faturamento de assinaturas anuais está associada aos registros com renovação automática habilitada. Esse resultado descreve a base observada; isoladamente, não comprova que a renovação automática cause maior faturamento nem permite prever a retenção futura.

### 3. Qual é o valor associado às assinaturas do EA Play Season Pass?

**Objetivo:** mensurar o valor associado ao complemento EA Play Season Pass no recorte de assinaturas anuais.

**Abordagem:** filtrar `Subscription Type = Annual` e resumir os valores do complemento por plano.

| Plano | Valor registrado |
|---|---:|
| Core | R$ 0,00 |
| Standard | R$ 0,00 |
| Ultimate | R$ 600,00 |
| **Total** | **R$ 600,00** |

**Interpretação:** nos dados analisados, o valor registrado para o EA Play Season Pass está concentrado no plano Ultimate.

**Nota metodológica:** a leitura deste indicador depende de como o campo `EA Play Season Pass` foi construído. Se ele contém valores monetários, a soma pode representar valor associado ao complemento. Se contém apenas marcações de adesão, a análise deve usar uma contagem de assinantes, não uma soma monetária. O campo de preço correspondente deve ser conferido antes de interpretar o resultado como receita efetiva.

### 4. Qual é o valor associado às assinaturas do Minecraft Season Pass?

**Objetivo:** analisar o valor associado ao complemento Minecraft Season Pass por plano, considerando as assinaturas anuais.

**Abordagem:** filtrar `Subscription Type = Annual` e agrupar o campo `Minecraft Season Pass Price` por `Plan`.

| Plano | Valor registrado |
|---|---:|
| Core | R$ 0,00 |
| Standard | R$ 540,00 |
| Ultimate | R$ 400,00 |
| **Total** | **R$ 940,00** |

**Interpretação:** no recorte analisado, o maior valor associado ao Minecraft Season Pass aparece no plano Standard, seguido pelo Ultimate.

O indicador representa a soma dos valores de preço registrados para o complemento. Para tratá-lo como faturamento efetivamente realizado, é necessário confirmar que os campos de preço correspondem a valores cobrados, e não apenas a preços de referência.

### 5. Qual tipo de assinatura gera o maior faturamento médio por assinante?

**Objetivo:** comparar a receita média por assinatura entre os planos Core, Standard e Ultimate.

**Abordagem:** filtrar `Subscription Type = Annual`, agrupar os registros por `Plan`, somar `Total Value` e dividir o resultado pela quantidade de assinaturas de cada plano.

**Fórmula utilizada:**

```text
Receita média por assinatura = Soma de Total Value / Quantidade de assinaturas
```

**Resultados registrados no dashboard:**

| Plano | Quantidade de assinaturas | Faturamento total | Receita média por assinatura |
|---|---:|---:|---:|
| Core | 24 | R$ 120,00 | R$ 5,00 |
| Standard | 27 | R$ 448,00 | R$ 16,59 |
| Ultimate | 20 | R$ 1.186,00 | R$ 59,30 |
| **Total** | **71** | **R$ 1.754,00** | **R$ 24,70** |

**Principal insight:** o plano **Ultimate** apresenta a maior receita média por assinatura no recorte anual, com **R$ 59,30** por registro. O plano Standard apresenta média de R$ 16,59, enquanto o Core apresenta R$ 5,00.

A média geral de R$ 24,70 é calculada dividindo o faturamento total de R$ 1.754,00 pelas 71 assinaturas anuais consideradas.

**Visualização recomendada:** gráfico de barras horizontais com a receita média por assinatura de cada plano. A quantidade de assinaturas pode aparecer como informação complementar, mas deve ser distinguida visualmente da receita média. O total geral não deve ser apresentado como se fosse um quarto plano; pode ser mantido em um cartão ou em uma tabela de apoio.

**Terminologia em inglês:** `Average Revenue per Subscription` é um título adequado para esse indicador, pois a conta utiliza o número de assinaturas como denominador. O termo `Average Revenue per User (ARPU)` deve ser utilizado apenas quando o denominador representar usuários únicos.

## Indicadores e cálculos

### Faturamento total de assinaturas anuais

```text
Faturamento anual = Soma de Total Value com Subscription Type = Annual
```

### Faturamento por renovação automática

```text
Faturamento por status = Soma de Total Value agrupada por Auto Renewal
```

O filtro de periodicidade deve permanecer em `Annual` para reproduzir os resultados apresentados.

### Receita média por assinatura

```text
Receita média por assinatura = Faturamento do plano / Quantidade de assinaturas do plano
```

Exemplo para o plano Ultimate:

```text
R$ 1.186,00 / 20 = R$ 59,30
```

Exemplo para o plano Standard:

```text
R$ 448,00 / 27 ≈ R$ 16,59
```

Exemplo para o plano Core:

```text
R$ 120,00 / 24 = R$ 5,00
```

Esses cálculos usam a quantidade de registros de assinatura. Se um mesmo assinante puder ter mais de uma assinatura na base, o indicador deve ser descrito como receita média por assinatura, e não necessariamente por pessoa única.

## Desenvolvimento do dashboard

O dashboard foi pensado para facilitar a leitura dos resultados sem exigir que o usuário examine toda a base de dados. A organização do projeto contempla:

- Título principal relacionado às vendas de assinaturas do Xbox Game Pass.
- Período de análise indicado no cabeçalho.
- Tabelas dinâmicas como fonte de agregação.
- Gráficos para comparação entre categorias.
- Indicadores financeiros formatados em reais.
- Filtros para delimitar o recorte analisado.
- Paleta visual inspirada na identidade do Xbox.

### Recomendações de apresentação

- Utilizar títulos que expressem diretamente a pergunta respondida.
- Exibir unidades nos valores monetários, preferencialmente com o formato `R$`.
- Manter os filtros visíveis para deixar claro o escopo da análise.
- Evitar misturar escalas diferentes no mesmo gráfico sem uma justificativa clara.
- Diferenciar faturamento total, quantidade de assinaturas e receita média.
- Atualizar tabelas dinâmicas e gráficos após alterações na base.
- Manter uma hierarquia visual consistente entre título, indicadores, tabelas e gráficos.

## Como utilizar o arquivo

1. Baixe ou clone o repositório que contém o arquivo Excel.
2. Abra `projDashboardXbox.xlsx` em uma versão compatível do Microsoft Excel.
3. Acesse a planilha `Dashboard` para visualizar o painel.
4. Consulte `Bases` para verificar os registros de origem.
5. Acesse `Cálculos` para consultar as tabelas dinâmicas e os resultados utilizados.
6. Utilize os filtros disponíveis para explorar os recortes de dados.
7. Se modificar ou acrescentar registros, confira os intervalos de origem e atualize as tabelas dinâmicas e os gráficos.
8. Valide os resultados após a atualização, especialmente quando novos registros forem adicionados ou campos forem alterados.

Os nomes e a disposição de alguns comandos podem variar de acordo com a versão do Excel.

## Principais aprendizados

Este projeto permite praticar competências importantes para análise de dados:

- Estruturação e leitura de bases tabulares.
- Agrupamento e sumarização de dados com tabelas dinâmicas.
- Construção de indicadores a partir de perguntas de negócio.
- Comparação entre categorias e segmentos.
- Cálculo e interpretação de médias.
- Escolha de visualizações de acordo com a mensagem que se deseja comunicar.
- Organização de um dashboard com foco em clareza e consistência visual.
- Cuidado com a diferença entre preço registrado, valor de complemento e faturamento efetivamente realizado.

## Limitações e cuidados de interpretação

- Os resultados apresentados dependem dos registros existentes no arquivo e do filtro aplicado.
- O recorte anual considera registros classificados como `Annual`; não deve ser confundido com o total de todos os tipos de assinatura.
- Receita média por assinatura não é necessariamente receita média por cliente único.
- A soma de valores associados a complementos não comprova, por si só, que todos os valores foram efetivamente recebidos.
- O campo `Total Value` já considera o desconto aplicado, conforme a lógica informada para a planilha. Portanto, o valor do cupom não deve ser subtraído novamente do total.
- Os dados permitem identificar associações e diferenças entre grupos, mas não demonstram causalidade.
- Antes de utilizar os resultados em decisões reais, é recomendável validar a definição de cada campo, a consistência dos preços e a atualização das tabelas dinâmicas.

## Possíveis melhorias futuras

- Incluir cartões de KPI para faturamento anual, total de assinaturas e receita média por assinatura.
- Criar uma comparação visual específica da receita média por plano.
- Analisar a distribuição das assinaturas por periodicidade: mensal, trimestral e anual.
- Comparar a adesão aos complementos por plano utilizando contagem de assinantes e receita separadamente.
- Avaliar a participação percentual de cada plano no faturamento anual.
- Acrescentar verificações de qualidade de dados para valores ausentes, categorias inconsistentes e possíveis duplicidades.
- Melhorar a atualização do dashboard para incorporar novos registros com menos ajustes manuais.

## Conclusão

O projeto demonstra como o Excel pode ser utilizado para transformar dados de assinaturas em informações organizadas para análise de negócio. A partir de tabelas dinâmicas, cálculos auxiliares e gráficos, o dashboard explora o faturamento anual, a renovação automática, os complementos e a receita média por assinatura.

A principal conclusão da quinta pergunta é que, dentro do recorte de assinaturas anuais apresentado, o plano Ultimate possui a maior receita média por assinatura, de R$ 59,30. Esse resultado complementa a análise do faturamento total ao mostrar como a receita média varia entre os planos.

O trabalho também reforça a importância de selecionar métricas adequadas, explicitar os filtros aplicados e distinguir valores registrados de receita efetivamente realizada.

---

## Autor

Desenvolvido por Guilherme Breno Martins Jordão como projeto de prática em análise de dados e construção de dashboards com Microsoft Excel.
