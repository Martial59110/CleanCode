Code Sale (Java)

public class School {
    public static void main(String[] args) {
        int[] a = {15, 12, 18, 10, 8}; // notes
        String[] b = {"Prof1", "Prof2", "Prof3"}; // profs
        double x = 0;
        int y = 0;

        for (int i = 0; i < a.length; i++) {
            x = x + a[i];
            y++;
        }
        double z = x / y;

        int studentNumber = 0;
        for (int i = 0; i < a.length; i++) {
            studentNumber++;
        }

        int teacherNumber = 0;
        for (int i = 0; i < b.length; i++) {
            teacherNumber++;
        }

        System.out.println("Moyenne: " + z);
        System.out.println("Nombre d'étudiants: " + studentNumber);
        System.out.println("Nombre de professeurs: " + teacherNumber);
    }
}

Comment ce code enfreint les 7 principes du Clean Code ?
1. Nomination descriptive

    Problème : Les noms des variables sont vagues et non descriptifs.
        a pour les notes : Pas clair. Pourquoi pas studentGrades ?
        b pour les professeurs : Incompréhensible. Pourquoi pas teacherNames ?
        x, y, z : Ces noms ne donnent aucune information sur leur rôle ou leur signification.

2. Fonctions courtes

    Problème : La méthode main fait tout : calcul des moyennes, comptage des élèves, comptage des professeurs et affichage des résultats.
        Une méthode par responsabilité aurait dû être utilisée, par exemple calculateAverage, countStudents, et displayResults.

3. Commentaires utiles ou absents

    Problème : Les commentaires présents ne servent à rien.
        // notes et // profs n’apportent aucune valeur.
        Il n’y a pas d’explication sur le pourquoi ni le comment des calculs.

4. Gestion des erreurs

    Problème : Aucune vérification des données d’entrée.
        Si a est vide, une division par zéro provoque une exception.
        Pas de vérification de b non plus pour éviter un NullPointerException.

5. Respect des conventions

    Problème :
        Utilisation de tableaux bruts (int[], String[]) au lieu de structures modernes comme List<Integer> ou List<String>.
        Non-respect des conventions de nommage (variables en une seule lettre).
        Mauvaise séparation des responsabilités dans le code.

6. Éviter la redondance

    Problème :
        Les boucles for pour compter les élèves (studentNumber) et les professeurs (teacherNumber) sont redondantes. Ces informations peuvent être obtenues directement avec .length.
        La boucle pour calculer la moyenne et celle pour compter les élèves pourraient être fusionnées.

7. Priorité aux tests unitaires

    Problème : Tout est dans main, ce qui rend le code difficile à tester.
        Aucun des calculs (moyenne, comptage des élèves ou des professeurs) n’est isolé dans des méthodes testables.

        Exemple corrigé : Application des 7 principes du Clean Code

Voici une version qui respecte les 7 principes du Clean Code :

import java.util.List;

public class School {
    public static void main(String[] args) {
        List<Integer> studentGrades = List.of(15, 12, 18, 10, 8);
        List<String> teacherNames = List.of("Prof1", "Prof2", "Prof3");

        double averageGrade = calculateAverage(studentGrades);
        int studentCount = studentGrades.size();
        int teacherCount = teacherNames.size();

        displayResults(averageGrade, studentCount, teacherCount);
    }

    // Méthode pour calculer la moyenne
    public static double calculateAverage(List<Integer> grades) {
        double sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return grades.isEmpty() ? 0 : sum / grades.size();
    }

    // Méthode pour afficher les résultats
    public static void displayResults(double average, int students, int teachers) {
        System.out.println("Moyenne des élèves : " + average);
        System.out.println("Nombre total d'élèves : " + students);
        System.out.println("Nombre total de professeurs : " + teachers);
    }
}
