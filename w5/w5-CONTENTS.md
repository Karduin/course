## Vidéo 1 (Itérable, itérateur, itération)
### NIVEAU: BASIC
###
### Compléments Vidéo 1

Pour mémoire, notebook du précédent MOOC sur Python 2

   * OK Complement-instructions-break-et-continue.ipynb
   * OK Complement-ne-pas-modifier-sujet-boucle-for.ipynb: il ne faut pas pas modifier l'objet sur lequel on fait un for
   * ONGOING Complement-variables-de-boucle.ipynb  
   * OK Complement-iterateurs-et-performances.ipynb:
   * OK Complement-iterable-vs-iterateur.ipynb: un complément qui précise un peu mieux la notion d'itérable et d'itérateur

   * BOF : je laisse tomber tout ca pour l'instant
     -voir le else du for
     -présenter la méthode built-in iter() en expliquant que comme
     __iter__() est une méthode Python privée, on ne doit pas l'appeler
     		directement dans un programme, on doit utiliser la built-in iter()
		à la place.

### Quizz Vidéo 1
## Exercices Vidéo 1
   Pour mémoire, exercices du précédent MOOC sur Python 2

   * OK W3-S8-E1-iterables.quiz
   * NICETOHAVE: W3-S8-E2-for.ipynb: des exercices sur des fors un peu torturés  


## Vidéo 2 (Objet fonction, fonction `lambda`, `map` et `filter`)
### NIVEAU: BASIC
### Compléments Vidéo 2

* parler de la librairie functools

Pour mémoire, notebook du précédent MOOC sur Python 2

* OK Complement-fonctions.ipynb
* DROPPED *voir exec et eval. Ça n'est pas en lien direct, mais il faut
     le voir et il y a peu de compléments pour cette vidéo alors
     autant le placer ici.

## Quizz Vidéo 2

Pour mémoire, quizz du précédent MOOC sur Python 2

* NICETOHAVE W4-S3-E1-functions.quiz
* comparer def et lambda
* comparer map/filter

## Exercices Vidéo 2

Pour mémoire, exercices du précédent MOOC sur Python 2

* OK Exercice-fonctions.ipynb


## Vidéo 3 (Compréhension de listes, sets et dictionnaires)
### NIVEAU: BASIC
### Compléments Vidéo 3

Pour mémoire, notebook du précédent MOOC sur Python 2

* OK Complement-comprehensions-imbriquees.ipynb compréhensions
  multiples

* DROPPED Comparer la performance des boucles for, de map, de la
  compréhension. - pas le temps S'inspirer de :
     http://www-sop.inria.fr/members/Arnaud.Legout/EDU/Python/performanceFonctions2.py

### Quizz Vidéo 3

## Exercices Vidéo 3

Pour mémoire, exercices du précédent MOOC sur Python 2

   * ONGOING Exercice-comprehensions.ipynb


## Vidéo 4 (Expressions et fonctions génératrices)
### NIVEAU: BASIC
### Compléments Vidéo 4

* Parler de la délégation avec yield from et du refactoring de
  générateur

* Ça serait sympa de concevoir des générateurs utiles que l'on chaine
  en fonction de traitements à faire.

  J'ai droppé ma séquence vidéo sur "Diagnostiquer son code
   d'itération". L'idée est de montrer du code écrit à la C ou Java et
   de le diagnostiquer jusqu'à obtenir un code pythonique. Un exemple

```
   ages = dict(eve=10, ana=30, bill=40, bob=12, jim=35)

   noms = list(ages.keys())
   nb_noms = len(noms)

   for i in range(nb_noms):
       print(noms[i], ages[noms[i]])
```

On pourrait faire un complément très simple avec des règles de
   dianostique

* vous manipulez des indices dans un itération, c'est mauvais
   signe, pensez à itérer sur votre objet directement et pensez au
   unpacking
* vous caster des objets en listes, c'est mauvais signe, avez
   vous vraiement besoin d'une liste, travaillez de préférence avec
   des itérateurs.
* on pourrait également présenter des cas d'implémentations qui
   peuvent être grandement simplifié par la librairie Collections



* illustrer le gain de performance entre une boucle for sur des
     indices (à la Java), une comprréhension, une expression
     génératrice

Pour mémoire, notebook du précédent MOOC sur Python 2

* OK (S1-C1-)Complement-expressions-generatrices.ipynb

* parler des expressions génératrice et de leur intérêt (faible occupation
     mémoire) (x**6 + 3*x for x in xrange(100000000))

* Donner le lien vers
  http://python-history.blogspot.fr/2010/06/from-list-comprehensions-to-generator.html
  pour une discussion intéressante sur la compréhension, les expression
  génératrice et Python 2 et 3.

* faire un test de performance avec
  timeit pour montrer que les expressions génératrices sont un peu plus
  lente que les compréhensions, mais que lorsqu'on arrive à des
  très grosses listes, l'allocation mémoire et le swap disque font
  que les générateurs sont beaucoup plus rapides.


## Quizz Vidéo 4

## Exercices Vidéo 4


## Vidéo 5 (Modules et espaces de nommage)
### NIVEAU: BASIC
### Compléments Vidéo 5

   Parler de  dict, globals(), locals(), var(), dir() et en
   particulier montrer comment on peut explorer les espaces de
   nommages des fonctions et des objets.

Pour mémoire, notebook du précédent MOOC sur Python 2

* OK Complement-attributs.ipynb
* OK Complement-fonctions-globals-et-locals.ipynb

* DROPPED parler de l'impossibilité de faire __dict__ du module
     courant (en particulier du prompt interactif) et expliquer que
     l'on ne peut y accéder que depuis sys.modules[__name__].__dict__
     Citer http://docs.python.org/2.6/tutorial/classes.html#id2
     http://stackoverflow.com/questions/4877290/what-is-the-dict-dict-attribute-of-a-python-class
     pareil je vais laisser tomber tout ça c'est beaucoup trop bas
     niveau

### Quizz Vidéo 5

Pour mémoire, quizz du précédent MOOC sur Python 2

* OK W5-S1-E1.quiz

en relisant les exos des semaines passées je tombe sur ceci

```
   import string
   chaine = string.lowercase
   print chaine
```

on pourrait sûrement contruire un quiz en élaborant là-dessus, non ?

### Exercices Vidéo 5

Idée: faire un affichage qui dump l'espace de nommage par type
d'objet référencé. faire un dict avec comme clef le type de l'objet
référencé et comme valeur une liste de tuple (variable, objet)

```
def dump_naming_space(obj):
    naming_space = {}
    for v, o in vars(obj).items():
        naming_space.setdefault(type(o), []).append((v, o))

    for k, lst in naming_space.items():
        print(f"\n{k}")
        for v, o in lst:
            print(f"   {v}: {o}")
```


## Vidéo 6 (Processus d'importation des modules)
### NIVEAU: BASIC

### Compléments Vidéo 6

   parler de importlib.reload(), attention, reload a changée de place en
   python 3.4, ça peut donc être une source de confusion, il faut en
   dire un mot. avant on utilisait imp.reload(), mais c'est
   deprecated.
   https://docs.python.org/3/library/imp.html?highlight=reload#imp.reload

Pour mémoire, notebook du précédent MOOC sur Python 2

* OK `Complement-import.ipynb`
   avancé
   . en profiter pour mentionner sys.modules
   . parler de sys.builtin_module_names et de, par exemple, math
   et sys, qui sont des modules built-in implémentés en C pour
   des questions de vitesse.

* NICETOHAVE
   montrer que si bar importe foo et que foo importe sys, alors bar peut accéder à foo.sys

   NICETOHAVE W5-S2-C2-pyc.ipynb
   intermédiaire
   *compléter la
   discussion de la video sur les .pyc. Par exemple, on peut directement
   distribuer les .pyc sans les .py je suis pas très clair là-dessus, le
   pyc ne dépend pas du hardware, d'accord, mais dépend-il de la version
   de python (je présume que oui)

   DROPPED *exécuter un module comme un script avec  if __name__ == '__main__':
   déjà vu en Complement-packages.ipynb

### Quizz Vidéo 6
Pour mémoire, quizz du précédent MOOC sur Python 2

* OK W5-S2-E1.quiz

### Exercices Vidéo 6


## Vidéo 7 (Importation des modules et espaces de nommage)
### NIVEAU: BASIC
### Compléments Vidéo 7

* xxx : s'assurer qu'on couvre bien les packages
Pour mémoire, notebook du précédent MOOC sur Python 2

   * OK Complement-import-as.ipynb

   * DROPPED - Introduire aussi les variables commençant par _ en
     expliquant que l'on ne doit pas les modifier et qu'elles ne sont
     pas importée par un import * - je laisse tomber puisqu'il ne faut
     pas le faire de toutes façons

### Quizz Vidéo 7
Pour mémoire, quizz du précédent MOOC sur Python 2

   * OK W5-S3-E1.quiz

### Exercices Vidéo 7
Pour mémoire, exercices du précédent MOOC sur Python 2
