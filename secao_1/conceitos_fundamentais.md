
# Select / Where


### `Select`  
Esse comando nos permite recuperar informações de uma tabela.

- É possível combinar esse comando com outros para realizar queries mais complexas.

**Exemplo sintático para o comando `select`:**

```sql
SELECT column_name FROM table_name
-- Aqui estamos selecionando uma coluna de uma tabela
```

**Como o PostgreSQL opera:**

![Diagrama PostgreSQL](https://prod-files-secure.s3.us-west-2.amazonaws.com/3101f74e-8233-4b5a-a530-b97ea1c8ccf4/0665c217-2f43-41c9-b6d3-c376eb53d0f5/Untitled.png)

- Teremos uma base de dados constituída normalmente por diversas tabelas, cada uma dessas tabelas vai operar de forma análoga a uma planilha (spreadsheet), sendo formada por colunas e linhas.
- Ao usar o `select`, ele analisará qual a tabela que desejamos trabalhar e, em seguida, quais colunas dessa tabela queremos acessar.

```sql
SELECT c1 FROM table_1;
-- Nesse contexto, a coluna 1 da tabela 1 será completamente selecionada

-- Também é possível selecionar múltiplas colunas de uma tabela

SELECT c1, c2 FROM table_1;

-- Para selecionar todas as colunas de uma tabela usamos *

SELECT * FROM table_1;
```

- Não é uma boa prática utilizar `*`, pois isso aumentará o tráfego entre o servidor da base de dados e a aplicação, o que pode reduzir a velocidade de recuperação de resultados.
- Se possível, selecione apenas as colunas necessárias para a operação que você deseja realizar.
- O ponto e vírgula (`;`) é utilizado para denotar o final de uma query.
- Existe um histórico de queries, o que significa que você pode acessar todas as queries feitas e copiá-las de volta para o editor.

**Business situation:** Algo muito comum e fundamental ao usar SQL é ser capaz de traduzir uma situação de negócio em uma query concreta que forneça insights ou que responda à pergunta de negócio que você tem.

**Desafio 01:** Desejamos enviar um e-mail promocional para os nossos clientes existentes.

- Utilize `Select` para coletar o primeiro e o segundo nome de cada um dos clientes, assim como seus endereços de e-mail.

**Solução:**

```sql
SELECT first_name, last_name, email FROM customer;
```

### `Distinct`
Às vezes, uma coluna possui valores duplicados, e você pode querer selecionar apenas valores distintos/únicos. Esse comando é muito útil nessas circunstâncias.

```sql
SELECT DISTINCT column_ FROM table_;
-- Sintaxe

-- Também podemos usar parênteses para deixar mais claro
SELECT DISTINCT (column_) FROM table_;
```

**Exemplo:**

| Name   | Choice  |
|--------|---------|
| Zach   | Green   |
| David  | Green   |
| Claire | Yellow  |
| David  | Red     |

- Temos duas instâncias do nome "David" dentro dessa tabela. Quando selecionamos usando `distinct`, apenas os nomes distintos serão selecionados.

| Name   |
|--------|
| Zach   |
| David  |
| Claire |

- Nós não sabemos se o nome "David" foi uma entrada duplicada ou se são duas pessoas com o mesmo nome.
- Apenas os nomes únicos foram selecionados!

**Desafio 02:** Precisamos saber todos os tipos de avaliação que constituem o sistema de avaliação de filmes. Como resolver esse problema?

```sql
SELECT DISTINCT rating FROM film;
```

### `Count`

Função que retorna o número de linhas de entrada que atendem a uma condição específica de uma query.

- Podemos aplicar `COUNT` em uma coluna específica ou apenas passar `COUNT(*)`.

**Exemplo:**

```sql
SELECT COUNT(name) FROM table;
SELECT COUNT(choice) FROM table;
SELECT COUNT(*) FROM table;

-- Todos esses comandos retornarão 4
```

| Name   | Choice  |
|--------|---------|
| Zach   | Green   |
| David  | Green   |
| Claire | Yellow  |
| David  | Red     |

- A função `count` retornará 4, o total de elementos da coluna "name". Ou seja, `Count` retorna por si só o total de linhas em uma tabela ou coluna.

**Combinando:**

```sql
SELECT COUNT(DISTINCT name) FROM table;
-- A resposta será 3
```


