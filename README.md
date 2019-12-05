# Banco de Dados com DBeaver e Heroku.

#### 1. Primeiro criar um New App no Heroku, ir na opção Resources e no campo Add-ons adicionar Heroku Postgres.

#### 2. Dentro de Heroku Postgres ir em Settings e View Credentials para pegar os dados de acesso que irão conectar com o Dbeaver.

#### 3. No Dbeaver ir na opção New Database Connection e selecionar a opção PostgreSQL, usar as credenciais do Heroku para conectar.

#### 4. Ir na aba New SQL Editor para criar tabelas e colunas usando os códigos abaixo:

```
create table tbl_cliente (
	CodCliente integer CONSTRAINT pk_CodCliente primary key, -- 
	nome varchar(50) not null, -- 
	DataNasc date,
	genero char(1),
	email varchar(100)
	);

create table tbl_produto (
	CodProduto integer constraint pk_codProduto primary key,
	nome_produto varchar(50) not null,
	descrição varchar(100),
	estoque int,
	valor numeric(9,2)
	);
	
create table tbl_pedido (
	CodPedido integer constraint pk_CodPedido primary key,
	TotalPedido numeric(10,2),
	fk_CodCliente integer references tbl_cliente(CodCliente),
	fk_CodProduto integer references tbl_produto(CodProduto)
	);
```	
	

	
	
#### 5. Inserindo informações dentro das colunas criadas em cada tabela com os códigos abaixo:

```
insert into tbl_cliente(codcliente, nome, datanasc, genero, email) values 
        (1, 'Tercio Rodrigues', '1994-03-25', 'M', 'tercio25@gmail.com'),
        (2, 'Gabriela Amaral', '1993-02-23', 'F', 'gabriela@gmail.com'),
        (3, 'Jordana Da Silva', '1996-04-11', 'F', 'jordana@gmail.com'),
        (4, 'Mariele Franco', '2015-03-07', 'F', 'mariele@gmail.com'),
        (5, 'Marcelo Yuri', '1988-08-12', 'M', 'marcelo@gmail.com'),
        (6, 'Paola Nardini', '1973-07-29', 'F', 'paola@gmail.com'),
        (7, 'Paulo Guedes', '2003-01-09', 'M', 'paulo@gmail.com'),
        (8, 'Mariana Correa', '2005-02-02', 'F', 'mariana@gmail.com');
	
insert into tbl_produto(codproduto, nome_produto, descrição, estoque, valor) values 
        (1, 'Iphone 11', 'Apple Iphone 11 Preto', '10', '6999'),
        (2, 'Airpods', 'Fones sem fio', '07', '1299'),
        (3, 'MacBook', 'Notebook i7', '01', '12000'),
        (4, 'Imac', 'All in one Apple', '02', '150.00'),
        (5, 'Capinha', 'Capinha Iphone 6S vermelha', '15', '199'),
        (6, 'Teclado', 'Teclado sem fio', '06', '399'),
        (7, 'Mouse', 'Mouse sem fio', '22', '259'),
        (8, 'Fone', 'Fone com fio', '199', '99');
 
insert into tbl_pedido(codpedido, fk_codcliente, fk_codproduto, totalpedido) values
	(1,1,2,'99'),
	(2,2,3,'99'),
	(3,3,4,'99'),
	(4,4,5,'99'),
	(5,5,1,'99');
	(6,6,4,'99'),
	(7,7,5,'99'),
	(8,8,1,'99');
```	

#### 6. Comandos para adicionar, editar, deletar e atualizar:

Adicionar nova coluna a tabela:
```
ALTER TABLE table_name
ADD COLUMN new_columm_name date_type;

ALTER TABLE tbl_cliente
ADD COLUMN CPF varchar(50);
```

Alterar o tipo da coluna:
```
ALTER TABLE table_name
ALTER COLUMN column_name TYPE new_data_type;

ALTER TABLE tbl_cliente
ALTER COLUMN nome TYPE varchar(40);
```

Deletar uma coluna ou tabela:
```
ALTER TABLE table_name
DROP COLUMN column_name;

ALTER TABLE tbl_cliente
DROP COLUMN CPF;

DROP TABLE table_name;

DROP TABLE tbl_cliente;
```

Atualizar dados dentro de uma coluna:
```
update tbl_cliente
set nome = 'Gabriela Nascimento'
where
	codcliente = 2;
```

Selecionar dados dentro de uma tabela ou coluna:
```
select * from tbl_cliente
where codcliente = 2;

select * from tbl_cliente
WHERE genero ='M' AND nome LIKE 'Terc%';
```







	
	






