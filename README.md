# Opérations entre types de variables en C

## Introduction

Cet exercice vous permettra de comprendre comment le C gère les opérations entre différents types de variables. En C, lorsque vous effectuez des opérations entre variables de types différents, le compilateur applique des règles de conversion implicites (ou "promotion de type") pour garantir que les calculs s'effectuent correctement.

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

### Partie 4 : Calculatrice interactive avec entrées utilisateur

Créez maintenant une calculatrice simple qui :

1. Demande à l'utilisateur d'entrer deux valeurs :

   - Un nombre entier (`int_input`)
   - Un nombre à virgule flottante (`float_input`)

2. Utilise la fonction `scanf()` pour lire ces entrées. Voici un exemple de code :

   ```c
   int int_input;
   float float_input;

   printf("Entrez un nombre entier : ");
   scanf("%d", &int_input);

   printf("Entrez un nombre à virgule flottante : ");
   scanf("%f", &float_input);
   ```

3. Effectue les opérations arithmétiques suivantes et affiche les résultats :

   - Addition : `int_input + float_input`
   - Soustraction : `float_input - int_input`
   - Multiplication : `int_input * float_input`
   - Division : `float_input / int_input`
   - Division entière : `int_input / (int)float_input`
   - Modulo (après conversion) : `int_input % (int)float_input`

4. Pour chaque opération :

   - Affichez l'opération effectuée (par exemple : "12 + 3.5 = 15.50")
   - Indiquez le type du résultat
   - Pour la division entière et le modulo, expliquez brièvement pourquoi la conversion est nécessaire

5. Ajoutez une gestion d'erreur simple :
   - Vérifiez si la partie entière de `float_input` est 0 avant d'effectuer la division entière et le modulo
   - Si c'est le cas, affichez un message d'erreur approprié au lieu d'effectuer l'opération

## Résultat attendu

Votre programme doit afficher un résultat similaire à celui-ci :

```
PARTIE 1: OPÉRATIONS ENTRE TYPES DIFFÉRENTS
int_var (10) + float_var (3.5) = 13.50 (type: float)
int_var (10) * float_var (3.5) = 35.00 (type: float)
int_var (10) + char_var ('A' = 65) = 75 (type: int)
float_var (3.5) / int_var (10) = 0.35 (type: float)
short_var (100) * char_var ('A' = 65) = 6500 (type: int)

PARTIE 2: CONVERSIONS EXPLICITES
int_var + float_var = 13.50 (sans cast)
int_var + (int)float_var = 13 (avec cast de float_var en int)

int_var * float_var = 35.00 (sans cast)
int_var * (float)char_var = 650.00 (avec cast de char_var en float)

int_var / short_var = 0 (division entière)
(float)int_var / short_var = 0.10 (avec cast pour division flottante)

PARTIE 3: DIVISION ENTIÈRE ET MODULO
a = 17, b = 5
a / b = 3 (division entière)
(float)a / b = 3.40 (division flottante)
a % b = 2 (reste de la division)

a = -17, b = 5
a / b = -3 (division entière avec négatif)
(float)a / b = -3.40 (division flottante avec négatif)
a % b = -2 (reste de la division avec négatif)

PARTIE 4: CALCULATRICE INTERACTIVE
Entrez un nombre entier : 42
Entrez un nombre à virgule flottante : 7.5

RÉSULTATS DES OPÉRATIONS :
Addition : 42 + 7.50 = 49.50 (type: float)
Soustraction : 7.50 - 42 = -34.50 (type: float)
Multiplication : 42 * 7.50 = 315.00 (type: float)
Division : 7.50 / 42 = 0.18 (type: float)
Division entière : 42 / 7 = 6 (type: int) - La partie décimale est tronquée après conversion
Modulo : 42 % 7 = 0 (type: int) - Le modulo nécessite des opérandes entiers
```

Si l'utilisateur entre 0 ou un nombre dont la partie entière est 0 comme deuxième nombre :

```
Division entière : Impossible - Division par zéro non autorisée
Modulo : Impossible - Opération modulo par zéro non autorisée
```

## Astuces

- En C, lors d'opérations entre types différents, le type "inférieur" est généralement converti vers le type "supérieur" (par exemple, `int` vers `float`).
- La hiérarchie générale des conversions est : `char` → `short` → `int` → `long` → `float` → `double`.
- Une division entre deux entiers donne toujours un résultat entier (la partie fractionnaire est tronquée).
- Le modulo (`%`) ne fonctionne qu'avec des opérandes entiers.
- Attention au comportement du modulo avec des nombres négatifs, qui peut varier selon les compilateurs.
- Pour `scanf()`, n'oubliez pas d'utiliser l'opérateur `&` devant les variables pour passer leur adresse mémoire.
- Pour vérifier si un nombre à virgule flottante a une partie entière égale à zéro, vous pouvez utiliser la conversion : `(int)float_input == 0`

## Pour aller plus Loin

- Explorez les effets de débordement (overflow) lorsque le résultat d'une opération dépasse la capacité du type.
- Étudiez les conséquences des conversions implicites sur la précision des calculs (notamment avec `float` et `double`).
- Ajoutez une gestion d'erreur plus robuste, par exemple en vérifiant si `scanf()` a réussi à lire les entrées.

---

_Comprendre les règles de conversion de types est essentiel pour éviter des bugs subtils. Prenez le temps d'expérimenter avec différentes combinaisons d'opérations et de types pour bien assimiler ces concepts._
