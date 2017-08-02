# Gestion d'une bibliothèque  
_(extrait de "Initiation à Merise", auteur inconnu)_

## Situation existante
Une bibliothèque de prêts utilise les documents suivants:

#### LISTE DES COLLECTIONS

Code collection | Nom collection | N° éditeur 
--- | --- | ---  
001 | PLEIADE | 01 
002 | FOLIO | 01 
003 | AILLEURS ET DEMAIN | 02 
004 | SUSKE EN WISKE | 03 
... | ... | ...  

#### LISTE DES ÉDITEURS 

N° | Nom 
--- | ---   
01 | GALLIMARD 
02 | LAFFONT 
03 | STANDAARD UITGEVERIJ 
... | ...   

#### LISTE DES AUTEURS

N° | Nom 
--- | ---   
0001 | MOLIÈRE 
... | ...   
... | ...   
0428 | HUGO 
0951 | WILLY VANDERSTEEN 
... | ...   



### FICHE LIVRE

```
CODE LIVRE  : 00328
TITRE       : STERRENROOD 
CODE AUTEUR : 0951
AUTEUR      : WILLY VANDERSTEEN
```

###### EXEMPLAIRES POSSÉDÉS:

| CODE COLLECTION | NOMBRE D'EXEMPLAIRES |
| --- | --- |
| 004 | 10 |
| 001 | 2 |


###### EMPRUNTS EN COURS:

|N° ADHÉRENT EMPRUNTEUR | DATE D'EMPRUNT | CODE COLLECTION DE L'EXEMPLAIRE EMPRUNTÉ
|--- | --- | ---   
|~~001~~ | ~~31/07/2017~~ | ~~004~~
|002 | 31/07/2017 | 004
|009 | 28/07/2017 | 001

La ligne est rayée lorsque l'exemplaire est rendu.



### FICHE ADHÉRENT

```
N° ADHÉRENT : 002
NOM         : STICHELBOUT 
ADRESSE     : 1 place Augustin Laurent, 59000 Lille 
```

### DEMANDE D'EMPRUNT

```
DATE D'EMPRUNT  : 31/07/2017
CODE LIVRE      : 00328
TITRE           : STERRENROOD 
N° COLLECTION   : 004
COLLECTION      : SUSKE EN WISKE
N° COLLECTION   : 004
N° ADHÉRENT     : 002
NOM             : STICHELBOUT 
SIGNATURE       :  
```

On note les règles de gestion suivantes: 

- un livre existe en 1 ou plusieurs exemplaires dans une ou plusieurs collections chez 1 ou plusieurs éditeurs; 
- un livre est emprunté ou non par 1 ou plusieurs adhérents dans la limite du nombre d'exemplaires disponibles; 
- un adhérent peut emprunter un ou plusieurs livres mais il ne peut pas emprunter plusieurs exemplaires du même livre dans la même collection.


## Objectif: 
Mettre en place un système d'information aisé à maintenir et tenant compte des règles de gestion de l'établissement.

## Solution proposée

#### 1. Dictionnaire des données (DD)

NOM	 | 	SIGNIFICATION	 | 	TYPE 	 | 	LONGUEUR	 | 	NATURE	 | 	INTÉGRITÉ
---	 | 	---	 | 	---	 | 	---	 | 	---	 | 	---	 
CODLIVR	 | 	code livre	 | 	N	 | 	5	 | 	élémentaire   signalétique 	 | 	
TITRE	 | 	titre livre	 | 	A	 | 	30	 | 	élémentaire   signalétique	 | 	
CODAUT	 | 	code auteur	 | 	N	 | 	4	 | 	élémentaire   signalétique	 | 	
NOMAUT	 | 	nom auteur	 | 	A	 | 	30	 | 	élémentaire   signalétique	 | 	
NBEX	 | 	nombre d'exemplaires	 | 	N	 | 	2	 | 	élémentaire   signalétique	 | 	entier > 0
CODCOL	 | 	code collection	 | 	N	 | 	3	 | 	élémentaire   signalétique	 | 	
NOMCOL	 | 	nom collection	 | 	A	 | 	30	 | 	élémentaire   signalétique	 | 	
CODADH	 | 	code adhérent	 | 	N	 | 	3	 | 	élémentaire   signalétique	 | 	
NOM	 | 	nom adhérent	 | 	A	 | 	30	 | 	élémentaire   signalétique	 | 	
RUE	 | 	rue 	 | 	A	 | 	30	 | 	élémentaire   signalétique	 | 	
CODPOST	 | 	code postal	 | 	N	 | 	5	 | 	élémentaire	signalétique | 	
VILLE	 | 	ville  | 	A	 | 	30	 | 	élémentaire   signalétique	 | 	
CODEDIT	 | 	code éditeur	 | 	N	 | 	2	 | 	élémentaire   signalétique	 | 	
NOMEDIT	 | 	nom éditeur	 | 	A	 | 	30	 | 	élémentaire   signalétique 	 | 	
DATE	 | 	date d’emprunt	 | 	N	 | 	8	 | 	élémentaire   mouvement	 | 	date plausible


#### 2. Modèle Conceptuel des Données (MCD)
![MCD](/images/MCD.jpg)



#### 3. Modèle logique des Données (MLD)
![MLD](/images/MLD.jpg)



#### 4. Script MySQL
![Cliquer ici pour afficher le script MySQL.](/scripts/script.sql)

---
