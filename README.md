# bd_aula_04

Exercício 01- Crie um banco de dados para uma empresa de aviaçao. No banco, crie a tabela "Voo". Crie as consultas abaixo. Insira dados na tabela "Voo" que atendam às consultas. Apresente todos os voos com:

    Partida de Belo Horizonte.
    Destino Fortaleza.
    Viagem de volta agendada.
    Valor abaixo de R$ 950,00.
    Valor acima de R$ 1.200,00.
    Valor entre R$ 500,00 e R$ 800,00.
    Partida agendada para 2027.
    Volta agendada para 2028.
    Partida de Cuiabá e destino Curitiba.
    Partida de Minas Gerais.
    Destino Rio Grande do Sul.
    Partida de Tocantins ou do Pará.
    Destino Salvador ou Aracajú.
    Viagem de volta não agendada.
    Substring "es" na cidade/estado de partida.
    Substring "ta" na cidade/estado de destino.
    Substring "or" na cidade/estado de partida ou de destino.
__________________________________________________________________________________________________________________________________________________________________________________________________________________

Criar Banco de Dados:
CREATE DATABASE aviacao_db;
USE aviacao_db;

Criar Tabela Voo:
CREATE TABLE Voo (
id INT,
partida VARCHAR(100),
destino VARCHAR(100),
data_partida DATE,
data_volta DATE,
valor DECIMAL(10,2)
);

Inserir Dados:
INSERT INTO Voo VALUES
(1,'Belo Horizonte, MG','Fortaleza, CE','2027-01-10','2027-01-20',850.00),
 
(2,'Cuiabá, MT','Curitiba, PR','2027-03-05','2027-03-12',1300.00),
 
(3,'Palmas, TO','Salvador, BA','2026-11-15',NULL,650.00),
 
(4,'Belém, PA','Aracaju, SE','2027-08-01','2028-01-10',780.00),
 
(5,'Uberlândia, Minas Gerais','Porto Alegre, RS','2027-06-20','2028-02-15',1500.00),
 
(6,'Montes Claros, MG','Florianópolis, SC','2026-07-20',NULL,920.00),
 
(7,'Belo Horizonte, MG','Rio de Janeiro, RJ','2027-09-15','2027-09-25',500.00),
 
(8,'Santarém, Pará','Fortaleza, CE','2026-12-10','2028-03-18',1250.00);

Consultas
1. Partida de Belo Horizonte
SELECT *
FROM Voo
WHERE partida LIKE 'Belo Horizonte%';
----------------------------------------------
2. Destino Fortaleza
SELECT *
FROM Voo
WHERE destino LIKE 'Fortaleza%';
----------------------------------------------
3. Viagem de volta agendada
SELECT *
FROM Voo
WHERE data_volta IS NOT NULL;
----------------------------------------------
4. Valor abaixo de R$ 950,00
SELECT *
FROM Voo
WHERE valor < 950;
----------------------------------------------
5. Valor acima de R$ 1.200,00
SELECT *
FROM Voo
WHERE valor > 1200;
----------------------------------------------
6. Valor entre R$ 500,00 e R$ 800,00
SELECT *
FROM Voo
WHERE valor BETWEEN 500 AND 800;
----------------------------------------------
7. Partida agendada para 2027
SELECT *
FROM Voo
WHERE YEAR(data_partida) = 2027;
----------------------------------------------
8. Volta agendada para 2028
SELECT *
FROM Voo
WHERE YEAR(data_volta) = 2028;
----------------------------------------------
9. Partida de Cuiabá e destino Curitiba
SELECT *
FROM Voo
WHERE partida LIKE 'Cuiabá%'
AND destino LIKE 'Curitiba%';
----------------------------------------------
10. Partida de Minas Gerais
SELECT *
FROM Voo
WHERE partida LIKE '%MG%'
OR partida LIKE '%Minas Gerais%';
----------------------------------------------
11. Destino Rio Grande do Sul
SELECT *
FROM Voo
WHERE destino LIKE '%RS%'
OR destino LIKE '%Rio Grande do Sul%';
----------------------------------------------
12. Partida de Tocantins ou do Pará
SELECT *
FROM Voo
WHERE partida LIKE '%TO%'
OR partida LIKE '%Pará%';
----------------------------------------------
13. Destino Salvador ou Aracaju
SELECT *
FROM Voo
WHERE destino LIKE 'Salvador%'
OR destino LIKE 'Aracaju%';
----------------------------------------------
14. Viagem de volta não agendada
SELECT *
FROM Voo
WHERE data_volta IS NULL;
----------------------------------------------
15. Substring "es" na cidade/estado de partida
SELECT *
FROM Voo
WHERE partida LIKE '%es%';
----------------------------------------------
16. Substring "ta" na cidade/estado de destino
SELECT *
FROM Voo
WHERE destino LIKE '%ta%';
----------------------------------------------
17. Substring "or" na partida ou destino
SELECT *
FROM Voo
WHERE partida LIKE '%or%'
OR destino LIKE '%or%';

__________________________________________________________________________________________________________________________________________________________________________________________________________________
Exercício 02- Crie um banco de dados para uma empresa de hotelaria. No banco, crie a tabela "Hotel". Crie as consultas abaixo. Insira dados na tabela "Hotel" que atendam às consultas. Apresente todos os hotéis com:

    Cidade de Minas Gerais.
    Valor da diária abaixo de R$ 300,00.
    Cidade São Luís.
    Categoria 3 estrelas.
    Substring "resort" no nome do hotel.
    Cidade Recife ou Salvador.
    Tipo de acomodação "Quarto duplo".
    Valor da diária acima de R$ 100,00.
    Substring "elite" no nome do hotel ou da acomodação.
    Hotel com check-in agendado para 2027.
    Cidade Curitiba e acomodação tipo "Suite".
    Estado Rio Grande do Sul.
    Estado São Paulo ou Paraná.
    Hospedagem sem café incluso.
    Substring "standard" no tipo da acomodação.
    Valor da diária entre R$ 250,00 e R$ 450,00.
    Hotel com check-out agendado para 2028.
    Garagem inclusa na hospedagem.
    Garagem inclusa, mas sem café incluso.
    Café incluso, mas sem garagem inclusa.
__________________________________________________________________________________________________________________________________________________________________________________________________________________

CREATE DATABASE hotelaria_db;
USE hotelaria_db;
------------------------------------------------------------
Criar Tabela Hotel

CREATE TABLE Hotel (
id INT,
nome VARCHAR(200),
cidade VARCHAR(100),
estado VARCHAR(100),
categoria INT,
acomodacao VARCHAR(100),
valor_diaria DECIMAL(10,2),
cafe_incluso BOOLEAN,
garagem_inclusa BOOLEAN,
checkin DATE,
checkout DATE
);

------------------------------------------------------------
Inserir Dados
INSERT INTO Hotel VALUES
 
(1,'Resort Paraíso Tropical',
'Salvador',
'Bahia',
5,
'Suite',
650.00,
TRUE,
TRUE,
'2027-01-10',
'2027-01-20'),
 
(2,'Hotel Elite Business',
'Curitiba',
'Paraná',
4,
'Suite',
420.00,
TRUE,
TRUE,
'2026-06-20',
'2026-06-25'),
 
(3,'Pousada Mineira',
'Ouro Preto',
'Minas Gerais',
3,
'Quarto duplo',
250.00,
TRUE,
FALSE,
'2026-08-15',
'2026-08-18'),
 
(4,'Recife Palace',
'Recife',
'Pernambuco',
4,
'Quarto duplo',
280.00,
FALSE,
TRUE,
'2027-09-01',
'2027-09-05'),
 
(5,'Standard Hotel',
'São Luís',
'Maranhão',
3,
'Standard',
180.00,
FALSE,
FALSE,
'2026-05-01',
'2026-05-04'),
 
(6,'Resort Elite Premium',
'Gramado',
'Rio Grande do Sul',
5,
'Suite',
500.00,
TRUE,
TRUE,
'2028-02-12',
'2028-02-20'),
 
(7,'Hotel Econômico',
'Belo Horizonte',
'Minas Gerais',
2,
'Quarto duplo',
120.00,
TRUE,
FALSE,
'2027-07-14',
'2027-07-20');

------------------------------------------------------------------------------------------------------------------------
Consultas
1. Cidade de Minas Gerais

SELECT *
FROM Hotel
WHERE estado = 'Minas Gerais';
------------------------------------------------------------
2. Diária abaixo de R$ 300,00

SELECT *
FROM Hotel
WHERE valor_diaria < 300;
------------------------------------------------------------
3. Cidade São Luís

SELECT *
FROM Hotel
WHERE cidade = 'São Luís';
------------------------------------------------------------
4. Categoria 3 estrelas

SELECT *
FROM Hotel
WHERE categoria = 3;
------------------------------------------------------------
5. Substring "resort" no nome

SELECT *
FROM Hotel
WHERE nome LIKE '%resort%';
------------------------------------------------------------
6. Cidade Recife ou Salvador

SELECT *
FROM Hotel
WHERE cidade='Recife'
OR cidade='Salvador';
------------------------------------------------------------
7. Acomodação "Quarto duplo"

SELECT *
FROM Hotel
WHERE acomodacao='Quarto duplo';
------------------------------------------------------------
8. Diária acima de R$ 100,00

SELECT *
FROM Hotel
WHERE valor_diaria > 100;
------------------------------------------------------------
9. Substring "elite" no hotel ou acomodação

SELECT *
FROM Hotel
WHERE nome LIKE '%elite%'
OR acomodacao LIKE '%elite%';
------------------------------------------------------------
10. Check-in em 2027

SELECT *
FROM Hotel
WHERE YEAR(checkin)=2027;
------------------------------------------------------------
11. Curitiba e acomodação Suite

SELECT *
FROM Hotel
WHERE cidade='Curitiba'
AND acomodacao='Suite';
------------------------------------------------------------
12. Estado Rio Grande do Sul

SELECT *
FROM Hotel
WHERE estado='Rio Grande do Sul';
------------------------------------------------------------
13. Estado São Paulo ou Paraná

SELECT *
FROM Hotel
WHERE estado='São Paulo'
OR estado='Paraná';
------------------------------------------------------------
14. Sem café incluso

SELECT *
FROM Hotel
WHERE cafe_incluso = FALSE;
------------------------------------------------------------
15. Substring "standard" na acomodação

SELECT *
FROM Hotel
WHERE acomodacao LIKE '%standard%';
------------------------------------------------------------
16. Diária entre R$ 250 e R$ 450

SELECT *
FROM Hotel
WHERE valor_diaria BETWEEN 250 AND 450;
------------------------------------------------------------
17. Check-out em 2028

SELECT *
FROM Hotel
WHERE YEAR(checkout)=2028;
------------------------------------------------------------
18. Garagem inclusa

SELECT *
FROM Hotel
WHERE garagem_inclusa = TRUE;
------------------------------------------------------------
19. Garagem inclusa e sem café incluso

SELECT *
FROM Hotel
WHERE garagem_inclusa = TRUE
AND cafe_incluso = FALSE;
------------------------------------------------------------
20. Café incluso e sem garagem inclusa

SELECT *
FROM Hotel
WHERE cafe_incluso = TRUE
AND garagem_inclusa = FALSE;
