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

R:
```
Curso | Carga Hr | Nivel | Turmas Abertas
Tecnologia Criativa	80	INTRODUTORIO	1
Narrativas e Cultura Pop	60	INTERMEDIARIO	1
Laboratório de Dados	100	AVANCADO	1
```

```sql
SELECT 
    c.curso_nome,
    c.carga_horaria,
    nc.nome AS nivel_curso,
    COUNT(t.turma_id) AS total_turmas_abertas
FROM cursos c
INNER JOIN niveis_curso nc ON c.nivel_curso_id = nc.nivel_curso_id
LEFT JOIN turmas t ON c.curso_id = t.curso_id
WHERE c.ativo = 1
GROUP BY c.curso_id, c.curso_nome, c.carga_horaria, nc.nome;
```

**7.2 — Quem chegou até aqui?**

Para cada turma, mostre curso, professores, capacidade e número de matrículas. Há vagas disponíveis ou turmas ainda sem estudantes? O que isso sugere sobre oferta e procura?

R: Faltam bastante vagas a serem preenchidas, sugere uma melhor divulgação do curso
```
TEC-2025-01	Tecnologia Criativa	Filius Flitwick	30	2	28
NAR-2025-01	Narrativas e Cultura Pop	Ninfadora Tonks	25	1	24
DAD-2025-01	Laboratório de Dados	Fleur Dascores	20	1	19
```

```sql
SELECT 
    t.codigo AS turma_codigo,
    c.curso_nome,
    CONCAT(f.primeiro_nome, ' ', f.sobrenome) AS professor,
    t.capacidade,
    COUNT(m.matricula_id) AS total_matriculas,
    (t.capacidade - COUNT(m.matricula_id)) AS vagas_disponiveis
FROM turmas t
INNER JOIN cursos c ON t.curso_id = c.curso_id
INNER JOIN funcionarios f ON t.professor_funcionario_id = f.funcionario_id
LEFT JOIN matriculas m ON t.turma_id = m.turma_id
GROUP BY t.turma_id, t.codigo, c.curso_nome, professor, t.capacidade;
```

**7.3 — Acesso à formação**

Quantos estudantes receberam bolsa, qual foi o percentual concedido e em quais cursos? 

R:
```
Curso | Porcentual desconto | Estudantes bolsistas
Narrativas e Cultura Pop	50.00	1
Tecnologia Criativa	100.00	1
```

```sql
SELECT 
    c.curso_nome,
    b.percentual_desconto,
    COUNT(b.aluno_id) AS total_estudantes_bolsistas
FROM bolsas b
INNER JOIN cursos c ON b.curso_id = c.curso_id
GROUP BY c.curso_nome, b.percentual_desconto;
```

**7.4 — Conclusão e reconhecimento**

Por curso e turma, calcule matrículas, concluintes, certificados emitidos e nota média. Quais perguntas adicionais seriam necessárias antes de afirmar que um curso teve “mais sucesso” que outro?

R:Se o curso já foi finalizado.
```
Curso | Codigo | Matriculas | Conclusão | Certificados | Média 
Laboratório de Dados	DAD-2025-01	1	0	0	
Narrativas e Cultura Pop	NAR-2025-01	1	0	0	
Tecnologia Criativa	TEC-2025-01	2	2	2	88.75
```

```sql
SELECT 
    c.curso_nome,
    t.codigo AS turma_codigo,
    COUNT(m.matricula_id) AS total_matriculas,
    SUM(CASE WHEN sm.nome = 'CONCLUIDA' THEN 1 ELSE 0 END) AS total_concluintes,
    SUM(CASE WHEN m.certificado_emitido = 1 THEN 1 ELSE 0 END) AS total_certificados,
    ROUND(AVG(m.nota_final), 2) AS nota_media
FROM turmas t
INNER JOIN cursos c ON t.curso_id = c.curso_id
LEFT JOIN matriculas m ON t.turma_id = m.turma_id
LEFT JOIN status_matricula sm ON m.status_matricula_id = sm.status_matricula_id
GROUP BY c.curso_nome, t.turma_id, t.codigo;
```

**7.5 — O próximo capítulo de Ariel**

Reconstrua a trajetória de Ariel Nunes: curso, turma, matrícula, bolsa, estágio e contratação. Em que momento a formação passou a se conectar com uma oportunidade corporativa?

R:Quando ele encerrou o curso.
```
Ariel Nunes	Tecnologia Criativa	TEC-2025-01	2025-01-15	100.00	ESTAGIO	2025-05-05	2025-05-11	ENCERRADO	Tecnologia da Informação
Ariel Nunes	Tecnologia Criativa	TEC-2025-01	2025-01-15	100.00	CONTRATACAO	2025-05-12		ATIVO	Tecnologia da Informação
```

```sql
SELECT 
    a.nome AS aluno,
    c.curso_nome,
    t.codigo AS turma_codigo,
    m.data_matricula,
    b.percentual_desconto AS bolsa_percentual,
    tv.nome AS tipo_vinculo,
    v.data_inicio,
    v.data_fim,
    sv.nome AS status_vinculo,
    d.departamento_nome
FROM alunos a
INNER JOIN matriculas m ON a.aluno_id = m.aluno_id
INNER JOIN turmas t ON m.turma_id = t.turma_id
INNER JOIN cursos c ON t.curso_id = c.curso_id
LEFT JOIN bolsas b ON a.aluno_id = b.aluno_id AND c.curso_id = b.curso_id
LEFT JOIN vinculos_talentos v ON a.aluno_id = v.aluno_id
LEFT JOIN tipos_vinculo tv ON v.tipo_vinculo_id = tv.tipo_vinculo_id
LEFT JOIN status_vinculo sv ON v.status_vinculo_id = sv.status_vinculo_id
LEFT JOIN departamentos d ON v.departamento_id = d.departamento_id
WHERE a.nome = 'Ariel Nunes';
```

**7.6 — Da aprendizagem para o trabalho**

Liste os vínculos de talentos com estudante, tipo de vínculo, departamento, status e, quando existir, a pessoa funcionária associada. Quantas pessoas passaram por estágio e quantas chegaram à contratação?

R: Apenas a Ariel Nunes

```sql
SELECT 
    a.nome AS estudante,
    tv.nome AS tipo_vinculo,
    d.departamento_nome,
    sv.nome AS status_vinculo,
    CONCAT(f.primeiro_nome, ' ', f.sobrenome) AS funcionario_associado
FROM vinculos_talentos v
INNER JOIN alunos a ON a.aluno_id = v.aluno_id
INNER JOIN tipos_vinculo tv ON v.tipo_vinculo_id = tv.tipo_vinculo_id
INNER JOIN departamentos d ON v.departamento_id = d.departamento_id
INNER JOIN status_vinculo sv ON v.status_vinculo_id = sv.status_vinculo_id
LEFT JOIN funcionarios f ON v.funcionario_id = f.funcionario_id;
```

**7.7 — Onde a ponte encontra a empresa?**

Quais departamentos recebem talentos da escola? Compare-os com seu total de funcionários e média salarial. Como evitar a conclusão apressada de que um departamento é “melhor” apenas porque contratou mais estudantes?

R: O departamento: Tecnologia da Informação, Quantidades de alunos:	1, Total de funcionarios: 6 e Média salarial: 8855.87

```sql
SELECT 
    d.departamento_nome,
    COUNT(DISTINCT v.aluno_id) AS talentos_recebidos,
    COUNT(DISTINCT f.funcionario_id) AS total_funcionarios,
    ROUND(AVG(f.salario), 2) AS media_salarial_depto
FROM departamentos d
INNER JOIN vinculos_talentos v ON d.departamento_id = v.departamento_id
LEFT JOIN funcionarios f ON d.departamento_id = f.departamento_id
GROUP BY d.departamento_id, d.departamento_nome;
```

**7.8 — Um retrato para a liderança**

Crie uma única consulta que apresente: total de alunos, matrículas ativas, concluintes, bolsas concedidas, estágios, contratações e departamentos que receberam talentos. Escreva, abaixo do resultado, um parágrafo de até cinco linhas explicando o que a liderança pode aprender — e o que ainda não é possível afirmar.

R: Total Alunos: 4,	Matriculas Ativas: 2, Concluientes: 2, bolsas concedidas: 2, estagios: 1, Contratações:	1 e Departamentos beneficiados: 1.

```sql
SELECT 
    (SELECT COUNT(*) FROM alunos) AS total_alunos,
    (SELECT COUNT(*) FROM matriculas m INNER JOIN status_matricula sm ON m.status_matricula_id = sm.status_matricula_id WHERE sm.nome = 'ATIVA') AS matriculas_ativas,
    (SELECT COUNT(*) FROM matriculas m INNER JOIN status_matricula sm ON m.status_matricula_id = sm.status_matricula_id WHERE sm.nome = 'CONCLUIDA') AS concluintes,
    (SELECT COUNT(*) FROM bolsas) AS bolsas_concedidas,
    (SELECT COUNT(*) FROM vinculos_talentos v INNER JOIN tipos_vinculo tv ON v.tipo_vinculo_id = tv.tipo_vinculo_id WHERE tv.nome = 'ESTAGIO') AS estagios,
    (SELECT COUNT(*) FROM vinculos_talentos v INNER JOIN tipos_vinculo tv ON v.tipo_vinculo_id = tv.tipo_vinculo_id WHERE tv.nome = 'CONTRATACAO') AS contratacoes,
    (SELECT COUNT(DISTINCT departamento_id) FROM vinculos_talentos) AS departamentos_beneficiados;
```

**7.9 — Educação e negócio, lado a lado**

Monte uma consulta comparando, por período, indicadores educacionais (matrículas, certificados e vínculos) com indicadores corporativos (vendas, receita e pessoas contratadas). Quais limites existem nessa comparação, já que correlação não comprova causalidade?

R:Existe o limite por conta do numero de matriculas
```
Periodo | Nova Matriculas | Novo vinculo | total vendas | total receitas
2025-01	2	0	1	26341.16
2025-02	1	0	2	16310.61
2025-05	1	2	2	15848.38
```

```sql
SELECT 
    DATE_FORMAT(m.data_matricula, '%Y-%m') AS periodo,
    COUNT(DISTINCT m.matricula_id) AS novas_matriculas,
    COUNT(DISTINCT v_talento.vinculo_id) AS novos_vinculos,
    COUNT(DISTINCT v.venda_id) AS total_vendas,
    SUM(iv.quantidade * iv.preco_unitario) AS receita_vendas
FROM matriculas m
LEFT JOIN vinculos_talentos v_talento ON DATE_FORMAT(m.data_matricula, '%Y-%m') = DATE_FORMAT(v_talento.data_inicio, '%Y-%m')
LEFT JOIN vendas v ON DATE_FORMAT(m.data_matricula, '%Y-%m') = DATE_FORMAT(v.data_venda, '%Y-%m')
LEFT JOIN itens_venda iv ON v.venda_id = iv.venda_id
GROUP BY periodo
ORDER BY periodo ASC;
```

**7.10 — A próxima pergunta**

Imagine que você terá recursos para coletar somente um dado novo para tornar essa história mais justa e completa. Qual seria ele: critério socioeconômico, satisfação de estudantes, área de interesse profissional, colocação após a formação ou outro? Justifique e descreva como protegeria a privacidade das pessoas.

R:Satisfação dos estudantes, para ver o nivel de qualidade do curso e do objetivo de agregar novos talentos a empresa. protegeria por esse dados serem descritos de forma anonima sem vincular ao estudante.

**7.11 — A próxima pergunta**

O que faz a tabela **__vinculos_talentos__**?

R: Ela vicula os estudantes a empresa.

## Nível 8: Duas Frentes, Duas Operações

**8.1** Quanto custa manter a frente educacional em comparação à operação comercial? (Faça uma análise de custo total com salários, suprimentos e despesas gerais para cada departamento.)

R:
```
Frente Operacional | Custo total de Salarios
Frente Comercial/Corporativa	720743.07
Frente Educacional	406100.00
```

```sql
SELECT 
    CASE 
        WHEN d.educacional = 1 THEN 'Frente Educacional'
        ELSE 'Frente Comercial/Corporativa'
    END AS frente_operacional,
    SUM(f.salario) AS custo_total_salarios
FROM funcionarios f
INNER JOIN departamentos d ON f.departamento_id = d.departamento_id
GROUP BY frente_operacional;
```

**8.2** Quais escritórios concentram equipes comerciais e quais concentram equipes da escola?

R:
```
Nome escritorio | Tipo de Operação
Torre de Paris	Possui Escola/Educacional
Wayne Offices	Exclusivo Comercial/Corporativo
Stark Tower	Exclusivo Comercial/Corporativo
Sala Winter	Exclusivo Comercial/Corporativo
Arkham Base	Exclusivo Comercial/Corporativo
House of Mystery	Exclusivo Comercial/Corporativo
Shuri's Palace	Exclusivo Comercial/Corporativo
Umbrella Corp	Exclusivo Comercial/Corporativo
Campus de Lisboa	Exclusivo Comercial/Corporativo
Archies Mad House	Exclusivo Comercial/Corporativo
Verstebona	Possui Escola/Educacional
Daily Planet Bureau	Exclusivo Comercial/Corporativo
Castelo Encantado	Possui Escola/Educacional
Cape Town Studio	Exclusivo Comercial/Corporativo
Koboa Koboa	Possui Escola/Educacional
Paititi Operations	Possui Escola/Educacional
Baxter Building	Exclusivo Comercial/Corporativo
Instituto Rio	Possui Escola/Educacional
Castelo Principal	Possui Escola/Educacional
Tokyo Lab	Possui Escola/Educacional
```

```sql
SELECT 
    esc.escritorio_nome,
    CASE 
        WHEN SUM(d.educacional) > 0 THEN 'Possui Escola/Educacional'
        ELSE 'Exclusivo Comercial/Corporativo'
    END AS tipo_operacao_escritorio
FROM escritorios esc
INNER JOIN departamentos d ON esc.escritorio_id = d.escritorio_id
GROUP BY esc.escritorio_id, esc.escritorio_nome;
```

**8.3** A receita das vendas consegue sustentar investimentos educacionais?

R: Total de vendas:863042.05 e custo educacional: 406100.00

```sql
SELECT 
(SELECT SUM(iv.quantidade * iv.preco_unitario)
FROM itens_venda iv) AS receita_total_vendas,
    (SELECT SUM(f.salario) 
    FROM funcionarios f INNER JOIN departamentos d ON f.departamento_id = d.departamento_id
    WHERE d.educacional = 1) AS custo_total_educacao;
```

**8.4** Quais cargos e departamentos são compartilhados pelas duas frentes?

R:
```
Nome do Cargo | Departamento | Frente
Assistente Administrativo	Administração Executiva	Corporativo
CMO	Marketing	Corporativo
Representante de Vendas LATAM	Marketing	Corporativo
Gerente de Recursos Humanos	Recursos Humanos	Corporativo
Assistente de Compras	Recursos Humanos	Corporativo
Assistente de Recursos Humanos	Recursos Humanos	Corporativo
Gerente de Estoque	Logística	Corporativo
Desenvolvedor Web	Tecnologia da Informação	Corporativo
Analista de Qualidade	Tecnologia da Informação	Corporativo
Relações Públicas	Relações Públicas	Corporativo
Gerente de Vendas	Vendas	Corporativo
Representante de Vendas	Vendas	Corporativo
Contador	Finanças	Corporativo
CFO	Finanças	Corporativo
Gerente de Contabilidade	Contabilidade	Corporativo
Cientista de Dados	Biotecnologia	Corporativo
Senior Web Developer	Tecnologias Avançadas	Corporativo
Cientista de Dados	Tecnologias Avançadas	Corporativo
Cientista de Dados	Dados e Inteligência	Corporativo
Analista de Atendimento	Experiência do Cliente	Corporativo
Gerente de Operações	Operações LATAM	Corporativo
Especialista de Segurança	Segurança da Informação	Corporativo
Designer de Produto	Pesquisa e Desenvolvimento	Corporativo
Especialista de Marketing Digital	Comércio Digital	Corporativo
Gerente de Operações	Operações APAC	Corporativo
Designer de Produto	Criação de Conteúdo	Corporativo
Estoquista	Operações África	Corporativo
Diretor	Poções	Educacional
Mestre de Poções	Poções	Educacional
Professor Titular	Transfiguração	Educacional
Professor Assistente	Transfiguração	Educacional
Professor Assistente	Projeções Astrais	Educacional
Oficial de Segurança Biológia	Projeções Astrais	Educacional
Tratador de Criaturas	Criaturas Mágicas	Educacional
Guardião	Criaturas Mágicas	Educacional
Professor Titular	Criaturas Mágicas	Educacional
Aprendiz	Criaturas Mágicas	Educacional
Diretor	Criaturas Mágicas	Educacional
Bibliotecário Arcano	Biblioteca Arcana	Educacional
Professor Titular	Biblioteca Arcana	Educacional
Professor Assistente	Biblioteca Arcana	Educacional
Diretor	Administração Educacional	Educacional
Guardião	Administração Educacional	Educacional
Professor Assistente	Administração Educacional	Educacional
Secretário Administrativo	Administração Educacional	Educacional
Professor Titular	Administração Educacional	Educacional
Aprendiz	Administração Educacional	Educacional
Professor Assistente	Astronomia	Educacional
Diretor	Astronomia	Educacional
Astrônomago	Astronomia	Educacional
Aprendiz	Astronomia	Educacional
Herbólogo	Herbologia	Educacional
Diretor	Herbologia	Educacional
Guardião	Herbologia	Educacional
Aprendiz	Herbologia	Educacional
```

```sql
SELECT DISTINCT 
    c.cargo_nome,
    d.departamento_nome,
    CASE WHEN d.educacional = 1 THEN 'Educacional' ELSE 'Corporativo' END AS frente
FROM funcionarios f
INNER JOIN cargos c ON f.cargo_id = c.cargo_id
INNER JOIN departamentos d ON f.departamento_id = d.departamento_id;
```

**8.5** Como a expansão internacional afeta vendas, equipes e o projeto educacional?

R: Aumenta o numero de possiveis moedas se não for feito o cambio atraves do dollar ou otra moeda e aumenta o numero de escolas entre os paises trazendo um maior numero de dados também

## Nível 9: Análise Avançada com Agregações

**9.1** Crie um relatório mostrando cada departamento com: nome do departamento, número de funcionários, salário total e média salarial.

R:
```
Nome Departamento | Total Funcionarios | Salario total | Média salarial
Administração Executiva	1	4653.76	4653.76
Marketing	2	17197.79	8598.90
Recursos Humanos	6	32442.93	5407.16
Recursos Humanos	1	6035.47	6035.47
Logística	4	29147.03	7286.76
Tecnologia da Informação	6	53135.22	8855.87
Relações Públicas	2	14866.99	7433.50
Vendas	5	59390.76	11878.15
Executivo	0		
Finanças	6	46109.77	7684.96
Contabilidade	1	13265.79	13265.79
Biotecnologia	2	58526.95	29263.48
Tecnologias Avançadas	4	80168.26	20042.07
Dados e Inteligência	3	85328.25	28442.75
Experiência do Cliente	3	19327.94	6442.65
Operações LATAM	3	40925.89	13641.96
Segurança da Informação	3	39900.07	13300.02
Pesquisa e Desenvolvimento	3	29967.18	9989.06
Comércio Digital	3	25804.49	8601.50
Operações APAC	3	39909.61	13303.20
Criação de Conteúdo	2	17564.49	8782.25
Operações África	2	7074.43	3537.22
Poções	4	51300.00	12825.00
Transfiguração	3	25600.00	8533.33
Projeções Astrais	6	43400.00	7233.33
Criaturas Mágicas	8	51100.00	6387.50
Biblioteca Arcana	7	32700.00	4671.43
Administração Educacional	10	117100.00	11710.00
Astronomia	5	38700.00	7740.00
Herbologia	7	46200.00	6600.00
Inovações	0		
```

```sql
SELECT 
    d.departamento_nome,
    COUNT(f.funcionario_id) AS total_funcionarios,
    SUM(f.salario) AS salario_total,
    ROUND(AVG(f.salario), 2) AS media_salarial
FROM departamentos d
LEFT JOIN funcionarios f ON d.departamento_id = f.departamento_id
GROUP BY d.departamento_id, d.departamento_nome;
```

**9.2** Liste os 3 cargos mais comuns na empresa e quantos funcionários ocupam cada cargo.

R:
```
Cargo nome | total de ocupantes
Professor Assistente	8
Cientista de Dados	8
Diretor	6
```

```sql
SELECT 
    c.cargo_nome,
    COUNT(f.funcionario_id) AS total_ocupantes
FROM funcionarios f
INNER JOIN cargos c ON f.cargo_id = c.cargo_id
GROUP BY c.cargo_id, c.cargo_nome
ORDER BY total_ocupantes DESC
LIMIT 3;
```

**9.3** Encontre todos os funcionários que ganham acima da média salarial de seus respectivos departamentos.

R:
```
Nome/Sobrenome Funcionario | Salário | Departamento | Média Departamento
Elisabeth	Braddock	11971.26	Marketing	8598.895000
Den	Raphaely	13557.76	Recursos Humanos	5407.155000
Matthew	Weiss	7959.36	Logística	7286.757500
Payam	Kaufling	7902.10	Logística	7286.757500
Diana	Lorentz	9054.44	Tecnologia da Informação	8855.870000
Dick	Grayson	9401.37	Tecnologia da Informação	8855.870000
Samus	Aran	12860.02	Tecnologia da Informação	8855.870000
Hermann	Baer	9854.88	Relações Públicas	7433.495000
John	Russell	16957.66	Vendas	11878.152000
Karen	Partners	16435.94	Vendas	11878.152000
Luis	Popp	8163.72	Finanças	7684.961667
Lucius	Fox	15035.54	Finanças	7684.961667
Spock	Sarek	34770.49	Biotecnologia	29263.475000
Shuri	Udaku	32002.61	Tecnologias Avançadas	20042.065000
Miles	Morales	29124.80	Dados e Inteligência	28442.750000
Victor	Stone	33179.12	Dados e Inteligência	28442.750000
Kamala	Khan	6803.69	Experiência do Cliente	6442.646667
Elena	Rossi	6822.11	Experiência do Cliente	6442.646667
Rogue	LeBeau	17673.60	Operações LATAM	13641.963333
Ana	Costa	16876.26	Segurança da Informação	13300.023333
Clint	Barton	11661.65	Pesquisa e Desenvolvimento	9989.060000
Jean	Grey	11494.56	Pesquisa e Desenvolvimento	9989.060000
Barbara	Gordon	9059.15	Comércio Digital	8601.496667
Scott	Summers	11433.38	Comércio Digital	8601.496667
Cyborg	Stone	16578.59	Operações APAC	13303.203333
Barry	Allen	9230.10	Criação de Conteúdo	8782.245000
Arthur	Curry	4208.78	Operações África	3537.215000
Minerva	McGivver	15000.00	Poções	12825.000000
Lucas	Pereira	18000.00	Poções	12825.000000
Rodrigo	Alves	12000.00	Transfiguração	8533.333333
Kingsley	Tremerraios	10500.00	Projeções Astrais	7233.333333
Daniel	Ravenwood	9200.00	Projeções Astrais	7233.333333
Fleur	Dascores	9200.00	Criaturas Mágicas	6387.500000
Olympe	Maxime	14000.00	Criaturas Mágicas	6387.500000
Fernanda	Lima	9500.00	Criaturas Mágicas	6387.500000
Beatriz	Gonçalves	7200.00	Biblioteca Arcana	4671.428571
Tomas	Ferreira	4900.00	Biblioteca Arcana	4671.428571
Olivia	Moon	4700.00	Biblioteca Arcana	4671.428571
Helena	Parker	18000.00	Administração Educacional	11710.000000
Paulo	Andrade	45000.00	Administração Educacional	11710.000000
Marina	Costa	22000.00	Administração Educacional	11710.000000
Elizabeth	Madpreta	17000.00	Astronomia	7740.000000
Nathan	Hawthorne	7800.00	Astronomia	7740.000000
Haruki	Tanaka	16500.00	Herbologia	6600.000000
Yuki	Sato	6800.00	Herbologia	6600.000000
```

```sql
SELECT 
    f.primeiro_nome,
    f.sobrenome,
    f.salario,
    d.departamento_nome,
    m.media_depto
FROM funcionarios f
INNER JOIN departamentos d ON f.departamento_id = d.departamento_id
INNER JOIN (
SELECT
    departamento_id,
    AVG(salario) AS media_depto
    FROM funcionarios
    GROUP BY departamento_id
) m ON f.departamento_id = m.departamento_id
WHERE f.salario > m.media_depto;
```

**9.4** Calcule a taxa de crescimento da empresa por ano (quantos funcionários foram contratados a cada ano).

R:
```
Ano Contratação | Total de Contratação Ano | Total Ano Anterior | Taxa de crescimento porcentual
1990	3	0	Ano Base
1991	2	3	-33.33%
1992	3	2	50.00%
1993	3	3	0.00%
1994	2	3	-33.33%
1995	3	2	50.00%
1996	3	3	0.00%
1997	3	3	0.00%
1998	3	3	0.00%
1999	3	3	0.00%
2000	2	3	-33.33%
2001	3	2	50.00%
2002	1	3	-66.67%
2003	3	1	200.00%
2004	2	3	-33.33%
2005	3	2	50.00%
2006	3	3	0.00%
2007	2	3	-33.33%
2008	3	2	50.00%
2009	3	3	0.00%
2010	3	3	0.00%
2011	5	3	66.67%
2012	4	5	-20.00%
2013	4	4	0.00%
2014	4	4	0.00%
2015	6	4	50.00%
2016	6	6	0.00%
2017	6	6	0.00%
2018	6	6	0.00%
2019	6	6	0.00%
2020	3	6	-50.00%
2021	3	3	0.00%
2022	3	3	0.00%
2023	2	3	-33.33%
2025	1	0	Ano Base
```

```sql
SELECT 
    atual.ano_contratacao,
    atual.total_contratacoes AS total_contratacoes_ano,
    COALESCE(anterior.total_contratacoes, 0) AS total_ano_anterior,
    CASE 
        WHEN anterior.total_contratacoes IS NULL OR anterior.total_contratacoes = 0 THEN 'Ano Base'
        ELSE CONCAT(
            ROUND(
                ((atual.total_contratacoes - anterior.total_contratacoes) / anterior.total_contratacoes) * 100, 
                2
            ), 
            '%'
        )
    END AS taxa_crescimento_percentual
FROM (
    -- Agrupa o total de contratados por ano
    SELECT 
        YEAR(data_contratacao) AS ano_contratacao,
        COUNT(*) AS total_contratacoes
    FROM funcionarios
    GROUP BY YEAR(data_contratacao)
) AS atual
LEFT JOIN (
    -- Mesma consulta, deslocada em 1 ano para trás para comparação
    SELECT 
        YEAR(data_contratacao) AS ano_contratacao,
        COUNT(*) AS total_contratacoes
    FROM funcionarios
    GROUP BY YEAR(data_contratacao)
) AS anterior ON atual.ano_contratacao = anterior.ano_contratacao + 1
ORDER BY atual.ano_contratacao ASC;
```

**9.5** Crie um ranking dos vendedores, mostrando: nome do vendedor, número de vendas realizadas e receita total gerada.

R:
```
Nome Vendedor | Total de Vendas | Receita Total
John Russell	11	196953.14
Jack Livingston	11	188362.86
Jonathon Taylor	11	184155.75
Kimberly Grant	10	150135.73
Karen Partners	11	143434.57
```

```sql
SELECT 
    CONCAT(f.primeiro_nome, ' ', f.sobrenome) AS nome_vendedor,
    COUNT(DISTINCT v.venda_id) AS total_vendas,
    SUM(iv.quantidade * iv.preco_unitario) AS receita_total
FROM vendas v
INNER JOIN funcionarios f ON v.funcionario_id = f.funcionario_id
INNER JOIN itens_venda iv ON v.venda_id = iv.venda_id
GROUP BY f.funcionario_id, nome_vendedor
ORDER BY receita_total DESC;
```

**9.6** Encontre os produtos que foram vendidos por apenas um vendedor.

R:
```
Nome do Produto
Capacete Iron Man Mark 5
Sabre de luz de Mace Windu
Pokébola clássica
Capacete Darth Vader
Escudo do Capitão América
Blaster Imperial
Capa do Batman
Chapéu Seletor
```

```sql
SELECT 
    p.produto_nome
FROM itens_venda iv
INNER JOIN vendas v ON iv.venda_id = v.venda_id
INNER JOIN produtos p ON iv.produto_id = p.produto_id
GROUP BY p.produto_id, p.produto_nome
HAVING COUNT(DISTINCT v.funcionario_id) = 1;
```

---

## Nível 10:  Auditoria de Vendas

O departamento financeiro suspeita de irregularidades.

**10.1** Encontre vendas que não possuem vendedor associado.

R:
```
Venda ID | Referencia Origem | Data Venda | Cliente ID | Funcionario ID | Canal Venda ID | Status Venda ID
7001	ERP-7001	2023-01-03		124	1	3
7003	ERP-7003	2023-02-10		126	3	1
7004	ERP-7004	2023-03-01		127	4	1
7005	ERP-7005	2023-03-20		128	5	1
7006	ERP-7006	2023-04-08		124	1	1
7008	ERP-7008	2023-05-16		126	3	1
7009	ERP-7009	2023-06-04		127	4	1
7010	ERP-7010	2023-06-23		128	5	1
7011	ERP-7011	2023-07-12		124	1	1
7013	ERP-7013	2023-08-19		126	3	1
7014	ERP-7014	2023-09-07		127	4	2
7015	ERP-7015	2023-09-26		128	5	1
7016	ERP-7016	2023-10-15		124	1	1
7017	ERP-7017	2023-11-03		125	2	1
7018	ERP-7018	2023-11-22		126	3	3
7019	ERP-7019	2023-12-11		127	4	1
7020	ERP-7020	2023-12-30		128	5	1
7021	ERP-7021	2024-01-18		124	1	1
7023	ERP-7023	2024-02-25		126	3	1
7024	ERP-7024	2024-03-15		127	4	1
7025	ERP-7025	2024-04-03		128	5	1
7026	ERP-7026	2024-04-22		124	1	1
7028	ERP-7028	2024-05-30		126	3	1
7029	ERP-7029	2024-06-18		127	4	1
7030	ERP-7030	2024-07-07		128	5	1
7031	ERP-7031	2024-07-26		124	1	1
7032	ERP-7032	2024-08-14		125	2	1
7033	ERP-7033	2024-09-02		126	3	1
7034	ERP-7034	2024-09-21		127	4	1
7035	ERP-7035	2024-10-10		128	5	3
7036	ERP-7036	2024-10-29		124	1	1
7038	ERP-7038	2024-12-06		126	3	1
7039	ERP-7039	2024-12-25		127	4	1
7040	ERP-7040	2025-01-13		128	5	2
7041	ERP-7041	2025-02-01		124	1	1
7043	ERP-7043	2025-03-11		126	3	1
7044	ERP-7044	2025-03-30		127	4	1
7045	ERP-7045	2025-04-18		128	5	1
7046	ERP-7046	2025-05-07		124	1	1
7047	ERP-7047	2025-05-26		125	2	1
7049	ERP-7049	2025-07-03		127	4	1
7050	ERP-7050	2025-07-22		128	5	1
7052	ERP-7052	2023-01-12		125	2	3
7053	ERP-7053	2023-01-31		126	3	2
7054	ERP-7054	2023-02-19		127	4	1
						
```

```sql
SELECT * 
FROM vendas 
WHERE cliente_id IS NULL;
```

**10.2** Verifique se há vendedores registrados nas vendas que não existem na coleção de funcionários.

R: por conta da chave estrangeira o banco empedi registros de vendedores que não tenham em funcionarios e essa query abaixo confirma isso.

```sql
SELECT DISTINCT v.venda_id, v.funcionario_id
FROM vendas v
LEFT JOIN funcionarios f ON v.funcionario_id = f.funcionario_id
WHERE f.funcionario_id IS NULL;
```

**10.3** Identifique produtos que aparecem nas vendas mas com preços unitários muito diferentes entre transações (variação > 10%).

R:
```
Nome Produto | Menor Preço | Maior Preço
Batarang de treino	198.88	248.62
Lança-Teias	200.75	245.85
Laço da Verdade	271.67	332.87
Sentinela em miniatura	128.60	142.74
Laço da Honestidade	566.42	670.79
Batarangs oficiais	764.44	908.90
Pokédex portátil	172.37	205.16
Anel do Poder (réplica)	832.89	1025.63
Master Sword (réplica)	1498.64	1702.13
Buster Sword (réplica)	1123.55	1346.76
Tesseract decorativo	6124.70	7053.19
Blaster de Han Solo	341.85	409.25
Manopla do Infinito	4304.41	5047.48
Reator Arc decorativo	599.78	669.90
Boné do treinador	43.59	50.20
```

```sql
SELECT 
    p.produto_nome,
    MIN(iv.preco_unitario) AS menor_preco,
    MAX(iv.preco_unitario) AS maior_preco
FROM itens_venda iv
INNER JOIN produtos p ON iv.produto_id = p.produto_id
GROUP BY p.produto_id, p.produto_nome
HAVING (MAX(iv.preco_unitario) - MIN(iv.preco_unitario)) / MIN(iv.preco_unitario) > 0.10;
```

**10.4** O CEO pediu um dashboard completo.

Crie UMA ÚNICA query de agregação que retorne:
   - Total de funcionários
   - Custo total com salários
   - Número de departamentos
   - Número de escritórios
   - Receita total de vendas
   - Produto mais vendido

   
R:
```
Total de Funcionarios | Custo total de Salarios | Numero de Departamentos | Numero de Escritorios | Receita Total de Vendas |Produto mais vendido
115	                      1126843.07	              31	                     20	                    863042.05	        Reator Arc decorativo
```

```sql
SELECT 
    (SELECT COUNT(*) FROM funcionarios) AS total_funcionarios,
    (SELECT SUM(salario) FROM funcionarios) AS custo_total_salarios,
    (SELECT COUNT(*) FROM departamentos) AS numero_departamentos,
    (SELECT COUNT(*) FROM escritorios) AS numero_escritorios,
    (SELECT SUM(quantidade * preco_unitario) FROM itens_venda) AS receita_total_vendas,
    (
        SELECT p.produto_nome 
        FROM itens_venda iv 
        INNER JOIN produtos p ON iv.produto_id = p.produto_id 
        GROUP BY p.produto_id, p.produto_nome 
        ORDER BY SUM(iv.quantidade) DESC 
        LIMIT 1
    ) AS produto_mais_vendido;
```

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