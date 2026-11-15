# Momento 

Bem-vindo à base de dados da empresa **Momento**!

A Momento vende produtos de cultura pop e mantém escritórios em diferentes países, além de manter uma escola como seu projeto educacional. A equipe de dados recebeu duas fontes: uma base relacional usada pela empresa para gestão geral e um CSV exportado por um sistema de vendas recém-integrado para vendas.

Nestes exercícios, você vai explorar o banco de dados da empresa e responder perguntas que revelam insights importantes sobre o negócio. Prepare-se para usar queries básicas, agregações complexas, e operações avançadas!


## Ambiente e arquivos

Esses são os arquivos para vocês trabalharem

- [0_Base.sql](0_Base.sql)`: cria e preenche uma base MySQL para as consultas. Requer MySQL 8.0 ou superior.
- [vendas_campanha_bruto.csv](vendas_campanha_bruto.csv): exportação externa que será usada no exercício de ETL.

O script SQL usa o banco `momento` e **não apaga bancos nem tabelas existentes**. Execute-o em um banco/schema vazio. Ele cria uma área de pouso chamada `stg_vendas_csv`; essa tabela começa vazia para que a turma carregue o CSV. Os campos brutos dessa tabela são texto de propósito: a extração deve preservar os valores recebidos.

> O material é de SQL relacional e usa MySQL. As etapas de ETL podem ser feitas em SQL, Python ou Power Query, desde que o grupo documente as transformações e mantenha a rastreabilidade.

## Desafios 

Prepare dados que ajudem a equipe a responder perguntas sobre pessoas, departamentos, escritórios, produtos, vendas e atividade do sistema. Entregue consultas que possam ser explicadas e reproduzidas por outra pessoa.

---

### Etapa 0 — Explorar

Uma das técnicas mais utilizadas pelos profissional de dados é a Exploratory Data Analysis (EDA) (Análise de Dados Exploratória, em português). 

A Análise Exploratória de Dados (AED) é o processo inicial crucial de examinar, limpar e visualizar um conjunto de dados para compreender suas principais características, identificar anomalias e descobrir padrões antes de construir modelos estatísticos ou de aprendizado de máquina formais.

Objetivos principais da AED

• Descobrir padrões e estruturas: Permitir que os dados sugiram tendências e relações sem viés preestabelecido.

• Detectar anomalias e outliers: Identificar entradas corrompidas, erros de digitação ou valores extremos que distorcem os resultados.

• Lidar com dados faltantes: Decidir se deve descartar ou imputar registros incompletos usando métodos estatísticos ou de aprendizado de máquina.

Sua missão nesse momento, é explorar os dados. 

## Nível 1: Conhecendo a Empresa

### Seu Primeiro Dia na Momento

**1.1** Você acabou de ser contratado pela Momento! Vamos começar incluindo você no sistema, escolha um departamento, cargo e salário.

R:

```sql

  INSERT INTO funcionarios
  (funcionario_id, primeiro_nome, sobrenome, email, telefone, data_contratacao, cargo_id, salario, moeda_salario, gerente_id, departamento_id, status_funcionario_id)
VALUES
  (304, 'Douglas', 'Santos', 'douglas.santos@momento.org', '+1-222-7474', '2026-05-12', 9, 5200.00, 'USD', 103, 6, 1);
```

**1.2** Agora que você faz parte da equipe, quantos funcionários temos ao total na empresa?

R: tem 124 funcionarios

```sql
select count(*)
from funcionarios;
```

**1.3** Quantos funcionários trabalham especificamente no Departamento de Tecnologia?

R: Tem 14 funcionarios

```sql
select count(*)
from funcionarios
where departamento_id = 13 
or departamento_id = 6;
```

**1.4** Liste todos os departamentos que existem na empresa. Quantos são?

R: São 30 departamentos
```
departamento_id | Nome | Educacional | Escritorio
1	Administração Executiva	0	1700
2	Marketing	0	1800
3	Recursos Humanos	0	1700
4	Recursos Humanos	0	2400
5	Logística	0	1500
6	Tecnologia da Informação	0	1400
7	Relações Públicas	0	2700
8	Vendas	0	2500
9	Executivo	0	1700
10	Finanças	0	1700
11	Contabilidade	0	1700
12	Biotecnologia	0	3900
13	Tecnologias Avançadas	0	1900
14	Dados e Inteligência	0	1400
15	Experiência do Cliente	0	1800
16	Operações LATAM	0	2800
17	Segurança da Informação	0	1500
18	Pesquisa e Desenvolvimento	0	2400
19	Comércio Digital	0	2900
20	Operações APAC	0	3000
21	Criação de Conteúdo	0	2600
22	Operações África	0	3100
23	Poções	1	1300
24	Transfiguração	1	5100
25	Projeções Astrais	1	4500
26	Criaturas Mágicas	1	3200
27	Biblioteca Arcana	1	5000
28	Administração Educacional	1	3000
29	Astronomia	1	2800
30	Herbologia	1	3800
			
```

```sql
select * 
from departamentos;
select count(*) 
from departamentos;
```

**1.5** Quantos escritórios a Momento possui? Em quais países?

R: Possui 20 escritorios
```
Pais ID | Nome Pais
AR	Argentina
BM	Brasil Bruxo
BR	Brasil
CA	Canadá
DE	Alemanha
FM	França Mágica
FR	França
GB	Reino Unido
GB	Reino Unido
GB	Reino Unido
GM	Reino dos Mágos Unidos
JM	Japão Místico
JP	Japão
PE	Peru
PM	Portugal Bruxo
US	Estados Unidos
US	Estados Unidos
US	Estados Unidos
WA	Wakanda
ZA	África do Sul
```

```sql
select count(*) 
from escritorios;
select escritorios.pais_id, paises.pais_nome
from escritorios
inner join paises
on paises.pais_id = escritorios.pais_id;
```

---

## Nível 2: Análise Financeira Básica

O CFO precisa de relatórios urgentes sobre os custos da empresa.

**2.1** Quantos funcionários trabalham no Departamento de Vendas?

R: Trabalham 5 funcionários

```sql
select count(*)
from funcionarios
inner join departamentos
on departamentos.departamento_id = funcionarios.departamento_id
where departamento_nome = "Vendas";
```

**2.2** Qual é o custo total com salários do Departamento de Vendas?

R: O custo total é 59.390,76

```sql
select sum(salario)
from funcionarios
inner join departamentos
on departamentos.departamento_id = funcionarios.departamento_id
where departamento_nome = "Vendas";
```

**2.3** Qual é a média salarial da empresa, excluindo os cargos de CEO, CMO e CFO?

R: A média salarial é 9,735.21.

```sql
select format(sum(salario) / count(*), 2) as media_salario
from funcionarios
inner join cargos
on cargos.cargo_id = funcionarios.cargo_id
where cargo_nome not in(
select cargo_nome
from cargos
where cargo_nome = 'CEO' or cargo_nome = 'CFO' or cargo_nome = 'CMO');
```

**2.4** Qual é a média salarial do Departamento de Tecnologia?

R: A média de salario é 13,203.49.

```sql
select format(sum(salario) / count(*), 2) as media_salario
from funcionarios
inner join departamentos
on departamentos.departamento_id = funcionarios.departamento_id
where departamento_nome in(
select departamento_nome
from departamentos
where departamento_nome like '%tecnologia%');
```

**2.5** Qual departamento possui a maior média salarial?

R: O departamento Biotecnologia é o que possui a maior média salarial com R$: 29,263.48.

```sql
select distinct departamentos.departamento_nome , format(avg(funcionarios.salario), 2) as media_salario
from departamentos
inner join funcionarios
on departamentos.departamento_id = funcionarios.departamento_id
group by departamentos.departamento_id, departamentos.departamento_nome
order by cast(media_salario as decimal) desc
limit 1;
```

**2.6** Qual departamento possui o menor número de funcionários?

R: Os três departamentos com o menor numero de funcionario são: Administração Executiva, Contabilidade e
Recursos Humanos.

```sql
select distinct departamentos.departamento_nome , count(funcionarios.funcionario_id) as numero_funcionario
from departamentos
inner join funcionarios
on departamentos.departamento_id = funcionarios.departamento_id
group by departamentos.departamento_id, departamentos.departamento_nome
order by numero_funcionario desc;
```

---

## Nível 3: Recursos Humanos

O RH está fazendo uma análise demográfica da empresa.

**3.1** Quantos funcionários da empresa Momento possuem cônjuges?

R: Possui 15 funcionarios com cônjuges

```sql
SELECT count(funcionarios.funcionario_id) AS quantidade_funcionario
FROM funcionarios
INNER JOIN dependentes
ON funcionarios.funcionario_id = dependentes.funcionario_id
WHERE dependentes.relacionamento = 'Cônjuge';
```

**3.2** Quantos funcionários possuem filhos registrados?

R: Possui 80 funcionarios com filhos(as).

```sql
SELECT count(funcionarios.funcionario_id) AS quantidade_funcionario
FROM funcionarios
INNER JOIN dependentes
ON funcionarios.funcionario_id = dependentes.funcionario_id
WHERE dependentes.relacionamento = 'Filha(o)';
```

**3.3** Qual funcionário foi contratado há mais tempo na empresa?

R:Foi a Madeleine Prior.

```sql
SELECT concat(primeiro_nome, ' ',sobrenome) AS nome_completo
FROM funcionarios
WHERE data_contratacao IN(
SELECT min(data_contratacao)
FROM funcionarios);
```

**3.4** Qual funcionário foi contratado há menos tempo na empresa?

R:Foi o Ariel Nunes.

```sql
SELECT concat(primeiro_nome, ' ',sobrenome) AS nome_completo
FROM funcionarios
WHERE data_contratacao IN(
SELECT max(data_contratacao)
FROM funcionarios);
```

**3.5** Liste os 5 funcionários com mais tempo de casa, ordenados pela data de contratação.

R:
```
Madeleine Prior	23/03/1987
Noah Kim	11/04/1987
Yuki Tanaka	31/07/1987
Neena Kochhar	17/08/1987
Lex T.Challa	08/02/1988
```

```sql
SELECT concat(primeiro_nome, ' ',sobrenome) AS nome_completo, 
DATE_FORMAT(data_contratacao, '%d/%m/%Y') AS data_de_contratacao
FROM funcionarios
ORDER BY data_contratacao
LIMIT 5;
```

**3.6** Quantos funcionários foram contratados na década de 1990 (entre 1990-1999)?

R: Nesse periodo foram contratados 28 colaboladores.

```sql
SELECT count(*)
FROM funcionarios
WHERE data_contratacao >= '1990-01-01' AND data_contratacao < '2000-01-01';
```

**3.7** Como a média salarial da Momento evoluiu ao longo dos anos? Agrupe por ano de contratação e calcule a média salarial.

R:
```
Ano  Média Salarial/Média anterior   taxa de crescimento
1987	13766.54		Ano Base (Sem histórico anterior)
1988	17173.97	13766.54	24.75%
1989	5342.03	17173.97	-68.89%
1990	6304.27	5342.03	18.01%
1991	8200.84	6304.27	30.08%
1992	5913.76	8200.84	-27.89%
1993	5710.36	5913.76	-3.44%
1994	8628.88	5710.36	51.11%
1995	8320.19	8628.88	-3.58%
1996	5329.73	8320.19	-35.94%
1997	6198.26	5329.73	16.30%
1998	9859.48	6198.26	59.07%
1999	11022.30	9859.48	11.79%
2000	11780.72	11022.30	6.88%
2001	7890.56	11780.72	-33.02%
2002	4653.76	7890.56	-41.02%
2003	7565.93	4653.76	62.58%
2004	7945.18	7565.93	5.01%
2005	17007.42	7945.18	114.06%
2006	15090.58	17007.42	-11.27%
2007	7800.50	15090.58	-48.31%
2008	18944.08	7800.50	142.86%
2009	16194.20	18944.08	-14.52%
2010	10763.64	16194.20	-33.53%
2011	14372.11	10763.64	33.52%
2012	9028.19	14372.11	-37.18%
2013	16164.79	9028.19	79.05%
2014	8743.75	16164.79	-45.91%
2015	12681.32	8743.75	45.03%
2016	9229.29	12681.32	-27.22%
2017	7477.88	9229.29	-18.98%
2018	8402.00	7477.88	12.36%
2019	4166.67	8402.00	-50.41%
2020	12474.78	4166.67	199.39%
2021	8414.11	12474.78	-32.55%
2022	9495.74	8414.11	12.85%
2023	8299.04	9495.74	-12.60%
2025	5200.00		Ano Base (Sem histórico anterior)
```

```sql
SELECT 
    atual.ano,
    ROUND(atual.media_salario, 2) AS media_salario_atual,
    ROUND(anterior.media_salario, 2) AS media_salario_ano_anterior,
    CASE 
        WHEN anterior.media_salario IS NULL THEN 'Ano Base (Sem histórico anterior)'
        ELSE CONCAT(
            ROUND(((atual.media_salario - anterior.media_salario) / anterior.media_salario) * 100, 2), 
            '%'
        )
    END AS taxa_crescimento
FROM (
    -- Subconsulta 1: Média salarial agrupada por ano
    SELECT 
        YEAR(data_contratacao) AS ano,
        AVG(salario) AS media_salario
    FROM funcionarios
    GROUP BY YEAR(data_contratacao)
) AS atual
LEFT JOIN (
    -- Subconsulta 2: Mesma tabela de médias, deslocada em 1 ano para trás
    SELECT 
        YEAR(data_contratacao) AS ano,
        AVG(salario) AS media_salario
    FROM funcionarios
    GROUP BY YEAR(data_contratacao)
) AS anterior ON atual.ano = anterior.ano + 1
ORDER BY atual.ano ASC;
```

---

## Nível 4: Operações e Escritórios

**4.1** Qual é o custo total de suprimentos em cada escritório? Ordene do mais caro ao mais barato.

R:
```
Koboa Koboa	70605.50
Verstebona	61879.50
Cape Town Studio	58750.50
Campus de Lisboa	57457.00
House of Mystery	56320.00
Shuri's Palace	53923.00
Arkham Base	52208.50
Umbrella Corp	51522.50
Castelo Encantado	44747.00
Baxter Building	43268.50
Sala Winter	40897.50
Daily Planet Bureau	31160.00
Archies Mad House	30633.50
Stark Tower	29214.50
Wayne Offices	17948.00
```

```sql
SELECT 
    e.escritorio_nome,
    SUM(s.quantidade_estoque * s.custo_unitario) AS custo_total_suprimentos
FROM escritorios e
INNER JOIN suprimentos s ON e.escritorio_id = s.escritorio_id
GROUP BY e.escritorio_id, e.escritorio_nome
ORDER BY custo_total_suprimentos DESC;
```

**4.2** Qual escritório possui a maior quantidade de diferentes tipos de suprimentos?

R: O koboa koboa com 7 suprimentos diferentes.

```sql
SELECT 
    e.escritorio_nome,
    COUNT(DISTINCT s.suprimento_nome) AS total_tipos_suprimentos
FROM escritorios e
INNER JOIN suprimentos s ON e.escritorio_id = s.escritorio_id
GROUP BY e.escritorio_id, e.escritorio_nome
ORDER BY total_tipos_suprimentos DESC
LIMIT 1;
```

**4.3** Qual é o suprimento mais caro (considerando preço unitário) em toda a empresa?

R:Computadores custando 909.50 Dolares. 

```sql
SELECT suprimento_nome, custo_unitario, moeda
FROM suprimentos
ORDER BY custo_unitario DESC
LIMIT 1;
```

**4.4** Calcule o valor total do inventário de suprimentos da empresa (quantidade × preço unitário de todos os itens em todos os escritórios).

R: O valor total é 700.535,50.

```sql
SELECT FORMAT(SUM(quantidade_estoque * custo_unitario),2) AS valor_total_inventario
FROM suprimentos;
```

---

## Nível 5: Produtos e Vendas

**5.1** Quais produtos foram vendidos pela Momento? Liste todos os produtos únicos.

R:
```
ID / SKU / Nome
2	BAT-001	Batarang de treino
3	WEB-001	Lança-Teias
6	WW-001	Laço da Verdade
7	IM-005	Capacete Iron Man Mark 5
8	SW-001	Sabre de luz de Mace Windu
9	X-001	Sentinela em miniatura
11	WW-002	Laço da Honestidade
12	BAT-002	Batarangs oficiais
14	PKM-001	Pokébola clássica
15	PKM-002	Pokédex portátil
16	SW-002	Capacete Darth Vader
17	MAR-001	Escudo do Capitão América
18	LOTR-001	Anel do Poder (réplica)
20	ZEL-001	Master Sword (réplica)
21	FF-001	Buster Sword (réplica)
23	SW-003	Blaster Imperial
24	MAR-002	Tesseract decorativo
27	GOW-001	Lâminas do Caos cenográficas
29	SW-004	Blaster de Han Solo
30	MAR-003	Manopla do Infinito
32	DC-004	Capa do Batman
33	MAR-004	Reator Arc decorativo
34	HP-002	Chapéu Seletor
36	PKM-003	Boné do treinador
```

```sql
SELECT DISTINCT 
    p.produto_id,
    p.sku,
    p.produto_nome
FROM produtos p
INNER JOIN itens_venda iv ON p.produto_id = iv.produto_id;
```

**5.2** Qual é o produto mais vendido (maior quantidade total)?

R: É o Reator ARC decorativo com 48 vendas

```sql
SELECT 
    p.produto_nome,
    SUM(iv.quantidade) AS quantidade_total_vendida
FROM itens_venda iv
INNER JOIN produtos p ON iv.produto_id = p.produto_id
GROUP BY p.produto_id, p.produto_nome
ORDER BY quantidade_total_vendida DESC
LIMIT 1;
```

**5.3** Qual é o produto menos vendido?

R: É o chapeu seletor com apenas 1 venda

```sql
SELECT 
    p.produto_nome,
    SUM(iv.quantidade) AS quantidade_total_vendida
FROM itens_venda iv
INNER JOIN produtos p ON iv.produto_id = p.produto_id
GROUP BY p.produto_id, p.produto_nome
ORDER BY quantidade_total_vendida ASC
LIMIT 1;
```

**5.4** Pensando na relação quantidade × valor unitário, qual produto gerou mais receita para a empresa?

R: O Tesseract decorativo com o valor total em vendas de	236788.65

```sql
SELECT 
    p.produto_nome,
    SUM(iv.quantidade * iv.preco_unitario) AS receita_total
FROM itens_venda iv
INNER JOIN produtos p ON iv.produto_id = p.produto_id
GROUP BY p.produto_id, p.produto_nome
ORDER BY receita_total DESC
LIMIT 1;
```

**5.5** Qual é o produto mais caro (maior preço unitário) no catálogo?

R: É o Tesseract decorativo	custando	7000.00	USD

```sql
SELECT 
    produto_nome,
    preco_catalogo,
    moeda
FROM produtos
ORDER BY preco_catalogo DESC
LIMIT 1;
```

**5.6** Qual foi o faturamento total da empresa em vendas?

R: Faturamento total de 863042.05

```sql
SELECT 
    SUM(iv.quantidade * iv.preco_unitario) AS faturamento_total
FROM itens_venda iv;
```

**5.7** Quantas vendas foram realizadas no mês de junho de 2023?

R: Foram realizadas duas vendas

```sql
SELECT 
    COUNT(*) AS total_vendas
FROM vendas
WHERE DATE_FORMAT(data_venda, '%Y-%m') = '2023-06';
```

**5.8** Qual vendedor realizou mais vendas (em quantidade de transações)?

R: Foi o funcionario do ID: 127, Nome: Jack Livingston com o total de	11 transações.

```sql
SELECT 
    f.funcionario_id,
    CONCAT(f.primeiro_nome, ' ', f.sobrenome) AS nome_vendedor,
    COUNT(v.venda_id) AS total_transacoes
FROM vendas v
INNER JOIN funcionarios f ON v.funcionario_id = f.funcionario_id
GROUP BY f.funcionario_id, nome_vendedor
ORDER BY total_transacoes DESC
LIMIT 1;
```

**5.9** Qual vendedor gerou mais receita para a empresa?

R:Foi o funcionario do ID: 124, Nome: John Russell com o total de 196953.14 em vendas.	

```sql
SELECT 
    f.funcionario_id,
    CONCAT(f.primeiro_nome, ' ', f.sobrenome) AS nome_vendedor,
    SUM(iv.quantidade * iv.preco_unitario) AS receita_gerada
FROM vendas v
INNER JOIN funcionarios f ON v.funcionario_id = f.funcionario_id
INNER JOIN itens_venda iv ON v.venda_id = iv.venda_id
GROUP BY f.funcionario_id, nome_vendedor
ORDER BY receita_gerada DESC
LIMIT 1;
```

---

## Nível 6: Operações de Atualização

A empresa está crescendo e mudanças precisam acontecer!

**6.1** Um novo departamento foi criado: **Inovações**. Ele será alocado no escritório "Wayne Offices". Adicione-o ao banco de dados.

```sql
INSERT INTO departamentos (departamento_id, departamento_nome, educacional, escritorio_id)
VALUES (31, 'Inovações', 0, 1400);
```

**6.2** O departamento de Inovações está sem funcionários. Transfira 2 funcionários do departamento de Tecnologia para Inovações.

```sql
UPDATE funcionarios
SET departamento_id = 31
WHERE departamento_id = 6
LIMIT 2;
```

**6.3** A empresa decidiu dar um aumento de 10% para todos os funcionários do departamento de Tecnologia. Atualize os salários.

```sql
UPDATE funcionarios
SET salario = salario * 1.10
WHERE departamento_id = 6;
```

**6.4** O funcionário "Bruce Ernst" foi promovido a "Senior Web Developer" e recebeu um aumento para $5.000. Atualize suas informações.

```sql
UPDATE funcionarios
SET cargo_id = 26, 
    salario = 5000.00
WHERE primeiro_nome = 'Bruce' AND sobrenome = 'Ernst';
```

**6.5** Adicione um novo suprimento ao escritório "Wayne Offices": 15 unidades de "Headsets" com preço unitário de $150 cada.

```sql
INSERT INTO suprimentos (suprimento_id, referencia_compra, suprimento_nome, quantidade_estoque, custo_unitario, moeda, data_compra, escritorio_id)
VALUES (106, 'PO-1400-08', 'Headsets', 15, 150.00, 'USD', CURRENT_DATE(), 1400);
```

**6.6** Todos os funcionários contratados antes de 1990 estão aposentando. Remova-os do banco de dados (CUIDADO: execute um **SELECT** antes para ver quantos serão afetados!).

```sql
SELECT funcionario_id, primeiro_nome, sobrenome, data_contratacao 
FROM funcionarios 
WHERE YEAR(data_contratacao) < 1990;

DELETE FROM dependentes 
WHERE funcionario_id IN (
    SELECT funcionario_id 
    FROM funcionarios 
    WHERE YEAR(data_contratacao) < 1990); --Tive que deletar também os dependentes deles para conseguir deletar por causa da chave estrangeira

DELETE FROM funcionarios 
WHERE YEAR(data_contratacao) < 1990;
```

---

## Nível 7: Da sala de aula ao impacto corporativo

Agora a história acompanha pessoas. A Momento quer entender se sua escola está formando talentos, ampliando acesso e criando pontes reais para o mundo do trabalho. Use os dados para contar essa jornada com cuidado: números revelam tendências, mas não substituem histórias individuais.

**7.1 — O ponto de partida**

Quais cursos estão ativos? Para cada um, mostre carga horária, nível e quantas turmas já foram abertas. Que jornada de aprendizagem a escola oferece hoje?

**7.2 — Quem chegou até aqui?**

Para cada turma, mostre curso, professores, capacidade e número de matrículas. Há vagas disponíveis ou turmas ainda sem estudantes? O que isso sugere sobre oferta e procura?

**7.3 — Acesso à formação**

Quantos estudantes receberam bolsa, qual foi o percentual concedido e em quais cursos? 

**7.4 — Conclusão e reconhecimento**

Por curso e turma, calcule matrículas, concluintes, certificados emitidos e nota média. Quais perguntas adicionais seriam necessárias antes de afirmar que um curso teve “mais sucesso” que outro?

**7.5 — O próximo capítulo de Ariel**

Reconstrua a trajetória de Ariel Nunes: curso, turma, matrícula, bolsa, estágio e contratação. Em que momento a formação passou a se conectar com uma oportunidade corporativa?

**7.6 — Da aprendizagem para o trabalho**

Liste os vínculos de talentos com estudante, tipo de vínculo, departamento, status e, quando existir, a pessoa funcionária associada. Quantas pessoas passaram por estágio e quantas chegaram à contratação?

**7.7 — Onde a ponte encontra a empresa?**

Quais departamentos recebem talentos da escola? Compare-os com seu total de funcionários e média salarial. Como evitar a conclusão apressada de que um departamento é “melhor” apenas porque contratou mais estudantes?

**7.8 — Um retrato para a liderança**

Crie uma única consulta que apresente: total de alunos, matrículas ativas, concluintes, bolsas concedidas, estágios, contratações e departamentos que receberam talentos. Escreva, abaixo do resultado, um parágrafo de até cinco linhas explicando o que a liderança pode aprender — e o que ainda não é possível afirmar.

**7.9 — Educação e negócio, lado a lado**

Monte uma consulta comparando, por período, indicadores educacionais (matrículas, certificados e vínculos) com indicadores corporativos (vendas, receita e pessoas contratadas). Quais limites existem nessa comparação, já que correlação não comprova causalidade?

**7.10 — A próxima pergunta**

Imagine que você terá recursos para coletar somente um dado novo para tornar essa história mais justa e completa. Qual seria ele: critério socioeconômico, satisfação de estudantes, área de interesse profissional, colocação após a formação ou outro? Justifique e descreva como protegeria a privacidade das pessoas.

**7.11 — A próxima pergunta**

O que faz a tabela **__vinculos_talentos__**?

## Nível 8: Duas Frentes, Duas Operações

**8.1** Quanto custa manter a frente educacional em comparação à operação comercial? (Faça uma análise de custo total com salários, suprimentos e despesas gerais para cada departamento.)

**8.2** Quais escritórios concentram equipes comerciais e quais concentram equipes da escola?

**8.3** A receita das vendas consegue sustentar investimentos educacionais?

**8.4** Quais cargos e departamentos são compartilhados pelas duas frentes?

**8.5** Como a expansão internacional afeta vendas, equipes e o projeto educacional?

## Nível 9: Análise Avançada com Agregações

**9.1** Crie um relatório mostrando cada departamento com: nome do departamento, número de funcionários, salário total e média salarial.

**9.2** Liste os 3 cargos mais comuns na empresa e quantos funcionários ocupam cada cargo.

**9.3** Encontre todos os funcionários que ganham acima da média salarial de seus respectivos departamentos.

**9.4** Calcule a taxa de crescimento da empresa por ano (quantos funcionários foram contratados a cada ano).

**9.5** Crie um ranking dos vendedores, mostrando: nome do vendedor, número de vendas realizadas e receita total gerada.

**9.6** Encontre os produtos que foram vendidos por apenas um vendedor.

---

## Nível 10:  Auditoria de Vendas

O departamento financeiro suspeita de irregularidades.

**10.1** Encontre vendas que não possuem vendedor associado.

**10.2** Verifique se há vendedores registrados nas vendas que não existem na coleção de funcionários.

**10.3** Identifique produtos que aparecem nas vendas mas com preços unitários muito diferentes entre transações (variação > 10%).

**10.4** O CEO pediu um dashboard completo.

Crie UMA ÚNICA query de agregação que retorne:
   - Total de funcionários
   - Custo total com salários
   - Número de departamentos
   - Número de escritórios
   - Receita total de vendas
   - Produto mais vendido

## Nível 11: ETL do CSV

O arquivo [vendas_campanha_bruto.csv](vendas_campanha_bruto.csv) contém dados de pedidos e itens em formatos variados. 
O que você deve fazer: carregá-lo na tabela `stg_vendas_csv`, sem converter nem corrigir os valores na importação. 

> stg é uma abreviação de staging (preparação, em portugês): uma área intermediária onde os dados brutos são carregados antes de serem tratados e enviados às tabelas finais.

Neste exercício, stg_vendas_csv recebe o conteúdo do CSV como chegou. Depois, os dados são validados e transformados, carregados os aceitos em vendas e itens_venda. Então, são documentados os casos problemáticos em etl_rejeicoes. Apesar do nome, essa tabela não é necessariamente temporária: ela pode ser mantida para rastrear a origem dos dados.

**Dica**: No MySQL Workbench, vocês podem usar o **Table Data Import Wizard** apontando para a tabela já criada, com delimitador `;` e a primeira linha como cabeçalho. Se o ambiente permitir `LOAD DATA LOCAL INFILE`, também é possível usá-lo.

Construam um fluxo com estas fases:

1. **Extract:** importar todas as linhas e conservar `source_row_id` e `lote_origem`.
2. **Transform:** normalizar espaços e capitalização; converter quantidades, datas e preços; padronizar canal e status; conferir SKU e e-mail do vendedor; identificar duplicatas e conflitos.
3. **Load:** inserir pedidos em `vendas` e linhas em `itens_venda`. Registrar pendências ou rejeições em `etl_rejeicoes`, preservando o valor original, o campo e o motivo.

Regras para orientar a análise:

- usem `locale_origem` ao interpretar datas e separadores decimais; se a localidade não estiver identificada, não escolham uma interpretação por palpite;
- `moeda_raw` precisa ser identificável; preservem a moeda original do registro;
- SKU desconhecido, vendedor sem correspondência, quantidade inválida, data impossível ou preço não interpretável precisam de tratamento documentado;
- linhas com a mesma combinação pedido/item podem ser duplicatas ou correções conflitantes. Compare os demais campos antes de decidir;
- se um pedido tiver uma linha pendente, decidam se carregam as linhas válidas ou mantêm o pedido inteiro em revisão. Registrem o critério usado;
- `source_row_id` em `itens_venda` liga uma linha carregada à linha original do CSV.

A tabela `etl_rejeicoes` foi criada para documentar decisões. Um registro rejeitado não deve desaparecer silenciosamente: indiquem se foi duplicata, rejeição definitiva ou revisão manual.

## Nível 12: Alterações seguras

Façam alterações em transações e verifiquem o resultado antes de confirmar:

- criar um departamento novo em um escritório existente;
- cadastrar o cargo “Senior Web Developer” e promover Bruce Ernst, atualizando cargo e salário;
- transferir duas pessoas de Tecnologia para o novo departamento, justificando a escolha;
- reajustar salários de quem permanecer em Tecnologia;
- adicionar uma compra de headsets com quantidade, custo unitário, moeda, data e referência de compra;
- simular aposentadoria alterando o status do funcionário para `INATIVO`, sem apagar o funcionário nem seu histórico.

Exemplo de fluxo seguro:

```sql
START TRANSACTION;
-- faça a alteração planejada
-- confira com SELECT se o resultado corresponde ao esperado
ROLLBACK; -- use COMMIT somente quando estiver validado
```