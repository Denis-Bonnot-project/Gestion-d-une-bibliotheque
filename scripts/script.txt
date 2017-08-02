#------------------------------------------------------------
#        Script MySQL.
#------------------------------------------------------------


#------------------------------------------------------------
# Table: LIVRE
#------------------------------------------------------------

CREATE TABLE LIVRE(
        CODLIVR Int NOT NULL ,
        TITRE   Varchar (30) NOT NULL ,
        CODAUT  Int NOT NULL ,
        PRIMARY KEY (CODLIVR )
)ENGINE=InnoDB;


#------------------------------------------------------------
# Table: AUTEUR
#------------------------------------------------------------

CREATE TABLE AUTEUR(
        CODAUT Int NOT NULL ,
        NOMAUT Varchar (30) NOT NULL ,
        PRIMARY KEY (CODAUT )
)ENGINE=InnoDB;


#------------------------------------------------------------
# Table: ADHERENT
#------------------------------------------------------------

CREATE TABLE ADHERENT(
        CODADH  int (11) Auto_increment  NOT NULL ,
        NOM     Varchar (30) NOT NULL ,
        RUE     Varchar (30) NOT NULL ,
        CODPOST Int NOT NULL ,
        VILLE   Varchar (30) NOT NULL ,
        PRIMARY KEY (CODADH )
)ENGINE=InnoDB;


#------------------------------------------------------------
# Table: COLLECTION
#------------------------------------------------------------

CREATE TABLE COLLECTION(
        CODCOL  Int NOT NULL ,
        NOMCOL  Varchar (30) NOT NULL ,
        CODEDIT Int NOT NULL ,
        PRIMARY KEY (CODCOL )
)ENGINE=InnoDB;


#------------------------------------------------------------
# Table: EDITEUR
#------------------------------------------------------------

CREATE TABLE EDITEUR(
        CODEDIT Int NOT NULL ,
        NOMEDIT Varchar (30) NOT NULL ,
        PRIMARY KEY (CODEDIT )
)ENGINE=InnoDB;


#------------------------------------------------------------
# Table: EXISTE
#------------------------------------------------------------

CREATE TABLE EXISTE(
        NBEX    Int NOT NULL ,
        CODLIVR Int NOT NULL ,
        CODCOL  Int NOT NULL ,
        PRIMARY KEY (CODLIVR ,CODCOL )
)ENGINE=InnoDB;


#------------------------------------------------------------
# Table: EMPRUNTE
#------------------------------------------------------------

CREATE TABLE EMPRUNTE(
        DATEPRET Date ,
        CODADH   Int NOT NULL ,
        CODCOL   Int NOT NULL ,
        CODLIVR  Int NOT NULL ,
        PRIMARY KEY (CODADH ,CODCOL ,CODLIVR )
)ENGINE=InnoDB;

ALTER TABLE LIVRE ADD CONSTRAINT FK_LIVRE_CODAUT FOREIGN KEY (CODAUT) REFERENCES AUTEUR(CODAUT);
ALTER TABLE COLLECTION ADD CONSTRAINT FK_COLLECTION_CODEDIT FOREIGN KEY (CODEDIT) REFERENCES EDITEUR(CODEDIT);
ALTER TABLE EXISTE ADD CONSTRAINT FK_EXISTE_CODLIVR FOREIGN KEY (CODLIVR) REFERENCES LIVRE(CODLIVR);
ALTER TABLE EXISTE ADD CONSTRAINT FK_EXISTE_CODCOL FOREIGN KEY (CODCOL) REFERENCES COLLECTION(CODCOL);
ALTER TABLE EMPRUNTE ADD CONSTRAINT FK_EMPRUNTE_CODADH FOREIGN KEY (CODADH) REFERENCES ADHERENT(CODADH);
ALTER TABLE EMPRUNTE ADD CONSTRAINT FK_EMPRUNTE_CODCOL FOREIGN KEY (CODCOL) REFERENCES COLLECTION(CODCOL);
ALTER TABLE EMPRUNTE ADD CONSTRAINT FK_EMPRUNTE_CODLIVR FOREIGN KEY (CODLIVR) REFERENCES LIVRE(CODLIVR);
