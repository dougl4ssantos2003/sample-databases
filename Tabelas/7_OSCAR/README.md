# Oscar - Exercícios SQL

Bem-vindo à base de dados do **Oscar**!

O Oscar é a premiação mais prestigiada do cinema mundial, realizada anualmente desde 1929 pela Academia de Artes e Ciências Cinematográficas. Nesta base de dados, você encontrará registros históricos de indicados e vencedores de diversas categorias ao longo de quase 100 anos de história do cinema.

Nestes exercícios, você vai explorar o banco de dados SQL do Oscar e responder perguntas que revelam insights fascinantes sobre a história do cinema, tendências de premiação, e momentos marcantes da indústria cinematográfica.

## Avaliação

- **Nível 1-4**: Operações básicas e queries simples
- **Nível 5-8**: Agregações e análise de dados
- **Nível 9-11**: Queries complexas e pensamento analítico
- **Nível 12-14**: Expertise avançada e pensamento estratégico

**Objetivo de aprendizado**: Ao completar todos os níveis, você será capaz de trabalhar com bases de dados históricas complexas, realizar análises estatísticas sofisticadas e extrair insights valiosos de grandes volumes de dados.

---

## Nível 1: Primeiros Passos

### Conhecendo a Base de Dados

**1.1** Quantos registros existem na tabela de indicados ao Oscar?

R: 10889 registros

```sql
SELECT COUNT(*) FROM oscar_indicados;
```

**1.2.1** Quais são as diferentes categorias de premiação que existem no banco de dados? Liste todas as categorias únicas.


R:
```
Categotias:
ACTOR
ACTRESS
ART DIRECTION
CINEMATOGRAPHY
DIRECTING (Comedy Picture)
DIRECTING (Dramatic Picture)
ENGINEERING EFFECTS
OUTSTANDING PICTURE
UNIQUE AND ARTISTIC PICTURE
WRITING (Adaptation)
WRITING (Original Story)
WRITING (Title Writing)
SPECIAL AWARD
DIRECTING
WRITING
OUTSTANDING PRODUCTION
SOUND RECORDING
SHORT SUBJECT (Cartoon)
SHORT SUBJECT (Comedy)
SHORT SUBJECT (Novelty)
ASSISTANT DIRECTOR
FILM EDITING
MUSIC (Scoring)
MUSIC (Song)
DANCE DIRECTION
WRITING (Screenplay)
ACTOR IN A SUPPORTING ROLE
ACTRESS IN A SUPPORTING ROLE
SHORT SUBJECT (Color)
SHORT SUBJECT (One-reel)
SHORT SUBJECT (Two-reel)
IRVING G. THALBERG MEMORIAL AWARD
MUSIC (Original Score)
CINEMATOGRAPHY (Black-and-White)
CINEMATOGRAPHY (Color)
SPECIAL EFFECTS
ART DIRECTION (Black-and-White)
ART DIRECTION (Color)
WRITING (Original Screenplay)
DOCUMENTARY (Short Subject)
MUSIC (Music Score of a Dramatic Picture)
MUSIC (Scoring of a Musical Picture)
OUTSTANDING MOTION PICTURE
DOCUMENTARY
MUSIC (Music Score of a Dramatic or Comedy Picture)
WRITING (Original Motion Picture Story)
DOCUMENTARY (Feature)
BEST MOTION PICTURE
WRITING (Motion Picture Story)
COSTUME DESIGN (Black-and-White)
COSTUME DESIGN (Color)
SPECIAL FOREIGN LANGUAGE FILM AWARD
WRITING (Story and Screenplay)
HONORARY FOREIGN LANGUAGE FILM AWARD
HONORARY AWARD
FOREIGN LANGUAGE FILM
WRITING (Screenplay--Adapted)
WRITING (Screenplay--Original)
JEAN HERSHOLT HUMANITARIAN AWARD
COSTUME DESIGN
SHORT SUBJECT (Live Action)
WRITING (Screenplay--based on material from another medium)
WRITING (Story and Screenplay--written directly for the screen)
SOUND
MUSIC (Music Score--substantially original)
MUSIC (Scoring of Music--adaptation or treatment)
BEST PICTURE
SOUND EFFECTS
SPECIAL VISUAL EFFECTS
MUSIC (Original Music Score)
MUSIC (Original Score--for a motion picture [not a musical])
MUSIC (Score of a Musical Picture--original or adaptation)
MUSIC (Song--Original for the Picture)
WRITING (Story and Screenplay--based on material not previously published or produced)
MUSIC (Original Song Score)
WRITING (Story and Screenplay--based on factual material or material not previously published or produced)
MUSIC (Original Dramatic Score)
MUSIC (Scoring: Adaptation and Original Song Score)
SHORT SUBJECT (Animated)
SPECIAL ACHIEVEMENT AWARD (Visual Effects)
MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)
SHORT FILM (Animated)
SHORT FILM (Live Action)
WRITING (Screenplay Adapted from Other Material)
MUSIC (Original Song)
SPECIAL ACHIEVEMENT AWARD (Sound Effects)
ACTOR IN A LEADING ROLE
ACTRESS IN A LEADING ROLE
MUSIC (Original Song Score and Its Adaptation or Adaptation Score)
WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)
VISUAL EFFECTS
SPECIAL ACHIEVEMENT AWARD
SPECIAL ACHIEVEMENT AWARD (Sound Effects Editing)
MUSIC (Adaptation Score)
WRITING (Screenplay Based on Material from Another Medium)
WRITING (Screenplay Written Directly for the Screen)
MUSIC (Original Song Score and Its Adaptation -or- Adaptation Score)
SPECIAL ACHIEVEMENT AWARD (Sound Editing)
SHORT FILM (Dramatic Live Action)
MAKEUP
SOUND EFFECTS EDITING
MUSIC (Original Song Score or Adaptation Score)
WRITING (Screenplay Based on Material Previously Produced or Published)
MUSIC (Original Musical or Comedy Score)
SOUND EDITING
ANIMATED FEATURE FILM
WRITING (Adapted Screenplay)
SOUND MIXING
MAKEUP AND HAIRSTYLING
PRODUCTION DESIGN
INTERNATIONAL FEATURE FILM
DOCUMENTARY FEATURE FILM
DOCUMENTARY SHORT FILM
GORDON E. SAWYER AWARD
AWARD OF COMMENDATION
```

```sql
SELECT DISTINCT categoria FROM oscar_indicados;
```

**1.2.2** **Quantas** categorias únicas existem?

R: 115 registros

```sql
SELECT COUNT(DISTINCT categoria) FROM oscar_indicados;
```

**1.3** Qual foi o primeiro ano de cerimônia do Oscar registrado na base?

R: 1928

```sql
SELECT ano_cerimonia 
FROM indicados_ao_oscar 
ORDER BY edicao_cerimonia ASC 
LIMIT 1;
```

**1.4** Qual foi o último ano de cerimônia registrado na base?

R: 2024

```sql
SELECT ano_cerimonia 
FROM indicados_ao_oscar 
ORDER BY edicao_cerimonia DESC
LIMIT 1;
```

**1.5** Quantas cerimônias do Oscar estão registradas no total?

R: 10889

```sql
SELECT COUNT(edicao_cerimonia)  
FROM indicados_ao_oscar;
```

**1.6** Atualize os registros da tabela com os dados do Oscar 2025 e 2026 (pesquise os vencedores e adicione-os).

```sql
-- ========================================================
-- OSCAR 2025 (97ª Edição) - DADOS REAIS
-- ========================================================

-- BEST PICTURE
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2024,2025,97,'BEST PICTURE','Anora','Anora',true),
(2024,2025,97,'BEST PICTURE','The Substance','The Substance',false),
(2024,2025,97,'BEST PICTURE','The Brutalist','The Brutalist',false),
(2024,2025,97,'BEST PICTURE','Conclave','Conclave',false),
(2024,2025,97,'BEST PICTURE','Dune: Part Two','Dune: Part Two',false),
(2024,2025,97,'BEST PICTURE','Emilia Pérez','Emilia Pérez',false),
(2024,2025,97,'BEST PICTURE','A Complete Unknown','A Complete Unknown',false),
(2024,2025,97,'BEST PICTURE','Nickel Boys','Nickel Boys',false),
(2024,2025,97,'BEST PICTURE','Sing Sing','Sing Sing',false),
(2024,2025,97,'BEST PICTURE','Wicked','Wicked',false);

-- DIRECTING
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2024,2025,97,'DIRECTING','Sean Baker','Anora',true),
(2024,2025,97,'DIRECTING','Brady Corbet','The Brutalist',false),
(2024,2025,97,'DIRECTING','Coralie Fargeat','The Substance',false),
(2024,2025,97,'DIRECTING','Jacques Audiard','Emilia Pérez',false),
(2024,2025,97,'DIRECTING','James Mangold','A Complete Unknown',false);

-- ACTOR
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2024,2025,97,'ACTOR','Adrien Brody','The Brutalist',true),
(2024,2025,97,'ACTOR','Timothée Chalamet','A Complete Unknown',false),
(2024,2025,97,'ACTOR','Colman Domingo','Sing Sing',false),
(2024,2025,97,'ACTOR','Ralph Fiennes','Conclave',false),
(2024,2025,97,'ACTOR','Sebastian Stan','The Apprentice',false);

-- ACTRESS
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2024,2025,97,'ACTRESS','Mikey Madison','Anora',true),
(2024,2025,97,'ACTRESS','Fernanda Torres','I\'m Still Here',false),
(2024,2025,97,'ACTRESS','Cynthia Erivo','Wicked',false),
(2024,2025,97,'ACTRESS','Demi Moore','The Substance',false),
(2024,2025,97,'ACTRESS','Karla Sofía Gascón','Emilia Pérez',false);

-- INTERNATIONAL FEATURE FILM
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2024,2025,97,'INTERNATIONAL FEATURE FILM','I\'m Still Here','I\'m Still Here',true),
(2024,2025,97,'INTERNATIONAL FEATURE FILM','The Girl with the Needle','The Girl with the Needle',false),
(2024,2025,97,'INTERNATIONAL FEATURE FILM','The Seed of the Sacred Fig','The Seed of the Sacred Fig',false),
(2024,2025,97,'INTERNATIONAL FEATURE FILM','Emilia Pérez','Emilia Pérez',false),
(2024,2025,97,'INTERNATIONAL FEATURE FILM','Flow','Flow',false);

-- ANIMATED FEATURE FILM
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2024,2025,97,'ANIMATED FEATURE FILM','Flow','Flow',true),
(2024,2025,97,'ANIMATED FEATURE FILM','Inside Out 2','Inside Out 2',false),
(2024,2025,97,'ANIMATED FEATURE FILM','Memoir of a Snail','Memoir of a Snail',false),
(2024,2025,97,'ANIMATED FEATURE FILM','The Wild Robot','The Wild Robot',false),
(2024,2025,97,'ANIMATED FEATURE FILM','Wallace & Gromit: Vengeance Most Fowl','Wallace & Gromit: Vengeance Most Fowl',false);


-- ========================================================
-- OSCAR 2026 (98ª Edição) - DADOS REAIS
-- ========================================================

-- BEST PICTURE
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2025,2026,98,'BEST PICTURE','Sinners','Sinners',false),
(2025,2026,98,'BEST PICTURE','One Battle After Another','One Battle After Another',false),
(2025,2026,98,'BEST PICTURE','Frankenstein','Frankenstein',false),
(2025,2026,98,'BEST PICTURE','Marty Supreme','Marty Supreme',false),
(2025,2026,98,'BEST PICTURE','Sentimental Value','Sentimental Value',false),
(2025,2026,98,'BEST PICTURE','Hamnet','Hamnet',false),
(2025,2026,98,'BEST PICTURE','Bugonia','Bugonia',false),
(2025,2026,98,'BEST PICTURE','F1','F1',false),
(2025,2026,98,'BEST PICTURE','The Secret Agent','The Secret Agent',false),
(2025,2026,98,'BEST PICTURE','Train Dreams','Train Dreams',false);

-- DIRECTING
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2025,2026,98,'DIRECTING','Chloé Zhao','Hamnet',false),
(2025,2026,98,'DIRECTING','Josh Safdie','Marty Supreme',false),
(2025,2026,98,'DIRECTING','Paul Thomas Anderson','One Battle After Another',false),
(2025,2026,98,'DIRECTING','Joachim Trier','Sentimental Value',false),
(2025,2026,98,'DIRECTING','Ryan Coogler','Sinners',false);

-- ACTOR
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2025,2026,98,'ACTOR','Timothée Chalamet','Marty Supreme',false),
(2025,2026,98,'ACTOR','Leonardo DiCaprio','One Battle After Another',false),
(2025,2026,98,'ACTOR','Ethan Hawke','Blue Moon',false),
(2025,2026,98,'ACTOR','Michael B. Jordan','Sinners',false),
(2025,2026,98,'ACTOR','Wagner Moura','The Secret Agent',false);

-- ACTRESS
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2025,2026,98,'ACTRESS','Jessie Buckley','Hamnet',false),
(2025,2026,98,'ACTRESS','Rose Byrne','If I Had Legs I\'d Kick You',false),
(2025,2026,98,'ACTRESS','Kate Hudson','Song Sung Blue',false),
(2025,2026,98,'ACTRESS','Renate Reinsve','Sentimental Value',false),
(2025,2026,98,'ACTRESS','Emma Stone','Bugonia',false);

-- INTERNATIONAL FEATURE FILM
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2025,2026,98,'INTERNATIONAL FEATURE FILM','The Secret Agent','The Secret Agent',false),
(2025,2026,98,'INTERNATIONAL FEATURE FILM','It Was Just an Accident','It Was Just an Accident',false),
(2025,2026,98,'INTERNATIONAL FEATURE FILM','Sentimental Value','Sentimental Value',false),
(2025,2026,98,'INTERNATIONAL FEATURE FILM','Sirât','Sirât',false),
(2025,2026,98,'INTERNATIONAL FEATURE FILM','The Voice of Hind Rajab','The Voice of Hind Rajab',false);

-- ANIMATED FEATURE FILM
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,edicao_cerimonia,categoria,nome_indicado,nome_filme,vencedor) VALUES 
(2025,2026,98,'ANIMATED FEATURE FILM','K-Pop: Demon Hunters','K-Pop: Demon Hunters',false),
(2025,2026,98,'ANIMATED FEATURE FILM','Zootopia 2','Zootopia 2',false),
(2025,2026,98,'ANIMATED FEATURE FILM','Arco','Arco',false),
(2025,2026,98,'ANIMATED FEATURE FILM','Elio','Elio',false),
(2025,2026,98,'ANIMATED FEATURE FILM','Little Amélie','Little Amélie',false);
```

## Nível 2: Explorando Categorias

**2.1** Quantas indicações existem para cada categoria? Agrupe por categoria e ordene da mais frequente para a menos frequente.

R:
```
CATEGORIA  / QUANTIDADE DE INDICAÇÕES
DIRECTING	469
FILM EDITING	450
ACTOR IN A SUPPORTING ROLE	450
ACTRESS IN A SUPPORTING ROLE	450
DOCUMENTARY (Short Subject)	378
BEST PICTURE	371
DOCUMENTARY (Feature)	345
CINEMATOGRAPHY	338
FOREIGN LANGUAGE FILM	315
ART DIRECTION	307
COSTUME DESIGN	295
MUSIC (Original Score)	270
ACTRESS	246
SOUND	245
ACTOR	242
ACTOR IN A LEADING ROLE	240
ACTRESS IN A LEADING ROLE	240
MUSIC (Original Song)	235
SHORT FILM (Live Action)	226
SHORT FILM (Animated)	215
MUSIC (Song)	215
SOUND RECORDING	195
SHORT SUBJECT (Cartoon)	169
CINEMATOGRAPHY (Black-and-White)	161
WRITING (Original Screenplay)	160
VISUAL EFFECTS	155
MUSIC (Music Score of a Dramatic or Comedy Picture)	148
ART DIRECTION (Black-and-White)	138
CINEMATOGRAPHY (Color)	135
HONORARY AWARD	133
MUSIC (Scoring of a Musical Picture)	127
WRITING (Screenplay Written Directly for the Screen)	120
ART DIRECTION (Color)	112
WRITING (Adapted Screenplay)	110
WRITING (Screenplay)	104
OUTSTANDING PRODUCTION	102
ANIMATED FEATURE FILM	99
WRITING (Screenplay--based on material from another medium)	95
SPECIAL EFFECTS	93
SHORT SUBJECT (One-reel)	90
BEST MOTION PICTURE	90
MAKEUP	87
SOUND EDITING	86
SOUND MIXING	85
SHORT SUBJECT (Two-reel)	81
COSTUME DESIGN (Black-and-White)	77
COSTUME DESIGN (Color)	77
SHORT SUBJECT (Live Action)	68
WRITING (Screenplay Based on Material from Another Medium)	65
MUSIC (Scoring)	64
PRODUCTION DESIGN	60
WRITING (Story and Screenplay--written directly for the screen)	60
SPECIAL AWARD	56
WRITING (Screenplay Based on Material Previously Produced or Published)	55
WRITING (Original Story)	52
WRITING (Motion Picture Story)	50
SOUND EFFECTS EDITING	47
MAKEUP AND HAIRSTYLING	46
IRVING G. THALBERG MEMORIAL AWARD	45
JEAN HERSHOLT HUMANITARIAN AWARD	44
MUSIC (Original Dramatic Score)	41
WRITING (Story and Screenplay)	35
ASSISTANT DIRECTOR	35
MUSIC (Scoring of Music--adaptation or treatment)	30
OUTSTANDING MOTION PICTURE	30
MUSIC (Song--Original for the Picture)	25
DOCUMENTARY	25
WRITING (Original Motion Picture Story)	25
INTERNATIONAL FEATURE FILM	25
DANCE DIRECTION	21
MUSIC (Original Musical or Comedy Score)	20
MUSIC (Music Score of a Dramatic Picture)	20
WRITING (Story and Screenplay--based on factual material or material not previously published or produced)	20
MUSIC (Music Score--substantially original)	20
WRITING (Adaptation)	17
SPECIAL VISUAL EFFECTS	16
SHORT SUBJECT (Comedy)	13
SHORT SUBJECT (Novelty)	12
WRITING	11
SOUND EFFECTS	10
WRITING (Screenplay Adapted from Other Material)	10
MUSIC (Original Music Score)	10
MUSIC (Original Score--for a motion picture [not a musical])	10
MUSIC (Score of a Musical Picture--original or adaptation)	10
WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)	10
DOCUMENTARY FEATURE FILM	10
DOCUMENTARY SHORT FILM	10
SHORT SUBJECT (Animated)	9
SPECIAL ACHIEVEMENT AWARD (Visual Effects)	9
MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)	9
OUTSTANDING PICTURE	8
MUSIC (Original Song Score)	8
MUSIC (Scoring: Adaptation and Original Song Score)	8
MUSIC (Original Song Score and Its Adaptation or Adaptation Score)	6
SHORT SUBJECT (Color)	6
MUSIC (Original Song Score and Its Adaptation -or- Adaptation Score)	6
HONORARY FOREIGN LANGUAGE FILM AWARD	5
WRITING (Screenplay--Adapted)	5
WRITING (Screenplay--Original)	5
WRITING (Story and Screenplay--based on material not previously published or produced)	5
SPECIAL ACHIEVEMENT AWARD (Sound Effects Editing)	4
SHORT FILM (Dramatic Live Action)	3
DIRECTING (Dramatic Picture)	3
MUSIC (Original Song Score or Adaptation Score)	3
ENGINEERING EFFECTS	3
UNIQUE AND ARTISTIC PICTURE	3
WRITING (Title Writing)	3
SPECIAL ACHIEVEMENT AWARD	3
MUSIC (Adaptation Score)	3
SPECIAL FOREIGN LANGUAGE FILM AWARD	2
DIRECTING (Comedy Picture)	2
SPECIAL ACHIEVEMENT AWARD (Sound Editing)	1
GORDON E. SAWYER AWARD	1
AWARD OF COMMENDATION	1
SPECIAL ACHIEVEMENT AWARD (Sound Effects)	1
```

```sql
SELECT categoria, COUNT(categoria) 
FROM indicados_ao_oscar
GROUP BY categoria
ORDER BY count(categoria) DESC;
```

**2.2** Qual categoria teve mais indicações ao longo da história do Oscar?

R: DIRECTING com 469 indicacões

```sql
SELECT categoria, COUNT(categoria) 
FROM indicados_ao_oscar
GROUP BY categoria
ORDER BY count(categoria) DESC
LIMIT 1;
```

**2.3** Qual categoria teve menos indicações ao longo da história?

R: SPECIAL ACHIEVEMENT AWARD (Sound Editing)
GORDON E. SAWYER AWARD
AWARD OF COMMENDATION
SPECIAL ACHIEVEMENT AWARD (Sound Effects) 
todos com 1 indicação

```sql
SELECT categoria, COUNT(categoria) 
FROM indicados_ao_oscar
GROUP BY categoria
ORDER BY count(categoria) 
LIMIT 1;
```

**2.4** A partir de que ano a categoria "ACTRESS" deixou de existir? (Dica: procure a última cerimônia com essa categoria)

R: Essa categoria não deixou de existir no Oscar.

```sql
select max(ano_cerimonia) from indicados_ao_oscar where categoria = 'actress';
```

**2.5** Quais categorias existiam na primeira cerimônia (1928) e não existem mais hoje?

R:
```
ART DIRECTION
CINEMATOGRAPHY
DIRECTING (Comedy Picture)
DIRECTING (Dramatic Picture)
ENGINEERING EFFECTS
OUTSTANDING PICTURE
UNIQUE AND ARTISTIC PICTURE
WRITING (Adaptation)
WRITING (Original Story)
WRITING (Title Writing)
SPECIAL AWARD
```

```sql

SELECT DISTINCT categoria 
FROM indicados_ao_oscar
WHERE ano_cerimonia = 1928
  AND categoria NOT IN (
      SELECT DISTINCT categoria 
      FROM indicados_ao_oscar 
      WHERE ano_cerimonia = 2026 
  );

```

**2.6** Liste todas as categorias que contêm a palavra "DIRECTING" no nome.

R:
```
DIRECTING (Comedy Picture)
DIRECTING (Dramatic Picture)
DIRECTING
```

```sql
select distinct categoria 
from indicados_ao_oscar
where categoria like '%DIRECTING%';
```

---

## Nível 3: Atores e Atrizes Famosos

### Natalie Portman

**3.1** Quantas vezes Natalie Portman foi indicada ao Oscar?

R: 3

```sql
SELECT COUNT(*) FROM indicados_ao_oscar
WHERE nome_indicado LIKE "%Natalie Portman%";
```

**3.2** Quantos Oscars Natalie Portman ganhou?

R: 1 vez

```sql
SELECT COUNT(*) FROM indicados_ao_oscar
WHERE nome_indicado LIKE "%Natalie Portman%" 
and vencedor = true;
```

**3.3** Em quais anos e por quais filmes Natalie Portman foi indicada?

R:
```
Ano / Filme
2005	Closer
2011	Black Swan
2017	Jackie
```

```sql
SELECT ano_cerimonia, nome_filme 
FROM indicados_ao_oscar
WHERE nome_indicado LIKE "%Natalie Portman%";
```

**3.4** Liste todas as indicações de Natalie Portman mostrando: ano, categoria, filme e se venceu.

R:
```
Ano  /         Categoria           / Filme      / Venceu?
2005	ACTRESS IN A SUPPORTING ROLE	Closer	     Não Venceu
2011	ACTRESS IN A LEADING ROLE	   Black Swan	  Venceu
2017	ACTRESS IN A LEADING ROLE	   Jackie	     Não Venceu
```

```sql
SELECT ano_cerimonia, categoria, nome_filme, 
if(vencedor = true, 'Venceu', 'Não Venceu') as vencendor
FROM indicados_ao_oscar
WHERE nome_indicado LIKE "%Natalie Portman%";
```

### Viola Davis

**3.5** Quantas vezes Viola Davis foi indicada ao Oscar?

R: 4

```sql
SELECT COUNT(*) FROM indicados_ao_oscar
WHERE nome_indicado LIKE "%Viola Davis%"
```

**3.6** Quantos Oscars Viola Davis ganhou?

R: 1

```sql
SELECT COUNT(*) FROM indicados_ao_oscar
WHERE nome_indicado LIKE "%Viola Davis%"
AND 
vencedor = true;
```

**3.7** Por quais filmes Viola Davis foi indicada?

R:
```
Filmes
Doubt
The Help
Fences
Ma Rainey's Black Bottom
```
```sql
select nome_filme
from indicados_ao_oscar
where nome_indicado = "Viola Davis";
```

### Amy Adams

**3.8** Amy Adams já ganhou algum Oscar?

R: Não ganhou

```sql
select count(*) from indicados_ao_oscar
where nome_indicado  
like "%Amy Adams%" and vencedor = true;
```

**3.9** Quantas vezes Amy Adams foi indicada sem ganhar?

R: 6 Vezes

```sql
select count(*) from indicados_ao_oscar
where nome_indicado  
like "%Amy Adams%"; 
```

### Denzel Washington

**3.10** Denzel Washington já ganhou algum Oscar?

R: Ganhou 2 vezes

```sql
select count(*) from indicados_ao_oscar
where nome_indicado like "%Denzel Washington%"
and vencedor = true;
```

**3.11** Quantas vezes Denzel Washington foi indicado ao Oscar?

R: Foi indicado 10 vezes.

```sql
select count(*) from indicados_ao_oscar
where nome_indicado like "%Denzel Washington%";
```

**3.12** Liste todos os Oscars que Denzel Washington ganhou (ano, categoria, filme).

R:
```
 Ano /     Categoria            /  Nome Filme 
1990	ACTOR IN A SUPPORTING ROLE	   Glory
2002	ACTOR IN A LEADING ROLE	   Training Day
```

```sql
select ano_cerimonia, categoria, nome_filme 
from indicados_ao_oscar
where nome_indicado like "%Denzel Washington%"
and vencedor = true; 
```

---

## Nível 4: Vencedores Históricos

**4.1** Quem ganhou o primeiro Oscar para Melhor Atriz (ACTRESS)? Em que ano e por qual filme?

R:
```
Nome          Ano     Filme
Janet Gaynor	1928	7th Heaven
```

```sql
select  nome_indicado, ano_cerimonia, nome_filme
from indicados_ao_oscar
where vencedor = true and categoria = 'ACTRESS'
and ano_cerimonia in (
select min(ano_cerimonia) as menor_ano
from indicados_ao_oscar); 
```

**4.2** Quem ganhou o primeiro Oscar para Melhor Ator (ACTOR)? Em que ano e por qual filme?

R:
```
Nome          Ano     Filme
Emil Jannings	1928	The Last Command
```

```sql
select  nome_indicado, ano_cerimonia, nome_filme
from indicados_ao_oscar
where vencedor = true and categoria = 'ACTOR'
and ano_cerimonia in (
select min(ano_cerimonia) as menor_ano
from indicados_ao_oscar); 
```

**4.3** Quantos vencedores existem ao todo na base de dados?

R: 2477

```sql
select  count(vencedor)
from indicados_ao_oscar
where vencedor = true;
```

**4.4** Liste todos os filmes que ganharam o Oscar de Melhor Filme (categoria "OUTSTANDING PICTURE" ou "BEST PICTURE").

R:
```
Wings
The Broadway Melody
Lawrence of Arabia
Tom Jones
My Fair Lady
The Sound of Music
A Man for All Seasons
In the Heat of the Night
Oliver!
Midnight Cowboy
Patton
The French Connection
The Godfather
The Sting
The Godfather Part II
One Flew over the Cuckoo's Nest
Rocky
Annie Hall
The Deer Hunter
Kramer vs. Kramer
Ordinary People
Chariots of Fire
Gandhi
Terms of Endearment
Amadeus
Out of Africa
Platoon
The Last Emperor
Rain Man
Driving Miss Daisy
Dances With Wolves
The Silence of the Lambs
Unforgiven
Schindler's List
Forrest Gump
Braveheart
The English Patient
Titanic
Shakespeare in Love
American Beauty
Gladiator
A Beautiful Mind
Chicago
The Lord of the Rings: The Return of the King
Million Dollar Baby
Crash
The Departed
No Country for Old Men
Slumdog Millionaire
The Hurt Locker
The King's Speech
The Artist
Argo
12 Years a Slave
Birdman or (The Unexpected Virtue of Ignorance)
Spotlight
Moonlight
The Shape of Water
Green Book
Parasite
Nomadland
CODA
Everything Everywhere All at Once
Oppenheimer
Anora
```

```sql
select  nome_filme
from indicados_ao_oscar
where vencedor = true and categoria in(
select categoria
from indicados_ao_oscar
where categoria = "OUTSTANDING PICTURE" 
or categoria = "BEST PICTURE");
```

**4.5** Quantos filmes diferentes já ganharam o Oscar?

R:65 filmes

```sql
select count(nome_filme)
from indicados_ao_oscar
where vencedor = true and categoria in(
select categoria
from indicados_ao_oscar
where categoria = "OUTSTANDING PICTURE" 
or categoria = "BEST PICTURE");
```

---

## Nível 5: Análise de Indicações

**5.1** Quais atores/atrizes foram indicados mais de uma vez? Liste o nome e o número de indicações.

R:
```
Nome indicado / Numero de Indicações
Meryl Streep	21
Katharine Hepburn	12
Jack Nicholson	12
Bette Davis	11
Spencer Tracy	9
Laurence Olivier	9
Paul Newman	9
Al Pacino	9
Denzel Washington	9
Marlon Brando	8
Geraldine Page	8
Jack Lemmon	8
Peter O'Toole	8
Robert De Niro	8
Glenn Close	8
Judi Dench	8
Cate Blanchett	8
Greer Garson	7
Ingrid Bergman	7
Richard Burton	7
Dustin Hoffman	7
Jane Fonda	7
Jeff Bridges	7
Robert Duvall	7
Leonardo DiCaprio	7
Kate Winslet	7
Paul Muni	6
Norma Shearer	6
Deborah Kerr	6
Thelma Ritter	6
Maggie Smith	6
Michael Caine	6
Vanessa Redgrave	6
Ellen Burstyn	6
Sissy Spacek	6
Jessica Lange	6
Tom Hanks	6
Frances McDormand	6
Anthony Hopkins	6
Amy Adams	6
Fredric March	5
Irene Dunne	5
Gary Cooper	5
James Stewart	5
Olivia de Havilland	5
Jennifer Jones	5
Gregory Peck	5
Susan Hayward	5
Arthur Kennedy	5
Audrey Hepburn	5
Elizabeth Taylor	5
Shirley MacLaine	5
Anne Bancroft	5
Albert Finney	5
Gene Hackman	5
Jodie Foster	5
Susan Sarandon	5
Morgan Freeman	5
Annette Bening	5
Daniel Day-Lewis	5
Sean Penn	5
Julianne Moore	5
Nicole Kidman	5
Michelle Williams	5
Bradley Cooper	5
Emma Stone	5
Walter Huston	4
Walter Brennan	4
Charles Boyer	4
Barbara Stanwyck	4
Mickey Rooney	4
Claude Rains	4
Rosalind Russell	4
Agnes Moorehead	4
Ethel Barrymore	4
Jane Wyman	4
Montgomery Clift	4
Shelley Winters	4
Lee Grant	4
Alec Guinness	4
Anthony Quinn	4
Burt Lancaster	4
Joanne Woodward	4
Maureen Stapleton	4
George C. Scott	4
Julie Christie	4
Alan Arkin	4
Warren Beatty	4
Jon Voight	4
Jane Alexander	4
Glenda Jackson	4
Marsha Mason	4
Diane Keaton	4
Ben Kingsley	4
William Hurt	4
Willem Dafoe	4
Robin Williams	4
Holly Hunter	4
Julia Roberts	4
Kathy Bates	4
Tommy Lee Jones	4
Emma Thompson	4
Helen Mirren	4
Ed Harris	4
Brad Pitt	4
Geoffrey Rush	4
Javier Bardem	4
Joaquin Phoenix	4
Renée Zellweger	4
Philip Seymour Hoffman	4
George Clooney	4
Penélope Cruz	4
Saoirse Ronan	4
Viola Davis	4
Christian Bale	4
Mark Ruffalo	4
Jennifer Lawrence	4
Gloria Swanson	3
Ronald Colman	3
Greta Garbo	3
Charles Laughton	3
Clark Gable	3
William Powell	3
Claudette Colbert	3
Claire Trevor	3
James Cagney	3
Fay Bainter	3
Wendy Hiller	3
Joan Fontaine	3
Charles Coburn	3
Teresa Wright	3
Gladys Cooper	3
Humphrey Bogart	3
Charles Bickford	3
Anne Revere	3
Bing Crosby	3
Clifton Webb	3
Angela Lansbury	3
Joan Crawford	3
Celeste Holm	3
José Ferrer	3
Kirk Douglas	3
William Holden	3
Eleanor Parker	3
Peter Ustinov	3
Gig Young	3
Jack Palance	3
James Mason	3
Rod Steiger	3
Natalie Wood	3
Maximilian Schell	3
Piper Laurie	3
Marcello Mastroianni	3
Melvyn Douglas	3
Dame Edith Evans	3
Julie Andrews	3
Walter Matthau	3
Faye Dunaway	3
Diane Ladd	3
Jason Robards	3
Sally Field	3
Joe Pesci	3
Debra Winger	3
Anjelica Huston	3
Sigourney Weaver	3
Dianne Wiest	3
Martin Landau	3
Michelle Pfeiffer	3
Tom Cruise	3
Nick Nolte	3
Laura Dern	3
Robert Downey Jr.	3
Marisa Tomei	3
Ralph Fiennes	3
Joan Allen	3
Woody Harrelson	3
Edward Norton	3
Matt Damon	3
Russell Crowe	3
Laura Linney	3
Will Smith	3
Ethan Hawke	3
Johnny Depp	3
Charlize Theron	3
Natalie Portman	3
Ryan Gosling	3
Viggo Mortensen	3
Christopher Plummer	3
Carey Mulligan	3
Gary Oldman	3
Jessica Chastain	3
Octavia Spencer	3
Timothée Chalamet	3
Olivia Colman	3
Janet Gaynor	2
Ruth Chatterton	2
George Arliss	2
Wallace Beery	2
Marie Dressler	2
Helen Hayes	2
Leslie Howard	2
Frank Morgan	2
Victor McLaglen	2
Basil Rathbone	2
Akim Tamiroff	2
Luise Rainer	2
Beulah Bondi	2
Alice Brady	2
Maria Ouspenskaya	2
Gale Sondergaard	2
Robert Montgomery	2
Thomas Mitchell	2
Dame May Whitty	2
Robert Donat	2
John Garfield	2
Vivien Leigh	2
Henry Fonda	2
Marjorie Rambeau	2
Cary Grant	2
Walter Pidgeon	2
Monty Woolley	2
J. Carrol Naish	2
Barry Fitzgerald	2
Anne Baxter	2
Edmund Gwenn	2
Loretta Young	2
Gloria Grahame	2
Cecil Kellaway	2
Jean Simmons	2
John Wayne	2
Ralph Richardson	2
James Whitmore	2
Elsa Lanchester	2
Mercedes McCambridge	2
Karl Malden	2
Mildred Dunnock	2
Eddie Albert	2
Frank Sinatra	2
Leslie Caron	2
Grace Kelly	2
Lee J. Cobb	2
Edmond O'Brien	2
Judy Garland	2
James Dean	2
Sal Mineo	2
Arthur O'Connell	2
Anna Magnani	2
Eileen Heckart	2
Sidney Poitier	2
Hugh Griffith	2
Simone Signoret	2
Peter Falk	2
Shirley Knight	2
Sophia Loren	2
Richard Harris	2
Rex Harrison	2
Patricia Neal	2
Joyce Redman	2
Peter Sellers	2
John Gielgud	2
Kim Stanley	2
Tom Courtenay	2
Ruth Gordon	2
Paul Scofield	2
Lynn Redgrave	2
Estelle Parsons	2
Barbra Streisand	2
Liza Minnelli	2
Dyan Cannon	2
Goldie Hawn	2
Sylvia Miles	2
Peter Finch	2
Roy Scheider	2
Ann-Margret	2
Liv Ullmann	2
Vincent Gardenia	2
Madeline Kahn	2
Gena Rowlands	2
Talia Shire	2
Burgess Meredith	2
Jack Warden	2
Isabelle Adjani	2
Sylvester Stallone	2
Richard Dreyfuss	2
John Travolta	2
Melinda Dillon	2
Bruce Dern	2
Richard Farnsworth	2
John Hurt	2
Christopher Walken	2
Jill Clayburgh	2
Bette Midler	2
Judd Hirsch	2
Charles Durning	2
John Lithgow	2
Julie Walters	2
Cher	2
John Malkovich	2
Judy Davis	2
Whoopi Goldberg	2
James Woods	2
Max von Sydow	2
Joan Cusack	2
Geena Davis	2
Kenneth Branagh	2
Jessica Tandy	2
Mary McDonnell	2
Clint Eastwood	2
Miranda Richardson	2
Angela Bassett	2
Winona Ryder	2
Nicolas Cage	2
Kevin Spacey	2
Billy Bob Thornton	2
Brenda Blethyn	2
Emily Watson	2
Juliette Binoche	2
Helena Bonham Carter	2
Helen Hunt	2
Ian McKellen	2
Jude Law	2
Janet McTeer	2
Hilary Swank	2
Angelina Jolie	2
Catherine Keener	2
Samantha Morton	2
Benicio Del Toro	2
Marcia Gay Harden	2
Kate Hudson	2
Tom Wilkinson	2
Adrien Brody	2
Djimon Hounsou	2
Naomi Watts	2
Jamie Foxx	2
Heath Ledger	2
Paul Giamatti	2
Keira Knightley	2
Reese Witherspoon	2
Rachel Weisz	2
Casey Affleck	2
Marion Cotillard	2
Richard Jenkins	2
Michael Shannon	2
Anne Hathaway	2
Melissa Leo	2
Colin Firth	2
Jeremy Renner	2
Christoph Waltz	2
Sandra Bullock	2
Jacki Weaver	2
Jonah Hill	2
Rooney Mara	2
Melissa McCarthy	2
Michael Fassbender	2
Sally Hawkins	2
Benedict Cumberbatch	2
Eddie Redmayne	2
J.K. Simmons	2
Andrew Garfield	2
Mahershala Ali	2
Daniel Kaluuya	2
Sam Rockwell	2
Margot Robbie	2
Adam Driver	2
Cynthia Erivo	2
Scarlett Johansson	2
Jessie Buckley	2
Colman Domingo	2
```

```sql
select nome_indicado, COUNT(*) as numero_de_indicações
from indicados_ao_oscar
where categoria like '%actor%' or categoria like '%actress%'
group by nome_indicado
having COUNT(*) > 1
order by numero_de_indicações desc;
```

**5.2** Qual ator ou atriz tem o maior número de indicações na história do Oscar?

R: A Meryl Streep	com 21 indicações.

```sql
select nome_indicado, COUNT(*) as numero_de_indicações
from indicados_ao_oscar
where categoria like '%actor%' or categoria like '%actress%'
group by nome_indicado
having COUNT(*) > 1
order by numero_de_indicações desc
limit 1;
```

**5.3** Quais atores foram indicados mais de 3 vezes, mas nunca ganharam?

R:
```
Nome indicado / Numero de Indicações
Peter O'Toole	8
Glenn Close	8
Richard Burton	7
Deborah Kerr	6
Thelma Ritter	6
Amy Adams	6
Irene Dunne	5
Arthur Kennedy	5
Albert Finney	5
Annette Bening	5
Michelle Williams	5
Bradley Cooper	5
Charles Boyer	4
Barbara Stanwyck	4
Mickey Rooney	4
Claude Rains	4
Rosalind Russell	4
Agnes Moorehead	4
Montgomery Clift	4
Warren Beatty	4
Jane Alexander	4
Marsha Mason	4
Willem Dafoe	4
Ed Harris	4
Saoirse Ronan	4
Mark Ruffalo	4
```

```sql
select nome_indicado, COUNT(*) as numero_de_indicações
from indicados_ao_oscar
where (categoria like '%actor%' or categoria like '%actress%')
and nome_indicado not in(
select nome_indicado
from indicados_ao_oscar
where (categoria like '%actor%' or categoria like '%actress%')
and vencedor = true)
group by nome_indicado
having COUNT(*) > 3
order by numero_de_indicações desc;
```

**5.4** Encontre todos os artistas que foram indicados em categorias diferentes (ex: ator e diretor).

R:
```
nome indicado /  quantidades      /   categorias
Metro-Goldwyn-Mayer	11	BEST MOTION PICTURE, DOCUMENTARY (Short Subject), OUTSTANDING MOTION PICTURE, OUTSTANDING PICTURE, OUTSTANDING PRODUCTION, SHORT SUBJECT (Cartoon), SHORT SUBJECT (Novelty), SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel), SPECIAL EFFECTS, UNIQUE AND A...
Warner Bros.	10	BEST MOTION PICTURE, DOCUMENTARY (Short Subject), OUTSTANDING MOTION PICTURE, OUTSTANDING PRODUCTION, SHORT SUBJECT (Cartoon), SHORT SUBJECT (Color), SHORT SUBJECT (Comedy), SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel), SPECIAL AWARD
Paramount	8	BEST MOTION PICTURE, DOCUMENTARY (Short Subject), OUTSTANDING MOTION PICTURE, OUTSTANDING PRODUCTION, SHORT SUBJECT (Cartoon), SHORT SUBJECT (Color), SHORT SUBJECT (One-reel), SPECIAL EFFECTS
Alex North	7	HONORARY AWARD, MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original), MUSIC (Original Dramatic Score), MUSIC (Original Music Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original...
RKO Radio	7	BEST MOTION PICTURE, DOCUMENTARY (Short Subject), OUTSTANDING MOTION PICTURE, OUTSTANDING PRODUCTION, SHORT SUBJECT (Comedy), SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel)
Alfred Newman	6	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Music Score--substantially original), MUSIC (Original Score), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Walt Disney, Producer	6	DOCUMENTARY, DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon), SHORT SUBJECT (Live Action), SHORT SUBJECT (Two-reel)
20th Century-Fox	5	BEST MOTION PICTURE, OUTSTANDING MOTION PICTURE, OUTSTANDING PRODUCTION, SHORT SUBJECT (Cartoon), SHORT SUBJECT (One-reel)
Elmer Bernstein	5	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original), MUSIC (Original Music Score), MUSIC (Original Score), MUSIC (Scoring of Music--adaptation or treatment)
Franz Waxman	5	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Music Score--substantially original), MUSIC (Original Score), MUSIC (Scoring)
Ingmar Bergman	5	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD, WRITING (Screenplay Written Directly for the Screen), WRITING (Story and Screenplay--based on factual material or material not previously published or produced), WRITING (Story and Screenplay--written directl...
Jerry Goldsmith	5	MUSIC (Music Score--substantially original), MUSIC (Original Dramatic Score), MUSIC (Original Music Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original Score)
John Williams	5	MUSIC (Original Dramatic Score), MUSIC (Original Musical or Comedy Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original Score), MUSIC (Scoring of Music--adaptation or treatment)
National Film Board of Canada	5	DOCUMENTARY, DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon), SHORT SUBJECT (Live Action), SHORT SUBJECT (One-reel)
Paul Newman	5	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE, HONORARY AWARD, JEAN HERSHOLT HUMANITARIAN AWARD
Robert Benton	5	DIRECTING, WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Based on Material Previously Produced or Published), WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previo...
Victor Young	5	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Carl Foreman	4	WRITING (Screenplay--based on material from another medium), WRITING (Screenplay), WRITING (Story and Screenplay--based on factual material or material not previously published or produced), WRITING (Story and Screenplay)
Columbia	4	BEST MOTION PICTURE, OUTSTANDING MOTION PICTURE, OUTSTANDING PRODUCTION, SHORT SUBJECT (Cartoon)
George Seaton	4	DIRECTING, JEAN HERSHOLT HUMANITARIAN AWARD, WRITING (Screenplay--based on material from another medium), WRITING (Screenplay)
Herbert Stothart	4	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Original Score), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
John Barry	4	MUSIC (Original Dramatic Score), MUSIC (Original Music Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original Score)
Kenneth Branagh	4	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE, DIRECTING, WRITING (Screenplay Based on Material Previously Produced or Published)
Lalo Schifrin	4	HONORARY AWARD, MUSIC (Original Music Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original Score)
Laurence Olivier	4	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE, DIRECTING
Max Steiner	4	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score), MUSIC (Scoring)
Neil Simon	4	WRITING (Screenplay Adapted from Other Material), WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced), WRITI...
Paddy Chayefsky	4	WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced), WRITING (Screenplay), WRITING (Story and Screenplay--based on factual material or material not previously published...
Piero Gherardi	4	ART DIRECTION (Black-and-White), ART DIRECTION (Color), COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Stanley Kubrick	4	DIRECTING, SPECIAL VISUAL EFFECTS, WRITING (Screenplay Adapted from Other Material), WRITING (Screenplay--based on material from another medium)
Warren Beatty	4	ACTOR, ACTOR IN A LEADING ROLE, DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
William Rose	4	WRITING (Screenplay--based on material from another medium), WRITING (Screenplay--Original), WRITING (Story and Screenplay--written directly for the screen), WRITING (Story and Screenplay)
Aaron Copland	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Original Score), MUSIC (Scoring)
Al Pacino	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Albert Finney	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Alec Guinness	3	ACTOR, ACTOR IN A SUPPORTING ROLE, WRITING (Screenplay--based on material from another medium)
Alfred Newman, Ken Darby	3	MUSIC (Music Score--substantially original), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
Andre Previn	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
Angelina Jolie	3	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE, JEAN HERSHOLT HUMANITARIAN AWARD
Anthony Collins	3	MUSIC (Original Score), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Ben Hecht	3	WRITING (Adaptation), WRITING (Original Screenplay), WRITING (Original Story)
Ben Sharpsteen, Producer	3	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Bernard Herrmann	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Bill Thomas	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Billy Bob Thornton	3	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE, WRITING (Screenplay Based on Material Previously Produced or Published)
British Ministry of Information	3	DOCUMENTARY, DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Cecil B. DeMille	3	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD, SPECIAL AWARD
Charles Chaplin	3	ACTOR, SPECIAL AWARD, WRITING (Original Screenplay)
Charles LeMaire, Mary Wills	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Clint Eastwood	3	ACTOR IN A LEADING ROLE, DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Conrad Hall	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Daniel L. Fapp	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Danny Elfman	3	MUSIC (Original Dramatic Score), MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
David Lean	3	DIRECTING, FILM EDITING, WRITING (Screenplay Based on Material from Another Medium)
Dimitri Tiomkin	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original), MUSIC (Scoring)
Dore Schary, Producer	3	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT SUBJECT (Two-reel)
Dorothy Jeakins	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Edgar Anstey, Producer	3	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Edith Head	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Edward Cronjager	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Edward Kay	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Scoring of a Musical Picture)
Ellen Burstyn	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Emma Stone	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Emma Thompson	3	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE, WRITING (Screenplay Based on Material Previously Produced or Published)
Ernest Gold	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original), MUSIC (Original Score--for a motion picture [not a musical])
Ernest Haller	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Ernest Laszlo	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Ernest Lehman	3	HONORARY AWARD, WRITING (Screenplay--based on material from another medium), WRITING (Story and Screenplay--written directly for the screen)
Fox	3	OUTSTANDING PICTURE, OUTSTANDING PRODUCTION, UNIQUE AND ARTISTIC PICTURE
Francis Ford Coppola	3	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD, WRITING (Original Screenplay)
Frank Sinatra	3	ACTOR, ACTOR IN A SUPPORTING ROLE, JEAN HERSHOLT HUMANITARIAN AWARD
Frank Skinner	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Frederic Ullman, Jr., Producer	3	DOCUMENTARY, DOCUMENTARY (Short Subject), SHORT SUBJECT (Two-reel)
Geena Davis	3	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE, JEAN HERSHOLT HUMANITARIAN AWARD
Gena Rowlands	3	ACTRESS, ACTRESS IN A LEADING ROLE, HONORARY AWARD
Gene Hackman	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
George Barnes	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
George Clooney	3	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE, DIRECTING
George Folsey	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
George Lucas	3	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD, WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)
George Stevens	3	DIRECTING, HONORARY AWARD, IRVING G. THALBERG MEMORIAL AWARD
Georges Delerue	3	MUSIC (Original Dramatic Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original Score)
Geraldine Page	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Gordon Hollingshead, Producer	3	DOCUMENTARY (Short Subject), SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel)
Hans Zimmer	3	MUSIC (Original Dramatic Score), MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
Harry Stradling	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Henry Fonda	3	ACTOR, ACTOR IN A LEADING ROLE, HONORARY AWARD
Henry Mancini	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original), MUSIC (Original Score)
Horton Foote	3	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Written Directly for the Screen), WRITING (Screenplay--based on material from another medium)
Ingrid Bergman	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Irene Sharaff	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Jack Cardiff	3	CINEMATOGRAPHY (Color), DIRECTING, HONORARY AWARD
Jack Lemmon	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jack Nicholson	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
James Carr, Producer	3	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
James L. Brooks	3	DIRECTING, WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Written Directly for the Screen)
James Wong Howe	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Jane Alexander	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Jane Fonda	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Jean Louis	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Jerry Fielding	3	MUSIC (Original Dramatic Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Original Score)
John Cassavetes	3	ACTOR IN A SUPPORTING ROLE, DIRECTING, WRITING (Story and Screenplay--written directly for the screen)
John Huston	3	ACTOR IN A SUPPORTING ROLE, DIRECTING, WRITING (Screenplay)
Jon Voight	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Joseph L. Mankiewicz	3	DIRECTING, WRITING (Screenplay), WRITING (Story and Screenplay)
Joseph Ruttenberg	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Joseph Walker	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Lamar Trotti	3	WRITING (Motion Picture Story), WRITING (Original Screenplay), WRITING (Original Story)
Larry Lansburgh, Producer	3	DOCUMENTARY (Feature), SHORT SUBJECT (Live Action), SHORT SUBJECT (Two-reel)
Leigh Harline	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
Leo McCarey	3	DIRECTING, WRITING (Motion Picture Story), WRITING (Original Motion Picture Story)
Leon Shamroy	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Leonardo DiCaprio	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Lina Wertmüller	3	DIRECTING, HONORARY AWARD, WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)
Louis Malle	3	DIRECTING, WRITING (Screenplay Written Directly for the Screen), WRITING (Story and Screenplay--based on factual material or material not previously published or produced)
Marshall Curry	3	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT FILM (Live Action)
Maurice Jarre	3	MUSIC (Music Score--substantially original), MUSIC (Original Score), MUSIC (Scoring of Music--adaptation or treatment)
Michael Caine	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Michel Legrand	3	MUSIC (Original Dramatic Score), MUSIC (Original Score--for a motion picture [not a musical]), MUSIC (Scoring of Music--adaptation or treatment)
Mickey Rooney	3	ACTOR, ACTOR IN A SUPPORTING ROLE, HONORARY AWARD
Miklos Rozsa	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Milton Krasner	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Music and Lyrics by Al Kasha and Joel Hirschhorn	3	MUSIC (Original Song), MUSIC (Song--Original for the Picture), MUSIC (Song)
Music and Lyrics by Richard M. Sherman and Robert B. Sherman	3	MUSIC (Original Song), MUSIC (Song--Original for the Picture), MUSIC (Song)
Music by Henry Mancini; Lyrics by Johnny Mercer	3	MUSIC (Original Song Score), MUSIC (Song--Original for the Picture), MUSIC (Song)
Music by Sammy Fain; Lyrics by Paul Francis Webster	3	MUSIC (Original Song), MUSIC (Song--Original for the Picture), MUSIC (Song)
Norman McLaren, Producer	3	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action), SHORT SUBJECT (One-reel)
Norman Panama, Melvin Frank	3	WRITING (Original Screenplay), WRITING (Story and Screenplay--written directly for the screen), WRITING (Story and Screenplay)
Oliver Stone	3	DIRECTING, WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Written Directly for the Screen)
Orry-Kelly	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Otto Lang, Producer	3	DOCUMENTARY (Short Subject), SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel)
Paramount Famous Lasky	3	OUTSTANDING PICTURE, OUTSTANDING PRODUCTION, UNIQUE AND ARTISTIC PICTURE
Pete Smith, Producer	3	SHORT SUBJECT (Color), SHORT SUBJECT (Novelty), SHORT SUBJECT (One-reel)
Quincy Jones	3	JEAN HERSHOLT HUMANITARIAN AWARD, MUSIC (Adaptation Score), MUSIC (Original Music Score)
Ralph Fiennes	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Randy Newman	3	MUSIC (Original Dramatic Score), MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
Richard Brooks	3	DIRECTING, WRITING (Screenplay--based on material from another medium), WRITING (Screenplay)
Richard Burton	3	ACTOR, ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Richard Hageman	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Robert Surtees	3	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Robert Wise	3	DIRECTING, FILM EDITING, IRVING G. THALBERG MEMORIAL AWARD
Samuel Goldwyn Productions	3	BEST MOTION PICTURE, OUTSTANDING MOTION PICTURE, OUTSTANDING PRODUCTION
Spike Lee	3	DIRECTING, HONORARY AWARD, WRITING (Screenplay Written Directly for the Screen)
Sylvester Stallone	3	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE, WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)
Tom Daly, Producer	3	DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon), SHORT SUBJECT (Live Action)
United States Army	3	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject), SHORT SUBJECT (Two-reel)
United States Army Air Force	3	DOCUMENTARY, DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
United States Navy	3	DOCUMENTARY, DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Vanessa Redgrave	3	ACTRESS, ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Walter Plunkett	3	COSTUME DESIGN, COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Werner Heymann	3	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Woody Allen	3	ACTOR IN A LEADING ROLE, DIRECTING, WRITING (Screenplay Written Directly for the Screen)
20th Century-Fox Studio Sound Department, Carl Faulkner, Sound Director	2	SOUND, SOUND RECORDING
Adam Driver	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Adaptation Score by Leonard Rosenman	2	MUSIC (Original Song Score and Its Adaptation or Adaptation Score), MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)
Adaptation score by Nelson Riddle	2	MUSIC (Score of a Musical Picture--original or adaptation), MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)
Adaptation Score by Ralph Burns	2	MUSIC (Original Song Score and Its Adaptation -or- Adaptation Score), MUSIC (Scoring: Adaptation and Original Song Score)
Adrien Brody	2	ACTOR, ACTOR IN A LEADING ROLE
Alan Arkin	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Alan J. Pakula	2	DIRECTING, WRITING (Screenplay Based on Material from Another Medium)
Alan Jay Lerner	2	WRITING (Screenplay--based on material from another medium), WRITING (Story and Screenplay)
Alan Robert Murray, Bub Asman	2	SOUND EDITING, SOUND EFFECTS EDITING
Alfonso Cuarón	2	CINEMATOGRAPHY, DIRECTING
Alfred Hitchcock	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Alvin Sargent	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay--based on material from another medium)
Amy Adams	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Angela Bassett	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Angela Lansbury	2	ACTRESS IN A SUPPORTING ROLE, HONORARY AWARD
Anjelica Huston	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Ann-Margret	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Anne Bancroft	2	ACTRESS, ACTRESS IN A LEADING ROLE
Anne Baxter	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Anne Hathaway	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Anne V. Coates	2	FILM EDITING, HONORARY AWARD
Annette Bening	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Anthony Hopkins	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Anthony Minghella	2	DIRECTING, WRITING (Screenplay Based on Material Previously Produced or Published)
Anthony Quinn	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Anton Grot	2	ART DIRECTION, ART DIRECTION (Black-and-White)
Argentina	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Arnold Schulman	2	WRITING (Screenplay--based on material from another medium), WRITING (Story and Screenplay--written directly for the screen)
Art Direction:  Cedric Gibbons, Paul Groesse;  Set Decoration:  Edwin B. Willis, Jack D. Moore	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Art Direction:  George W. Davis, Edward Carfagno;  Set Decoration:  Henry Grace, Dick Pefferle	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Art Direction:  Hal Pereira, Walter Tyler;  Set Decoration:  Sam Comer, Arthur Krams	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Art Direction:  Lyle R. Wheeler, John DeCuir;  Set Decoration:  Walter M. Scott, Paul S. Fox	2	ART DIRECTION, ART DIRECTION (Color)
Art Direction:  Lyle Wheeler, John DeCuir;  Set Decoration:  Thomas Little, Paul S. Fox	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Art Direction:  Richard Day, Joseph Wright;  Interior Decoration:  Thomas Little	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Art Direction:  Vincent Korda;  Interior Decoration:  Julia Heron	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Arthur Edeson	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Arthur Hiller	2	DIRECTING, JEAN HERSHOLT HUMANITARIAN AWARD
Arthur Kennedy	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Arthur Lange	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Arthur Miller	2	CINEMATOGRAPHY (Black-and-White), WRITING (Screenplay Based on Material Previously Produced or Published)
Artkino	2	DOCUMENTARY, DOCUMENTARY (Short Subject)
Atom Egoyan	2	DIRECTING, WRITING (Screenplay Based on Material Previously Produced or Published)
Audrey Hepburn	2	ACTRESS, JEAN HERSHOLT HUMANITARIAN AWARD
Australian News & Information Bureau	2	DOCUMENTARY, DOCUMENTARY (Short Subject)
Barry Fitzgerald	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Barry Levinson	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Belgium	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Ben Kingsley	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Ben Proudfoot and Kris Bowers	2	DOCUMENTARY (Short Subject), DOCUMENTARY SHORT FILM
Bernard Smith, Producer	2	BEST MOTION PICTURE, BEST PICTURE
Bernardo Bertolucci	2	DIRECTING, WRITING (Screenplay--based on material from another medium)
Bert Glennon	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Bert Haanstra, Producer	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Billy Wilder	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Billy Wilder, I. A. L. Diamond	2	WRITING (Screenplay--based on material from another medium), WRITING (Story and Screenplay--written directly for the screen)
Bo Goldman	2	WRITING (Screenplay Based on Material Previously Produced or Published), WRITING (Screenplay Written Directly for the Screen)
Bob Godfrey, Producer	2	SHORT FILM (Animated), SHORT SUBJECT (Animated)
Bob Hope	2	JEAN HERSHOLT HUMANITARIAN AWARD, SPECIAL AWARD
Brad Pitt	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Bradley Cooper	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Brenda Blethyn	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Bronislau Kaper	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original)
Bruce Dern	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Burnett Guffey	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Burt Lancaster	2	ACTOR, ACTOR IN A LEADING ROLE
Carmen D'Avino, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon)
Carson Davidson, Producer	2	SHORT SUBJECT (Live Action), SHORT SUBJECT (One-reel)
Casey Affleck	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Cate Blanchett	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Cecil Beaton	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Cedric Francis, Producer	2	SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel)
Cesare Zavattini	2	WRITING (Motion Picture Story), WRITING (Screenplay)
Charles Guggenheim	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Charles Guggenheim, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Charles Lang	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Charles Lang, Jr.	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Charles LeMaire	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Charles Previn	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Charles Rosher	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Color)
Charlton Heston	2	ACTOR, JEAN HERSHOLT HUMANITARIAN AWARD
Cher	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Chloé Zhao	2	DIRECTING, FILM EDITING
Chris Wedge	2	ANIMATED FEATURE FILM, SHORT FILM (Animated)
Christian Bale	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Christopher Chapman, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Cicely Tyson	2	ACTRESS, HONORARY AWARD
Claire Wilbur and Robin Lehman, Producers	2	DOCUMENTARY (Short Subject), SHORT FILM (Live Action)
Clifton Webb	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Colman Domingo	2	ACTOR, ACTOR IN A LEADING ROLE
Crown Film Unit	2	DOCUMENTARY (Feature), SHORT SUBJECT (One-reel)
Cy Feuer	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Cynthia Erivo	2	ACTRESS, ACTRESS IN A LEADING ROLE
Dalton Trumbo	2	WRITING (Motion Picture Story), WRITING (Screenplay)
Dame Edith Evans	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Daniel Kaluuya	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Danilo Donati	2	COSTUME DESIGN, COSTUME DESIGN (Black-and-White)
David Lynch	2	DIRECTING, HONORARY AWARD
Debbie Reynolds	2	ACTRESS, JEAN HERSHOLT HUMANITARIAN AWARD
Deborah Kerr	2	ACTRESS, HONORARY AWARD
Denmark	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Denzel Washington	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Donald Brooks	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Dudley Nichols	2	WRITING (Original Screenplay), WRITING (Screenplay)
Dustin Hoffman	2	ACTOR, ACTOR IN A LEADING ROLE
Ed Harris	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Edith Head, Gile Steele	2	COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Edmund Reek, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (One-reel)
Edward Colman	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Edward J. Kay	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Edward Norton	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Edward Selzer, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon)
Edward Ward	2	MUSIC (Music Score of a Dramatic Picture), MUSIC (Scoring of a Musical Picture)
Elia Kazan	2	DIRECTING, WRITING (Story and Screenplay--written directly for the screen)
Elizabeth Taylor	2	ACTRESS, JEAN HERSHOLT HUMANITARIAN AWARD
Elliot Goldenthal	2	MUSIC (Original Dramatic Score), MUSIC (Original Score)
Emeric Pressburger	2	WRITING (Motion Picture Story), WRITING (Original Motion Picture Story)
Emilia Pérez	2	BEST PICTURE, INTERNATIONAL FEATURE FILM
Erich Wolfgang Korngold	2	MUSIC (Original Score), MUSIC (Scoring)
Ernest Palmer	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Color)
Ethan Hawke	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Fay Bainter	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Faye Dunaway	2	ACTRESS, ACTRESS IN A LEADING ROLE
Flow	2	ANIMATED FEATURE FILM, INTERNATIONAL FEATURE FILM
France	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Frances Goodrich, Albert Hackett	2	WRITING (Adaptation), WRITING (Screenplay)
Frances Marion	2	WRITING, WRITING (Original Story)
Frances McDormand	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Frank Borzage	2	DIRECTING, DIRECTING (Dramatic Picture)
Frank DeVol	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score--substantially original)
Frank Morgan	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Fred Zinnemann, Producer	2	BEST MOTION PICTURE, BEST PICTURE
Freddie Francis	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Freddie Young	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Color)
Frederick Hollander, Morris Stoloff	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Gabriel Yared	2	MUSIC (Original Dramatic Score), MUSIC (Original Score)
Geoffrey Rush	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Geoffrey Unsworth	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Color)
George Bruns	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
George C. Scott	2	ACTOR, ACTOR IN A SUPPORTING ROLE
George J. Folsey	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Color)
George Miller	2	ANIMATED FEATURE FILM, DIRECTING
George V. Casey, Producer	2	DOCUMENTARY (Short Subject), SHORT FILM (Live Action)
Germany	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Glenn Close	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Goldie Hawn	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Grace Kelly	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Graham Greene	2	ACTOR IN A SUPPORTING ROLE, WRITING (Screenplay)
Gregg Toland	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Gregory Peck	2	ACTOR, JEAN HERSHOLT HUMANITARIAN AWARD
Guy Glover, Producer	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
H. J. Salter	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Hal Ashby	2	DIRECTING, FILM EDITING
Hal B. Wallis, Producer	2	BEST MOTION PICTURE, BEST PICTURE
Hal Mohr	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Hal Roach, Producer	2	SHORT SUBJECT (Comedy), SHORT SUBJECT (One-reel)
Hal Rosson	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Hans Dreier, Roland Anderson	2	ART DIRECTION, ART DIRECTION (Color)
Hans Kraly	2	WRITING, WRITING (Original Story)
Harry Stradling, Sr.	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Haskell Wexler	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Hayao Miyazaki	2	ANIMATED FEATURE FILM, HONORARY AWARD
Heath Ledger	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Hein Heckroth	2	ART DIRECTION (Color), COSTUME DESIGN (Color)
Helen Hayes	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Helen Hunt	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Helen Mirren	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Helen Rose	2	COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Helena Bonham Carter	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Herbert Morgan, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Two-reel)
Herschel Burke Gilbert	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Holly Hunter	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Hong Kong	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Hugo Friedhofer	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring)
Ian Ferguson, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Ian McKellen	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Irene	2	COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Irving Berlin	2	WRITING (Original Motion Picture Story), WRITING (Original Story)
Irving Ravetch, Harriet Frank, Jr.	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay--based on material from another medium)
Irwin Allen, Producer	2	BEST PICTURE, DOCUMENTARY (Feature)
Isabelle Adjani	2	ACTRESS, ACTRESS IN A LEADING ROLE
Italy	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Jacques-Yves Cousteau, Producer	2	DOCUMENTARY (Feature), SHORT SUBJECT (Live Action)
James Basevi	2	ART DIRECTION, ART DIRECTION (Black-and-White)
James Hill, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
James Horner	2	MUSIC (Original Dramatic Score), MUSIC (Original Score)
James Mason	2	ACTOR, ACTOR IN A SUPPORTING ROLE
James Newton Howard	2	MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
James Stewart	2	ACTOR, HONORARY AWARD
James Whitmore	2	ACTOR, ACTOR IN A SUPPORTING ROLE
James Woods	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jamie Foxx	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jane Campion	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Janet McTeer	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Japan	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Javier Bardem	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jay Rosenblatt	2	DOCUMENTARY (Short Subject), DOCUMENTARY SHORT FILM
Jean Simmons	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Jeff Bridges	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jeffrey Katzenberg	2	ANIMATED FEATURE FILM, JEAN HERSHOLT HUMANITARIAN AWARD
Jennifer Jones	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Jennifer Lawrence	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Jeremy Renner	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jessica Chastain	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Jessica Lange	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Jessica Tandy	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Jessie Buckley	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Joan Allen	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Joan Keller Stern, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Joanne Woodward	2	ACTRESS, ACTRESS IN A LEADING ROLE
Joaquin Phoenix	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Jodie Foster	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Joe MacDonald	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
John Addison	2	MUSIC (Music Score--substantially original), MUSIC (Original Dramatic Score)
John Boorman	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
John Garfield	2	ACTOR, ACTOR IN A SUPPORTING ROLE
John Healy, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Two-reel)
John Hurt	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
John Lasseter	2	ANIMATED FEATURE FILM, SPECIAL ACHIEVEMENT AWARD
John Michael Hayes	2	WRITING (Screenplay--based on material from another medium), WRITING (Screenplay)
John Seitz	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
John Singleton	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
John Steinbeck	2	WRITING (Original Motion Picture Story), WRITING (Story and Screenplay)
John Victor Mackay	2	ART DIRECTION, ART DIRECTION (Black-and-White)
Johnny Green	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Jonas Poher Rasmussen, Monica Hellström, Signe Byrge Sørensen and Charlotte De La Gournerie	2	ANIMATED FEATURE FILM, DOCUMENTARY (Feature)
José Ferrer	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Joseph LaShelle	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Joseph Valentine	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Jude Law	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Judi Dench	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Judy Davis	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Judy Garland	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Jules Dassin	2	DIRECTING, WRITING (Story and Screenplay--written directly for the screen)
Jules White, Producer	2	SHORT SUBJECT (Comedy), SHORT SUBJECT (Two-reel)
Julia Roberts	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Julianne Moore	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Julie Andrews	2	ACTRESS, ACTRESS IN A LEADING ROLE
Julie Christie	2	ACTRESS, ACTRESS IN A LEADING ROLE
Julie Harris	2	ACTRESS, COSTUME DESIGN (Black-and-White)
Julie Walters	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Juliette Binoche	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Julius J. Epstein	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay--based on material from another medium)
Karl Freund	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Kate Hudson	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Kate Winslet	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Katharine Hepburn	2	ACTRESS, ACTRESS IN A LEADING ROLE
Kathy Bates	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Keira Knightley	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Kevin Costner	2	ACTOR IN A LEADING ROLE, DIRECTING
Kevin Spacey	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Kim Stanley	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
King Vidor	2	DIRECTING, DIRECTING (Dramatic Picture)
Kirk Douglas	2	ACTOR, HONORARY AWARD
Kurt Luedtke	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Written Directly for the Screen)
Laura Dern	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Laura Linney	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Lee Garmes	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Color)
Leith Stevens	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
Lewis Milestone	2	DIRECTING, DIRECTING (Comedy Picture)
Lillian Hellman	2	WRITING (Original Screenplay), WRITING (Screenplay)
Lionel Barrymore	2	ACTOR, DIRECTING
Lionel Lindon	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Liv Ullmann	2	ACTRESS, ACTRESS IN A LEADING ROLE
Lou Forbes	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring)
Louis Clyde Stoumen, Producer	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Louis Gruenberg	2	MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Louis Marcus, Producer	2	DOCUMENTARY (Short Subject), SHORT FILM (Live Action)
Louis Silvers	2	MUSIC (Original Score), MUSIC (Scoring)
Loyal Griggs	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Luis Enrique Bacalov	2	MUSIC (Original Dramatic Score), MUSIC (Scoring of Music--adaptation or treatment)
Lyle Wheeler	2	ART DIRECTION, ART DIRECTION (Black-and-White)
Lynn Redgrave	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
M. Night Shyamalan	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Mack Sennett, Producer	2	SHORT SUBJECT (Comedy), SHORT SUBJECT (Novelty)
Maggie Smith	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Manuel Arango and Robert Amram, Producers	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Live Action)
Marc Shaiman	2	MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
Marcello Mastroianni	2	ACTOR, ACTOR IN A LEADING ROLE
Margaret Furse	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Margot Robbie	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Marik Vos	2	COSTUME DESIGN, COSTUME DESIGN (Black-and-White)
Marlon Brando	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Marsha Mason	2	ACTRESS, ACTRESS IN A LEADING ROLE
Martin McDonagh	2	DIRECTING, SHORT FILM (Live Action)
Marvin Hamlisch	2	MUSIC (Original Dramatic Score), MUSIC (Original Score)
Marvin Hatley	2	MUSIC (Original Score), MUSIC (Scoring)
Mary McDonnell	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Mary Wills	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Matt Damon	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Max von Sydow	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Maximilian Schell	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Melissa Leo	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Melissa McCarthy	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Melville Shavelson, Jack Rose	2	WRITING (Story and Screenplay--written directly for the screen), WRITING (Story and Screenplay)
Melvyn Douglas	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Meredith Willson	2	MUSIC (Music Score of a Dramatic Picture), MUSIC (Original Score)
Mervyn LeRoy	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Meryl Streep	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Metro-Goldwyn-Mayer Studio Sound Department	2	SOUND, SOUND RECORDING
Michael Cacoyannis	2	DIRECTING, WRITING (Screenplay--based on material from another medium)
Michael Fassbender	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Michael Mills, Producer	2	SHORT FILM (Animated), SHORT SUBJECT (Animated)
Michael Wilson	2	WRITING (Screenplay--Adapted), WRITING (Screenplay)
Michelle Pfeiffer	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Michelle Williams	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Mike Figgis	2	DIRECTING, WRITING (Screenplay Based on Material Previously Produced or Published)
Mike Leigh	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Millard Kaufman	2	WRITING (Screenplay), WRITING (Story and Screenplay)
Miranda Richardson	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Montgomery Clift	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Monty Woolley	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Morgan Freeman	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Morris Stoloff, Ernst Toch	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Music Score of a Dramatic Picture)
Morris Stoloff, George Duning	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Morris Stoloff, Harry Sukman	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Morton Haack	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Moss Hart	2	WRITING (Original Story), WRITING (Screenplay)
Music and Lyrics by Leslie Bricusse	2	MUSIC (Song--Original for the Picture), MUSIC (Song)
Music by Burt Bacharach; Lyrics by Hal David	2	MUSIC (Song--Original for the Picture), MUSIC (Song)
Music by Elmer Bernstein; Lyrics by Don Black	2	MUSIC (Song--Original for the Picture), MUSIC (Song)
Music by George Barrie; Lyrics by Sammy Cahn	2	MUSIC (Original Song), MUSIC (Song)
Music by Marvin Hamlisch; Lyrics by Alan Bergman and Marilyn Bergman	2	MUSIC (Original Song), MUSIC (Song)
Music by Quincy Jones; Lyrics by Bob Russell	2	MUSIC (Song--Original for the Picture), MUSIC (Song)
Natalie Portman	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Natalie Wood	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Nedrick Young, Harold Jacob Smith	2	WRITING (Screenplay--based on material from another medium), WRITING (Story and Screenplay--written directly for the screen)
Neil Jordan	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Nelson Riddle	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
Nick Nolte	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Nicole Kidman	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Norbert Brodine	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Norman Jewison	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Norman Krasna	2	WRITING (Original Screenplay), WRITING (Original Story)
Norway	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Oliver Wallace	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Olivia Colman	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Olivia de Havilland	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Oprah Winfrey	2	ACTRESS IN A SUPPORTING ROLE, JEAN HERSHOLT HUMANITARIAN AWARD
Orlando von Einsiedel and Joanna Natasegara	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Orson Welles	2	ACTOR, DIRECTING
Owen Roizman	2	CINEMATOGRAPHY, HONORARY AWARD
Paramount Publix	2	OUTSTANDING PRODUCTION, SHORT SUBJECT (Novelty)
Paramount Studio Sound Department, George Dutton, Sound Director	2	SOUND, SOUND RECORDING
Paul C. Vogel	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Paul Giamatti	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Paul Osborn	2	WRITING (Screenplay--based on material from another medium), WRITING (Screenplay)
Paul Scofield	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Paul Thomas Anderson	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Penélope Cruz	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Peter Finch	2	ACTOR, ACTOR IN A LEADING ROLE
Peter Lord	2	ANIMATED FEATURE FILM, SHORT FILM (Animated)
Peter O'Toole	2	ACTOR, ACTOR IN A LEADING ROLE
Peter Sellers	2	ACTOR, ACTOR IN A LEADING ROLE
Peter Shaffer	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay--based on material from another medium)
Peter Weir	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Philip Dunne	2	WRITING (Screenplay), WRITING (Story and Screenplay)
Philip Glass	2	MUSIC (Original Dramatic Score), MUSIC (Original Score)
Philip Seymour Hoffman	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Philip Yordan	2	WRITING (Motion Picture Story), WRITING (Original Screenplay)
Phyllis Dalton	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Piero Tosi	2	COSTUME DESIGN, COSTUME DESIGN (Color)
Pierre Collings, Sheridan Gibney	2	WRITING (Original Story), WRITING (Screenplay)
Piper Laurie	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Poland	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Production Design: Jess Gonchor; Set Decoration: Nancy Haigh	2	ART DIRECTION, PRODUCTION DESIGN
Production Design: John Myhre; Set Decoration: Gordon Sim	2	ART DIRECTION, PRODUCTION DESIGN
Production Design: Sarah Greenwood; Set Decoration: Katie Spencer	2	ART DIRECTION, PRODUCTION DESIGN
Rachel Portman	2	MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
Ray Heindorf	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring of Music--adaptation or treatment)
Renée Zellweger	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Richard Day	2	ART DIRECTION, ART DIRECTION (Black-and-White)
Richard Day, Joseph C. Wright	2	ART DIRECTION (Black-and-White), ART DIRECTION (Color)
Richard Farnsworth	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Richard Harris	2	ACTOR, ACTOR IN A LEADING ROLE
Richard Jenkins	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Richard Murphy	2	WRITING (Screenplay), WRITING (Story and Screenplay)
Richard Rodney Bennett	2	MUSIC (Original Dramatic Score), MUSIC (Original Music Score)
Richard Schweizer, David Wechsler	2	WRITING (Motion Picture Story), WRITING (Screenplay)
Robbie Robertson	2	MUSIC (Original Score), SPECIAL VISUAL EFFECTS
Robert Burks	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Robert De Niro	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Robert Downey Jr.	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Robert Duvall	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Robert Emmett Dolan	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Robert Getchell	2	WRITING (Original Screenplay), WRITING (Screenplay--based on material from another medium)
Robert Redford	2	ACTOR, DIRECTING
Robert Riskin	2	WRITING (Adaptation), WRITING (Screenplay)
Robert Rossen	2	DIRECTING, WRITING (Screenplay)
Robert Towne	2	WRITING (Original Screenplay), WRITING (Screenplay--based on material from another medium)
Robert Wise, Producer	2	BEST MOTION PICTURE, BEST PICTURE
Roberto Benigni	2	ACTOR IN A LEADING ROLE, DIRECTING
Robin Williams	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Rod Steiger	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Roger Edens, Georgie Stoll	2	MUSIC (Scoring of a Musical Picture), MUSIC (Scoring)
Roman Polanski	2	DIRECTING, WRITING (Screenplay--based on material from another medium)
Romulus Films	2	BEST MOTION PICTURE, SHORT SUBJECT (Two-reel)
Rooney Mara	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Rosalind Russell	2	ACTRESS, JEAN HERSHOLT HUMANITARIAN AWARD
Roy Scheider	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Roy Webb	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Original Score)
Russell Harlan	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Ruth Gordon, Garson Kanin	2	WRITING (Original Screenplay), WRITING (Story and Screenplay)
Ruth Prawer Jhabvala	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Based on Material Previously Produced or Published)
Ryan Gosling	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Sally Field	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Sally Hawkins	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Sam Leavitt	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Sam Spiegel, Producer	2	BEST MOTION PICTURE, BEST PICTURE
Samantha Morton	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Samuel Goldwyn	2	IRVING G. THALBERG MEMORIAL AWARD, JEAN HERSHOLT HUMANITARIAN AWARD
Samuel Goldwyn Studio Sound Department, Gordon E. Sawyer, Sound Director	2	SOUND, SOUND RECORDING
Saoirse Ronan	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Saul Bass, Producer	2	DOCUMENTARY (Short Subject), SHORT FILM (Live Action)
Scarlett Johansson	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Selznick International Pictures	2	BEST MOTION PICTURE, OUTSTANDING PRODUCTION
Sentimental Value	2	BEST PICTURE, INTERNATIONAL FEATURE FILM
Shelley Winters	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Shirley MacLaine	2	ACTRESS, ACTRESS IN A LEADING ROLE
Sidney Buchman	2	WRITING (Screenplay), WRITING (Story and Screenplay)
Sidney Franklin	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Sidney Howard	2	WRITING (Adaptation), WRITING (Screenplay)
Sigourney Weaver	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Skibo Productions	2	SHORT SUBJECT (Novelty), SHORT SUBJECT (One-reel)
Sol Polito	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Sophia Loren	2	ACTRESS, HONORARY AWARD
Spain	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
Stanley Kramer	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Stanley Kramer, Producer	2	BEST MOTION PICTURE, BEST PICTURE
Stephen Bosustow, Executive Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon)
Steve McQueen	2	ACTOR, DIRECTING
Steven Okazaki, Producer	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
Steven Soderbergh	2	DIRECTING, WRITING (Screenplay Written Directly for the Screen)
Steven Spielberg	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Steven Zaillian	2	WRITING (Screenplay Based on Material from Another Medium), WRITING (Screenplay Based on Material Previously Produced or Published)
Sylvain Chomet	2	ANIMATED FEATURE FILM, SHORT FILM (Animated)
Talia Shire	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Ted McCord	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
Tennessee Williams	2	WRITING (Screenplay--Adapted), WRITING (Screenplay)
Teresa Wright	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Terrence Malick	2	DIRECTING, WRITING (Screenplay Based on Material Previously Produced or Published)
The Caddo Company	2	OUTSTANDING PICTURE, OUTSTANDING PRODUCTION
The March of Time	2	DOCUMENTARY, DOCUMENTARY (Short Subject)
The Secret Agent	2	BEST PICTURE, INTERNATIONAL FEATURE FILM
Thomas Mead, Producer	2	SHORT SUBJECT (One-reel), SHORT SUBJECT (Two-reel)
Thomas Newman	2	MUSIC (Original Musical or Comedy Score), MUSIC (Original Score)
Tim Robbins	2	ACTOR IN A SUPPORTING ROLE, DIRECTING
Tim Yip	2	ART DIRECTION, COSTUME DESIGN
Timothée Chalamet	2	ACTOR, ACTOR IN A LEADING ROLE
Todd-AO Sound Department, Fred Hynes, Sound Director	2	SOUND, SOUND RECORDING
Tom Courtenay	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Tom Cruise	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Tom Hanks	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Tom Wilkinson	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Tommy Lee Jones	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Tony Walton	2	COSTUME DESIGN, COSTUME DESIGN (Color)
United Kingdom	2	FOREIGN LANGUAGE FILM, INTERNATIONAL FEATURE FILM
United States Army Pictorial Service	2	DOCUMENTARY (Feature), DOCUMENTARY (Short Subject)
United States Army Signal Corps	2	DOCUMENTARY, DOCUMENTARY (Short Subject)
Universal	2	OUTSTANDING PRODUCTION, SHORT SUBJECT (Novelty)
Universal-International Studio Sound Department, Leslie I. Carey, Sound Director	2	SOUND, SOUND RECORDING
Victor McLaglen	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Victor Milner	2	CINEMATOGRAPHY, CINEMATOGRAPHY (Black-and-White)
Viola Davis	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Vittorio Nino Novarese	2	COSTUME DESIGN (Black-and-White), COSTUME DESIGN (Color)
Walt Disney	2	IRVING G. THALBERG MEMORIAL AWARD, SPECIAL AWARD
Walter Huston	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Walter Matthau	2	ACTOR, ACTOR IN A SUPPORTING ROLE
Walter Mirisch	2	IRVING G. THALBERG MEMORIAL AWARD, JEAN HERSHOLT HUMANITARIAN AWARD
Walter Scharf	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Scoring of a Musical Picture)
Walter Wanger, Producer	2	BEST PICTURE, DOCUMENTARY (Short Subject)
Ward Kimball, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Cartoon)
Wendy Hiller	2	ACTRESS, ACTRESS IN A SUPPORTING ROLE
Werner Janssen	2	MUSIC (Music Score of a Dramatic or Comedy Picture), MUSIC (Original Score)
Wes Anderson	2	ANIMATED FEATURE FILM, DIRECTING
Whoopi Goldberg	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Wilbur T. Blume, Producer	2	DOCUMENTARY (Short Subject), SHORT SUBJECT (Two-reel)
Willem Dafoe	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
William Daniels	2	CINEMATOGRAPHY (Black-and-White), CINEMATOGRAPHY (Color)
William Goldman	2	WRITING (Screenplay--based on material from another medium), WRITING (Story and Screenplay--based on material not previously published or produced)
William Holden	2	ACTOR, ACTOR IN A LEADING ROLE
William Hurt	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
William Wyler	2	DIRECTING, IRVING G. THALBERG MEMORIAL AWARD
Winona Ryder	2	ACTRESS IN A LEADING ROLE, ACTRESS IN A SUPPORTING ROLE
Wolfgang Petersen	2	DIRECTING, WRITING (Screenplay Based on Material from Another Medium)
Woody Allen, Marshall Brickman	2	WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced), WRITING (Screenplay Written Directly for the Screen)
Woody Harrelson	2	ACTOR IN A LEADING ROLE, ACTOR IN A SUPPORTING ROLE
Written by Damien Chazelle	2	WRITING (Adapted Screenplay), WRITING (Original Screenplay)
Written by Joel Coen & Ethan Coen	2	WRITING (Adapted Screenplay), WRITING (Original Screenplay)
Written by Kenneth Lonergan	2	WRITING (Original Screenplay), WRITING (Screenplay Written Directly for the Screen)
Written by Rian Johnson	2	WRITING (Adapted Screenplay), WRITING (Original Screenplay)
Yoshiro Muraki	2	ART DIRECTION, COSTUME DESIGN (Black-and-White)
```

```sql
select nome_indicado, count(distinct categoria) as quantidade_Categorias , 
GROUP_CONCAT(DISTINCT categoria ORDER BY categoria SEPARATOR ', ') AS categorias
FROM indicados_ao_oscar
GROUP BY nome_indicado
HAVING COUNT(DISTINCT categoria) > 1
ORDER BY quantidade_Categorias DESC, nome_indicado ASC;
```

**5.5** Quantos indicados têm exatamente 1 indicação na história?

R: 5627 indicados

```sql
SELECT COUNT(*) 
FROM (
    SELECT nome_indicado
    FROM indicados_ao_oscar
    GROUP BY nome_indicado
    HAVING COUNT(*) = 1
) AS indicados_unicos;
```

**5.6** Qual o maior números de indicados em um único ano? Essa é uma pergunta franca.

R:
```
Ano / Edição / Indicações
1943	 15	   186
```

```sql
SELECT 
    ano_cerimonia, 
    edicao_cerimonia, 
    COUNT(*) AS total_indicados
FROM indicados_ao_oscar
GROUP BY ano_cerimonia, edicao_cerimonia
ORDER BY total_indicados DESC
LIMIT 1;
```

---

## Nível 6: Análise de Filmes

### Toy Story

**6.1** A série de filmes Toy Story ganhou Oscars em quais anos?

R:
```
Toy Story 3	 2011	Ganhou
Toy Story 3	 2011	Ganhou
Toy Story 4	 2020	Ganhou
```

```sql
select nome_filme, ano_cerimonia, 
if(vencedor = true,'Ganhou','Perdeu') as vencedor
from indicados_ao_oscar
where vencedor = true and nome_filme 
like '%toy story%';
```

**6.2** Quantas indicações a franquia Toy Story recebeu no total?

R: 11 Indicações

```sql
select count(nome_filme)
from indicados_ao_oscar
where  nome_filme 
like '%toy story%';
```

**6.3** Em quais categorias os filmes Toy Story foram indicados?

R:
```
MUSIC (Original Musical or Comedy Score)
MUSIC (Original Song)
WRITING (Screenplay Written Directly for the Screen)
ANIMATED FEATURE FILM
BEST PICTURE
SOUND EDITING
WRITING (Adapted Screenplay)
```

```sql
select distinct categoria
from indicados_ao_oscar
where  nome_filme 
like '%toy story%';
```

### Crash

**6.4** Em qual edição do Oscar o filme "Crash" concorreu?

R: na edição 78

```sql
select  edicao_cerimonia
from indicados_ao_oscar
where  nome_filme 
like 'crash';
```

**6.5** Quantas indicações o filme "Crash" recebeu?

R: 6 indicações

```sql
select count(nome_filme)
from indicados_ao_oscar
where  nome_filme 
like 'crash';
```

**6.6** "Crash" ganhou o Oscar de Melhor Filme?

R: Sim ele ganhou:
```
Crash	FILM EDITING
Crash	BEST PICTURE
Crash	WRITING (Original Screenplay)
```

```sql
select nome_filme, categoria
from indicados_ao_oscar
where  nome_filme 
like 'crash' and vencedor = true;
```

### Central do Brasil

**6.7** O filme "Central do Brasil" aparece no banco de dados?

R:Sim, porém seu nome esta em inglês Central Station

```sql
select nome_filme
from indicados_ao_oscar
where nome_filme = 'central station';
```

**6.8** Se sim, quantas indicações "Central do Brasil" recebeu?

R: 2 Indicações

```sql
select count(nome_filme)
from indicados_ao_oscar
where nome_filme = 'central station';
```

---

## Nível 7: Operações de Atualização

**7.1** No campo "vencedor", altere todos os valores "true" (string) para true (booleano) e "false" (string) para false (booleano).

R: foi

```sql
UPDATE indicados_ao_oscar
SET vencedor = CASE 
    WHEN CAST(vencedor AS CHAR) = 'true' THEN 1
    WHEN CAST(vencedor AS CHAR) = 'false' THEN 0
    ELSE vencedor 
END
WHERE id_registro >= 1;
```

**7.2** Inclua no banco 3 filmes que nunca foram nomeados ao Oscar, mas que você acha que merecem. Use dados fictícios, mas realistas.

R: No meu caso vou adicionar ganhadores

```sql
update indicados_ao_oscar
set vencedor = 1
where nome_filme like '%Harry Potter%';
update indicados_ao_oscar
set vencedor = 1
where nome_filme like 'Sinners';
update indicados_ao_oscar
set vencedor = 1
where nome_filme like 'Grown Ups';
```

**7.3** Adicione uma nova categoria chamada "BEST INTERNATIONAL FEATURE FILM" com alguns vencedores recentes (2020-2024).

R:

```sql
INSERT INTO indicados_ao_oscar(ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_indicado, nome_filme, vencedor) VALUES 
(2023, 2024, 96, 'BEST INTERNATIONAL FEATURE FILM', 'The Zone of Interest', 'The Zone of Interest', true),
(2022, 2023, 95, 'BEST INTERNATIONAL FEATURE FILM', 'All Quiet on the Western Front', 'All Quiet on the Western Front', true),
(2021, 2022, 94, 'BEST INTERNATIONAL FEATURE FILM', 'Drive My Car', 'Drive My Car', true),
(2020, 2021, 93, 'BEST INTERNATIONAL FEATURE FILM', 'Another Round', 'Another Round', true),
(2019, 2020, 92, 'BEST INTERNATIONAL FEATURE FILM', 'Parasite', 'Parasite', true);
```

**7.4** Corrija possíveis erros de digitação nos nomes dos filmes (ex: espaços extras, caracteres especiais desnecessários).

R:

```sql
UPDATE indicados_ao_oscar
SET nome_filme = TRIM(nome_filme)
WHERE id_registro >= 1;
```

**7.5** Remova todos os registros com valor NULL no campo nome_do_filme.

R:

```sql
DELETE FROM indicados_ao_oscar
WHERE nome_filme = null OR nome_filme ='' OR nome_filme ='null';

```

---

## Nível 8: Análise Temporal

**8.1** Quantas indicações aconteceram por década? Agrupe por década (1920s, 1930s, etc.) e mostre o total.

R:
```
Decada  |  Total Indicações
1920s	    73
1930s	    711
1940s	    1501
1950s	    1188
1960s	    1195
1970s	    1056
1980s	    1060
1990s	    1113
2000s	    1120
2010s	    1250
2020s	    712
```

```sql
SELECT 
    CONCAT(FLOOR(ano_cerimonia / 10) * 10, 's') AS decada,
    COUNT(*) AS total_indicacoes
FROM indicados_ao_oscar
GROUP BY decada
ORDER BY decada;
```

**8.2** Em qual década houve o maior número de indicações?

R: A decada de 1940s com 1501 indicações.

```sql
SELECT 
    CONCAT(FLOOR(ano_cerimonia / 10) * 10, 's') AS decada,
    COUNT(*) AS total_indicacoes
FROM indicados_ao_oscar
GROUP BY decada
ORDER BY total_indicacoes DESC
LIMIT 1 ;
```

**8.3** Como o número de categorias evoluiu ao longo dos anos? Mostre quantas categorias únicas existiam a cada década.

R: 
```
Decada | Total Categorias
1920s	    15
1930s	    27
1940s	    38
1950s	    43
1960s	    40
1970s	    50
1980s	    34
1990s	    31
2000s	    31
2010s	    30
2020s	    33
```

```sql
SELECT 
    CONCAT(FLOOR(ano_cerimonia / 10) * 10, 's') AS decada,
    COUNT(DISTINCT categoria) AS total_categorias
FROM indicados_ao_oscar
GROUP BY decada
ORDER BY decada;
```

**8.4** Qual foi o ano com o maior número de indicações registradas?

R: No ano de 1943 com 186 indicações.

```sql
SELECT ano_cerimonia AS ano,
    COUNT(*) AS total_indicações
FROM indicados_ao_oscar
GROUP BY ano
ORDER BY total_indicações DESC
LIMIT 1;
```

**8.5** Calcule a taxa de crescimento de indicações comparando a primeira década com a última.

R: Na primeira decada: 73, Na Ultima: 712 e Percentual de crescimento: 875.34.

```sql
SELECT 
    primeiro.total_indicacoes AS indicacoes_primeira_decada,
    ultimo.total_indicacoes AS indicacoes_ultima_decada,
    ROUND(
        ((ultimo.total_indicacoes - primeiro.total_indicacoes) / primeiro.total_indicacoes) * 100, 
        2
    ) AS taxa_crescimento_percentual
FROM 
    (
        SELECT 
            FLOOR(ano_cerimonia / 10) * 10 AS ano_base,
            COUNT(*) AS total_indicacoes
        FROM indicados_ao_oscar
        GROUP BY FLOOR(ano_cerimonia / 10) * 10
        ORDER BY ano_base ASC
        LIMIT 1
    ) AS primeiro,
    (
        SELECT 
            FLOOR(ano_cerimonia / 10) * 10 AS ano_base,
            COUNT(*) AS total_indicacoes
        FROM indicados_ao_oscar
        GROUP BY FLOOR(ano_cerimonia / 10) * 10
        ORDER BY ano_base DESC
        LIMIT 1
    ) AS ultimo;
```

---

## Nível 9: Questões Históricas e Sociais

### Representatividade

**9.1** Sidney Poitier foi o primeiro ator negro a ser indicado ao Oscar. Em que ano ele foi indicado? Por qual filme?

R:
```
Sidney Poitier | The Defiant Ones | 1959.
```

```sql
select  nome_indicado, nome_filme, ano_cerimonia 
from indicados_ao_oscar
where nome_indicado = 'Sidney Poitier';
```

**9.2** Sidney Poitier ganhou o Oscar nessa indicação?

R: Não, só veio a ganhar depois no ano de 1964.

```sql
select  nome_indicado, nome_filme, ano_cerimonia, vencedor 
from indicados_ao_oscar
where nome_indicado = 'Sidney Poitier';
```

**9.3** Quantos atores/atrizes negros foram indicados na categoria ACTOR ou ACTRESS antes de 1970?

R: Tive que pesquisar na inter mas fiz a query com os nomes que achei dando 2 artistas 

```sql
SELECT 
    COUNT(DISTINCT nome_indicado) AS total_atores_atrizes_negros
FROM indicados_ao_oscar
WHERE (categoria LIKE '%ACTOR%' OR categoria LIKE '%ACTRESS%')
  AND ano_cerimonia < 1970
  AND nome_indicado IN ('Sidney Poitier', 'Dorothy Dandridge' );
```

**9.4** Liste todos os filmes dirigidos por mulheres que ganharam algum Oscar.

R: Tambem tive que pesquisar na internet
```
The Power of the Dog | Jane Campion | 2022
Nomadland | Chloé Zhao | 2021
The Hurt Locker | Kathryn Bigelow | 2010
```

```sql
SELECT DISTINCT 
    nome_filme,
    nome_indicado AS diretora,
    ano_cerimonia
FROM indicados_ao_oscar
WHERE categoria LIKE '%DIRECTING%'
  AND vencedor = 1
  AND nome_indicado IN (
      'Kathryn Bigelow', 
      'Chloé Zhao', 
      'Jane Campion')
ORDER BY ano_cerimonia DESC;
```

### Coincidências

**9.5** Denzel Washington e Jamie Foxx já concorreram ao Oscar no mesmo ano?

R: Não concorreram no mesmo ano.
```
Denzel Washington	1988
Denzel Washington	1990
Denzel Washington	1993
Denzel Washington	2000
Denzel Washington	2002
Jamie Foxx	2005
Jamie Foxx	2005
Denzel Washington	2013
Denzel Washington	2017
Denzel Washington	2018
Denzel Washington	2022
```

```sql
select  nome_indicado, ano_cerimonia 
from indicados_ao_oscar
where nome_indicado = 'Denzel Washington'
or nome_indicado = 'Jamie Foxx';

```

**9.6** Se sim, em qual ano e quem ganhou?

R: Não concorreram

```sql
```

**9.7** Encontre casos onde o mesmo filme ganhou Oscar em múltiplas categorias na mesma cerimônia. Mostre o nome do filme e quantas categorias ele venceu.

R:O filme: Ben-Hur, o ano: 1960	e a quantidade de categorias vencidas: 11.

```sql
SELECT 
    nome_filme,
    ano_cerimonia,
    COUNT(*) AS total_categorias_vencidas
FROM indicados_ao_oscar
WHERE vencedor = TRUE
GROUP BY nome_filme, ano_cerimonia
HAVING COUNT(*) > 1
ORDER BY total_categorias_vencidas DESC, ano_cerimonia ASC
LIMIT 1;
```

---

## Nível 10: Análise Avançada

**10.1** Quais filmes ganharam o Oscar de Melhor Filme ("OUTSTANDING PICTURE" ou "BEST PICTURE") e Melhor Diretor na mesma cerimônia?

R:
```
Ano Cerimonia  | Edição Cerimonia | Nome filme | Diretor Vencedor
2025	97	Anora	Sean Baker
2024	96	Oppenheimer	Christopher Nolan
2023	95	Everything Everywhere All at Once	Daniel Kwan and Daniel Scheinert
2021	93	Nomadland	Chloé Zhao
2020	92	Parasite	Bong Joon Ho
2018	90	The Shape of Water	Guillermo del Toro
2015	87	Birdman or (The Unexpected Virtue of Ignorance)	Alejandro G. Iñárritu
2012	84	The Artist	Michel Hazanavicius
2011	83	The King's Speech	Tom Hooper
2010	82	The Hurt Locker	Kathryn Bigelow
2009	81	Slumdog Millionaire	Danny Boyle
2008	80	No Country for Old Men	Joel Coen and Ethan Coen
2007	79	The Departed	Martin Scorsese
2005	77	Million Dollar Baby	Clint Eastwood
2004	76	The Lord of the Rings: The Return of the King	Peter Jackson
2002	74	A Beautiful Mind	Ron Howard
2000	72	American Beauty	Sam Mendes
1998	70	Titanic	James Cameron
1997	69	The English Patient	Anthony Minghella
1996	68	Braveheart	Mel Gibson
1995	67	Forrest Gump	Robert Zemeckis
1994	66	Schindler's List	Steven Spielberg
1993	65	Unforgiven	Clint Eastwood
1992	64	The Silence of the Lambs	Jonathan Demme
1991	63	Dances With Wolves	Kevin Costner
1989	61	Rain Man	Barry Levinson
1988	60	The Last Emperor	Bernardo Bertolucci
1987	59	Platoon	Oliver Stone
1986	58	Out of Africa	Sydney Pollack
1985	57	Amadeus	Milos Forman
1984	56	Terms of Endearment	James L. Brooks
1983	55	Gandhi	Richard Attenborough
1981	53	Ordinary People	Robert Redford
1980	52	Kramer vs. Kramer	Robert Benton
1979	51	The Deer Hunter	Michael Cimino
1978	50	Annie Hall	Woody Allen
1977	49	Rocky	John G. Avildsen
1976	48	One Flew over the Cuckoo's Nest	Milos Forman
1975	47	The Godfather Part II	Francis Ford Coppola
1974	46	The Sting	George Roy Hill
1972	44	The French Connection	William Friedkin
1971	43	Patton	Franklin J. Schaffner
1970	42	Midnight Cowboy	John Schlesinger
1969	41	Oliver!	Carol Reed
1967	39	A Man for All Seasons	Fred Zinnemann
1966	38	The Sound of Music	Robert Wise
1965	37	My Fair Lady	George Cukor
1964	36	Tom Jones	Tony Richardson
1963	35	Lawrence of Arabia	David Lean
```

```sql
SELECT 
    f.ano_cerimonia,
    f.edicao_cerimonia,
    f.nome_filme,
    d.nome_indicado AS diretor_vencedor
FROM indicados_ao_oscar f
INNER JOIN indicados_ao_oscar d 
    ON f.ano_cerimonia = d.ano_cerimonia 
    AND f.nome_filme = d.nome_filme
WHERE (f.categoria = 'BEST PICTURE' OR f.categoria = 'OUTSTANDING PICTURE')
  AND f.vencedor = TRUE
  AND d.categoria = 'DIRECTING'
  AND d.vencedor = TRUE
ORDER BY f.ano_cerimonia DESC;
```

**10.2** Qual filme recebeu o maior número de indicações em uma única cerimônia?

R: Nome do filme: La La Land, ano cerimonia: 2017 e total de indicações: 14.

```sql
SELECT 
    nome_filme,
    ano_cerimonia,
    COUNT(*) AS total_indicacoes
FROM indicados_ao_oscar
WHERE nome_filme IN(
SELECT nome_filme = 'null'
FROM indicados_ao_oscar)
GROUP BY nome_filme, ano_cerimonia
ORDER BY total_indicacoes DESC
LIMIT 1;
```

**10.3** Qual filme teve a maior taxa de conversão (porcentagem de indicações que viraram vitórias)?

R:Filme: The Lord of the Rings: The Return of the King, total de indicações: 11, total de vitorias:	11, Porcentagem de vitoria: 100.00

```sql
SELECT 
    nome_filme,
    COUNT(*) AS total_indicacoes,
    SUM(CASE WHEN vencedor = TRUE THEN 1 ELSE 0 END) AS total_vitorias,
    ROUND((SUM(CASE WHEN vencedor = TRUE THEN 1 ELSE 0 END) / COUNT(*)) * 100, 2) AS taxa_conversao_percentual
FROM indicados_ao_oscar
GROUP BY nome_filme
HAVING COUNT(*) >= 2
ORDER BY taxa_conversao_percentual DESC, total_vitorias DESC
LIMIT 1;
```

**10.4** Encontre atores que foram indicados em anos consecutivos. Liste o nome e os anos.

R:
```
Nome indicado | Ano Atual | Ano Seguinte
Adam Driver	2019	2020
Al Pacino	1973	1974
Al Pacino	1974	1975
Al Pacino	1975	1976
Albert Finney	1984	1985
Alec Guinness	1958	1959
Alice Brady	1937	1938
Amy Adams	2013	2014
Angela Lansbury	1945	1946
Anjelica Huston	1990	1991
Anthony Hopkins	2020	2021
Anthony Quinn	1957	1958
Arthur Kennedy	1958	1959
Audrey Hepburn	1954	1955
Bette Davis	1935	1936
Bette Davis	1939	1940
Bette Davis	1940	1941
Bette Davis	1941	1942
Bette Davis	1942	1943
Bing Crosby	1945	1946
Bradley Cooper	2013	2014
Bradley Cooper	2014	2015
Burgess Meredith	1976	1977
Cate Blanchett	2007	2008
Celeste Holm	1950	1951
Charles Bickford	1948	1949
Charles Boyer	1938	1939
Charles Durning	1983	1984
Clark Gable	1935	1936
Claude Rains	1944	1945
Claudette Colbert	1935	1936
Colin Firth	2010	2011
Colman Domingo	2024	2025
Dame Edith Evans	1964	1965
Deborah Kerr	1957	1958
Deborah Kerr	1958	1959
Debra Winger	1983	1984
Denzel Washington	2017	2018
Diane Ladd	1991	1992
Eddie Redmayne	2015	2016
Eleanor Parker	1951	1952
Elizabeth Taylor	1958	1959
Elizabeth Taylor	1959	1960
Elizabeth Taylor	1960	1961
Ellen Burstyn	1974	1975
Emma Thompson	1993	1994
Estelle Parsons	1968	1969
Ethel Barrymore	1947	1948
Fredric March	1931	1932
Gary Cooper	1942	1943
Gary Cooper	1943	1944
Gene Hackman	1971	1972
George C. Scott	1971	1972
Geraldine Page	1962	1963
Geraldine Page	1985	1986
Gladys Cooper	1943	1944
Glenda Jackson	1971	1972
Glenn Close	1983	1984
Glenn Close	1984	1985
Glenn Close	1988	1989
Grace Kelly	1954	1955
Greer Garson	1942	1943
Greer Garson	1943	1944
Greer Garson	1944	1945
Greer Garson	1945	1946
Gregory Peck	1946	1947
Gregory Peck	1947	1948
Ingrid Bergman	1944	1945
Ingrid Bergman	1945	1946
Irene Dunne	1937	1938
Jack Lemmon	1960	1961
Jack Lemmon	1980	1981
Jack Nicholson	1970	1971
Jack Nicholson	1974	1975
Jack Nicholson	1975	1976
Jack Palance	1953	1954
James Dean	1956	1957
James Stewart	1940	1941
Jane Fonda	1978	1979
Jane Fonda	1979	1980
Jason Robards	1977	1978
Jeff Bridges	2010	2011
Jennifer Jones	1944	1945
Jennifer Jones	1945	1946
Jennifer Jones	1946	1947
Jennifer Lawrence	2013	2014
Jeremy Renner	2010	2011
Jessica Chastain	2012	2013
Jessica Lange	1985	1986
Jill Clayburgh	1979	1980
Joan Allen	1996	1997
Joan Fontaine	1941	1942
John Cassavetes	1968	1969
John Lithgow	1983	1984
Johnny Depp	2004	2005
Judi Dench	1998	1999
Judi Dench	2001	2002
Judi Dench	2006	2007
Julia Roberts	1990	1991
Julie Andrews	1965	1966
Katharine Hepburn	1956	1957
Katharine Hepburn	1968	1969
Laurence Olivier	1940	1941
Lee Grant	1976	1977
Luise Rainer	1937	1938
Madeline Kahn	1974	1975
Marie Dressler	1931	1932
Mark Ruffalo	2015	2016
Marlon Brando	1952	1953
Marlon Brando	1953	1954
Marlon Brando	1954	1955
Marlon Brando	1973	1974
Martin Landau	1989	1990
Meryl Streep	1979	1980
Meryl Streep	1982	1983
Meryl Streep	1983	1984
Meryl Streep	1988	1989
Meryl Streep	1999	2000
Meryl Streep	2009	2010
Meryl Streep	2014	2015
Meryl Streep	2017	2018
Michelle Pfeiffer	1989	1990
Michelle Williams	2011	2012
Nicole Kidman	2002	2003
Norma Shearer	1930	1931
Octavia Spencer	2017	2018
Olivia Colman	2021	2022
Olivia de Havilland	1949	1950
Paul Muni	1936	1937
Paul Muni	1937	1938
Paul Newman	1982	1983
Penélope Cruz	2009	2010
Peter Falk	1961	1962
Peter O'Toole	1969	1970
Philip Seymour Hoffman	2008	2009
Renée Zellweger	2002	2003
Renée Zellweger	2003	2004
Rex Harrison	1964	1965
Richard Burton	1953	1954
Richard Burton	1965	1966
Richard Burton	1966	1967
Robert De Niro	1991	1992
Robert Donat	1939	1940
Robert Duvall	1980	1981
Robert Duvall	1998	1999
Rosalind Russell	1947	1948
Russell Crowe	2000	2001
Russell Crowe	2001	2002
Ruth Chatterton	1929	1930
Sam Rockwell	2018	2019
Spencer Tracy	1937	1938
Spencer Tracy	1938	1939
Spencer Tracy	1961	1962
Susan Sarandon	1992	1993
Susan Sarandon	1995	1996
Teresa Wright	1942	1943
Thelma Ritter	1951	1952
Thelma Ritter	1952	1953
Thelma Ritter	1953	1954
Timothée Chalamet	2025	2026
Tom Hanks	1994	1995
Walter Brennan	1941	1942
Walter Huston	1942	1943
Walter Pidgeon	1943	1944
Willem Dafoe	2018	2019
William Hurt	1986	1987
William Hurt	1987	1988
Winona Ryder	1994	1995
Woody Allen	1978	1979
```

```sql
SELECT DISTINCT 
    a1.nome_indicado,
    a1.ano_cerimonia AS ano_atual,
    a2.ano_cerimonia AS ano_seguinte
FROM indicados_ao_oscar a1
INNER JOIN indicados_ao_oscar a2 
    ON a1.nome_indicado = a2.nome_indicado 
    AND a2.ano_cerimonia = a1.ano_cerimonia + 1
WHERE a1.categoria LIKE '%ACTOR%' OR a1.categoria LIKE '%ACTRESS%'
ORDER BY a1.nome_indicado, a1.ano_cerimonia;
```

**10.5** Qual a média de indicações por cerimônia ao longo da história?

R: A média é 112.03%

```sql
SELECT 
    ROUND(AVG(total_por_ano), 2) AS media_indicacoes_por_cerimonia
FROM (
    SELECT 
        ano_cerimonia,
        COUNT(*) AS total_por_ano
    FROM indicados_ao_oscar
    GROUP BY ano_cerimonia
) AS sub;
```

**10.6** Identifique "surpresas" - indicados em categorias principais (ACTOR, ACTRESS, BEST PICTURE) cujo filme só teve uma indicação.

R:
```
Ano cerimonia | Categoria | Nome indicado | Nome FIlme
1928	ACTOR	Richard Barthelmess	The Noose
1928	ACTRESS	Louise Dresser	A Ship Comes In
1928	ACTRESS	Gloria Swanson	Sadie Thompson
1928	OUTSTANDING PICTURE	The Caddo Company	The Racket
1929	ACTOR	George Bancroft	Thunderbolt
1929	ACTOR	Paul Muni	The Valiant
1929	ACTRESS	Betty Compson	The Barker
1929	ACTRESS	Jeanne Eagels	The Letter
1929	ACTRESS	Mary Pickford	Coquette
1929	OUTSTANDING PICTURE	Metro-Goldwyn-Mayer	Hollywood Revue
1930	ACTOR	George Arliss	The Green Goddess
1930	ACTOR	Maurice Chevalier	The Big Pond
1930	ACTOR	Lawrence Tibbett	The Rogue Song
1930	ACTRESS	Nancy Carroll	The Devil's Holiday
1930	ACTRESS	Ruth Chatterton	Sarah and Son
1930	ACTRESS	Norma Shearer	Their Own Desire
1930	ACTRESS	Gloria Swanson	The Trespasser
1931	ACTOR	Fredric March	The Royal Family of Broadway
1931	ACTRESS	Marie Dressler	Min and Bill
1932	ACTRESS	Marie Dressler	Emma
1932	ACTRESS	Helen Hayes	The Sin of Madelon Claudet
1933	ACTOR	Leslie Howard	Berkeley Square
1933	ACTRESS	Katharine Hepburn	Morning Glory
1935	ACTRESS	Bette Davis	Of Human Bondage
1936	ACTOR	Paul Muni	Black Fury
1936	ACTRESS	Elisabeth Bergner	Escape Me Never
1936	ACTRESS	Claudette Colbert	Private Worlds
1936	ACTRESS	Bette Davis	Dangerous
1936	ACTRESS	Miriam Hopkins	Becky Sharp
1937	ACTRESS	Gladys George	Valiant Is the Word for Carrie
1938	ACTRESS	Greta Garbo	Camille
1939	ACTRESS	Fay Bainter	White Banners
1939	ACTRESS	Margaret Sullavan	Three Comrades
1942	ACTOR	Cary Grant	Penny Serenade
1943	ACTRESS	Rosalind Russell	My Sister Eileen
1944	ACTRESS	Joan Fontaine	The Constant Nymph
1947	ACTRESS	Rosalind Russell	Sister Kenny
1948	ACTRESS	Joan Crawford	Possessed
1949	ACTOR	Clifton Webb	Sitting Pretty
1949	ACTRESS	Barbara Stanwyck	Sorry, Wrong Number
1950	ACTOR	Richard Todd	The Hasty Heart
1950	ACTRESS	Deborah Kerr	Edward, My Son
1951	ACTOR	José Ferrer	Cyrano de Bergerac
1953	ACTRESS	Bette Davis	The Star
1953	ACTRESS	Julie Harris	The Member of the Wedding
1955	ACTOR	Dan O'Herlihy	Adventures of Robinson Crusoe
1955	ACTRESS	Jane Wyman	Magnificent Obsession
1957	ACTOR	Sir Laurence Olivier	Richard III
1958	ACTOR	Anthony Franciosa	A Hatful of Rain
1958	ACTRESS	Joanne Woodward	The Three Faces of Eve
1961	ACTOR	Laurence Olivier	The Entertainer
1962	ACTOR	Stuart Whitman	The Mark
1962	ACTRESS	Sophia Loren	Two Women
1963	ACTRESS	Katharine Hepburn	Long Day's Journey into Night
1964	ACTRESS	Leslie Caron	The L-Shaped Room
1965	ACTRESS	Anne Bancroft	The Pumpkin Eater
1965	ACTRESS	Sophia Loren	Marriage Italian Style
1965	ACTRESS	Kim Stanley	Seance on a Wet Afternoon
1966	ACTOR	Rod Steiger	The Pawnbroker
1967	ACTRESS	Ida Kaminska	The Shop on Main Street
1968	ACTRESS	Dame Edith Evans	The Whisperers
1968	ACTRESS	Audrey Hepburn	Wait until Dark
1969	ACTOR	Alan Bates	The Fixer
1969	ACTOR	Cliff Robertson	Charly
1969	ACTRESS	Vanessa Redgrave	Isadora
1971	ACTRESS	Carrie Snodgress	Diary of a Mad Housewife
1972	ACTRESS	Julie Christie	McCabe & Mrs. Miller
1973	ACTOR	Peter O'Toole	The Ruling Class
1975	ACTRESS	Diahann Carroll	Claudine
1976	ACTOR	Maximilian Schell	The Man in the Glass Booth
1976	ACTOR	James Whitmore	Give 'em Hell, Harry!
1976	ACTRESS	Isabelle Adjani	The Story of Adele H.
1976	ACTRESS	Glenda Jackson	Hedda
1976	ACTRESS	Carol Kane	Hester Street
2025	ACTRESS	Demi Moore	The Substance
2025	ACTRESS	Fernanda Torres	I'm Still Here
2026	ACTOR	Ethan Hawke	Blue Moon
2026	ACTOR	Wagner Moura	The Secret Agent
2026	ACTRESS	Jessie Buckley	Hamnet
2026	ACTRESS	Rose Byrne	If I Had Legs I'd Kick You
2026	ACTRESS	Kate Hudson	Song Sung Blue
2025	BEST PICTURE	Duna: Parte 2	Duna: Parte 2
2025	BEST PICTURE	Nickel Boys	Nickel Boys
2026	BEST PICTURE	F1: O Filme	F1: O Filme
2026	BEST PICTURE	Sonhos de Trem	Sonhos de Trem
```

```sql
SELECT DISTINCT 
    i.ano_cerimonia,
    i.categoria,
    i.nome_indicado,
    i.nome_filme
FROM indicados_ao_oscar i
INNER JOIN (
    SELECT nome_filme, ano_cerimonia
    FROM indicados_ao_oscar
    GROUP BY nome_filme, ano_cerimonia
    HAVING COUNT(*) = 1
) AS filme_unico 
    ON i.nome_filme = filme_unico.nome_filme 
    AND i.ano_cerimonia = filme_unico.ano_cerimonia
WHERE i.categoria IN ('ACTOR', 'ACTRESS', 'BEST PICTURE', 'OUTSTANDING PICTURE');
```

---

## Nível 11: Desafios Complexos

**11.1** Crie um ranking dos 10 filmes mais premiados da história (que ganharam mais Oscars).

R:
```
Nome Filme | Total de Oscars
Titanic	12
Ben-Hur	11
The Lord of the Rings: The Return of the King	11
West Side Story	11
Gigi	9
The English Patient	9
The Last Emperor	9
Amadeus	8
Cabaret	8
From Here to Eternity	8
```

```sql
SELECT 
    nome_filme,
    COUNT(*) AS total_oscars
FROM indicados_ao_oscar
WHERE vencedor = TRUE
  AND nome_filme IS NOT NULL 
  AND nome_filme != ''
GROUP BY nome_filme
ORDER BY total_oscars DESC, nome_filme ASC
LIMIT 10;
```

**11.2** Crie um ranking dos 10 artistas (atores/diretores) mais indicados da história, independente da categoria.

R:
```
Nome indicado | Total Indicações
Metro-Goldwyn-Mayer	64
Walt Disney, Producer	59
John Williams	46
Warner Bros.	44
France	37
Alfred Newman	34
Italy	29
Paramount	25
Edith Head	22
Gordon Hollingshead, Producer	22
```

```sql
SELECT 
    nome_indicado,
    COUNT(*) AS total_indicacoes
FROM indicados_ao_oscar
WHERE nome_indicado IS NOT NULL 
  AND nome_indicado != ''
GROUP BY nome_indicado
ORDER BY total_indicacoes DESC
LIMIT 10;
```

**11.3** Encontre "azarões" - artistas com mais de 5 indicações e 0 vitórias.

R:
```
Nome Indicado | Total Indicações | Vitorias
Thomas Newman	14	0
George Folsey	12	0
Music and Lyric by Diane Warren	11	0
Paramount Studio Sound Department, Loren L. Ryder, Sound Director	10	0
Israel	10	0
Walter Lantz, Producer	10	0
Randy Newman	9	0
Belgium	8	0
Peter O'Toole	8	0
Glenn Close	8	0
Robert Emmett Dolan	8	0
Bill Thomas	7	0
James Newton Howard	7	0
Richard Burton	7	0
George Pal, Producer	7	0
Walter Plunkett	6	0
Norway	6	0
Wylie Stateman	6	0
Gerry Hambling	6	0
Ernest Haller	6	0
Russell Harlan	6	0
Samuel Goldwyn Studio Sound Department, Thomas T. Moulton, Sound Director	6	0
Paul Thomas Anderson	6	0
Caleb Deschanel	6	0
Patricia Norris	6	0
Herbert Morgan, Producer	6	0
Samuel Goldwyn Studio Sound Department, Gordon E. Sawyer, Sound Director	6	0
Edward Cronjager	6	0
Stanley Kramer, Producer	6	0
Bruno Delbonnel	6	0
Yugoslavia	6	0
Republic Studio Sound Department, Daniel J. Bloomberg, Sound Director	6	0
Leon Schlesinger, Producer	6	0
Amy Adams	6	0
Thelma Ritter	6	0
RKO Radio Studio Sound Department, John Aalberg, Sound Director	6	0
```

```sql
SELECT 
    nome_indicado,
    COUNT(*) AS total_indicacoes,
    SUM(CASE WHEN vencedor = TRUE THEN 1 ELSE 0 END) AS total_vitorias
FROM indicados_ao_oscar
WHERE nome_indicado IS NOT NULL 
  AND nome_indicado != ''
GROUP BY nome_indicado
HAVING total_indicacoes > 5 AND total_vitorias = 0
ORDER BY total_indicacoes DESC;
```

**11.4** Qual categoria tem a maior concentração de vitórias (menos vencedores diferentes ao longo do tempo)?

R:
```
Categoria | Total de vencedores Unicos | Total Premios 
HONORARY AWARD	133	133
DIRECTING	74	96
FILM EDITING	80	90
ACTOR IN A SUPPORTING ROLE	81	90
ACTRESS IN A SUPPORTING ROLE	88	90
DOCUMENTARY (Short Subject)	78	80
DOCUMENTARY (Feature)	77	79
CINEMATOGRAPHY	59	70
FOREIGN LANGUAGE FILM	28	63
BEST PICTURE	62	63
COSTUME DESIGN	41	59
ART DIRECTION	57	59
SPECIAL AWARD	56	56
ACTRESS	42	51
ACTOR	47	51
SHORT FILM (Animated)	47	50
SHORT FILM (Live Action)	50	50
MUSIC (Original Score)	39	49
MUSIC (Original Song)	45	49
SOUND	47	49
ACTRESS IN A LEADING ROLE	41	48
ACTOR IN A LEADING ROLE	43	48
JEAN HERSHOLT HUMANITARIAN AWARD	39	44
VISUAL EFFECTS	43	43
SHORT SUBJECT (Cartoon)	18	39
IRVING G. THALBERG MEMORIAL AWARD	36	39
MUSIC (Song)	31	36
WRITING (Original Screenplay)	32	32
MAKEUP	28	30
SOUND RECORDING	18	28
CINEMATOGRAPHY (Black-and-White)	22	27
CINEMATOGRAPHY (Color)	24	27
SPECIAL EFFECTS	24	25
ART DIRECTION (Black-and-White)	25	25
ART DIRECTION (Color)	25	25
ANIMATED FEATURE FILM	22	24
WRITING (Screenplay Written Directly for the Screen)	24	24
WRITING (Adapted Screenplay)	22	22
SHORT SUBJECT (Two-reel)	10	21
SHORT SUBJECT (One-reel)	17	21
SOUND EDITING	17	21
WRITING (Screenplay)	19	21
MUSIC (Scoring of a Musical Picture)	18	20
MUSIC (Music Score of a Dramatic or Comedy Picture)	13	19
WRITING (Screenplay--based on material from another medium)	18	19
BEST MOTION PICTURE	14	18
COSTUME DESIGN (Black-and-White)	13	17
SOUND MIXING	16	17
COSTUME DESIGN (Color)	16	17
SHORT SUBJECT (Live Action)	17	17
SOUND EFFECTS EDITING	15	16
WRITING (Screenplay Based on Material from Another Medium)	13	13
MAKEUP AND HAIRSTYLING	12	12
WRITING (Story and Screenplay--written directly for the screen)	12	12
PRODUCTION DESIGN	12	12
WRITING (Original Story)	12	12
OUTSTANDING PRODUCTION	7	11
WRITING (Screenplay Based on Material Previously Produced or Published)	11	11
ASSISTANT DIRECTOR	11	11
WRITING (Motion Picture Story)	9	10
SPECIAL ACHIEVEMENT AWARD (Visual Effects)	9	9
MUSIC (Scoring)	7	8
SPECIAL VISUAL EFFECTS	8	8
MUSIC (Original Dramatic Score)	8	8
WRITING (Story and Screenplay)	7	7
MUSIC (Scoring of Music--adaptation or treatment)	5	6
INTERNATIONAL FEATURE FILM	6	6
MUSIC (Song--Original for the Picture)	5	5
WRITING (Adaptation)	5	5
HONORARY FOREIGN LANGUAGE FILM AWARD	5	5
WRITING (Original Motion Picture Story)	5	5
SOUND EFFECTS	5	5
MUSIC (Music Score--substantially original)	3	4
WRITING (Story and Screenplay--based on factual material or material not previously published or produced)	4	4
SHORT SUBJECT (Comedy)	4	4
SHORT SUBJECT (Novelty)	4	4
SPECIAL ACHIEVEMENT AWARD (Sound Effects Editing)	4	4
DOCUMENTARY	4	4
MUSIC (Original Musical or Comedy Score)	4	4
MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)	3	3
SPECIAL ACHIEVEMENT AWARD	3	3
OUTSTANDING MOTION PICTURE	3	3
DANCE DIRECTION	3	3
SHORT SUBJECT (Animated)	3	3
MUSIC (Original Score--for a motion picture [not a musical])	2	2
DOCUMENTARY FEATURE FILM	2	2
MUSIC (Original Song Score and Its Adaptation -or- Adaptation Score)	2	2
DOCUMENTARY SHORT FILM	2	2
SHORT SUBJECT (Color)	2	2
MUSIC (Original Song Score and Its Adaptation or Adaptation Score)	2	2
WRITING	2	2
MUSIC (Original Song Score)	2	2
OUTSTANDING PICTURE	2	2
WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)	2	2
MUSIC (Score of a Musical Picture--original or adaptation)	2	2
MUSIC (Original Music Score)	2	2
MUSIC (Scoring: Adaptation and Original Song Score)	2	2
SPECIAL FOREIGN LANGUAGE FILM AWARD	2	2
WRITING (Screenplay Adapted from Other Material)	2	2
UNIQUE AND ARTISTIC PICTURE	1	1
WRITING (Story and Screenplay--based on material not previously published or produced)	1	1
ENGINEERING EFFECTS	1	1
MUSIC (Adaptation Score)	1	1
MUSIC (Original Song Score or Adaptation Score)	1	1
WRITING (Title Writing)	1	1
SPECIAL ACHIEVEMENT AWARD (Sound Editing)	1	1
MUSIC (Music Score of a Dramatic Picture)	1	1
GORDON E. SAWYER AWARD	1	1
AWARD OF COMMENDATION	1	1
DIRECTING (Comedy Picture)	1	1
SPECIAL ACHIEVEMENT AWARD (Sound Effects)	1	1
DIRECTING (Dramatic Picture)	1	1
WRITING (Screenplay--Adapted)	1	1
SHORT FILM (Dramatic Live Action)	1	1
WRITING (Screenplay--Original)	1	1
```

```sql
SELECT 
    categoria,
    COUNT(DISTINCT nome_indicado) AS total_vencedores_unicos,
    COUNT(*) AS total_premios_concedidos
FROM indicados_ao_oscar
WHERE vencedor = TRUE
GROUP BY categoria
ORDER BY total_vencedores_unicos ASC;
```

**11.5** Calcule a "competitividade" de cada categoria (média de indicados por cerimônia).

R:
```
Categora   |   Média
DOCUMENTARY	25.00
MUSIC (Music Score of a Dramatic Picture)	20.00
OUTSTANDING MOTION PICTURE	10.00
OUTSTANDING PRODUCTION	9.27
MUSIC (Scoring)	8.00
MUSIC (Music Score of a Dramatic or Comedy Picture)	7.79
ASSISTANT DIRECTOR	7.00
DANCE DIRECTION	7.00
SOUND RECORDING	6.96
MUSIC (Scoring of a Musical Picture)	6.35
BEST PICTURE	6.11
MUSIC (Song)	5.97
CINEMATOGRAPHY (Black-and-White)	5.96
ART DIRECTION (Black-and-White)	5.52
MUSIC (Original Score)	5.51
WRITING	5.50
ART DIRECTION	5.20
MUSIC (Original Dramatic Score)	5.13
ACTOR IN A LEADING ROLE	5.00
COSTUME DESIGN	5.00
PRODUCTION DESIGN	5.00
SOUND MIXING	5.00
WRITING (Motion Picture Story)	5.00
WRITING (Screenplay--based on material from another medium)	5.00
ACTOR IN A SUPPORTING ROLE	5.00
WRITING (Original Motion Picture Story)	5.00
WRITING (Screenplay Adapted from Other Material)	5.00
WRITING (Screenplay--Original)	5.00
DOCUMENTARY FEATURE FILM	5.00
INTERNATIONAL FEATURE FILM	5.00
MUSIC (Music Score--substantially original)	5.00
WRITING (Original Screenplay)	5.00
WRITING (Screenplay Based on Material from Another Medium)	5.00
WRITING (Story and Screenplay)	5.00
ACTRESS IN A LEADING ROLE	5.00
BEST MOTION PICTURE	5.00
DOCUMENTARY SHORT FILM	5.00
WRITING (Screenplay Based on Material Previously Produced or Published)	5.00
WRITING (Story and Screenplay--based on factual material or material not previously published or produced)	5.00
ACTRESS IN A SUPPORTING ROLE	5.00
MUSIC (Original Music Score)	5.00
MUSIC (Song--Original for the Picture)	5.00
SOUND	5.00
WRITING (Screenplay Written Directly for the Screen)	5.00
WRITING (Story and Screenplay--based on material not previously published or produced)	5.00
FILM EDITING	5.00
MUSIC (Original Musical or Comedy Score)	5.00
MUSIC (Score of a Musical Picture--original or adaptation)	5.00
WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)	5.00
WRITING (Story and Screenplay--written directly for the screen)	5.00
FOREIGN LANGUAGE FILM	5.00
CINEMATOGRAPHY (Color)	5.00
MUSIC (Original Score--for a motion picture [not a musical])	5.00
MUSIC (Scoring of Music--adaptation or treatment)	5.00
WRITING (Adapted Screenplay)	5.00
WRITING (Screenplay--Adapted)	5.00
WRITING (Screenplay)	4.95
DIRECTING	4.94
ACTRESS	4.92
CINEMATOGRAPHY	4.90
ACTOR	4.84
MUSIC (Original Song)	4.80
DOCUMENTARY (Short Subject)	4.78
SHORT FILM (Live Action)	4.61
COSTUME DESIGN (Black-and-White)	4.53
COSTUME DESIGN (Color)	4.53
ART DIRECTION (Color)	4.48
DOCUMENTARY (Feature)	4.42
ANIMATED FEATURE FILM	4.36
WRITING (Original Story)	4.33
SHORT SUBJECT (Cartoon)	4.33
SHORT FILM (Animated)	4.30
SOUND EDITING	4.30
SHORT SUBJECT (One-reel)	4.29
SHORT SUBJECT (Live Action)	4.00
MUSIC (Scoring: Adaptation and Original Song Score)	4.00
MUSIC (Original Song Score)	4.00
OUTSTANDING PICTURE	4.00
SHORT SUBJECT (Two-reel)	3.86
MAKEUP AND HAIRSTYLING	3.83
SPECIAL EFFECTS	3.72
VISUAL EFFECTS	3.60
WRITING (Adaptation)	3.40
SHORT SUBJECT (Comedy)	3.25
MUSIC (Original Song Score and Its Adaptation -or- Adaptation Score)	3.00
MUSIC (Original Song Score and Its Adaptation or Adaptation Score)	3.00
SHORT SUBJECT (Novelty)	3.00
MUSIC (Original Song Score or Adaptation Score)	3.00
MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)	3.00
SHORT FILM (Dramatic Live Action)	3.00
UNIQUE AND ARTISTIC PICTURE	3.00
ENGINEERING EFFECTS	3.00
SHORT SUBJECT (Animated)	3.00
DIRECTING (Dramatic Picture)	3.00
SHORT SUBJECT (Color)	3.00
WRITING (Title Writing)	3.00
MUSIC (Adaptation Score)	3.00
SPECIAL AWARD	2.95
SOUND EFFECTS EDITING	2.94
MAKEUP	2.90
SPECIAL VISUAL EFFECTS	2.00
DIRECTING (Comedy Picture)	2.00
SOUND EFFECTS	2.00
HONORARY AWARD	1.99
IRVING G. THALBERG MEMORIAL AWARD	1.15
SPECIAL ACHIEVEMENT AWARD (Visual Effects)	1.13
JEAN HERSHOLT HUMANITARIAN AWARD	1.05
HONORARY FOREIGN LANGUAGE FILM AWARD	1.00
SPECIAL FOREIGN LANGUAGE FILM AWARD	1.00
AWARD OF COMMENDATION	1.00
SPECIAL ACHIEVEMENT AWARD	1.00
SPECIAL ACHIEVEMENT AWARD (Sound Editing)	1.00
SPECIAL ACHIEVEMENT AWARD (Sound Effects Editing)	1.00
SPECIAL ACHIEVEMENT AWARD (Sound Effects)	1.00
GORDON E. SAWYER AWARD	1.00
```

```sql
SELECT DISTINCT
    categoria,
    ROUND(AVG(total_indicados), 2) AS media_indicados_por_cerimonia
FROM (
    SELECT 
        categoria,
        ano_cerimonia,
        COUNT(*) AS total_indicados
    FROM indicados_ao_oscar
    GROUP BY categoria, ano_cerimonia
) AS sub
GROUP BY categoria
ORDER BY media_indicados_por_cerimonia DESC;
```

**11.6** Encontre filmes que foram indicados em uma categoria em um ano e ganharam em outra categoria em outro ano.

R:
```
Nome Filme | Ano Indicação | Categoria Indicado | Ano Vitoria | Categoria Vencedor
 A Farewell to Arms	1958	ACTOR IN A SUPPORTING ROLE	1933	CINEMATOGRAPHY
A Farewell to Arms	1958	ACTOR IN A SUPPORTING ROLE	1933	SOUND RECORDING
A Place in the Sun	1961	SHORT SUBJECT (Cartoon)	1952	CINEMATOGRAPHY (Black-and-White)
A Place in the Sun	1961	SHORT SUBJECT (Cartoon)	1952	COSTUME DESIGN (Black-and-White)
A Place in the Sun	1961	SHORT SUBJECT (Cartoon)	1952	DIRECTING
A Place in the Sun	1961	SHORT SUBJECT (Cartoon)	1952	FILM EDITING
A Place in the Sun	1961	SHORT SUBJECT (Cartoon)	1952	MUSIC (Music Score of a Dramatic or Comedy Picture)
A Place in the Sun	1961	SHORT SUBJECT (Cartoon)	1952	WRITING (Screenplay)
A Star Is Born	1977	MUSIC (Original Song Score and Its Adaptation or Adaptation Score)	2019	MUSIC (Original Song)
A Star Is Born	1955	ACTRESS	1938	WRITING (Original Story)
A Star Is Born	2019	CINEMATOGRAPHY	1938	WRITING (Original Story)
A Star Is Born	1977	SOUND	2019	MUSIC (Original Song)
A Star Is Born	1955	ART DIRECTION (Color)	1938	WRITING (Original Story)
A Star Is Born	2019	BEST PICTURE	1938	WRITING (Original Story)
A Star Is Born	1955	COSTUME DESIGN (Color)	1938	WRITING (Original Story)
A Star Is Born	1938	ACTOR	1977	MUSIC (Original Song)
A Star Is Born	2019	SOUND MIXING	1938	WRITING (Original Story)
A Star Is Born	1955	MUSIC (Scoring of a Musical Picture)	1938	WRITING (Original Story)
A Star Is Born	1938	ACTRESS	1977	MUSIC (Original Song)
A Star Is Born	1938	ACTOR	2019	MUSIC (Original Song)
A Star Is Born	1955	MUSIC (Song)	1938	WRITING (Original Story)
A Star Is Born	1938	ASSISTANT DIRECTOR	1977	MUSIC (Original Song)
A Star Is Born	1938	ACTRESS	2019	MUSIC (Original Song)
A Star Is Born	1977	CINEMATOGRAPHY	1938	WRITING (Original Story)
A Star Is Born	1938	DIRECTING	1977	MUSIC (Original Song)
A Star Is Born	1938	ASSISTANT DIRECTOR	2019	MUSIC (Original Song)
A Star Is Born	1977	MUSIC (Original Song Score and Its Adaptation or Adaptation Score)	1938	WRITING (Original Story)
A Star Is Born	2019	ACTOR IN A LEADING ROLE	1977	MUSIC (Original Song)
A Star Is Born	1938	OUTSTANDING PRODUCTION	1977	MUSIC (Original Song)
A Star Is Born	2019	WRITING (Adapted Screenplay)	1938	WRITING (Original Story)
A Star Is Born	1938	DIRECTING	2019	MUSIC (Original Song)
A Star Is Born	2019	ACTOR IN A SUPPORTING ROLE	1977	MUSIC (Original Song)
A Star Is Born	1938	WRITING (Screenplay)	1977	MUSIC (Original Song)
A Star Is Born	1938	OUTSTANDING PRODUCTION	2019	MUSIC (Original Song)
A Star Is Born	2019	ACTRESS IN A LEADING ROLE	1977	MUSIC (Original Song)
A Star Is Born	1955	ACTOR	1977	MUSIC (Original Song)
A Star Is Born	1938	WRITING (Screenplay)	2019	MUSIC (Original Song)
A Star Is Born	2019	CINEMATOGRAPHY	1977	MUSIC (Original Song)
A Star Is Born	1955	ACTRESS	1977	MUSIC (Original Song)
A Star Is Born	1955	ACTOR	2019	MUSIC (Original Song)
A Star Is Born	2019	BEST PICTURE	1977	MUSIC (Original Song)
A Star Is Born	1955	ART DIRECTION (Color)	1977	MUSIC (Original Song)
A Star Is Born	1955	ACTRESS	2019	MUSIC (Original Song)
A Star Is Born	2019	SOUND MIXING	1977	MUSIC (Original Song)
A Star Is Born	1955	COSTUME DESIGN (Color)	1977	MUSIC (Original Song)
A Star Is Born	1955	ART DIRECTION (Color)	2019	MUSIC (Original Song)
A Star Is Born	2019	WRITING (Adapted Screenplay)	1977	MUSIC (Original Song)
A Star Is Born	1955	MUSIC (Scoring of a Musical Picture)	1977	MUSIC (Original Song)
A Star Is Born	1955	COSTUME DESIGN (Color)	2019	MUSIC (Original Song)
A Star Is Born	1955	MUSIC (Song)	1977	MUSIC (Original Song)
A Star Is Born	2019	ACTOR IN A LEADING ROLE	1938	WRITING (Original Story)
A Star Is Born	1977	SOUND	1938	WRITING (Original Story)
A Star Is Born	1955	MUSIC (Scoring of a Musical Picture)	2019	MUSIC (Original Song)
A Star Is Born	2019	ACTOR IN A SUPPORTING ROLE	1938	WRITING (Original Story)
A Star Is Born	1955	MUSIC (Song)	2019	MUSIC (Original Song)
A Star Is Born	1955	ACTOR	1938	WRITING (Original Story)
A Star Is Born	2019	ACTRESS IN A LEADING ROLE	1938	WRITING (Original Story)
A Star Is Born	1977	CINEMATOGRAPHY	2019	MUSIC (Original Song)
Alice in Wonderland	1952	MUSIC (Scoring of a Musical Picture)	2011	ART DIRECTION
Alice in Wonderland	1952	MUSIC (Scoring of a Musical Picture)	2011	COSTUME DESIGN
All Quiet on the Western Front	1930	WRITING	2023	CINEMATOGRAPHY
All Quiet on the Western Front	2023	BEST PICTURE	1930	OUTSTANDING PRODUCTION
All Quiet on the Western Front	1930	CINEMATOGRAPHY	2023	INTERNATIONAL FEATURE FILM
All Quiet on the Western Front	2023	SOUND	1930	OUTSTANDING PRODUCTION
All Quiet on the Western Front	1930	WRITING	2023	INTERNATIONAL FEATURE FILM
All Quiet on the Western Front	2023	VISUAL EFFECTS	1930	OUTSTANDING PRODUCTION
All Quiet on the Western Front	1930	CINEMATOGRAPHY	2023	MUSIC (Original Score)
All Quiet on the Western Front	2023	WRITING (Adapted Screenplay)	1930	OUTSTANDING PRODUCTION
All Quiet on the Western Front	1930	WRITING	2023	MUSIC (Original Score)
All Quiet on the Western Front	1930	CINEMATOGRAPHY	2023	PRODUCTION DESIGN
All Quiet on the Western Front	1930	WRITING	2023	PRODUCTION DESIGN
All Quiet on the Western Front	2023	MAKEUP AND HAIRSTYLING	1930	DIRECTING
All Quiet on the Western Front	2023	BEST PICTURE	1930	DIRECTING
All Quiet on the Western Front	2023	SOUND	1930	DIRECTING
All Quiet on the Western Front	2023	VISUAL EFFECTS	1930	DIRECTING
All Quiet on the Western Front	2023	WRITING (Adapted Screenplay)	1930	DIRECTING
All Quiet on the Western Front	1930	CINEMATOGRAPHY	2023	CINEMATOGRAPHY
All Quiet on the Western Front	2023	MAKEUP AND HAIRSTYLING	1930	OUTSTANDING PRODUCTION
Amarcord	1976	DIRECTING	1975	FOREIGN LANGUAGE FILM
Amarcord	1976	WRITING (Original Screenplay)	1975	FOREIGN LANGUAGE FILM
Anastasia	1998	MUSIC (Original Musical or Comedy Score)	1957	ACTRESS
Anastasia	1998	MUSIC (Original Song)	1957	ACTRESS
Beauty and the Beast	2018	COSTUME DESIGN	1992	MUSIC (Original Score)
Beauty and the Beast	2018	PRODUCTION DESIGN	1992	MUSIC (Original Score)
Beauty and the Beast	2018	COSTUME DESIGN	1992	MUSIC (Original Song)
Beauty and the Beast	2018	PRODUCTION DESIGN	1992	MUSIC (Original Song)
Charade	1964	MUSIC (Song)	1985	SHORT FILM (Animated)
Cimarron	1961	ART DIRECTION (Color)	1931	ART DIRECTION
Cimarron	1961	SOUND	1931	ART DIRECTION
Cimarron	1961	ART DIRECTION (Color)	1931	OUTSTANDING PRODUCTION
Cimarron	1961	SOUND	1931	OUTSTANDING PRODUCTION
Cimarron	1961	ART DIRECTION (Color)	1931	WRITING (Adaptation)
Cimarron	1961	SOUND	1931	WRITING (Adaptation)
Cleopatra	1935	SOUND RECORDING	1964	ART DIRECTION (Color)
Cleopatra	1935	ASSISTANT DIRECTOR	1964	CINEMATOGRAPHY (Color)
Cleopatra	1935	FILM EDITING	1964	CINEMATOGRAPHY (Color)
Cleopatra	1964	ACTOR	1935	CINEMATOGRAPHY
Cleopatra	1935	OUTSTANDING PRODUCTION	1964	CINEMATOGRAPHY (Color)
Cleopatra	1964	FILM EDITING	1935	CINEMATOGRAPHY
Cleopatra	1935	SOUND RECORDING	1964	CINEMATOGRAPHY (Color)
Cleopatra	1935	ASSISTANT DIRECTOR	1964	COSTUME DESIGN (Color)
Cleopatra	1964	MUSIC (Music Score--substantially original)	1935	CINEMATOGRAPHY
Cleopatra	1935	FILM EDITING	1964	COSTUME DESIGN (Color)
Cleopatra	1964	BEST PICTURE	1935	CINEMATOGRAPHY
Cleopatra	1935	OUTSTANDING PRODUCTION	1964	COSTUME DESIGN (Color)
Cleopatra	1964	SOUND	1935	CINEMATOGRAPHY
Cleopatra	1935	SOUND RECORDING	1964	COSTUME DESIGN (Color)
Cleopatra	1935	ASSISTANT DIRECTOR	1964	SPECIAL EFFECTS
Cleopatra	1935	FILM EDITING	1964	SPECIAL EFFECTS
Cleopatra	1935	OUTSTANDING PRODUCTION	1964	SPECIAL EFFECTS
Cleopatra	1935	SOUND RECORDING	1964	SPECIAL EFFECTS
Cleopatra	1935	ASSISTANT DIRECTOR	1964	ART DIRECTION (Color)
Cleopatra	1935	FILM EDITING	1964	ART DIRECTION (Color)
Cleopatra	1935	OUTSTANDING PRODUCTION	1964	ART DIRECTION (Color)
Cyrano de Bergerac	1991	ACTOR IN A LEADING ROLE	1951	ACTOR
Cyrano de Bergerac	1991	ART DIRECTION	1951	ACTOR
Cyrano de Bergerac	1991	FOREIGN LANGUAGE FILM	1951	ACTOR
Cyrano de Bergerac	1991	MAKEUP	1951	ACTOR
Day for Night	1975	ACTRESS IN A SUPPORTING ROLE	1974	FOREIGN LANGUAGE FILM
Day for Night	1975	DIRECTING	1974	FOREIGN LANGUAGE FILM
Day for Night	1975	WRITING (Original Screenplay)	1974	FOREIGN LANGUAGE FILM
Dr. Jekyll and Mr. Hyde	1942	CINEMATOGRAPHY (Black-and-White)	1932	ACTOR
Dr. Jekyll and Mr. Hyde	1942	FILM EDITING	1932	ACTOR
Dr. Jekyll and Mr. Hyde	1942	MUSIC (Music Score of a Dramatic Picture)	1932	ACTOR
Dune	1985	SOUND	2022	CINEMATOGRAPHY
Dune	1985	SOUND	2022	FILM EDITING
Dune	1985	SOUND	2022	MUSIC (Original Score)
Dune	1985	SOUND	2022	PRODUCTION DESIGN
Dune	1985	SOUND	2022	SOUND
Dune	1985	SOUND	2022	VISUAL EFFECTS
Emma	2021	COSTUME DESIGN	1997	MUSIC (Original Musical or Comedy Score)
Emma	2021	MAKEUP AND HAIRSTYLING	1997	MUSIC (Original Musical or Comedy Score)
Emma	1932	ACTRESS	1997	MUSIC (Original Musical or Comedy Score)
Goodbye, Mr. Chips	1970	ACTOR	1940	ACTOR
Goodbye, Mr. Chips	1970	MUSIC (Score of a Musical Picture--original or adaptation)	1940	ACTOR
Grand Canyon	1992	WRITING (Screenplay Written Directly for the Screen)	1959	SHORT SUBJECT (Live Action)
Hamlet	1997	MUSIC (Original Dramatic Score)	1949	ACTOR
Hamlet	1997	ART DIRECTION	1949	BEST MOTION PICTURE
Hamlet	1997	WRITING (Screenplay Based on Material Previously Produced or Published)	1949	ACTOR
Hamlet	1997	COSTUME DESIGN	1949	BEST MOTION PICTURE
Hamlet	1991	ART DIRECTION	1949	ART DIRECTION (Black-and-White)
Hamlet	1997	MUSIC (Original Dramatic Score)	1949	BEST MOTION PICTURE
Hamlet	1991	COSTUME DESIGN	1949	ART DIRECTION (Black-and-White)
Hamlet	1997	WRITING (Screenplay Based on Material Previously Produced or Published)	1949	BEST MOTION PICTURE
Hamlet	1997	ART DIRECTION	1949	ART DIRECTION (Black-and-White)
Hamlet	1997	COSTUME DESIGN	1949	ART DIRECTION (Black-and-White)
Hamlet	1997	MUSIC (Original Dramatic Score)	1949	ART DIRECTION (Black-and-White)
Hamlet	1997	WRITING (Screenplay Based on Material Previously Produced or Published)	1949	ART DIRECTION (Black-and-White)
Hamlet	1991	ART DIRECTION	1949	COSTUME DESIGN (Black-and-White)
Hamlet	1991	COSTUME DESIGN	1949	COSTUME DESIGN (Black-and-White)
Hamlet	1997	ART DIRECTION	1949	COSTUME DESIGN (Black-and-White)
Hamlet	1997	COSTUME DESIGN	1949	COSTUME DESIGN (Black-and-White)
Hamlet	1991	ART DIRECTION	1949	ACTOR
Hamlet	1997	MUSIC (Original Dramatic Score)	1949	COSTUME DESIGN (Black-and-White)
Hamlet	1991	COSTUME DESIGN	1949	ACTOR
Hamlet	1997	WRITING (Screenplay Based on Material Previously Produced or Published)	1949	COSTUME DESIGN (Black-and-White)
Hamlet	1997	ART DIRECTION	1949	ACTOR
Hamlet	1991	ART DIRECTION	1949	BEST MOTION PICTURE
Hamlet	1997	COSTUME DESIGN	1949	ACTOR
Hamlet	1991	COSTUME DESIGN	1949	BEST MOTION PICTURE
Heaven Can Wait	1944	OUTSTANDING MOTION PICTURE	1979	ART DIRECTION
Heaven Can Wait	1944	CINEMATOGRAPHY (Color)	1979	ART DIRECTION
Heaven Can Wait	1944	DIRECTING	1979	ART DIRECTION
Henry V	1947	ACTOR	1990	COSTUME DESIGN
Henry V	1947	ART DIRECTION (Color)	1990	COSTUME DESIGN
Henry V	1947	MUSIC (Music Score of a Dramatic or Comedy Picture)	1990	COSTUME DESIGN
Henry V	1947	BEST MOTION PICTURE	1990	COSTUME DESIGN
Investigation of a Citizen above Suspicion	1972	WRITING (Story and Screenplay--based on factual material or material not previously published or produced)	1971	FOREIGN LANGUAGE FILM
King Kong	1977	CINEMATOGRAPHY	2006	SOUND EDITING
King Kong	1977	SOUND	2006	SOUND EDITING
King Kong	1977	CINEMATOGRAPHY	2006	SOUND MIXING
King Kong	1977	SOUND	2006	SOUND MIXING
King Kong	1977	CINEMATOGRAPHY	2006	VISUAL EFFECTS
King Kong	1977	SOUND	2006	VISUAL EFFECTS
King Kong	2006	ART DIRECTION	1977	SPECIAL ACHIEVEMENT AWARD (Visual Effects)
Kon-Tiki	2013	FOREIGN LANGUAGE FILM	1952	DOCUMENTARY (Feature)
Les Miserables	1936	FILM EDITING	2013	SOUND MIXING
Les Miserables	1936	OUTSTANDING PRODUCTION	2013	SOUND MIXING
Les Miserables	1936	ASSISTANT DIRECTOR	2013	ACTRESS IN A SUPPORTING ROLE
Les Miserables	1936	CINEMATOGRAPHY	2013	ACTRESS IN A SUPPORTING ROLE
Les Miserables	1936	FILM EDITING	2013	ACTRESS IN A SUPPORTING ROLE
Les Miserables	1936	OUTSTANDING PRODUCTION	2013	ACTRESS IN A SUPPORTING ROLE
Les Miserables	1936	ASSISTANT DIRECTOR	2013	MAKEUP AND HAIRSTYLING
Les Miserables	1936	CINEMATOGRAPHY	2013	MAKEUP AND HAIRSTYLING
Les Miserables	1936	FILM EDITING	2013	MAKEUP AND HAIRSTYLING
Les Miserables	1936	OUTSTANDING PRODUCTION	2013	MAKEUP AND HAIRSTYLING
Les Miserables	1936	ASSISTANT DIRECTOR	2013	SOUND MIXING
Les Miserables	1936	CINEMATOGRAPHY	2013	SOUND MIXING
Les Misérables	2020	INTERNATIONAL FEATURE FILM	2013	ACTRESS IN A SUPPORTING ROLE
Les Misérables	2020	INTERNATIONAL FEATURE FILM	2013	MAKEUP AND HAIRSTYLING
Les Misérables	2020	INTERNATIONAL FEATURE FILM	2013	SOUND MIXING
Little Women	1995	COSTUME DESIGN	2020	COSTUME DESIGN
Little Women	1950	CINEMATOGRAPHY (Color)	1933	WRITING (Adaptation)
Little Women	1995	MUSIC (Original Score)	2020	COSTUME DESIGN
Little Women	1933	DIRECTING	2020	COSTUME DESIGN
Little Women	1933	DIRECTING	1950	ART DIRECTION (Color)
Little Women	1933	OUTSTANDING PRODUCTION	2020	COSTUME DESIGN
Little Women	1933	OUTSTANDING PRODUCTION	1950	ART DIRECTION (Color)
Little Women	1950	CINEMATOGRAPHY (Color)	2020	COSTUME DESIGN
Little Women	1995	ACTRESS IN A LEADING ROLE	1933	WRITING (Adaptation)
Little Women	1995	ACTRESS IN A LEADING ROLE	1950	ART DIRECTION (Color)
Little Women	1995	COSTUME DESIGN	1933	WRITING (Adaptation)
Little Women	1995	COSTUME DESIGN	1950	ART DIRECTION (Color)
Little Women	1995	MUSIC (Original Score)	1933	WRITING (Adaptation)
Little Women	1995	MUSIC (Original Score)	1950	ART DIRECTION (Color)
Little Women	2020	ACTRESS IN A LEADING ROLE	1950	ART DIRECTION (Color)
Little Women	2020	ACTRESS IN A LEADING ROLE	1933	WRITING (Adaptation)
Little Women	2020	ACTRESS IN A SUPPORTING ROLE	1950	ART DIRECTION (Color)
Little Women	2020	ACTRESS IN A SUPPORTING ROLE	1933	WRITING (Adaptation)
Little Women	2020	MUSIC (Original Score)	1950	ART DIRECTION (Color)
Little Women	2020	MUSIC (Original Score)	1933	WRITING (Adaptation)
Little Women	2020	BEST PICTURE	1950	ART DIRECTION (Color)
Little Women	2020	BEST PICTURE	1933	WRITING (Adaptation)
Little Women	2020	WRITING (Adapted Screenplay)	1933	WRITING (Adaptation)
Little Women	2020	WRITING (Adapted Screenplay)	1950	ART DIRECTION (Color)
Little Women	1995	ACTRESS IN A LEADING ROLE	2020	COSTUME DESIGN
Marie Antoinette	1939	ACTOR IN A SUPPORTING ROLE	2007	COSTUME DESIGN
Marie Antoinette	1939	ACTRESS	2007	COSTUME DESIGN
Marie Antoinette	1939	ART DIRECTION	2007	COSTUME DESIGN
Marie Antoinette	1939	MUSIC (Original Score)	2007	COSTUME DESIGN
Men in Black	1935	SHORT SUBJECT (Comedy)	1998	MAKEUP
Mighty Joe Young	1999	VISUAL EFFECTS	1950	SPECIAL EFFECTS
Moulin Rouge	2002	SOUND	1953	COSTUME DESIGN (Color)
Moulin Rouge	1953	BEST MOTION PICTURE	2002	ART DIRECTION
Moulin Rouge	1953	ACTOR	2002	COSTUME DESIGN
Moulin Rouge	1953	ACTRESS IN A SUPPORTING ROLE	2002	COSTUME DESIGN
Moulin Rouge	1953	DIRECTING	2002	COSTUME DESIGN
Moulin Rouge	1953	FILM EDITING	2002	COSTUME DESIGN
Moulin Rouge	2002	ACTRESS IN A LEADING ROLE	1953	ART DIRECTION (Color)
Moulin Rouge	1953	BEST MOTION PICTURE	2002	COSTUME DESIGN
Moulin Rouge	2002	CINEMATOGRAPHY	1953	ART DIRECTION (Color)
Moulin Rouge	2002	FILM EDITING	1953	ART DIRECTION (Color)
Moulin Rouge	2002	MAKEUP	1953	ART DIRECTION (Color)
Moulin Rouge	2002	BEST PICTURE	1953	ART DIRECTION (Color)
Moulin Rouge	2002	SOUND	1953	ART DIRECTION (Color)
Moulin Rouge	2002	ACTRESS IN A LEADING ROLE	1953	COSTUME DESIGN (Color)
Moulin Rouge	2002	CINEMATOGRAPHY	1953	COSTUME DESIGN (Color)
Moulin Rouge	1953	ACTOR	2002	ART DIRECTION
Moulin Rouge	2002	FILM EDITING	1953	COSTUME DESIGN (Color)
Moulin Rouge	1953	ACTRESS IN A SUPPORTING ROLE	2002	ART DIRECTION
Moulin Rouge	2002	MAKEUP	1953	COSTUME DESIGN (Color)
Moulin Rouge	1953	DIRECTING	2002	ART DIRECTION
Moulin Rouge	2002	BEST PICTURE	1953	COSTUME DESIGN (Color)
Moulin Rouge	1953	FILM EDITING	2002	ART DIRECTION
Mutiny on the Bounty	1963	ART DIRECTION (Color)	1936	OUTSTANDING PRODUCTION
Mutiny on the Bounty	1963	CINEMATOGRAPHY (Color)	1936	OUTSTANDING PRODUCTION
Mutiny on the Bounty	1963	FILM EDITING	1936	OUTSTANDING PRODUCTION
Mutiny on the Bounty	1963	MUSIC (Music Score--substantially original)	1936	OUTSTANDING PRODUCTION
Mutiny on the Bounty	1963	MUSIC (Song)	1936	OUTSTANDING PRODUCTION
Mutiny on the Bounty	1963	BEST PICTURE	1936	OUTSTANDING PRODUCTION
Mutiny on the Bounty	1963	SPECIAL EFFECTS	1936	OUTSTANDING PRODUCTION
Pinocchio	2021	COSTUME DESIGN	1941	MUSIC (Original Score)
Pinocchio	2021	MAKEUP AND HAIRSTYLING	1941	MUSIC (Original Score)
Pinocchio	2021	COSTUME DESIGN	1941	MUSIC (Song)
Pinocchio	2021	MAKEUP AND HAIRSTYLING	1941	MUSIC (Song)
Romeo and Juliet	1937	ART DIRECTION	1969	CINEMATOGRAPHY
Romeo and Juliet	1937	OUTSTANDING PRODUCTION	1969	CINEMATOGRAPHY
Romeo and Juliet	1937	ACTOR IN A SUPPORTING ROLE	1969	COSTUME DESIGN
Romeo and Juliet	1937	ACTRESS	1969	COSTUME DESIGN
Romeo and Juliet	1937	ART DIRECTION	1969	COSTUME DESIGN
Romeo and Juliet	1937	OUTSTANDING PRODUCTION	1969	COSTUME DESIGN
Romeo and Juliet	1937	ACTOR IN A SUPPORTING ROLE	1969	CINEMATOGRAPHY
Romeo and Juliet	1937	ACTRESS	1969	CINEMATOGRAPHY
Sabrina	1996	MUSIC (Original Musical or Comedy Score)	1955	COSTUME DESIGN (Black-and-White)
Sabrina	1996	MUSIC (Original Song)	1955	COSTUME DESIGN (Black-and-White)
Scent of a Woman	1976	FOREIGN LANGUAGE FILM	1993	ACTOR IN A LEADING ROLE
Scent of a Woman	1976	WRITING (Screenplay Adapted from Other Material)	1993	ACTOR IN A LEADING ROLE
Spellbound	2003	DOCUMENTARY (Feature)	1946	MUSIC (Music Score of a Dramatic or Comedy Picture)
State Fair	1933	OUTSTANDING PRODUCTION	1946	MUSIC (Song)
State Fair	1933	WRITING (Adaptation)	1946	MUSIC (Song)
Sundays and Cybele	1964	MUSIC (Scoring of Music--adaptation or treatment)	1963	FOREIGN LANGUAGE FILM
Sundays and Cybele	1964	WRITING (Screenplay--based on material from another medium)	1963	FOREIGN LANGUAGE FILM
Superman	1942	SHORT SUBJECT (Cartoon)	1979	SPECIAL ACHIEVEMENT AWARD (Visual Effects)
Tango	1999	FOREIGN LANGUAGE FILM	1983	SHORT FILM (Animated)
The Bridge of San Luis Rey	1945	MUSIC (Music Score of a Dramatic or Comedy Picture)	1929	ART DIRECTION
The Champ	1980	MUSIC (Original Score)	1932	ACTOR
The Champ	1980	MUSIC (Original Score)	1932	WRITING (Original Story)
The Hurricane	2000	ACTOR IN A LEADING ROLE	1938	SOUND RECORDING
The Jungle Book	1968	MUSIC (Song)	2017	VISUAL EFFECTS
The Last of the Mohicans	1937	ASSISTANT DIRECTOR	1993	SOUND
The Lion King	2020	VISUAL EFFECTS	1995	MUSIC (Original Score)
The Lion King	2020	VISUAL EFFECTS	1995	MUSIC (Original Song)
The Merry Widow	1953	ART DIRECTION (Color)	1935	ART DIRECTION
The Merry Widow	1953	COSTUME DESIGN (Color)	1935	ART DIRECTION
The Old Man and the Sea	1959	ACTOR	2000	SHORT FILM (Animated)
The Old Man and the Sea	1959	CINEMATOGRAPHY (Color)	2000	SHORT FILM (Animated)
The Patriot	2001	CINEMATOGRAPHY	1929	WRITING
The Patriot	2001	MUSIC (Original Score)	1929	WRITING
The Patriot	2001	SOUND	1929	WRITING
The Shop on Main Street	1967	ACTRESS	1966	FOREIGN LANGUAGE FILM
The Time Machine	2003	MAKEUP	1961	SPECIAL EFFECTS
Through a Glass Darkly	1963	WRITING (Story and Screenplay--written directly for the screen)	1962	FOREIGN LANGUAGE FILM
Titanic	1954	ART DIRECTION (Black-and-White)	1998	COSTUME DESIGN
Titanic	1998	ACTRESS IN A LEADING ROLE	1954	WRITING (Story and Screenplay)
Titanic	1954	ART DIRECTION (Black-and-White)	1998	DIRECTING
Titanic	1998	ACTRESS IN A SUPPORTING ROLE	1954	WRITING (Story and Screenplay)
Titanic	1954	ART DIRECTION (Black-and-White)	1998	FILM EDITING
Titanic	1998	MAKEUP	1954	WRITING (Story and Screenplay)
Titanic	1954	ART DIRECTION (Black-and-White)	1998	MUSIC (Original Dramatic Score)
Titanic	1954	ART DIRECTION (Black-and-White)	1998	MUSIC (Original Song)
Titanic	1954	ART DIRECTION (Black-and-White)	1998	BEST PICTURE
Titanic	1954	ART DIRECTION (Black-and-White)	1998	SOUND
Titanic	1954	ART DIRECTION (Black-and-White)	1998	SOUND EFFECTS EDITING
Titanic	1954	ART DIRECTION (Black-and-White)	1998	VISUAL EFFECTS
Titanic	1954	ART DIRECTION (Black-and-White)	1998	ART DIRECTION
Titanic	1954	ART DIRECTION (Black-and-White)	1998	CINEMATOGRAPHY
True Grit	2011	COSTUME DESIGN	1970	ACTOR
True Grit	2011	DIRECTING	1970	ACTOR
True Grit	2011	BEST PICTURE	1970	ACTOR
True Grit	2011	SOUND EDITING	1970	ACTOR
True Grit	2011	SOUND MIXING	1970	ACTOR
True Grit	2011	WRITING (Adapted Screenplay)	1970	ACTOR
True Grit	2011	ACTOR IN A LEADING ROLE	1970	ACTOR
True Grit	2011	ACTRESS IN A SUPPORTING ROLE	1970	ACTOR
True Grit	2011	ART DIRECTION	1970	ACTOR
True Grit	2011	CINEMATOGRAPHY	1970	ACTOR
Up	2010	SOUND EDITING	1985	SHORT FILM (Live Action)
Up	2010	WRITING (Original Screenplay)	1985	SHORT FILM (Live Action)
Up	2010	BEST PICTURE	1985	SHORT FILM (Live Action)
War and Peace	1957	CINEMATOGRAPHY (Color)	1969	FOREIGN LANGUAGE FILM
War and Peace	1957	COSTUME DESIGN (Color)	1969	FOREIGN LANGUAGE FILM
War and Peace	1957	DIRECTING	1969	FOREIGN LANGUAGE FILM
West Side Story	2022	CINEMATOGRAPHY	1962	BEST MOTION PICTURE
West Side Story	2022	CINEMATOGRAPHY	1962	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	COSTUME DESIGN	1962	CINEMATOGRAPHY (Color)
West Side Story	2022	SOUND	1962	DIRECTING
West Side Story	2022	COSTUME DESIGN	1962	BEST MOTION PICTURE
West Side Story	2022	COSTUME DESIGN	1962	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	DIRECTING	1962	CINEMATOGRAPHY (Color)
West Side Story	2022	CINEMATOGRAPHY	1962	FILM EDITING
West Side Story	2022	DIRECTING	1962	BEST MOTION PICTURE
West Side Story	2022	DIRECTING	1962	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	BEST PICTURE	1962	CINEMATOGRAPHY (Color)
West Side Story	2022	COSTUME DESIGN	1962	FILM EDITING
West Side Story	2022	BEST PICTURE	1962	BEST MOTION PICTURE
West Side Story	2022	PRODUCTION DESIGN	1962	CINEMATOGRAPHY (Color)
West Side Story	2022	DIRECTING	1962	FILM EDITING
West Side Story	2022	PRODUCTION DESIGN	1962	BEST MOTION PICTURE
West Side Story	2022	SOUND	1962	CINEMATOGRAPHY (Color)
West Side Story	2022	BEST PICTURE	1962	FILM EDITING
West Side Story	1962	WRITING (Screenplay--based on material from another medium)	2022	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	SOUND	1962	BEST MOTION PICTURE
West Side Story	2022	CINEMATOGRAPHY	1962	COSTUME DESIGN (Color)
West Side Story	2022	PRODUCTION DESIGN	1962	FILM EDITING
West Side Story	2022	CINEMATOGRAPHY	1962	SOUND
West Side Story	2022	BEST PICTURE	1962	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	COSTUME DESIGN	1962	COSTUME DESIGN (Color)
West Side Story	2022	SOUND	1962	FILM EDITING
West Side Story	2022	COSTUME DESIGN	1962	SOUND
West Side Story	2022	PRODUCTION DESIGN	1962	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	DIRECTING	1962	COSTUME DESIGN (Color)
West Side Story	2022	CINEMATOGRAPHY	1962	MUSIC (Scoring of a Musical Picture)
West Side Story	2022	DIRECTING	1962	SOUND
West Side Story	2022	SOUND	1962	ACTRESS IN A SUPPORTING ROLE
West Side Story	2022	BEST PICTURE	1962	COSTUME DESIGN (Color)
West Side Story	2022	COSTUME DESIGN	1962	MUSIC (Scoring of a Musical Picture)
West Side Story	2022	BEST PICTURE	1962	SOUND
West Side Story	2022	CINEMATOGRAPHY	1962	ART DIRECTION (Color)
West Side Story	2022	PRODUCTION DESIGN	1962	COSTUME DESIGN (Color)
West Side Story	2022	DIRECTING	1962	MUSIC (Scoring of a Musical Picture)
West Side Story	2022	PRODUCTION DESIGN	1962	SOUND
West Side Story	2022	CINEMATOGRAPHY	1962	ACTOR IN A SUPPORTING ROLE
West Side Story	2022	COSTUME DESIGN	1962	ART DIRECTION (Color)
West Side Story	2022	SOUND	1962	COSTUME DESIGN (Color)
West Side Story	2022	BEST PICTURE	1962	MUSIC (Scoring of a Musical Picture)
West Side Story	2022	SOUND	1962	SOUND
West Side Story	2022	COSTUME DESIGN	1962	ACTOR IN A SUPPORTING ROLE
West Side Story	2022	DIRECTING	1962	ART DIRECTION (Color)
West Side Story	2022	CINEMATOGRAPHY	1962	DIRECTING
West Side Story	2022	DIRECTING	1962	ACTOR IN A SUPPORTING ROLE
West Side Story	2022	BEST PICTURE	1962	ART DIRECTION (Color)
West Side Story	2022	COSTUME DESIGN	1962	DIRECTING
West Side Story	2022	BEST PICTURE	1962	ACTOR IN A SUPPORTING ROLE
West Side Story	2022	PRODUCTION DESIGN	1962	ART DIRECTION (Color)
West Side Story	2022	DIRECTING	1962	DIRECTING
West Side Story	2022	PRODUCTION DESIGN	1962	ACTOR IN A SUPPORTING ROLE
West Side Story	2022	SOUND	1962	ART DIRECTION (Color)
West Side Story	2022	BEST PICTURE	1962	DIRECTING
West Side Story	2022	PRODUCTION DESIGN	1962	MUSIC (Scoring of a Musical Picture)
West Side Story	2022	SOUND	1962	ACTOR IN A SUPPORTING ROLE
West Side Story	2022	CINEMATOGRAPHY	1962	CINEMATOGRAPHY (Color)
West Side Story	2022	PRODUCTION DESIGN	1962	DIRECTING
West Side Story	2022	SOUND	1962	MUSIC (Scoring of a Musical Picture)
```

```sql
SELECT DISTINCT 
    i1.nome_filme,
    i1.ano_cerimonia AS ano_indicacao,
    i1.categoria AS categoria_indicado,
    i2.ano_cerimonia AS ano_vitoria,
    i2.categoria AS categoria_vencedor
FROM indicados_ao_oscar i1
INNER JOIN indicados_ao_oscar i2 
    ON i1.nome_filme = i2.nome_filme
WHERE i1.vencedor = FALSE 
  AND i2.vencedor = TRUE 
  AND i1.ano_cerimonia != i2.ano_cerimonia
ORDER BY i1.nome_filme;
```

---

## Nível 12: Casos Práticos

### Cenário 1: Curadoria de Mostra de Cinema

Você está organizando uma mostra de cinema e precisa selecionar filmes.

**12.1** Liste os 20 filmes mais premiados do Oscar para sua mostra.

R:
```
Nome Filme  |   Total de Oscars
Titanic	12
Ben-Hur	11
The Lord of the Rings: The Return of the King	11
West Side Story	11
Gigi	9
The English Patient	9
The Last Emperor	9
Amadeus	8
Cabaret	8
From Here to Eternity	8
Gandhi	8
Gone with the Wind	8
My Fair Lady	8
On the Waterfront	8
Slumdog Millionaire	8
Dances With Wolves	7
Everything Everywhere All at Once	7
Going My Way	7
Gravity	7
Lawrence of Arabia	7
```

```sql
SELECT 
    nome_filme,
    COUNT(*) AS total_oscars
FROM indicados_ao_oscar
WHERE vencedor = TRUE AND
nome_filme IS NOT NULL 
  AND nome_filme != ''
GROUP BY nome_filme
ORDER BY total_oscars DESC, nome_filme ASC
LIMIT 20;
```

**12.2** Selecione 5 filmes de cada década (1930s até 2020s) que ganharam pelo menos um Oscar.

R:
```
Decada  |   Nome Filme  |   Ano Cerimonia
1920s	7th Heaven	1928
1920s	The Dove;	1928
1920s	Two Arabian Knights	1928
1920s	Sunrise	1928
1920s	The Last Command	1928
1930s	All Quiet on the Western Front	1930
1930s	King of Jazz	1930
1930s	The Divorcee	1930
1930s	Disraeli	1930
1930s	The Big House	1930
1940s	Gone with the Wind	1940
1940s	Mr. Smith Goes to Washington	1940
1940s	Busy Little Bears	1940
1940s	Goodbye, Mr. Chips	1940
1940s	Sons of Liberty	1940
1950s	All the King's Men	1950
1950s	Battleground	1950
1950s	A Letter to Three Wives	1950
1950s	Aquatic House-Party	1950
1950s	A Chance to Live	1950
1960s	A Hole in the Head	1960
1960s	Black Orpheus	1960
1960s	Moonbird	1960
1960s	Ben-Hur	1960
1960s	Glass	1960
1970s	Czechoslovakia 1968	1970
1970s	Arthur Rubinstein - The Love of Life	1970
1970s	Cactus Flower	1970
1970s	Anne of the Thousand Days	1970
1970s	Butch Cassidy and the Sundance Kid	1970
1980s	Alien	1980
1980s	Apocalypse Now	1980
1980s	A Little Romance	1980
1980s	All That Jazz	1980
1980s	Being There	1980
1990s	Common Threads: Stories from the Quilt	1990
1990s	Batman	1990
1990s	Cinema Paradiso	1990
1990s	Balance	1990
1990s	Born on the Fourth of July	1990
2000s	Boys Don't Cry	2000
2000s	King Gimp	2000
2000s	American Beauty	2000
2000s	Girl, Interrupted	2000
2000s	All about My Mother	2000
2010s	Avatar	2010
2010s	Inglourious Basterds	2010
2010s	Music by Prudence	2010
2010s	Crazy Heart	2010
2010s	Logorama	2010
2020s	American Factory	2020
2020s	Ford v Ferrari	2020
2020s	1917	2020
2020s	Bombshell	2020
2020s	Hair Love	2020
```

```sql
SELECT 
    sub.decada,
    sub.nome_filme,
    sub.ano_cerimonia
FROM (
    SELECT 
        nome_filme,
        ano_cerimonia,
        CONCAT(FLOOR(ano_cerimonia / 10) * 10, 's') AS decada,
        @rn := IF(@current_decada = CONCAT(FLOOR(ano_cerimonia / 10) * 10, 's'), @rn + 1, 1) AS rk,
        @current_decada := CONCAT(FLOOR(ano_cerimonia / 10) * 10, 's')
    FROM (
        SELECT DISTINCT nome_filme, ano_cerimonia
        FROM indicados_ao_oscar
        WHERE vencedor = TRUE 
          AND nome_filme IS NOT NULL 
          AND nome_filme != ''
        ORDER BY ano_cerimonia ASC
    ) AS vencedores_unicos,
    (SELECT @rn := 0, @current_decada := '') AS vars
) AS sub
WHERE sub.rk <= 5
ORDER BY sub.decada ASC, sub.ano_cerimonia ASC;
```

**12.3** Crie uma lista de "clássicos esquecidos" - filmes que ganharam Oscars, mas são de mais de 50 anos atrás.

R:
```
Nome Filme  |   Ano Cerimonia
	1928
7th Heaven	1928
Sunrise	1928
The Dove;	1928
The Last Command	1928
Two Arabian Knights	1928
Underworld	1928
Wings	1928
Coquette	1929
In Old Arizona	1929
The Bridge of San Luis Rey	1929
The Broadway Melody	1929
The Divine Lady	1929
The Patriot	1929
White Shadows in the South Seas	1929
All Quiet on the Western Front	1930
Disraeli	1930
King of Jazz	1930
The Big House	1930
The Divorcee	1930
With Byrd at the South Pole	1930
	1931
A Free Soul	1931
Cimarron	1931
Min and Bill	1931
Skippy	1931
Tabu	1931
The Dawn Patrol	1931
	1932
Bad Girl	1932
Dr. Jekyll and Mr. Hyde	1932
Flowers and Trees	1932
Grand Hotel	1932
Shanghai Express	1932
The Champ	1932
The Music Box	1932
The Sin of Madelon Claudet	1932
Transatlantic	1932
Wrestling Swordfish	1932
	1933
A Farewell to Arms	1933
Cavalcade	1933
Krakatoa	1933
Little Women	1933
Morning Glory	1933
One Way Passage	1933
So This Is Harris	1933
The Private Life of Henry VIII	1933
The Three Little Pigs	1933
	1935
City of Wax	1935
Cleopatra	1935
Eskimo	1935
It Happened One Night	1935
La Cucaracha	1935
Manhattan Melodrama	1935
One Night of Love	1935
The Gay Divorcee	1935
The Merry Widow	1935
The Tortoise and the Hare	1935
Viva Villa!	1935
	1936
A Midsummer Night's Dream	1936
Broadway Melody of 1936;	1936
Dangerous	1936
Gold Diggers of 1935	1936
How to Sleep	1936
Mutiny on the Bounty	1936
Naughty Marietta	1936
The Dark Angel	1936
The Informer	1936
The Lives of a Bengal Lancer	1936
The Scoundrel	1936
Three Orphan Kittens	1936
Wings over Mt. Everest	1936
	1937
Anthony Adverse	1937
Bored of Education	1937
Come and Get It	1937
Dodsworth	1937
Give Me Liberty	1937
Mr. Deeds Goes to Town	1937
San Francisco	1937
Swing Time	1937
The Charge of the Light Brigade	1937
The Country Cousin	1937
The Great Ziegfeld	1937
The Public Pays	1937
The Story of Louis Pasteur	1937
	1938
A Damsel in Distress	1938
A Star Is Born	1938
Captains Courageous	1938
In Old Chicago	1938
Lost Horizon	1938
One Hundred Men and a Girl	1938
Penny Wisdom	1938
The Awful Truth	1938
The Good Earth	1938
The Hurricane	1938
The Life of Emile Zola	1938
The Old Mill	1938
The Private Life of the Gannets	1938
Torture Money	1938
Waikiki Wedding	1938
	1939
Alexander's Ragtime Band	1939
Boys Town	1939
Declaration of Independence	1939
Ferdinand the Bull	1939
Jezebel	1939
Kentucky	1939
Pygmalion	1939
That Mothers Might Live	1939
The Adventures of Robin Hood	1939
The Big Broadcast of 1938	1939
The Cowboy and the Lady	1939
The Great Waltz	1939
You Can't Take It with You	1939
	1940
Busy Little Bears	1940
Gone with the Wind	1940
Goodbye, Mr. Chips	1940
Mr. Smith Goes to Washington	1940
Sons of Liberty	1940
Stagecoach	1940
The Rains Came	1940
The Ugly Duckling	1940
The Wizard of Oz	1940
When Tomorrow Comes	1940
Wuthering Heights	1940
	1941
Arise, My Love	1941
Kitty Foyle	1941
North West Mounted Police	1941
Pinocchio	1941
Pride and Prejudice	1941
Quicker 'N a Wink	1941
Rebecca	1941
Strike Up the Band	1941
Teddy, the Rough Rider	1941
The Grapes of Wrath	1941
The Great McGinty	1941
The Milky Way	1941
The Philadelphia Story	1941
The Thief of Bagdad	1941
The Westerner	1941
Tin Pan Alley	1941
	1942
All That Money Can Buy	1942
Blood and Sand	1942
Blossoms in the Dust	1942
Churchill's Island	1942
Citizen Kane	1942
Dumbo	1942
Here Comes Mr. Jordan	1942
How Green Was My Valley	1942
I Wanted Wings	1942
Lady Be Good	1942
Lend a Paw	1942
Main Street on the March!	1942
Of Pups and Puzzles	1942
Sergeant York	1942
Suspicion	1942
That Hamilton Woman	1942
The Great Lie	1942
	1943
Beyond the Line of Duty	1943
Der Fuehrer's Face	1943
Holiday Inn	1943
Johnny Eager	1943
Kokoda Front Line!	1943
Moscow Strikes Back	1943
Mrs. Miniver	1943
My Gal Sal	1943
Now, Voyager	1943
Prelude to War	1943
Reap the Wild Wind	1943
Speaking of Animals and Their Families	1943
The Battle of Midway	1943
The Black Swan	1943
The Invaders	1943
The Pride of the Yankees	1943
This above All	1943
Woman of the Year	1943
Yankee Doodle Dandy	1943
	1944
Air Force	1944
Amphibious Fighters	1944
Casablanca	1944
Crash Dive	1944
December 7th	1944
Desert Victory	1944
For Whom the Bell Tolls	1944
Heavenly Music	1944
Hello, Frisco, Hello	1944
Phantom of the Opera	1944
Princess O'Rourke	1944
The Human Comedy	1944
The More the Merrier	1944
The Song of Bernadette	1944
This Is the Army	1944
This Land Is Mine	1944
Watch on the Rhine	1944
Yankee Doodle Mouse	1944
	1945
Cover Girl	1945
Gaslight	1945
Going My Way	1945
I Won't Play	1945
Laura	1945
Mouse Trouble	1945
None but the Lonely Heart	1945
Since You Went Away	1945
The Fighting Lady	1945
Thirty Seconds over Tokyo	1945
Who's Who in Animal Land	1945
Wilson	1945
With the Marines at Tarawa	1945
	1946
A Tree Grows in Brooklyn	1946
Anchors Aweigh	1946
Blood on the Sun	1946
Frenchman's Creek	1946
Hitler Lives?	1946
Leave Her to Heaven	1946
Marie-Louise	1946
Mildred Pierce	1946
National Velvet	1946
Quiet Please!	1946
Spellbound	1946
Stairway to Light	1946
Star in the Night	1946
State Fair	1946
The Bells of St. Mary's	1946
The House on 92nd Street	1946
The Lost Weekend	1946
The Picture of Dorian Gray	1946
The True Glory	1946
Wonder Man	1946
	1947
A Boy and His Dog	1947
Anna and the King of Siam	1947
Blithe Spirit	1947
Facing Your Danger	1947
Seeds of Destiny	1947
The Best Years of Our Lives	1947
The Cat Concerto	1947
The Harvey Girls	1947
The Jolson Story	1947
The Razor's Edge	1947
The Seventh Veil	1947
The Yearling	1947
To Each His Own	1947
Vacation from Marriage	1947
	1948
A Double Life	1948
Black Narcissus	1948
Body and Soul	1948
Climbing the Matterhorn	1948
Design for Death	1948
First Steps	1948
Gentleman's Agreement	1948
Good-bye Miss Turlock	1948
Great Expectations	1948
Green Dolphin Street	1948
Miracle on 34th Street	1948
Mother Wore Tights	1948
Song of the South	1948
The Bachelor and the Bobby-Soxer	1948
The Bishop's Wife	1948
The Farmer's Daughter	1948
Tweetie Pie	1948
	1949
Easter Parade	1949
Hamlet	1949
Joan of Arc	1949
Johnny Belinda	1949
Key Largo	1949
Portrait of Jennie	1949
Seal Island	1949
Symphony of a City	1949
The Little Orphan	1949
The Naked City	1949
The Paleface	1949
The Red Shoes	1949
The Search	1949
The Secret Land	1949
The Snake Pit	1949
The Treasure of the Sierra Madre	1949
Toward Independence	1949
	1950
A Chance to Live	1950
A Letter to Three Wives	1950
All the King's Men	1950
Aquatic House-Party	1950
Battleground	1950
Champion	1950
Daybreak in Udi	1950
For Scent-Imental Reasons	1950
Little Women	1950
Mighty Joe Young	1950
Neptune's Daughter	1950
On the Town	1950
She Wore a Yellow Ribbon	1950
So Much for So Little	1950
The Adventures of Don Juan	1950
The Heiress	1950
The Stratton Story	1950
Twelve O'Clock High	1950
Van Gogh	1950
	1951
All about Eve	1951
Annie Get Your Gun	1951
Born Yesterday	1951
Captain Carey, U.S.A.	1951
Cyrano de Bergerac	1951
Destination Moon	1951
Gerald McBoing-Boing	1951
Grandad of Races	1951
Harvey	1951
In Beaver Valley	1951
King Solomon's Mines	1951
Panic in the Streets	1951
Samson and Delilah	1951
Sunset Blvd.	1951
The Third Man	1951
The Titan: Story of Michelangelo	1951
Why Korea?	1951
	1952
A Place in the Sun	1952
A Streetcar Named Desire	1952
An American in Paris	1952
Benjy	1952
Here Comes the Groom	1952
Kon-Tiki	1952
Nature's Half Acre	1952
Seven Days to Noon	1952
The African Queen	1952
The Great Caruso	1952
The Two Mouseketeers	1952
When Worlds Collide	1952
World of Kids	1952
	1953
Breaking the Sound Barrier	1953
Come Back, Little Sheba	1953
High Noon	1953
Johann Mouse	1953
Light in the Window: The Art of Vermeer	1953
Moulin Rouge	1953
Neighbours	1953
Plymouth Adventure	1953
The Bad and the Beautiful	1953
The Greatest Show on Earth	1953
The Lavender Hill Mob	1953
The Quiet Man	1953
The Sea around Us	1953
Viva Zapata!	1953
Water Birds	1953
With a Song in My Heart	1953
	1954
Bear Country	1954
Calamity Jane	1954
Call Me Madam	1954
From Here to Eternity	1954
Julius Caesar	1954
Lili	1954
Roman Holiday	1954
Shane	1954
Stalag 17	1954
The Alaskan Eskimo	1954
The Living Desert	1954
The Merry Wives of Windsor Overture	1954
The Robe	1954
The War of the Worlds	1954
Titanic	1954
Toot, Whistle, Plunk and Boom	1954
	1955
20,000 Leagues under the Sea	1955
A Time Out of War	1955
Broken Lance	1955
Gate of Hell	1955
On the Waterfront	1955
Sabrina	1955
Seven Brides for Seven Brothers	1955
The Barefoot Contessa	1955
The Country Girl	1955
The Glenn Miller Story	1955
The High and the Mighty	1955
The Vanishing Prairie	1955
This Mechanical Age	1955
Three Coins in the Fountain	1955
Thursday's Children	1955
When Magoo Flew	1955
	1956
East of Eden	1956
Helen Keller in Her Story	1956
I'll Cry Tomorrow	1956
Interrupted Melody	1956
Love Is a Many-Splendored Thing	1956
Love Me or Leave Me	1956
Marty	1956
Men against the Arctic	1956
Mister Roberts	1956
Oklahoma!	1956
Picnic	1956
Speedy Gonzales	1956
Survival City	1956
The Bridges at Toko-Ri	1956
The Face of Lincoln	1956
The Rose Tattoo	1956
To Catch a Thief	1956
	1957
Anastasia	1957
Around the World in 80 Days	1957
Crashing the Water Barrier	1957
Giant	1957
La Strada	1957
Lust for Life	1957
Mister Magoo's Puddle Jumper	1957
Somebody Up There Likes Me	1957
The Bespoke Overcoat	1957
The Brave One	1957
The King and I	1957
The Man Who Knew Too Much	1957
The Red Balloon	1957
The Silent World	1957
The Solid Gold Cadillac	1957
The Ten Commandments	1957
The True Story of the Civil War	1957
Written on the Wind	1957
	1958
Albert Schweitzer	1958
Birds Anonymous	1958
Designing Woman	1958
Les Girls	1958
Sayonara	1958
The Bridge on the River Kwai	1958
The Enemy Below	1958
The Joker Is Wild	1958
The Nights of Cabiria	1958
The Three Faces of Eve	1958
The Wetback Hound	1958
	1959
Ama Girls	1959
Gigi	1959
Grand Canyon	1959
I Want to Live!	1959
Knighty Knight Bugs	1959
My Uncle	1959
Separate Tables	1959
South Pacific	1959
The Big Country	1959
The Defiant Ones	1959
The Old Man and the Sea	1959
tom thumb	1959
White Wilderness	1959
	1960
A Hole in the Head	1960
Ben-Hur	1960
Black Orpheus	1960
Glass	1960
Moonbird	1960
Pillow Talk	1960
Porgy and Bess	1960
Room at the Top	1960
Serengeti Shall Not Die	1960
Some Like It Hot	1960
The Diary of Anne Frank	1960
The Golden Fish	1960
	1961
Butterfield 8	1961
Day of the Painter	1961
Elmer Gantry	1961
Exodus	1961
Giuseppina	1961
Munro	1961
Never on Sunday	1961
Song without End (The Story of Franz Liszt)	1961
Sons and Lovers	1961
Spartacus	1961
The Alamo	1961
The Apartment	1961
The Facts of Life	1961
The Horse with the Flying Tail	1961
The Time Machine	1961
The Virgin Spring	1961
	1962
Breakfast at Tiffany's	1962
Ersatz (The Substitute)	1962
Judgment at Nuremberg	1962
La Dolce Vita	1962
Le Ciel et la Boue (Sky Above and Mud Beneath)	1962
Project Hope	1962
Seawards the Great Ships	1962
Splendor in the Grass	1962
The Guns of Navarone	1962
The Hustler	1962
Through a Glass Darkly	1962
Two Women	1962
West Side Story	1962
	1963
Black Fox	1963
Days of Wine and Roses	1963
Divorce--Italian Style	1963
Dylan Thomas	1963
Heureux Anniversaire (Happy Anniversary)	1963
Lawrence of Arabia	1963
Meredith Willson's The Music Man	1963
Sundays and Cybele	1963
Sweet Bird of Youth	1963
The Hole	1963
The Longest Day	1963
The Miracle Worker	1963
The Wonderful World of the Brothers Grimm	1963
To Kill a Mockingbird	1963
What Ever Happened to Baby Jane?	1963
	1964
America America	1964
An Occurrence at Owl Creek Bridge	1964
Chagall	1964
Cleopatra	1964
Federico Fellini's 8-1/2	1964
How the West Was Won	1964
Hud	1964
Irma La Douce	1964
It's a Mad, Mad, Mad, Mad World	1964
Lilies of the Field	1964
Papa's Delicate Condition	1964
Robert Frost: A Lover's Quarrel with the World	1964
The Critic	1964
The V.I.P.s	1964
Tom Jones	1964
	1965
Becket	1965
Casals Conducts: 1964	1965
Father Goose	1965
Goldfinger	1965
Jacques-Yves Cousteau's World without Sun	1965
Mary Poppins	1965
My Fair Lady	1965
Nine from Little Rock	1965
The Night of the Iguana	1965
The Pink Phink	1965
Topkapi	1965
Yesterday, Today and Tomorrow	1965
Zorba the Greek	1965
	1966
A Patch of Blue	1966
A Thousand Clowns	1966
Cat Ballou	1966
Darling	1966
Doctor Zhivago	1966
Ship of Fools	1966
The Chicken (Le Poulet)	1966
The Dot and the Line	1966
The Eleanor Roosevelt Story	1966
The Great Race	1966
The Sandpiper	1966
The Shop on Main Street	1966
The Sound of Music	1966
Thunderball	1966
To Be Alive!	1966
	1967
A Funny Thing Happened on the Way to the Forum	1967
A Man and a Woman	1967
A Man for All Seasons	1967
A Year toward Tomorrow	1967
Born Free	1967
Fantastic Voyage	1967
Grand Prix	1967
Herb Alpert and the Tijuana Brass Double Feature	1967
The Fortune Cookie	1967
The War Game	1967
Who's Afraid of Virginia Woolf?	1967
Wild Wings	1967
	1968
A Place to Stand	1968
Bonnie and Clyde	1968
Camelot	1968
Closely Watched Trains	1968
Cool Hand Luke	1968
Doctor Dolittle	1968
Guess Who's Coming to Dinner	1968
In the Heat of the Night	1968
The Anderson Platoon	1968
The Box	1968
The Dirty Dozen	1968
The Graduate	1968
The Redwoods	1968
Thoroughly Modern Millie	1968
	1969
2001: A Space Odyssey	1969
Bullitt	1969
Charly	1969
Funny Girl	1969
Journey into Self	1969
Oliver!	1969
Robert Kennedy Remembered	1969
Romeo and Juliet	1969
Rosemary's Baby	1969
The Lion in Winter	1969
The Producers	1969
The Subject Was Roses	1969
The Thomas Crown Affair	1969
War and Peace	1969
Why Man Creates	1969
Winnie the Pooh and the Blustery Day	1969
	1970
Anne of the Thousand Days	1970
Arthur Rubinstein - The Love of Life	1970
Butch Cassidy and the Sundance Kid	1970
Cactus Flower	1970
Czechoslovakia 1968	1970
Hello, Dolly!	1970
It's Tough to Be a Bird	1970
Marooned	1970
Midnight Cowboy	1970
The Magic Machines	1970
The Prime of Miss Jean Brodie	1970
They Shoot Horses, Don't They?	1970
True Grit	1970
Z	1970
	1971
Airport	1971
Cromwell	1971
Interviews with My Lai Veterans	1971
Investigation of a Citizen above Suspicion	1971
Is It Always Right to Be Right?	1971
Let It Be	1971
Love Story	1971
Lovers and Other Strangers	1971
M*A*S*H	1971
Patton	1971
Ryan's Daughter	1971
The Resurrection of Broncho Billy	1971
Tora! Tora! Tora!	1971
Women in Love	1971
Woodstock	1971
	1972
Bedknobs and Broomsticks	1972
Fiddler on the Roof	1972
Klute	1972
Nicholas and Alexandra	1972
Sentinels of Silence	1972
Shaft	1972
Summer of '42	1972
The Crunch Bird	1972
The French Connection	1972
The Garden of the Finzi Continis	1972
The Hellstrom Chronicle	1972
The Hospital	1972
The Last Picture Show	1972
	1973
A Christmas Carol	1973
Butterflies Are Free	1973
Cabaret	1973
Limelight	1973
Marjoe	1973
Norman Rockwell's World...An American Dream	1973
The Candidate	1973
The Discreet Charm of the Bourgeoisie	1973
The Godfather	1973
The Poseidon Adventure	1973
This Tiny World	1973
Travels with My Aunt	1973
	1974
A Touch of Class	1974
Cries and Whispers	1974
Day for Night	1974
Frank Film	1974
Paper Moon	1974
Princeton: A Search for Answers	1974
Save the Tiger	1974
The Bolero	1974
The Exorcist	1974
The Great American Cowboy	1974
The Paper Chase	1974
The Sting	1974
The Way We Were	1974
	1975
Alice Doesn't Live Here Anymore	1975
Amarcord	1975
Chinatown	1975
Closed Mondays	1975
Don't	1975
Earthquake	1975
Harry and Tonto	1975
Hearts and Minds	1975
Murder on the Orient Express	1975
One-Eyed Men Are Kings	1975
The Godfather Part II	1975
The Great Gatsby	1975
The Towering Inferno	1975
	1976
Angel and Big Joe	1976
Barry Lyndon	1976
Dersu Uzala	1976
Dog Day Afternoon	1976
Great	1976
Jaws	1976
Nashville	1976
One Flew over the Cuckoo's Nest	1976
Shampoo	1976
The End of the Game	1976
The Hindenburg	1976
The Man Who Skied down Everest	1976
The Sunshine Boys	1976
```

```sql
SELECT DISTINCT 
    nome_filme,
    ano_cerimonia
FROM indicados_ao_oscar
WHERE vencedor = TRUE 
  AND ano_cerimonia <= (YEAR(CURRENT_DATE()) - 50)
ORDER BY ano_cerimonia ASC;
```

### Cenário 2: Análise para Documentário

Você está produzindo um documentário sobre a história do Oscar.

**12.4** Identifique os 5 momentos mais importantes (cerimônias com mais premiações históricas).

R:
```
Ano Cerimonia   |   Edição Cerimonia    |   Total de premios Entregues
1953	25	33
1955	27	33
1949	21	32
1950	22	32
1954	26	31
```

```sql
SELECT 
    ano_cerimonia,
    edicao_cerimonia,
    COUNT(*) AS total_premios_entregues
FROM indicados_ao_oscar
WHERE vencedor = TRUE
GROUP BY ano_cerimonia, edicao_cerimonia
ORDER BY total_premios_entregues DESC
LIMIT 5;
```

**12.5** Liste todos os "primeiros" históricos (primeira mulher a ganhar melhor direção, primeiro ator negro, etc.) - use sua criatividade para encontrar esses marcos.

R:
```
Categoria   |   Primeiro Ano    |   Nome indicado   |   Nome filme
ACTOR	1928	Emil Jannings	The Last Command
ACTRESS	1928	Janet Gaynor	7th Heaven
ART DIRECTION	1928	William Cameron Menzies	The Dove;
CINEMATOGRAPHY	1928	Charles Rosher	Sunrise
CINEMATOGRAPHY	1928	Karl Struss	Sunrise
DIRECTING (Comedy Picture)	1928	Lewis Milestone	Two Arabian Knights
DIRECTING (Dramatic Picture)	1928	Frank Borzage	7th Heaven
ENGINEERING EFFECTS	1928	Roy Pomeroy	Wings
OUTSTANDING PICTURE	1928	Paramount Famous Lasky	Wings
SPECIAL AWARD	1928	Warner Bros.	
SPECIAL AWARD	1928	Charles Chaplin	
UNIQUE AND ARTISTIC PICTURE	1928	Fox	Sunrise
WRITING (Adaptation)	1928	Benjamin Glazer	7th Heaven
WRITING (Original Story)	1928	Ben Hecht	Underworld
WRITING (Title Writing)	1928	Joseph Farnham	
DIRECTING	1929	Frank Lloyd	The Divine Lady
WRITING	1929	Hans Kraly	The Patriot
OUTSTANDING PRODUCTION	1930	Universal	All Quiet on the Western Front
SOUND RECORDING	1930	Metro-Goldwyn-Mayer Studio Sound Department, Douglas Shearer, Sound Director	The Big House
SHORT SUBJECT (Cartoon)	1932	Walt Disney, Producer	Flowers and Trees
SHORT SUBJECT (Comedy)	1932	Hal Roach, Producer	The Music Box
SHORT SUBJECT (Novelty)	1932	Mack Sennett, Producer	Wrestling Swordfish
ASSISTANT DIRECTOR	1933	William Tummel (Fox)	
ASSISTANT DIRECTOR	1933	Charles Dorian (Metro-Goldwyn-Mayer)	
ASSISTANT DIRECTOR	1933	Charles Barton (Paramount)	
ASSISTANT DIRECTOR	1933	Dewey Starkey (RKO Radio)	
ASSISTANT DIRECTOR	1933	Fred Fox (United Artists)	
ASSISTANT DIRECTOR	1933	Scott Beal (Universal)	
ASSISTANT DIRECTOR	1933	Gordon Hollingshead (Warner Bros.)	
FILM EDITING	1935	Conrad Nervig	Eskimo
MUSIC (Scoring)	1935	Columbia Studio Music Department, Louis Silvers, head of department  (Thematic Music by Victor Schertzinger and Gus Kahn)	One Night of Love
MUSIC (Song)	1935	Music by Con Conrad; Lyrics by Herb Magidson	The Gay Divorcee
DANCE DIRECTION	1936	Dave Gould	Broadway Melody of 1936;
WRITING (Screenplay)	1936	Dudley Nichols	The Informer
ACTOR IN A SUPPORTING ROLE	1937	Walter Brennan	Come and Get It
ACTRESS IN A SUPPORTING ROLE	1937	Gale Sondergaard	Anthony Adverse
SHORT SUBJECT (Color)	1937	Warner Bros.	Give Me Liberty
SHORT SUBJECT (One-reel)	1937	Hal Roach, Producer	Bored of Education
SHORT SUBJECT (Two-reel)	1937	Metro-Goldwyn-Mayer	The Public Pays
IRVING G. THALBERG MEMORIAL AWARD	1938	Darryl F. Zanuck	
MUSIC (Original Score)	1939	Erich Wolfgang Korngold	The Adventures of Robin Hood
CINEMATOGRAPHY (Black-and-White)	1940	Gregg Toland	Wuthering Heights
CINEMATOGRAPHY (Color)	1940	Ernest Haller, Ray Rennahan	Gone with the Wind
SPECIAL EFFECTS	1940	Fred Sersen, E. H. Hansen	The Rains Came
ART DIRECTION (Black-and-White)	1941	Cedric Gibbons, Paul Groesse	Pride and Prejudice
ART DIRECTION (Color)	1941	Vincent Korda	The Thief of Bagdad
WRITING (Original Screenplay)	1941	Preston Sturges	The Great McGinty
DOCUMENTARY (Short Subject)	1942	National Film Board of Canada	Churchill's Island
MUSIC (Music Score of a Dramatic Picture)	1942	Bernard Herrmann	All That Money Can Buy
MUSIC (Scoring of a Musical Picture)	1942	Frank Churchill, Oliver Wallace	Dumbo
OUTSTANDING MOTION PICTURE	1942	20th Century-Fox	How Green Was My Valley
DOCUMENTARY	1943	United States Navy	The Battle of Midway
DOCUMENTARY	1943	Australian News & Information Bureau	Kokoda Front Line!
DOCUMENTARY	1943	Artkino	Moscow Strikes Back
DOCUMENTARY	1943	United States Army Special Services	Prelude to War
MUSIC (Music Score of a Dramatic or Comedy Picture)	1943	Max Steiner	Now, Voyager
WRITING (Original Motion Picture Story)	1943	Emeric Pressburger	The Invaders
DOCUMENTARY (Feature)	1944	British Ministry of Information	Desert Victory
BEST MOTION PICTURE	1945	Paramount	Going My Way
WRITING (Motion Picture Story)	1948	Valentine Davies	Miracle on 34th Street
COSTUME DESIGN (Black-and-White)	1949	Roger K. Furse	Hamlet
COSTUME DESIGN (Color)	1949	Dorothy Jeakins, Karinska	Joan of Arc
SPECIAL FOREIGN LANGUAGE FILM AWARD	1949	Monsieur Vincent - voted by the Academy Board of Governors as the most outstanding foreign language film released in the United States during 1948.	
WRITING (Story and Screenplay)	1950	Robert Pirosh	Battleground
HONORARY AWARD	1951	George Murphy for his services in interpreting the film industry to the country at large.	
HONORARY AWARD	1951	Louis B. Mayer for distinguished service to the motion picture industry.	
HONORARY FOREIGN LANGUAGE FILM AWARD	1951	The Walls of Malapaga - voted by the Board of Governors as the most outstanding foreign language film released in the United States in 1950.	
FOREIGN LANGUAGE FILM	1957	Italy; Dino De Laurentiis and Carlo Ponti, Producers	La Strada
JEAN HERSHOLT HUMANITARIAN AWARD	1957	Y. Frank Freeman	
WRITING (Screenplay--Adapted)	1957	James Poe, John Farrow, S.J. Perelman	Around the World in 80 Days
WRITING (Screenplay--Original)	1957	Albert Lamorisse	The Red Balloon
COSTUME DESIGN	1958	Orry-Kelly	Les Girls
SHORT SUBJECT (Live Action)	1958	Larry Lansburgh, Producer	The Wetback Hound
WRITING (Screenplay--based on material from another medium)	1958	Michael Wilson, Carl Foreman, Pierre Boulle	The Bridge on the River Kwai
WRITING (Story and Screenplay--written directly for the screen)	1958	George Wells	Designing Woman
SOUND	1959	Todd-AO Sound Department, Fred Hynes, Sound Director	South Pacific
BEST PICTURE	1963	Sam Spiegel, Producer	Lawrence of Arabia
MUSIC (Music Score--substantially original)	1963	Maurice Jarre	Lawrence of Arabia
MUSIC (Scoring of Music--adaptation or treatment)	1963	Ray Heindorf	Meredith Willson's The Music Man
SOUND EFFECTS	1964	Walter G. Elliott	It's a Mad, Mad, Mad, Mad World
SPECIAL VISUAL EFFECTS	1965	Peter Ellenshaw, Eustace Lycett, Hamilton Luske	Mary Poppins
MUSIC (Original Music Score)	1967	John Barry	Born Free
MUSIC (Original Score--for a motion picture [not a musical])	1969	John Barry	The Lion in Winter
MUSIC (Score of a Musical Picture--original or adaptation)	1969	Adaptation score by John Green	Oliver!
MUSIC (Song--Original for the Picture)	1969	Music by Michel Legrand; Lyrics by Alan Bergman and Marilyn Bergman	The Thomas Crown Affair
WRITING (Story and Screenplay--based on material not previously published or produced)	1970	William Goldman	Butch Cassidy and the Sundance Kid
MUSIC (Original Song Score)	1971	Music and lyrics by The Beatles	Let It Be
WRITING (Story and Screenplay--based on factual material or material not previously published or produced)	1971	Francis Ford Coppola, Edmund H. North	Patton
MUSIC (Original Dramatic Score)	1972	Michel Legrand	Summer of '42
MUSIC (Scoring: Adaptation and Original Song Score)	1972	Adaptation Score by John Williams	Fiddler on the Roof
SHORT SUBJECT (Animated)	1972	Ted Petok, Producer	The Crunch Bird
SPECIAL ACHIEVEMENT AWARD (Visual Effects)	1973	L. B. Abbott, A. D. Flowers	The Poseidon Adventure
MUSIC (Scoring: Original Song Score and Adaptation -or- Scoring: Adaptation)	1974	Adaptation Score by Marvin Hamlisch	The Sting
SHORT FILM (Animated)	1975	Will Vinton and Bob Gardiner, Producers	Closed Mondays
SHORT FILM (Live Action)	1975	Paul Claudon and Edmond Sechan, Producers	One-Eyed Men Are Kings
WRITING (Screenplay Adapted from Other Material)	1975	Francis Ford Coppola, Mario Puzo	The Godfather Part II
MUSIC (Original Song)	1976	Music and Lyrics by Keith Carradine	Nashville
SPECIAL ACHIEVEMENT AWARD (Sound Effects)	1976	Peter Berkos	The Hindenburg
ACTOR IN A LEADING ROLE	1977	Peter Finch	Network
ACTRESS IN A LEADING ROLE	1977	Faye Dunaway	Network
MUSIC (Original Song Score and Its Adaptation or Adaptation Score)	1977	Adaptation Score by Leonard Rosenman	Bound for Glory
WRITING (Screenplay Written Directly for the Screen--based on factual material or on story material not previously published or produced)	1977	Paddy Chayefsky	Network
SPECIAL ACHIEVEMENT AWARD	1978	Benjamin Burtt	
SPECIAL ACHIEVEMENT AWARD (Sound Effects Editing)	1978	Frank E. Warner	Close Encounters of the Third Kind
VISUAL EFFECTS	1978	John Stears, John Dykstra, Richard Edlund, Grant McCune, Robert Blalack	Star Wars
MUSIC (Adaptation Score)	1979	Joe Renzetti	The Buddy Holly Story
WRITING (Screenplay Based on Material from Another Medium)	1979	Oliver Stone	Midnight Express
WRITING (Screenplay Written Directly for the Screen)	1979	Story by Nancy Dowd;  Screenplay by Waldo Salt, Robert C. Jones	Coming Home
MUSIC (Original Song Score and Its Adaptation -or- Adaptation Score)	1980	Adaptation Score by Ralph Burns	All That Jazz
SPECIAL ACHIEVEMENT AWARD (Sound Editing)	1980	Alan Splet	The Black Stallion
SHORT FILM (Dramatic Live Action)	1981	Lloyd Phillips, Producer	The Dollar Bottom
MAKEUP	1982	Rick Baker	An American Werewolf in London
SOUND EFFECTS EDITING	1983	Charles L. Campbell, Ben Burtt	E.T. The Extra-Terrestrial
MUSIC (Original Song Score or Adaptation Score)	1984	Song Score by Michel Legrand, Alan Bergman and Marilyn Bergman	Yentl
WRITING (Screenplay Based on Material Previously Produced or Published)	1992	Ted Tally	The Silence of the Lambs
MUSIC (Original Musical or Comedy Score)	1996	Music by Alan Menken; Lyrics by Stephen Schwartz; Orchestral Score by Alan Menken	Pocahontas
SOUND EDITING	2001	Jon Johnson	U-571
ANIMATED FEATURE FILM	2002	Aron Warner	Shrek
WRITING (Adapted Screenplay)	2003	Screenplay by Ronald Harwood	The Pianist
SOUND MIXING	2004	Christopher Boyes, Michael Semanick, Michael Hedges and Hammond Peek	The Lord of the Rings: The Return of the King
MAKEUP AND HAIRSTYLING	2013	Lisa Westcott and Julie Dartnell	Les Misérables
PRODUCTION DESIGN	2013	Production Design: Rick Carter; Set Decoration: Jim Erickson	Lincoln
INTERNATIONAL FEATURE FILM	2020	South Korea	Parasite
AWARD OF COMMENDATION	2023	To Ryan Laney for his innovative adaptation and deployment of AI-driven facial veiling technology used to protect the identities while preserving the visual relatability of subjects in documentary filmmaking as exemplified in Welcome to Chechnya (2020).	Welcome to Chechnya
DOCUMENTARY FEATURE FILM	2023	Daniel Roher, Odessa Rae, Diane Becker, Melanie Miller and Shane Boris	Navalny
DOCUMENTARY SHORT FILM	2023	Kartiki Gonsalves and Guneet Monga	The Elephant Whisperers
GORDON E. SAWYER AWARD	2023	Iain Neil	
```

```sql
SELECT 
    i.categoria,
    i.ano_cerimonia AS primeiro_ano,
    i.nome_indicado,
    i.nome_filme
FROM indicados_ao_oscar i
INNER JOIN (
    SELECT categoria, MIN(ano_cerimonia) AS min_ano
    FROM indicados_ao_oscar
    WHERE vencedor = TRUE
      AND categoria IS NOT NULL
    GROUP BY categoria
) primeiro_por_cat 
    ON i.categoria = primeiro_por_cat.categoria 
    AND i.ano_cerimonia = primeiro_por_cat.min_ano
WHERE i.vencedor = TRUE
ORDER BY primeiro_ano ASC, i.categoria ASC;
```

**12.6** Encontre casos de "injustiça" - filmes/atores muito indicados, mas que nunca ganharam.

R:
```
Nome indicado   |   Total Indicações
Thomas Newman	14
George Folsey	12
Music and Lyric by Diane Warren	11
Paramount Studio Sound Department, Loren L. Ryder, Sound Director	10
Walter Lantz, Producer	10
Israel	10
Randy Newman	9
Belgium	8
Glenn Close	8
Robert Emmett Dolan	8
```

```sql
SELECT 
    nome_indicado,
    COUNT(*) AS total_indicacoes
FROM indicados_ao_oscar
WHERE nome_indicado IS NOT NULL 
  AND nome_indicado != ''
GROUP BY nome_indicado
HAVING SUM(CASE WHEN vencedor = TRUE THEN 1 ELSE 0 END) = 0
ORDER BY total_indicacoes DESC
LIMIT 10;
```

### Cenário 3: Estatísticas para Apostas

Você trabalha para um site de apostas e precisa de estatísticas.

**12.7** Qual a probabilidade histórica de um filme indicado em 10 categorias ganhar Melhor Filme?

R: A probabilidade é de 20.45%

```sql
SELECT 
    ROUND(
        (SUM(CASE WHEN ganhou_melhor_filme = 1 THEN 1 ELSE 0 END) / COUNT(*)) * 100, 
        2
    ) as probabilidade_percentual
FROM (
    SELECT 
        i.nome_filme,
        i.ano_cerimonia,
        MAX(CASE WHEN i.categoria IN ('BEST PICTURE', 'OUTSTANDING PICTURE') AND i.vencedor = TRUE THEN 1 ELSE 0 END) AS ganhou_melhor_filme
    FROM indicados_ao_oscar i
    INNER JOIN (
        SELECT nome_filme, ano_cerimonia
        FROM indicados_ao_oscar
        GROUP BY nome_filme, ano_cerimonia
        HAVING COUNT(*) = 10
    ) f10 ON i.nome_filme = f10.nome_filme AND i.ano_cerimonia = f10.ano_cerimonia
    GROUP BY i.nome_filme, i.ano_cerimonia
) as sub;
```

**12.8** Atores que ganharam Melhor Ator tendem a ter quantas indicações antes da primeira vitória?

R: A média e de 1.79 indicações para vencer

```sql
SELECT 
    ROUND(AVG(indicacoes_anteriores.total_indicacoes_antes), 2) AS media_indicacoes_ate_vencer
FROM (
    SELECT 
        pv.nome_indicado,
        COUNT(i.id_registro) AS total_indicacoes_antes
    FROM (
        -- Subconsulta para achar o ano da primeira vitória de cada ator
        SELECT 
            nome_indicado,
            MIN(ano_cerimonia) AS ano_primeira_vitoria
        FROM indicados_ao_oscar
        WHERE categoria = 'ACTOR' AND vencedor = TRUE
          AND nome_indicado IS NOT NULL AND nome_indicado != ''
        GROUP BY nome_indicado
    ) AS pv
    INNER JOIN indicados_ao_oscar i 
        ON pv.nome_indicado = i.nome_indicado 
        AND i.categoria = 'ACTOR' 
        AND i.ano_cerimonia <= pv.ano_primeira_vitoria
    GROUP BY pv.nome_indicado
) AS indicacoes_anteriores;
```

**12.9** Qual categoria tem os vencedores mais "previsíveis" (mesmo artista/filme ganha múltiplas vezes)?

R:
```
Categoria   |   vencedor recorrente     |   Total vitorias
SHORT SUBJECT (Cartoon)	Walt Disney, Producer	12
FOREIGN LANGUAGE FILM	Italy	10
FOREIGN LANGUAGE FILM	France	9
SHORT SUBJECT (Two-reel)	Walt Disney, Producer	5
SOUND RECORDING	Metro-Goldwyn-Mayer Studio Sound Department, Douglas Shearer, Sound Director	5
CINEMATOGRAPHY (Color)	Leon Shamroy	4
COSTUME DESIGN	Colleen Atwood	4
DIRECTING	John Ford	4
FOREIGN LANGUAGE FILM	Spain	4
MUSIC (Original Score)	John Williams	4
SHORT SUBJECT (Cartoon)	Edward Selzer, Producer	4
SHORT SUBJECT (Two-reel)	Warner Bros.	4
ACTOR IN A SUPPORTING ROLE	Walter Brennan	3
ACTRESS	Katharine Hepburn	3
ACTRESS IN A LEADING ROLE	Frances McDormand	3
CINEMATOGRAPHY	Vittorio Storaro	3
CINEMATOGRAPHY	Robert Richardson	3
CINEMATOGRAPHY	Emmanuel Lubezki	3
CINEMATOGRAPHY (Black-and-White)	Arthur Miller	3
COSTUME DESIGN	Sandy Powell	3
COSTUME DESIGN	Anthony Powell	3
COSTUME DESIGN	James Acheson	3
COSTUME DESIGN	Milena Canonero	3
COSTUME DESIGN (Black-and-White)	Edith Head	3
DIRECTING	William Wyler	3
DIRECTING	Frank Capra	3
FILM EDITING	Michael Kahn	3
FILM EDITING	Thelma Schoonmaker	3
FILM EDITING	Ralph Dawson	3
FILM EDITING	Daniel Mandell	3
FOREIGN LANGUAGE FILM	Denmark	3
FOREIGN LANGUAGE FILM	Union of Soviet Socialist Republics	3
FOREIGN LANGUAGE FILM	The Netherlands	3
FOREIGN LANGUAGE FILM	Sweden	3
IRVING G. THALBERG MEMORIAL AWARD	Darryl F. Zanuck	3
MUSIC (Music Score of a Dramatic or Comedy Picture)	Dimitri Tiomkin	3
MUSIC (Original Score)	Alan Menken	3
MUSIC (Scoring of a Musical Picture)	Alfred Newman	3
MUSIC (Song)	Music by James Van Heusen; Lyrics by Sammy Cahn	3
OUTSTANDING PRODUCTION	Metro-Goldwyn-Mayer	3
SHORT FILM (Animated)	Nick Park	3
SHORT SUBJECT (Cartoon)	Fred Quimby, Producer	3
SHORT SUBJECT (Cartoon)	Frederick Quimby, Producer	3
SHORT SUBJECT (Cartoon)	Stephen Bosustow, Producer	3
SHORT SUBJECT (Two-reel)	Metro-Goldwyn-Mayer	3
SHORT SUBJECT (Two-reel)	Gordon Hollingshead, Producer	3
SOUND	Metro-Goldwyn-Mayer Studio Sound Department, Franklin E. Milton, Sound Director	3
SOUND EDITING	Richard King	3
SOUND RECORDING	20th Century-Fox Studio Sound Department, Thomas T. Moulton, Sound Director	3
ACTOR	Marlon Brando	2
ACTOR	Fredric March	2
ACTOR	Spencer Tracy	2
ACTOR	Gary Cooper	2
ACTOR IN A LEADING ROLE	Tom Hanks	2
ACTOR IN A LEADING ROLE	Daniel Day-Lewis	2
ACTOR IN A LEADING ROLE	Dustin Hoffman	2
ACTOR IN A LEADING ROLE	Anthony Hopkins	2
ACTOR IN A LEADING ROLE	Sean Penn	2
ACTOR IN A SUPPORTING ROLE	Christoph Waltz	2
ACTOR IN A SUPPORTING ROLE	Mahershala Ali	2
ACTOR IN A SUPPORTING ROLE	Melvyn Douglas	2
ACTOR IN A SUPPORTING ROLE	Anthony Quinn	2
ACTOR IN A SUPPORTING ROLE	Michael Caine	2
ACTOR IN A SUPPORTING ROLE	Jason Robards	2
ACTOR IN A SUPPORTING ROLE	Peter Ustinov	2
ACTRESS	Vivien Leigh	2
ACTRESS	Elizabeth Taylor	2
ACTRESS	Luise Rainer	2
ACTRESS	Ingrid Bergman	2
ACTRESS	Bette Davis	2
ACTRESS	Olivia de Havilland	2
ACTRESS	Glenda Jackson	2
ACTRESS IN A LEADING ROLE	Jodie Foster	2
ACTRESS IN A LEADING ROLE	Emma Stone	2
ACTRESS IN A LEADING ROLE	Hilary Swank	2
ACTRESS IN A LEADING ROLE	Sally Field	2
ACTRESS IN A LEADING ROLE	Meryl Streep	2
ACTRESS IN A SUPPORTING ROLE	Shelley Winters	2
ACTRESS IN A SUPPORTING ROLE	Dianne Wiest	2
ANIMATED FEATURE FILM	Andrew Stanton	2
ANIMATED FEATURE FILM	Brad Bird	2
ART DIRECTION	Art Direction: Dante Ferretti; Set Decoration: Francesca Lo Schiavo	2
ART DIRECTION	Richard Day	2
BEST MOTION PICTURE	20th Century-Fox	2
BEST MOTION PICTURE	Paramount	2
BEST MOTION PICTURE	Sam Spiegel, Producer	2
BEST MOTION PICTURE	Arthur Freed, Producer	2
BEST PICTURE	Saul Zaentz, Producer	2
CINEMATOGRAPHY	Conrad L. Hall	2
CINEMATOGRAPHY	Sven Nykvist	2
CINEMATOGRAPHY	John Toll	2
CINEMATOGRAPHY	Janusz Kaminski	2
CINEMATOGRAPHY	Chris Menges	2
CINEMATOGRAPHY (Black-and-White)	James Wong Howe	2
CINEMATOGRAPHY (Black-and-White)	Joseph Ruttenberg	2
CINEMATOGRAPHY (Black-and-White)	William C. Mellor	2
COSTUME DESIGN	Albert Wolsky	2
COSTUME DESIGN	Jenny Beavan	2
COSTUME DESIGN	Mark Bridges	2
COSTUME DESIGN	Ann Roth	2
COSTUME DESIGN	Danilo Donati	2
COSTUME DESIGN	Ruth Carter	2
COSTUME DESIGN	Jacqueline Durran	2
COSTUME DESIGN (Black-and-White)	Piero Gherardi	2
COSTUME DESIGN (Black-and-White)	Helen Rose	2
COSTUME DESIGN (Color)	Irene Sharaff	2
DIRECTING	Milos Forman	2
DIRECTING	Ang Lee	2
DIRECTING	Billy Wilder	2
DIRECTING	Oliver Stone	2
DIRECTING	Joseph L. Mankiewicz	2
DIRECTING	George Stevens	2
DIRECTING	Leo McCarey	2
DIRECTING	Fred Zinnemann	2
DIRECTING	Clint Eastwood	2
DIRECTING	Alfonso Cuarón	2
DIRECTING	Elia Kazan	2
DIRECTING	David Lean	2
DIRECTING	Steven Spielberg	2
DIRECTING	Alejandro G. Iñárritu	2
DIRECTING	Frank Lloyd	2
DOCUMENTARY (Feature)	Jacques-Yves Cousteau, Producer	2
DOCUMENTARY (Feature)	Walt Disney, Producer	2
DOCUMENTARY (Short Subject)	Walt Disney, Producer	2
DOCUMENTARY (Short Subject)	Charles Guggenheim, Producer	2
FILM EDITING	William Reynolds	2
FILM EDITING	Arthur Schmidt	2
FOREIGN LANGUAGE FILM	Iran	2
FOREIGN LANGUAGE FILM	Argentina	2
FOREIGN LANGUAGE FILM	Hungary	2
FOREIGN LANGUAGE FILM	Switzerland	2
FOREIGN LANGUAGE FILM	Austria	2
FOREIGN LANGUAGE FILM	Germany	2
FOREIGN LANGUAGE FILM	Czechoslovakia	2
IRVING G. THALBERG MEMORIAL AWARD	Hal B. Wallis	2
MAKEUP	Rick Baker, David LeRoy Anderson	2
MAKEUP	Rick Baker	2
MUSIC (Music Score of a Dramatic or Comedy Picture)	Alfred Newman	2
MUSIC (Music Score of a Dramatic or Comedy Picture)	Franz Waxman	2
MUSIC (Music Score of a Dramatic or Comedy Picture)	Miklos Rozsa	2
MUSIC (Music Score of a Dramatic or Comedy Picture)	Max Steiner	2
MUSIC (Music Score--substantially original)	Maurice Jarre	2
MUSIC (Original Score)	Hans Zimmer	2
MUSIC (Original Score)	John Barry	2
MUSIC (Original Score)	Alexandre Desplat	2
MUSIC (Original Score)	Gustavo Santaolalla	2
MUSIC (Original Score)	Howard Shore	2
MUSIC (Original Song)	Music and Lyric by Kristen Anderson-Lopez and Robert Lopez	2
MUSIC (Original Song)	Music by Alan Menken; Lyric by Howard Ashman	2
MUSIC (Original Song)	Music and Lyric by Billie Eilish and Finneas O'Connell	2
MUSIC (Original Song)	Music and Lyric by Randy Newman	2
MUSIC (Scoring of Music--adaptation or treatment)	Andre Previn	2
MUSIC (Scoring)	Alfred Newman	2
MUSIC (Song)	Music and Lyrics by Jay Livingston and Ray Evans	2
MUSIC (Song)	Music by Sammy Fain; Lyrics by Paul Francis Webster	2
MUSIC (Song)	Music by Henry Mancini; Lyrics by Johnny Mercer	2
OUTSTANDING PRODUCTION	Columbia	2
OUTSTANDING PRODUCTION	Selznick International Pictures	2
SHORT FILM (Animated)	Frédéric Back, Producer	2
SHORT SUBJECT (Cartoon)	John Hubley and Faith Hubley, Producers	2
SHORT SUBJECT (One-reel)	Paramount	2
SHORT SUBJECT (One-reel)	Metro-Goldwyn-Mayer	2
SHORT SUBJECT (One-reel)	Gordon Hollingshead, Producer	2
SHORT SUBJECT (One-reel)	Robert Youngson, Producer	2
SOUND EDITING	Paul N.J. Ottosson	2
SOUND EDITING	Alan Robert Murray and Bub Asman	2
SOUND EFFECTS EDITING	Gary Rydstrom, Richard Hymns	2
SOUND MIXING	Christopher Boyes, Michael Semanick, Michael Hedges and Hammond Peek	2
SOUND RECORDING	Columbia Studio Sound Department, John Livadary, Sound Director	2
SOUND RECORDING	Paramount Publix Studio Sound Department	2
SOUND RECORDING	RKO Radio Studio Sound Department, Stephen Dunn, Sound Director	2
SOUND RECORDING	United Artists Studio Sound Department, Thomas T. Moulton, Sound Director	2
SPECIAL EFFECTS	Paramount Studio	2
WRITING (Motion Picture Story)	Dalton Trumbo	2
WRITING (Screenplay)	George Seaton	2
WRITING (Screenplay)	Joseph L. Mankiewicz	2
WRITING (Screenplay--based on material from another medium)	Robert Bolt	2
```

```sql
SELECT 
    categoria,
    nome_indicado AS vencedor_recorrente,
    COUNT(*) AS total_vitorias
FROM indicados_ao_oscar
WHERE vencedor = TRUE 
  AND nome_indicado IS NOT NULL 
  AND nome_indicado != ''
GROUP BY categoria, nome_indicado
HAVING COUNT(*) > 1
ORDER BY total_vitorias DESC, categoria ASC;
```

---

## Nível 13: Queries Criativas

**13.1** Encontre todos os filmes cujo nome começa com "The" e ganharam pelo menos um Oscar.

**13.2** Liste todos os indicados cujo nome contém um sobrenome composto (ex: "Mary-Louise Parker").

**13.3** Encontre todas as cerimônias onde houve empate (múltiplos vencedores na mesma categoria no mesmo ano).

**13.4** Crie uma query que simule uma "loteria" - selecione 5 filmes aleatórios que ganharam Melhor Filme.

**13.5** Encontre padrões nos nomes dos filmes vencedores (ex: quantos têm uma palavra só, duas palavras, etc.).

---

## Desafio Final: Dashboard Completo

**14.1** Crie UMA ÚNICA query de agregação que retorne um dashboard executivo com:
   - Total de indicações
   - Total de cerimônias
   - Total de vencedores
   - Categoria com mais indicações
   - Filme mais premiado
   - Ator/atriz mais indicado(a)
   - Década com mais premiações
   - Número de categorias únicas

Bons estudos! 🏆
