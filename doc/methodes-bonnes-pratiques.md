1. Règles de nommage
Variables, fonctions, classes

    Variables :
        Utilisez des noms explicites qui décrivent clairement leur rôle ou leur contenu.
            Bon exemple : userAge, filePath, isActive
            Mauvais exemple : x, temp, data
        Préférez des noms concis mais compréhensibles.
        Évitez les abréviations non standard ou ambigües (e.g., usrNm pour userName).

    Fonctions :
        Les noms doivent indiquer l’action ou l’objectif de la fonction.
            Bon exemple : calculateInvoiceTotal(), fetchUserData()
            Mauvais exemple : doStuff(), process1().
        Utilisez des verbes pour les noms de fonctions (e.g., get, update, delete, process).

    Classes :
        Nommez les classes en fonction de leur responsabilité principale.
            Bon exemple : InvoiceProcessor, UserRepository
            Mauvais exemple : Helper, Manager (trop génériques).
        Utilisez des noms au singulier pour représenter une seule entité (e.g., User plutôt que Users).

Exemples de bons et mauvais noms

    Variables :
        Bon : orderList
        Mauvais : oList

    Fonctions :
        Bon : validatePassword()
        Mauvais : vp()

    Classes :
        Bon : PaymentGateway
        Mauvais : Utility.

2. Structure du code
Rôle des petites fonctions

    Pourquoi privilégier de petites fonctions ?
        Elles sont plus faciles à lire, à comprendre et à tester.
        Chaque fonction doit avoir une seule responsabilité (principe SRP - Single Responsibility Principle).
        Une fonction courte évite l’accumulation de logique complexe dans un seul bloc.

    Règle empirique : Si une fonction ne tient pas dans l’écran sans avoir à scroller, elle est probablement trop longue.

    Exemple :

    # Mauvais exemple
    def processOrder(order):
        # Contient plusieurs responsabilités (calcul, envoi de notification, mise à jour)
        pass

    # Bon exemple
    def calculateOrderTotal(order):
        pass

    def notifyCustomer(order):
        pass

    def updateOrderStatus(order):
        pass

Division en modules ou couches

    Avantages de modulariser le code :
        Facilite la maintenance et le test de parties isolées.
        Clarifie les responsabilités de chaque partie.
        Permet de réutiliser des modules dans d’autres projets.

    Structure typique par couches :
        Présentation (UI) : contient la logique de l’interface utilisateur.
        Logique métier (Service) : gère les règles d’application.
        Données (Repository) : interagit avec les bases de données ou APIs.

    Exemple (architecture simplifiée) :
        controllers/ → Gère les requêtes et les réponses.
        services/ → Contient les règles métier.
        repositories/ → Interagit avec les bases de données.

Gestion des dépendances

    Principes clés :
        Évitez les dépendances cycliques.
        Utilisez l’injection de dépendances (DI) pour découpler les composants.

    Bonnes pratiques :
        Déclarez explicitement les dépendances requises (par exemple via le constructeur ou une méthode dédiée).
        Favorisez les interfaces pour réduire les couplages rigides.

3. Commentaires : utile ou nuisible ?
Quand commenter, quand ne pas commenter

    Quand commenter :
        Expliquez pourquoi le code fait quelque chose, plutôt que comment il le fait.
        Documentez les choix techniques ou les décisions complexes.
        Indiquez les limitations ou les zones nécessitant une attention future.

    Quand ne pas commenter :
        Évitez les commentaires redondants qui décrivent un code évident.
        Mauvais exemple :

    # Ajouter 1 au compteur
    counter += 1

Exemple d’un bon commentaire :

    # Cette méthode utilise un algorithme optimisé pour les grandes listes
    def processLargeList(data):
        pass

    Priorité : Préférez un code clair et auto-explicatif à des commentaires excessifs.

4. Tests et validation
Rôle des tests unitaires dans un code propre

    Importance des tests :
        Garantissent que chaque composant fonctionne comme attendu.
        Facilitent les modifications en vérifiant que le comportement reste inchangé.
        Encouragent un design modulaire et découplé.

    Principes de base :
        Chaque test doit être indépendant.
        Respectez la règle AAA : Arrange, Act, Assert.
        Testez une seule fonctionnalité par test.

    Exemple :

    def test_calculate_total():
        # Arrange
        items = [10, 20, 30]
        # Act
        total = calculate_total(items)
        # Assert
        assert total == 60

Couverture de code et tests automatisés

    Couverture de code :
        Mesure le pourcentage de lignes ou de branches couvertes par les tests.
        Visez une couverture élevée (70-90%), mais comprenez que 100% n'est pas toujours réaliste.

    Automatisation des tests :
        Intégrez les tests dans le processus CI/CD pour éviter les régressions.
        Utilisez des outils comme Jest, JUnit, ou PyTest pour des tests unitaires automatisés.

    Bonnes pratiques :
        Ajoutez des tests pour les cas limites et les erreurs attendues.
        Gardez les tests clairs et lisibles.