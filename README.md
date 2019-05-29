# Taak 2 Algoritmen & Datastructuren II: Externe Datastructuren

## Gewijzigde bestanden

`database.rkt`:

* M gedefinieerd
* select*-from/inner-join toegevoegd

`table.rkt`:

* for-each-of-n-next-nodes toegevoegd
* read-next-n-nodes toegevoegd
* nr-of-datanodes toegevoegd

`external-chaining.rkt`:

* insert! gewijzigd
* find gewijzigd

## M

Om ervoor te zorgen dat de hele tabel niet in een keer wordt ingelezen, werd gebruikt gemaakt van een hulpfunctie die het aantal datanodes van de tabel telt (in het geval van de gebruikte test dataset zijn dat er 7).
Op basis van dat getal werd M gekozen (4).

## Dictionary

Ik koos voor een hashtable met gewijzigd external chaining algoritme met als hash functie de identiteit.
Voor de `insert!` wijzigt de collision strategie: in plaats van de de waarde te overschrijven bij gelijke key, wordt de chain op die key uitgebreid met de waarde. De grootte van de hashtable is de capaciteit van de in het centraal geheugen ingelezen data nodes.
De `find` methode geeft de volledige chain van de key terug.
Zowel `insert!` als `find` hebben een O(1) complexiteit, versus logaritmisch bij een bomenstructuur.