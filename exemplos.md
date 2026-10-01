```sql

    --Países
    INSERT INTO pais (codpais, nomepais) VALUES
        (1, 'Brasil'),
        (2, 'Espanha'),
        (3, 'França'),
        (4, 'Estados Unidos'),
        (5, 'Reino Unido'),
        (6, 'Itália'),
        (7, 'Sérvia'),
        (8, 'Suíça'),
        (9, 'Austrália'),
        (10, 'Polónia');

    -- Cidades
    INSERT INTO cidade (codcidade, nomecidade, codpais) VALUES
        (1, 'Rio de Janeiro', 1),
        (2, 'Madri', 2),
        (3, 'Paris', 3),
        (4, 'Nova York', 4),
        (5, 'Londres', 5),
        (6, 'Roma', 6),
        (7, 'Belgrado', 7),
        (8, 'Basileia', 8),
        (9, 'Melbourne', 9),
        (10, 'Varsóvia', 10);

    -- Torneios
    INSERT INTO torneio (codtorneio, nometorneio, codcidade) VALUES
        (1, 'Rio Open', 1),
        (2, 'Mutua Madrid Open', 2),
        (3, 'Roland Garros', 3),
        (4, 'US Open', 4),
        (5, 'Wimbledon', 5),
        (6, 'Internazionali d Italia', 6),
        (7, 'Serbia Open', 7),
        (8, 'Swiss Indoors', 8),
        (9, 'Australian Open', 9),
        (10, 'BNP Paribas Open', 4);

    -- Tenistas
    INSERT INTO tenista (codtenista, nometenista, codcidade) VALUES
        (1, 'Gustavo Kuerten', 1),
        (2, 'Rafael Nadal', 2),
        (3, 'Novak Djokovic', 7),
        (4, 'Roger Federer', 8),
        (5, 'Carlos Alcaraz', 2),
        (6, 'Iga Swiatek', 10),
        (7, 'Jannik Sinner', 6),
        (8, 'Andy Murray', 5),
        (9, 'Aryna Sabalenka', 4),
        (10, 'Beatriz Haddad Maia', 1);

    -- Patrocinadores
    INSERT INTO patrocinador (codpatrocinador, nomepatrocinador) VALUES
        (1, 'Nike'),
        (2, 'Adidas'),
        (3, 'Lacoste'),
        (4, 'Head'),
        (5, 'Babolat'),
        (6, 'Wilson'),
        (7, 'Uniqlo'),
        (8, 'ASICS'),
        (9, 'Yonex'),
        (10, 'Rolex');

    -- Patrocina
    INSERT INTO patrocina (codpatrocinador, codtenista) VALUES
        (1, 2), -- Nike patrocina Rafael Nadal
        (1, 5), -- Nike patrocina Carlos Alcaraz
        (1, 7), -- Nike patrocina Jannik Sinner
        (1, 10),-- Nike patrocina Bia Haddad
        (2, 6), -- Adidas patrocina Iga Swiatek
        (3, 1), -- Lacoste patrocinou Guga
        (3, 3), -- Lacoste patrocina Novak Djokovic
        (4, 3), -- Head patrocina Novak Djokovic
        (5, 2), -- Babolat patrocina Rafael Nadal
        (7, 4); -- Uniqlo patrocina Roger Federer

    -- Participa
    INSERT INTO participa (codtenista, codtorneio, anotorneio, colocacao) VALUES
        (1, 3, 1997, 1),  -- Guga campeão de Roland Garros em 1997
        (1, 3, 2000, 1),  -- Guga campeão de Roland Garros em 2000
        (1, 3, 2001, 1),  -- Guga campeão de Roland Garros em 2001
        (2, 3, 2020, 1),  -- Nadal campeão de Roland Garros em 2020
        (2, 2, 2017, 1),  -- Nadal campeão de Madri em 2017
        (3, 9, 2023, 1),  -- Djokovic campeão do Australian Open em 2023
        (4, 5, 2017, 1),  -- Federer campeão de Wimbledon em 2017
        (5, 4, 2022, 1),  -- Alcaraz campeão do US Open em 2022
        (6, 3, 2023, 1),  -- Swiatek campeã de Roland Garros em 2023
        (10, 3, 2023, 3); -- Bia Haddad semifinalista (3º/4º lugar) em Roland Garros em 2023

```