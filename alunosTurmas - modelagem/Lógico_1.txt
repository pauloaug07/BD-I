/* Lógico_1: */

CREATE TABLE Alunos (
    RM int PRIMARY KEY,
    Nome varchar,
    Dt_Nascimento int,
    Nome_Mae varchar
);

CREATE TABLE Turmas (
    SiglaTurma varchar PRIMARY KEY,
    Descricao varchar
);

CREATE TABLE Associacao (
    RM int,
    Sigla_Turma varchar,
    PRIMARY KEY (RM, Sigla_Turma)
);

CREATE TABLE Relacionamento_1 (
    fk_Alunos_RM int,
    fk_Associacao_RM int,
    fk_Associacao_Sigla_Turma varchar
);

CREATE TABLE Relacionamento_2 (
    fk_Turmas_SiglaTurma varchar,
    fk_Associacao_RM int,
    fk_Associacao_Sigla_Turma varchar
);
 
ALTER TABLE Relacionamento_1 ADD CONSTRAINT FK_Relacionamento_1_1
    FOREIGN KEY (fk_Alunos_RM)
    REFERENCES Alunos (RM)
    ON DELETE SET NULL;
 
ALTER TABLE Relacionamento_1 ADD CONSTRAINT FK_Relacionamento_1_2
    FOREIGN KEY (fk_Associacao_RM, fk_Associacao_Sigla_Turma)
    REFERENCES Associacao (RM, Sigla_Turma)
    ON DELETE SET NULL;
 
ALTER TABLE Relacionamento_2 ADD CONSTRAINT FK_Relacionamento_2_1
    FOREIGN KEY (fk_Turmas_SiglaTurma)
    REFERENCES Turmas (SiglaTurma)
    ON DELETE SET NULL;
 
ALTER TABLE Relacionamento_2 ADD CONSTRAINT FK_Relacionamento_2_2
    FOREIGN KEY (fk_Associacao_RM, fk_Associacao_Sigla_Turma)
    REFERENCES Associacao (RM, Sigla_Turma)
    ON DELETE SET NULL;