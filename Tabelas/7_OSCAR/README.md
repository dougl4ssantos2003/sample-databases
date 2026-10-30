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

```sql
```

**5.5** Quantos indicados têm exatamente 1 indicação na história?

R:

```sql
```

**5.6** Qual o maior números de indicados em um único ano? Essa é uma pergunta franca.

R:

```sql
```

---

## Nível 6: Análise de Filmes

### Toy Story

**6.1** A série de filmes Toy Story ganhou Oscars em quais anos?

**6.2** Quantas indicações a franquia Toy Story recebeu no total?

**6.3** Em quais categorias os filmes Toy Story foram indicados?

### Crash

**6.4** Em qual edição do Oscar o filme "Crash" concorreu?

**6.5** Quantas indicações o filme "Crash" recebeu?

**6.6** "Crash" ganhou o Oscar de Melhor Filme?

### Central do Brasil

**6.7** O filme "Central do Brasil" aparece no banco de dados?

**6.8** Se sim, quantas indicações "Central do Brasil" recebeu?

---

## Nível 7: Operações de Atualização

**7.1** No campo "vencedor", altere todos os valores "true" (string) para true (booleano) e "false" (string) para false (booleano).

**7.2** Inclua no banco 3 filmes que nunca foram nomeados ao Oscar, mas que você acha que merecem. Use dados fictícios, mas realistas.

**7.3** Adicione uma nova categoria chamada "BEST INTERNATIONAL FEATURE FILM" com alguns vencedores recentes (2020-2024).

**7.4** Corrija possíveis erros de digitação nos nomes dos filmes (ex: espaços extras, caracteres especiais desnecessários).

**7.5** Remova todos os registros com valor NULL no campo nome_do_filme.

---

## Nível 8: Análise Temporal

**8.1** Quantas indicações aconteceram por década? Agrupe por década (1920s, 1930s, etc.) e mostre o total.

**8.2** Em qual década houve o maior número de indicações?

**8.3** Como o número de categorias evoluiu ao longo dos anos? Mostre quantas categorias únicas existiam a cada década.

**8.4** Qual foi o ano com o maior número de indicações registradas?

**8.5** Calcule a taxa de crescimento de indicações comparando a primeira década com a última.

---

## Nível 9: Questões Históricas e Sociais

### Representatividade

**9.1** Sidney Poitier foi o primeiro ator negro a ser indicado ao Oscar. Em que ano ele foi indicado? Por qual filme?

**9.2** Sidney Poitier ganhou o Oscar nessa indicação?

**9.3** Quantos atores/atrizes negros foram indicados na categoria ACTOR ou ACTRESS antes de 1970?

**9.4** Liste todos os filmes dirigidos por mulheres que ganharam algum Oscar.

### Coincidências

**9.5** Denzel Washington e Jamie Foxx já concorreram ao Oscar no mesmo ano?

**9.6** Se sim, em qual ano e quem ganhou?

**9.7** Encontre casos onde o mesmo filme ganhou Oscar em múltiplas categorias na mesma cerimônia. Mostre o nome do filme e quantas categorias ele venceu.

---

## Nível 10: Análise Avançada

**10.1** Quais filmes ganharam o Oscar de Melhor Filme ("OUTSTANDING PICTURE" ou "BEST PICTURE") e Melhor Diretor na mesma cerimônia?

**10.2** Qual filme recebeu o maior número de indicações em uma única cerimônia?

**10.3** Qual filme teve a maior taxa de conversão (porcentagem de indicações que viraram vitórias)?

**10.4** Encontre atores que foram indicados em anos consecutivos. Liste o nome e os anos.

**10.5** Qual a média de indicações por cerimônia ao longo da história?

**10.6** Identifique "surpresas" - indicados em categorias principais (ACTOR, ACTRESS, BEST PICTURE) cujo filme só teve uma indicação.

---

## Nível 11: Desafios Complexos

**11.1** Crie um ranking dos 10 filmes mais premiados da história (que ganharam mais Oscars).

**11.2** Crie um ranking dos 10 artistas (atores/diretores) mais indicados da história, independente da categoria.

**11.3** Encontre "azarões" - artistas com mais de 5 indicações e 0 vitórias.

**11.4** Qual categoria tem a maior concentração de vitórias (menos vencedores diferentes ao longo do tempo)?

**11.5** Calcule a "competitividade" de cada categoria (média de indicados por cerimônia).

**11.6** Encontre filmes que foram indicados em uma categoria em um ano e ganharam em outra categoria em outro ano.

---

## Nível 12: Casos Práticos

### Cenário 1: Curadoria de Mostra de Cinema

Você está organizando uma mostra de cinema e precisa selecionar filmes.

**12.1** Liste os 20 filmes mais premiados do Oscar para sua mostra.

**12.2** Selecione 5 filmes de cada década (1930s até 2020s) que ganharam pelo menos um Oscar.

**12.3** Crie uma lista de "clássicos esquecidos" - filmes que ganharam Oscars, mas são de mais de 50 anos atrás.

### Cenário 2: Análise para Documentário

Você está produzindo um documentário sobre a história do Oscar.

**12.4** Identifique os 5 momentos mais importantes (cerimônias com mais premiações históricas).

**12.5** Liste todos os "primeiros" históricos (primeira mulher a ganhar melhor direção, primeiro ator negro, etc.) - use sua criatividade para encontrar esses marcos.

**12.6** Encontre casos de "injustiça" - filmes/atores muito indicados, mas que nunca ganharam.

### Cenário 3: Estatísticas para Apostas

Você trabalha para um site de apostas e precisa de estatísticas.

**12.7** Qual a probabilidade histórica de um filme indicado em 10 categorias ganhar Melhor Filme?

**12.8** Atores que ganharam Melhor Ator tendem a ter quantas indicações antes da primeira vitória?

**12.9** Qual categoria tem os vencedores mais "previsíveis" (mesmo artista/filme ganha múltiplas vezes)?

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
