# Nomeados ao Oscar

Contém a base de indicados ao Oscar em formato JSON para treinar comandos de consulta no MongoDB. 

* Quantas vezes Natalie Portman foi indicada ao Oscar?

R: 3 vezes

Q:
```sql
select count(*) from indicados
where "Name"
Like "%Natalie Portman%";
```

* Quantos Oscars Natalie Portman ganhou?

R: 1 vez

Q:
```sql
select count(*) from indicados_ao_oscar
where nome_do_indicado
like "%Natalie Portman%"
and vencedor = "true";
```

* Amy Adams já ganhou algum Oscar?

R: False

Q:
```sql
select nome_do_indicado, vencedor
from indicados_ao_oscar
where nome_do_indicado like "%Amy Adams%";
```

* A série de filmes Toy Story ganhou um Oscar em quais anos?
  
R: 2011 e 2020

Q:
```sql
select * from indicados_ao_oscar
where nome_do_filme like "%toy story%"
and vencedor = "true";
```

* A partir de que ano que a categoria "Actress" deixa de existir?

R: 1976

Q:
```sql
select ano_filmagem, ano_cerimonia, categoria
from indicados_ao_oscar
where categoria = "Actress"
order by ano_cerimonia desc ;
```
 

* Quem ganhou o primeiro Oscar para Melhor Atriz? Em que ano?

R: Janet Gaynor

Q:
```sql
select * from indicados_ao_oscar
where categoria= "ACTRESS"
and vencedor = "true";
```


* Na campo "Vencedor", altere todos os valores com "true" para 1 e todos os valores "false" para 0.

R: OK

Q:
```sql
update indicados_ao_oscar set vencedor = "1" where vencedor = "true";
update indicados_ao_oscar set vencedor = "0" where vencedor = "false";
```


* Em qual edição do Oscar "Crash" concorreu ao Oscar?

R: 78

Q:
```sql
select * from indicados_ao_oscar
where nome_do_filme like "Crash";
```


* O filme Central do Brasil aparece no Oscar?

R: Sim

Q: 
```sql
select * from indicados_ao_oscar
where nome_do_filme = "central station";
```


* Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser.

R: 

Q:
```sql
INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,cerimonia,categoria,nome_do_indicado,nome_do_filme,vencedor) 
VALUES (2004,2005,3,'Melhor Filme de Animação','Stephen Hillenburg','Bob Esponja: O Filme','true');

INSERT INTO indicados_ao_oscar(ano_filmagem,ano_cerimonia,cerimonia,categoria,nome_do_indicado,nome_do_filme,vencedor) 
VALUES (2015,2016,3,'Melhor Filme de Animação','Stephen Hillenburg','Bob Esponja: Um Herói Fora d. Água','true');

```


* Denzel Washington já ganhou algum Oscar?

R: True

Q:
```sql
select * from indicados_ao_oscar
where nome_do_indicado = "Denzel Washington"
and vencedor = "true";
```


* Quais os filmes que ganharam o Oscar de Melhor Filme?

R: Muitos

Q:
```sql
select nome_do_indicado, nome_do_filme, vencedor
from indicados_ao_oscar
where categoria = "best picture"
and vencedor = "true";
```

* Bonus: Quais os filmes que ganharam o Oscar de Melhor Filme e Melhor Diretor na mesma cerimonia?

* Bonus: Denzel Washington e Jamie Foxx já concorreram ao Oscar no mesmo ano?
