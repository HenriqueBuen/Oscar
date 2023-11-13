# Atividade de Banco de Dados - Oscar

Este repositório é dedicado a uma série de consultas SQL simuladas para explorar dados relacionados ao Oscar. As consultas abordam uma variedade de perguntas sobre indicados, vencedores, filmes e categorias de premiação.
Estrutura do Banco de Dados

A estrutura do banco de dados é hipotética, incluindo tabelas essenciais como indicacoes, categorias, filmes, diretores, entre outras, conforme necessário para suportar as consultas simuladas. As instruções assumem a presença dessas tabelas e campos.
Consultas SQL

### Quantas vezes Natalie Portman foi indicada ao Oscar?

sql

    SELECT COUNT(*) AS total_indicacoes
    FROM indicacoes
    WHERE nome_atriz = 'Natalie Portman';

### Quantos Oscars Natalie Portman ganhou?

sql

    SELECT COUNT(*) AS total_oscars
    FROM indicacoes
    WHERE nome_atriz = 'Natalie Portman' AND vencedor = 1;

### Amy Adams já ganhou algum Oscar?

sql

    SELECT COUNT(*) AS total_oscars
    FROM indicacoes
    WHERE nome_atriz = 'Amy Adams' AND vencedor = 1;

### A série de filmes Toy Story ganhou um Oscar em quais anos?

sql

    SELECT DISTINCT ano
    FROM indicacoes
    WHERE filme LIKE 'Toy Story%' AND vencedor = 1;

### A partir de que ano a categoria "Actress" deixa de existir?

sql

    SELECT MIN(ano)
    FROM categorias
    WHERE nome_categoria = 'Actress';

### O primeiro Oscar para melhor Atriz foi para quem? Em que ano?

sql

    SELECT nome_atriz, MIN(ano) AS primeiro_oscar
    FROM indicacoes
    WHERE categoria = 'Actress' AND vencedor = 1
    GROUP BY nome_atriz
    ORDER BY primeiro_oscar
    LIMIT 1;

### Na coluna/campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0.

sql

    UPDATE indicacoes
    SET vencedor = CASE WHEN vencedor = 'Sim' THEN 1 ELSE 0 END;
    
    Em qual edição do Oscar "Crash" ganhou o prêmio principal?
    
    sql
    
    SELECT ano
    FROM indicacoes
    WHERE filme = 'Crash' AND categoria = 'Best Picture' AND vencedor = 1;

### Dê um Oscar para um filme que merece muito, mas não ganhou.
(Escolha um filme e um ano fictício)

sql

    INSERT INTO indicacoes (ano, categoria, filme, vencedor)
    VALUES (2025, 'Best Picture', 'Filme Incrível', 1);

### O filme Central do Brasil aparece no Oscar?

sql

    SELECT COUNT(*) AS presenca
    FROM indicacoes
    WHERE filme = 'Central do Brasil';

### Inclua no banco 3 filmes que nunca foram nomeados ao Oscar, mas que merecem ser.
(Escolha três filmes fictícios e um ano fictício)

sql

    INSERT INTO indicacoes (ano, categoria, filme, vencedor)
    VALUES
      (2025, 'Best Picture', 'Filme1', 1),
      (2025, 'Best Picture', 'Filme2', 0),
      (2025, 'Best Picture', 'Filme3', 0);

### Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?
(Substitua ANO_PELO_QUAL_VOCE_NASCEU pelo ano correto)

sql

    SELECT 
      (SELECT filme FROM indicacoes WHERE ano = ANO_PELO_QUAL_VOCE_NASCEU AND categoria = 'Best Picture' AND vencedor = 1) AS melhor_filme,
      (SELECT nome_atriz FROM indicacoes WHERE ano = ANO_PELO_QUAL_VOCE_NASCEU AND categoria = 'Actress' AND vencedor = 1) AS melhor_atriz,
      (SELECT nome_diretor FROM indicacoes WHERE ano = ANO_PELO_QUAL_VOCE_NASCEU AND categoria = 'Director' AND vencedor = 1) AS melhor_diretor;

### Agora procure 7 atrizes que não sejam americanas, europeias ou brasileiras. Vamos cadastrá-las no nosso banco com o prêmio que você quiser.
(Escolha atrizes fictícias e um prêmio fictício)

sql

    INSERT INTO indicacoes (ano, categoria, nome_atriz, vencedor)
    VALUES
    (2025, 'Actress', 'Atriz1', 1),
    (2025, 'Actress', 'Atriz2', 0),
    (2025, 'Actress', 'Atriz3', 0),
    (2025, 'Actress', 'Atriz4', 1),
    (2025, 'Actress', 'Atriz5', 0),
    (2025, 'Actress', 'Atriz6', 0),
    (2025, 'Actress', 'Atriz7', 0);

### Agora vamos falar da sua vida. Me diga o nome de uma pessoa que você admira e o que ela fez na sua vida. Agora me diz: Quê prêmio essa pessoa merece?
(Substitua PESSOA_E_REALIZACOES e PREMIO_MERECE pelo nome da pessoa que você admira e suas realizações, e o prêmio que você acredita que ela merece)

sql

    INSERT INTO indicacoes (ano, categoria, nome_atriz, vencedor)
    VALUES
      (2025, 'Achievement', 'PESSOA_E_REALIZACOES', 1),
      (2025, 'Achievement', 'PESSOA_E_REALIZACOES', 0),
      (2025, 'Achievement', 'PESSOA_E_REALIZACOES', 0);

Executando os Comandos

Para executar os comandos, certifique-se de ter um servidor MySQL em execução. Importe o script SQL fornecido neste repositório para criar o banco de dados e suas tabelas. Adapte os comandos conforme necessário para reflet
