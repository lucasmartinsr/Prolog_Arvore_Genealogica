# Prolog_Arvore_Genealogica

%Relação de pais

%Ricardo e Luciane são pais de lucas, isabella e geovanna
progenitor(ricardo,lucas).
progenitor(luciane,lucas).
progenitor(ricardo,isabella).
progenitor(luciane,isabella).
progenitor(ricardo,geovanna).
progenitor(luciane,geovanna).

%ozair e magnolia  são pais de luciane,cristiane,daiane,lidiane,thays e lays
progenitor(magnolia,luciane).
progenitor(ozair,luciane).
progenitor(magnolia,cristiane).
progenitor(ozair,cristiane).
progenitor(magnolia,daiane).
progenitor(ozair,daiane).
progenitor(magnolia,lidiane).
progenitor(ozair,lidiane).
progenitor(magnolia,thays).
progenitor(ozair,thays).
progenitor(magnolia,lays).
progenitor(ozair,lays).


%divino e marizete são pais de ricardo,jaqueline,lilian,eliane,ieda
progenitor(divino,ricardo).
progenitor(marizete,ricardo).
progenitor(divino,jaqueline).
progenitor(marizete,jaqueline).
progenitor(divino,lilian).
progenitor(marizete,lilian).
progenitor(divino,eliane).
progenitor(marizete,eliane).
progenitor(divino,ieda).
progenitor(marizete,ieda).

%cristiane e juvenal são pais de matheus, nathalia e kuan

progenitor(juvenal,matheus).
progenitor(cristiane,matheus).
progenitor(juvenal,nathalia).
progenitor(cristiane,nathalia).
progenitor(juvenal,kuan).

%daiane e wilson são pais de joao_paulo,wilsin,daniele,bruna,debora
progenitor(wilson,joao_paulo).
progenitor(daiane,joao_paulo).
progenitor(wilson,wilsin).
progenitor(daiane,wilsin).
progenitor(wilson,daniele).
progenitor(daiane,daniele).
progenitor(wilson,bruna).
progenitor(daiane,bruna).
progenitor(wilson,debora).
progenitor(daiane,debora).

%lidiane e gilson são pais de igor,barbara,fernanda
progenitor(gilson,igor).
progenitor(lidiane,igor).
progenitor(wilson,barbara).
progenitor(daiane,barbara).
progenitor(wilson,fernanda).
progenitor(daiane,fernanda).


%ieda e welliton são pais de julia

progenitor(welliton,julia).
progenitor(ieda,julia).

%lillian e divino_chagas sõa pais de gabriel,henrrique

progenitor(divino_chagas,gabriel).
progenitor(lillian,gabriel).
progenitor(divino_chagas,henrrique).
progenitor(lillian,henrrique).




%CAMPO REFERENTE AO SEXO
%SEXO MARCULINO
sexo(ricardo,masculino).
sexo(lucas,masculino).
sexo(matheus,masculino).
sexo(ricardo,masculino).
sexo(kuan,masculino).
sexo(divino,masculino).
sexo(ozair,masculino).
sexo(juvenal,masculino).
sexo(joao_paulo,masculino).
sexo(wilsin,masculino).
sexo(wilson ,masculino).
sexo(gilson ,masculino).
sexo(igor,masculino).
sexo(welliton ,masculino).
sexo(gabriel ,masculino).
sexo(henrrique ,masculino).
sexo(divino_chagas ,masculino).


%SEXO FERMININO
sexo(luciane,feminino).
sexo(magnolia,feminino).
sexo(cristiane,feminino).
sexo(daiane,feminino).
sexo(lidiane,feminino).
sexo(thays,feminino).
sexo(lays,feminino).
sexo(marizete,feminino).
sexo(jaqueline,feminino).
sexo(lilian,feminino).
sexo(eliane,feminino).
sexo(ieda,feminino).
sexo(nathalia,feminino).
sexo(daniele,feminino).
sexo(bruna,feminino).
sexo(debora,feminino).
sexo(barbara,feminino).
sexo(fernanda,feminino).
sexo(julia,feminino).
sexo(ieda,feminino).
sexo(geovanna,feminino).
sexo(isabella,feminino).


%REGRAS


%AQUI O ALGORITMO PARA IDENTIFICAR IRMÃ 
irma(X,Y):- progenitor(A,X),progenitor(A,Y),X\==Y,sexo(X,feminino).

%AQUI O ALGORITMO PARA IDENTIFICAR IRMÃO
irmao(X,Y):- progenitor(A,X),progenitor(A,Y),X\==Y,sexo(X,masculino).

%AQUI O ALGORITMO PARA IDENTIFICAR O AVÔ
avô(X,Y):- progenitor(X,A),progenitor(A,Y),sexo(X,masculino).

%AQUI O ALGORITMO PARA IDENTIFICAR O AVÓ
avó(X,Y):- progenitor(X,A),progenitor(A,Y),sexo(X,feminino).

%AQUI O ALGORITMO PARA IDENTIFICAR O PAI
pai(X,Y):- progenitor(X,Y),sexo(X,masculino).

%AQUI O ALGORITMO PARA IDENTIFICAR A MÃE
mae(X,Y):- progenitor(X,Y),sexo(X,feminino).

%AQUI O ALGORITMO PARA IDENTIFICAR O TIO
tio(X,Y):- irmao(X,A), progenitor(A,Y).

%AQUI O ALGORITMO PARA IDENTIFICAR O TIA
tia(X,Y):- irma(X,A), progenitor(A,Y).

%AQUI O ALGORITMO PARA IDENTIFICAR O DESCENDENTE
descendente(X,Y):- progenitor(X,Y).
descendente(X,Y):- progenitor(X,A),descendente(A,Y).

%AQUI ALGORITMO PARA IDENTIFICAR FILHO
filho(Y,X):- progenitor(X,Y),sexo(Y,masculino).

%AQUI ALGORITMO PARA IDENTIFICAR FILHA
filho(Y,X):- progenitor(X,Y),sexo(Y,feminino).

%AQUI ALGORITMO PARA IDENTIFICAR PRIMO
primo(X,Y):- irmao(A,B), progenitor(A,X),progenitor(B,Y),x\==y.

%AQUI ALGORITMO PARA IDENTIFICAR PRIMA
prima(X,Y):- irma(A,B), progenitor(A,X),progenitor(B,Y),x\==y.

%AQUI ALGORITMO PARA IDENTIFICAR NETO
neto(X,Y):- progenitor(W,X), progenitor(Y,W),sexo(X,masculino).

%AQUI ALGORITMO PARA IDENTIFICAR NETA
neta(X,Y):- progenitor(W,X), progenitor(Y,W),sexo(X,feminino).






