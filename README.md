# Opérations entre types de variables en C

## Introduction

Cet exercice vous permettra de comprendre comment le C gère les opérations entre différents types de variables. En C, lorsque vous effectuez des opérations entre variables de types différents, le compilateur applique des règles de conversion implicites (ou "promotion de type") pour garantir que les calculs s'effectuent correctement. Comprendre ces règles est essentiel pour éviter des erreurs subtiles et des comportements inattendus dans vos programmes.

## Exercice

### Partie 1 : Opérations arithmétiques entre types différents

Créez un programme C qui :

1. Déclare et initialise les variables suivantes :

   - Un entier `int_var` avec la valeur 10
   - Un nombre à virgule flottante `float_var` avec la valeur 3.5
   - Un caractère `char_var` avec la valeur 'A' (code ASCII 65)
   - Un entier court `short_var` avec la valeur 100

2. Effectue et affiche le résultat des opérations suivantes :

   - `int_var + float_var`
   - `int_var * float_var`
   - `int_var + char_var`
   - `float_var / int_var`
   - `short_var * char_var`

3. Pour chaque résultat, affichez aussi le type de la variable résultante (en l'indiquant manuellement dans votre code).

Voici un modèle pour commencer :

```c
#include <stdio.h>

int main() {
    // Déclaration et initialisation des variables
    int int_var = 10;
    float float_var = 3.5;
    char char_var = 'A';
    short short_var = 100;

    // Calculs et affichage des résultats
    printf("int_var + float_var = %.2f (type: float)\n", int_var + float_var);

    // Complétez avec les autres opérations...

    return 0;
}
```

### Partie 2 : Conversions de types explicites (cast)

Modifiez votre programme pour :

1. Effectuer les opérations suivantes avec conversion explicite (cast) :

   - Conversion de `float_var` en `int` avant l'addition avec `int_var`
   - Conversion de `char_var` en `float` avant la multiplication avec `float_var`
   - Division de `int_var` par `short_var` avec résultat en `float`

2. Comparez les résultats obtenus avec et sans conversion explicite pour chaque opération et affichez-les côte à côte.

### Partie 3 : Division entière et modulo

Étendez votre programme pour explorer les particularités de la division entière et du modulo :

1. Déclarez deux nouvelles variables entières `a` et `b` avec les valeurs 17 et 5
2. Calculez et affichez :
   - Le résultat de `a / b` en tant qu'entier
   - Le résultat de `a / b` converti en `float`
   - Le reste de la division (`a % b`)
3. Effectuez la même série de calculs avec les valeurs -17 et 5 pour `a` et `b`, et observez les différences

## Résultat Attendu

Votre programme doit afficher un résultat similaire à celui-ci :

```
PARTIE 1: OPÉRATIONS ENTRE TYPES DIFFÉRENTS
entier (10) + flottant (3.5) = 13.50 (type: float)
entier (10) * flottant (3.5) = 35.00 (type: float)
entier (10) + caractere ('A' = 65) = 75 (type: int)
flottant (3.5) / entier (10) = 0.35 (type: float)
entier_court (100) * caractere ('A' = 65) = 6500 (type: int)

PARTIE 2: CONVERSIONS EXPLICITES
entier + flottant = 13.50 (sans cast)
entier + (int)flottant = 13 (avec cast de flottant en int)

entier * flottant = 35.00 (sans cast)
entier * (float)caractere = 650.00 (avec cast de caractere en float)

entier / entier_court = 0 (division entière)
(float)entier / entier_court = 0.10 (avec cast pour division flottante)

PARTIE 3: DIVISION ENTIÈRE ET MODULO
a = 17, b = 5
a / b = 3 (division entière)
(float)a / b = 3.40 (division flottante)
a % b = 2 (reste de la division)

a = -17, b = 5
a / b = -3 (division entière avec négatif)
(float)a / b = -3.40 (division flottante avec négatif)
a % b = -2 (reste de la division avec négatif)
```

## Astuces

- En C, lors d'opérations entre types différents, le type "inférieur" est généralement converti vers le type "supérieur" (par exemple, `int` vers `float`).
- La hiérarchie générale des conversions est : `char` → `short` → `int` → `long` → `float` → `double`.
- Une division entre deux entiers donne toujours un résultat entier (la partie fractionnaire est tronquée).
- Le modulo (`%`) ne fonctionne qu'avec des opérandes entiers.
- Attention au comportement du modulo avec des nombres négatifs, qui peut varier selon les compilateurs.

## Pour Aller Plus Loin

- Explorez les effets de débordement (overflow) lorsque le résultat d'une opération dépasse la capacité du type.
- Étudiez les conséquences des conversions implicites sur la précision des calculs (notamment avec `float` et `double`).
- Découvrez les types de taille fixe de la bibliothèque `<stdint.h>` comme `int32_t` et explorez comment ils interagissent dans les opérations mixtes.
- Investiguer les problèmes de précision lors de comparaisons de valeurs à virgule flottante.

---

_Comprendre les règles de conversion de types est essentiel pour éviter des bugs subtils. Prenez le temps d'expérimenter avec différentes combinaisons d'opérations et de types pour bien assimiler ces concepts._
