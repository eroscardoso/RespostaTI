# RespostaTI
Resposta TI - Eros P Cardoso
Questão 1. Quais alterações devemos fazer nessa estrutura para que o cliente consiga fazer mais de um serviço por solicitação?

Criaria uma nova entidade (Solicitação) em que cada solicitação (1) pode ter vários serviços atrelados. A tabela Solicitação teria os seguintes campos:
ID (auto incrementável)
ID Serviço
ID Ordem Serviço

A outra alteração seria na tabela Ordem de Serviço, onde eu removeria o campo ID Serviço.


Questão 2. E se a mesma ordem de serviço tivesse serviços para endereços diferentes. Como ficaria a nova estrutura de dados?

Acrescentaria o campo “Endereço de serviço” na tabela Ordem de Serviço


Questão 3. Utilizando qualquer Linguagem de Consulta Estruturada (SQL) e considerando a nova estrutura de dados criada na questão anterior:
    a. Selecione todos os clientes e a quantidade de ordem de serviços
SELECT CLIENTE.NOME, COUNT(*), ORDEM_DE_SERVICO.ID WHERE CLIENTE.ID = ORDEM_DE_SERVICO.IDCLIENTE

    b. Selecione todas as Ordens de Serviços com mais de um serviço
SELECT ID, COUNT (*) FROM ORDEM_DE_SERVICO GROUP BY ID HAVING COUNT (*) >= 2

    c. Selecione os serviços mais vendidos
SELECT NOME_SERVICO FROM SERVICOS ORDER BY (COUNT(ORDEM_DE_SERVICO.IDSERVICO) DESC)

    d. Atualize o valor final de todos os serviços em 12%
UPDATE SERVICOS SET VALOR_FINAL = VALOR_FINAL*1.12

    e. Remova a última ordem de serviço criada
DELETE FROM ORDEM_DE_SERVICO WHERE ID = MAX (ID)

    f. Insira um cliente
INSERT INTO CLIENTE (NOME, EMAIL, DTNASCIMENTO, TELCELULAR, TELRESIDENCIA)  VALUES ("JACK",  "JACK@EMAIL.COM",  01011990, 31999887766, 3134567890)
