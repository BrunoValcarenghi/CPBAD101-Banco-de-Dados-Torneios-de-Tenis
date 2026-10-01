# GABARITO LISTA EXERCÍCIOS

# Exercício 1: Insira pelo menos 5 países
## *Explicação:*  
Para cadastrar novos países no banco de dados, utilizamos o comando ***INSERT INTO.*** 
A tabela **pais** possui duas colunas:  
1- **codpais**: A chave primária (número inteiro único para cada país).  
2- **nomepais**: O nome do país (texto).  

Como as colunas seguintes do banco de dados (como a tabela cidade) dependem dos países cadastrados, é essencial criar esses registros primeiro.

## *Comando SQL:*  
```sql

INSERT INTO pais (codpais, nomepais) VALUES
    (1, 'Brasil'),
    (2, 'Espanha'),
    (3, 'França'),
    (4, 'Estados Unidos'),
    (5, 'Reino Unido');

```

# Exercício 2: Insira pelo menos 5 cidades
## *Explicação:*
O enunciado pede para inserir cinco localizações na tabela cidade. A tabela cidade requer o codpais como Chave Estrangeira (FK). Por isso, associamos cada cidade ao seu respectivo país cadastrado no Exercício 1:  

São Paulo e Rio de Janeiro $\rightarrow$ Brasil (codpais = 1)  
Madri $\rightarrow$ Espanha (codpais = 2)  
Paris $\rightarrow$ França (codpais = 3)  
Los Angeles $\rightarrow$ Estados Unidos (codpais = 4)  

## *Comando SQL:*  
```sql

INSERT INTO cidade (codcidade, nomecidade, codpais) VALUES
    (1, 'São Paulo', 1),
    (2, 'Madri', 2),
    (3, 'Paris', 3),       
    (4, 'Los Angeles', 4),
    (5, 'Rio de Janeiro', 1);

```

# Exercício 3: Insira torneios para essas cidades
## *Explicação:*
Agora que já temos as cidades cadastradas, vamos vincular os torneios de tênis a cada uma delas. A tabela torneio possui:

**codtorneio:** A Chave Primária (código único do torneio).  
**nometorneio:** O nome oficial do campeonato.  
**codcidade:** A Chave Estrangeira que indica em qual cidade o torneio é realizado.  

Fazemos a correspondência usando os **codcidade** do Exercício 2 ex:  
São Paulo Open (codcidade = 1 / São Paulo)

## *Comando SQL:*  
```sql

    INSERT INTO torneio (codtorneio, nometorneio, codcidade) VALUES
    (1, 'São Paulo Open', 1),
    (2, 'Mutua Madrid Open', 2),
    (3, 'Roland Garros', 3),
    (4, 'US Open', 4),
    (5, 'Rio Open', 5);

```
# Exercício 4: Insira tenistas de diferentes nacionalidades
## *Explicação:*
Neste passo, vamos cadastrar os atletas na tabela tenista. Segundo o nosso modelo, a tabela tenista possui:  
   
**codtenista:** Chave Primária (código único do atleta).  
**nometenista:** Nome completo do jogador.codcidade: Chave Estrangeira que indica a cidade com a qual o tenista está relacionado ex:  
Gustavo Kuerten (codcidade = 5 / Rio de Janeiro)
    
Vamos usar os **codcidade** das cidades que cadastramos no Exercício 2 para representar diferentes nacionalidades/origens.

## *Comando SQL:*  
```sql

INSERT INTO tenista (codtenista, nometenista, codcidade) VALUES
    (1, 'Gustavo Kuerten', 5),
    (2, 'Rafael Nadal', 2),
    (3, 'Novak Djokovic', 3),
    (4, 'Carlos Alcaraz', 2),
    (5, 'Beatriz Haddad Maia', 1);

```

# Exercício 5: Liste todos os países cadastrados
## *Explicação:*
Neste exercício, realizamos uma consulta simples de seleção na tabela pais.

Utilizamos o comando *SELECT* acompanhado do caractere curinga *, que indica ao banco de dados que desejamos retornar todas as colunas existentes na tabela (codpais e nomepais), sem aplicar nenhum filtro restritivo (*WHERE*).

## *Comando SQL:*  
```sql

    SELECT * FROM pais;

```

# Exercício 6: Liste as cidades com o nome da cidade e do país
## *Explicação:*
Para isso, listamos as duas tabelas (cidade e pais) separadas por vírgula no *FROM* e aplicamos um filtro na cláusula *WHERE* para relacionar a Chave Estrangeira **cidade.codpais** com a Chave Primária **pais.codpais**, garantindo que cada cidade seja exibida apenas com o seu país correto.

## *Comando SQL:*  
```sql

    SELECT c.nomecidade, p.nomepais
    FROM cidade c, pais p
    WHERE c.codpais = p.codpais;

```

# Exercício 7: Liste todos os tenistas por ordem alfabética com o nome da sua cidade
## *Explicação:*
Para relacionar cada tenista à sua respetiva cidade, realizamos o produto cartesiano entre as tabelas tenista e cidade.

Filtramos os registros no *WHERE* igualando a Chave Estrangeira **tenista.codcidade** com a Chave Primária cidade.**codcidade**. Por fim, utilizamos a cláusula *ORDER BY* no campo **t.nometenista** para classificar o resultado em ordem alfabética

## *Comando SQL:*  
```sql

    SELECT t.nometenista, c.nomecidade
    FROM tenista t, cidade c
    WHERE t.codcidade = c.codcidade
    ORDER BY t.nometenista;

```

# Exercício 8: Liste todos os patrocinadores e os respetivos tenistas patrocinados 
## *Explicação:*
Neste passo, inserimos os registros na tabela associativa participa para relacionar os tenistas aos torneios disputados e seus respetivos anos e colocações.

A tabela participa utiliza uma Chave Primária Composta pelos campos **codtenista**, **codtorneio** e **anotorneio**, além de guardar o atributo de **colocacao** do atleta no campeonato.

## *Comando SQL:*  
```sql

    INSERT INTO participa (codtenista, codtorneio, anotorneio, colocacao) VALUES
    (1, 3, 2001, 1),
    (2, 3, 2020, 1),
    (2, 2, 2021, 1),
    (3, 3, 2023, 1),
    (4, 4, 2022, 1);

```

# Exercício 9: Liste os tenistas e os torneios em que participaram a partir de 2020
## *Explicação:*
Para obter os tenistas e os respetivos torneios disputados a partir do ano de 2020, realizamos o produto cartesiano entre três tabelas: tenista, torneio e a tabela associativa participa.

Na cláusula *WHERE*, fazemos a junção das tabelas igualando as Chaves Estrangeiras assim como fizemos em exercícios anteriores. Adicionamos a condição ***p.anotorneio** >= 2020* para filtrar apenas as participações ocorridas a partir do ano de 2020.

Também vale ressaltar que quando queremos adicionar mais de uma condição na cláusula *WHERE* adicionamos o *AND*

## *Comando SQL:*  
```sql

    SELECT t.nometenista, tr.nometorneio, p.anotorneio, p.colocacao
    FROM tenista t, torneio tr, participa p
    WHERE p.codtenista = t.codtenista
    AND p.codtorneio = tr.codtorneio
    AND p.anotorneio >= 2020;

```
