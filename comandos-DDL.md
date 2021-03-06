# Criando tabelas 
## estrutura
CREATE TABLE nome_tabela (
   nome_campo TIPO,
   nome_campo TIPO,
   nome_campo TIPO
);

## aplicação
CREATE TABLE ALUNO (
   MATRICULA NUMBER,
   NOME VARCHAR2(200),
   SEXO CHAR(1),
   DATA_NASC DATE
);

## Not null
CREATE TABLE ALUNO (
   MATRICULA NUMBER NOT NULL,
   NOME VARCHAR2(200) NOT NULL,
   SEXO CHAR(1),
   DATA_NASC DATE
);

### criação da not null no nível da tabela 
CREATE TABLE ALUNO (
  MATRICULA NUMBER CONSTRAINT NN_ALUNO_MATRICULA NOT NULL,
  NOME VARCHAR2(200) CONSTRAINT NN_ALUNO_NOME NOT NULL,
  SEXO CHAR(1),
  DATA_NASC DATE
);

## Unique key
CREATE TABLE MATERIA (
CODIGO NUMBER CONSTRAINT NN_MATERIA_CODIGO NOT NULL,
DESCRICAO VARCHAR2(200) CONSTRAINT UK_MATERIA_DESCRICAO UNIQUE
);

### criação da unique key no nível da tabela 
CREATE TABLE MATERIA (
  CODIGO NUMBER CONSTRAINT NN_MATERIA_CODIGO NOT NULL,
  DESCRICAO VARCHAR2(200),
  CONSTRAINT UK_MATERIA_DESCRICAO UNIQUE(DESCRICAO)
);

## Primary key
CREATE TABLE MATERIA (
CODIGO NUMBER CONSTRAINT PK_MATERIA_CODIGO PRIMARY KEY,
DESCRICAO VARCHAR2(200) CONSTRAINT UK_MATERIA_DESCRICAO UNIQUE
);

### criação da primary key no nível da tabela 
CREATE TABLE MATERIA (
CODIGO NUMBER,
SIGLA CHAR(2),
DESCRICAO VARCHAR2(200) UNIQUE,
CONSTRAINT PK_MATERIA_CODIGO_SIGLA PRIMARY KEY (CODIGO, SIGLA)
);

## Foreign key
CREATE TABLE CELULAR (
   COD_CELULAR NUMBER PRIMARY KEY,
   NUMERO VARCHAR2(10) UNIQUE,
   MATRICULA NUMBER(3)
   CONSTRAINT FK_CELULAR_ALUNO_MATRICULA
   REFERENCES ALUNO (MATRICULA)
);

CREATE TABLE ALUNO (
   MATRICULA NUMBER(3),
   NONME VARCHAR2(50),
   MATRICULA NUMBER(3)
   CONSTRAINT PK_ ALUNO_MATRICULA
   PRIMARY KEY (MATRICULA)
);


### criação da foreign key no nível da tabela 
CREATE TABLE CELULAR (
   COD_CELULAR NUMBER PRIMARY KEY,
   NUMERO VARCHAR2(10) UNIQUE,
   CPF VARCHAR2(14),
   MATRICULA NUMBER(3),
   CONSTRAINT FK_CELULAR_ALUNO_CPF_MATRICULA
   FOREIGN KEY (CPF, MATRICULA)
   REFERENCES ALUNO (CPF, MATRICULA)
);

## Check
CREATE TABLE ALUNO (
  MATRICULA NUMBER,
  NOME VARCHAR2(30),
  SEXO CHAR(1) CONSTRAINT CK_ALUNO_SEXO CHECK (SEXO IN (‘M’, ‘F’))
);

### criação da check no nível da tabela 
CREATE TABLE ALUNO (
   MATRICULA NUMBER,
   NOME VARCHAR2(30),
   SEXO CHAR(1),
   CONSTRAINT CK_ALUNO_SEXO CHECK (SEXO IN(‘M’, ‘F’))
);