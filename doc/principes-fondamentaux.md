# Principes fondamentaux

Les 7 vertus du Clean Code selon Robert C. Martin

Robert C. Martin, dans son ouvrage Clean Code: A Handbook of Agile Software Craftsmanship, met en avant sept principes fondamentaux pour écrire un code propre, efficace et maintenable. Ces principes, souvent appelés les "vertus" du Clean Code, forment une base solide pour les bonnes pratiques de programmation.
1. Nomination descriptive

Les noms dans le code (variables, fonctions, classes) doivent être clairs, explicites et refléter leur rôle ou leur objectif.

    Pourquoi ? : Un bon nom réduit la nécessité de commentaires supplémentaires, évite la confusion et améliore la lisibilité du code.
    Exemple de bon nom :

double calculateMonthlyInterest(double principal, double rate);

Exemple de mauvais nom :

    double calc(double p, double r);

Un nom descriptif est un investissement pour l'avenir, permettant aux développeurs de comprendre rapidement le code sans relecture fastidieuse.
2. Fonctions courtes

Les fonctions doivent être courtes, souvent limitées à une seule tâche bien définie (principe SRP - Single Responsibility Principle). Une fonction courte est plus facile à lire, tester et maintenir.

    Pourquoi ? : Les longues fonctions sont difficiles à comprendre et à déboguer. En revanche, des fonctions concises favorisent la clarté et le découpage en responsabilités distinctes.
    Exemple : Mauvais :

def process_data(data):
    # Parsing, filtering, sorting, and analyzing all in one function

Bon :

    def parse_data(data):
    def filter_data(data):
    def analyze_data(data):

3. Commentaires utiles (ou leur absence)

Un code propre doit être suffisamment clair pour ne pas nécessiter de nombreux commentaires. Cependant, lorsqu’ils sont nécessaires, les commentaires doivent expliquer le pourquoi du code, pas simplement le comment.

    Pourquoi ? : Les commentaires obsolètes ou inutiles peuvent induire en erreur et encombrer le code.
    Exemple de commentaire utile :

# Convert temperature from Celsius to Fahrenheit as per user request
temperature = (temperature * 9/5) + 32

Exemple de commentaire inutile :

    # Add 5 to the temperature
    temperature = temperature + 5

4. Gestion des erreurs

Un Clean Code anticipe les erreurs et les traite de manière élégante et robuste. Il utilise des structures appropriées pour signaler, gérer et récupérer les erreurs.

    Pourquoi ? : Une mauvaise gestion des erreurs peut entraîner des crashs ou des comportements imprévisibles. Un code propre gère les exceptions sans interrompre l'exécution du programme.
    Bon exemple :

try:
    result = divide(a, b)
except ZeroDivisionError:
    print("Cannot divide by zero.")

Mauvais exemple :

    result = divide(a, b)  # Hope it works!

5. Respect des conventions

Un code propre respecte les conventions de codage adoptées par l’équipe ou la communauté, qu’il s’agisse de style, de structure ou de nommage.

    Pourquoi ? : Les conventions favorisent la cohérence du code, permettant aux membres de l’équipe de travailler efficacement sur un projet commun.
    Exemple : En Python, respecter les règles de PEP 8 :

    def calculate_area(radius):
        return 3.14 * radius**2

Ignorer les conventions peut créer des divergences déroutantes dans un projet, rendant le code plus difficile à lire et à maintenir.
6. Éviter la redondance

Le principe DRY (Don’t Repeat Yourself) est un pilier du Clean Code. Il encourage l’extraction de code redondant dans des fonctions ou modules réutilisables.

    Pourquoi ? : La duplication du code rend sa maintenance difficile. Une modification dans un endroit nécessite souvent des ajustements similaires ailleurs, ce qui augmente les risques d’erreur.
    Exemple de duplication : Mauvais :

def calculate_square_area(side):
    return side * side

def calculate_rectangle_area(length, width):
    return length * width

Bon :

    def calculate_area(*args):
        if len(args) == 1:  # Square
            return args[0] * args[0]
        elif len(args) == 2:  # Rectangle
            return args[0] * args[1]

7. Priorité aux tests unitaires

Un code propre est toujours accompagné de tests automatisés. Ces tests garantissent que le code fonctionne comme prévu, même après des modifications ou des ajouts de nouvelles fonctionnalités.

    Pourquoi ? : Les tests réduisent le risque de bugs introduits lors de futurs développements. Ils servent également de documentation pour expliquer le comportement attendu du code.
    Exemple :

    def test_calculate_area():
        assert calculate_area(4) == 16
        assert calculate_area(4, 5) == 20

Éléments contre-exemples (Code spaghetti, anti-patterns)
1. Code spaghetti

Le code spaghetti est un code difficile à suivre et à comprendre en raison de sa structure désordonnée. Il se caractérise par des dépendances excessives, des sauts imprévisibles (comme des goto) et une logique dispersée.

    Problèmes :
        Difficulté à déboguer.
        Risques accrus de bugs.
        Maintenance laborieuse.

2. Anti-patterns courants

    God Object : Une classe qui fait tout, violant le principe de responsabilité unique.
    Hard-Coding : Utilisation de valeurs fixes dans le code, rendant les modifications difficiles.
    Magic Numbers : Chiffres dans le code sans explication de leur signification.
    Big Ball of Mud : Code mal structuré, sans séparation claire des responsabilités.

En appliquant les vertus du Clean Code, les développeurs peuvent éviter ces pièges et garantir un logiciel fiable et maintenable.