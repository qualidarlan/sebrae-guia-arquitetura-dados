

Motivo | Descrição
------ | ---------
Concorrência | Isola a fonte de dados de origem (geração) da fonte de dados analíticos (consumo) Minimiza o uso de recursos
Segurança | Não abrir conexões externas com a fonte de dados de origem para consumo de dados
Padronização | Converte diferentes formatos em formatos abertos, não proprietários. Agenda a ingestão de diferentes momentos pra cada fonte
Semântica | Criar uma camada que faça mais sentido para análise de negócio (as fontes de dados são otimizadas para INSERT e UPDATE)
Abstração | Abstrair a complexidade de acesso aos dados. (conectores, drivers, linguagens, etc.) e unir dados de diferentes fontes. Cada fonte pode ter um agendamento diferente



# Como?
> Como padronizar formatos diferentes e aplicar regras de validação, duplicidade e inconsistencias
Como lidar com mudança de schema; tipagem, limpeza, padronização, validação, ofuscação, qualidade, performance

# Tecnologias de qualidade de dados
Garantir que dados precisos e úteis estejam disponíveis para cargas de trabalho downstream BI, analíticas e machine learning .

Manter a qualidade dos dados é uma premissa para o ciclo de vida. A medida que o dado é tratado ele ganha qualidade, o que representa que será validado quanto a consistência dos tipos de acordo com o schema definido, valores nulos, ranges de válidos, outliers, etc. Também são consideradas regras de negócio que caracterizam registro válidos ou não.

As ferramentas de qualidade de dados buscam aumentar eficiência através da automação das regras de vefirificação realizando a checagem de integridade como parte do pipeline de dados.

## Processamento distribuído
, quando é necessário, como funciona, quais são os limites


## Linguagens de processamento
Definir qual engine vai interagir como o lakehouse, 
de dados SQL, Python, SparkSQL, quando usar, qual é mais indicada para cada perfil de usuário, ou fase no ciclo de vida

Tabela indicativo de linguagem/ tipo de tecnologia de transformação para cada perfil

Linguagem | Analista | Cientista | Engenheiro
-------| -------- | --------- | -----------
SQL | x | x | x
Python | - | x | x
R | - | x | x
PySpark | - | x | x
SparkSQL | x | x | -
Bash | - | - | -


## Camada Semântica e Metric Store
A separação da camanda semantica e a criação de uma abstração para as métricas permite a independencia de qual ferramenta da analise de dados será usada 

https://airbyte.com/blog/the-rise-of-the-semantic-layer-metrics-on-the-fly
https://towardsdatascience.com/metrics-store-in-action-76b16a928b97

## Exemplos códigos comuns
Listar os comandos mais comuns e as transformações básicas em cada linguagem

Código | SQL | Pandas | PySpark 
------- | --- | ------ | -------
Projeção de atributos de uma tabela | SELECT col1 FROM Tab | df["col1] | df.select(col(col1))
Selecionar todos os atributos da tabela | SELECT * FROM Tab | display(df) | df.show()


## Recomendações
Código | Recomendação | Descrição | Princípios
------ | ------------ | --------- | ----------
R01-Transformações | Não devem ser incluídas regras de negócio na fase de transformação. Essa fase deve se concentrar em entregar valor através da validação, checagem, otimização e preparação dos dados. | Gerar datsets validados e com alta qualidade mas sem alterações de regras de negócio, os mantém com um propósito geram, servindo para múltiplos contextos e casos de uso onde a inclusão de regras de negócio poderiam limitar.
R02-Transformação | Os dados devem ser ter padrões de representação consistentes entre os conjuntos de dados. | Por exemplo, todas as tabelas que usar campos como: endereço, um telefone, representação de gênero, número de cpf/cnpj, um código de contrata, etc. devem armazená-los transformados da mesma forma.
R03-Transformação | As tecnologias usadas para o processamento devem ser escaláveis para conseguir lidar operações complexas de transformação ou limpeza.
R04-Transformação | Problemas com a qualidade dos dados devem sempre ser endereçados para serem corrigidos no sistema de origem
R05-Transformação | Dever ser estabelecido limites para a qualidade dos dados, quando é detectada que a qualidade está abaixo desses limites, deve haver uma análise por parte do proprietários dos dados se aceitam ou não a inclusão de dados com baixa qualidade.




> o que é
> Abordar aqui asrelações de dependência, entradas, saídas, limites, responsabilidades, tipos de tecnologias

> O que acontece nessa fase, qual o objetivo da fase. Delinear entradas, saídas limites e fronteiras

> ter uma camada de transformação específica. Qualidade dos dados, multiplos casos de uso (dados tratados mas não alterados com regras de negócio são ótimos para DS)