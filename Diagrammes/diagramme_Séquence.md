```mermaid
sequenceDiagram
    participant Utilisateur
    participant Système
    participant Administration

    Utilisateur->>Système: Saisie login et password
    alt login et psw correct
        Système-->>Utilisateur: redirection vers le compte d'utilisateur
    else login et psw incorrect
        Système-->>Utilisateur: Erreur
    end

    Administration->>Système: Saisie des informations (inscription élève)
    loop Données invalides
        Système-->>Administration: Erreur
    end
    Système->>Système: Contrôle des données
    alt Données correctes
        Système->>Système: Envoi des données
        Système->>Système: Traitement des données
        Système-->>Administration: redirection vers la liste d'élèves
    else En cas d'erreur
        Système->>Système: Authentification()
    end

    Administration->>Système: Saisie des informations (ajout professeur)
    loop Données invalides
        Système-->>Administration: Erreur
    end
    Système->>Système: Contrôle en temps réel
    Système->>Système: Validation des données
    Système->>Système: Traitement des données
    alt Données correctes
        Système-->>Administration: Ajout avec succès
    else Données incorrectes
        Système-->>Administration: Erreur
    end

    Administration->>Système: Choisir le niveau (affectation disciplines)
    Administration->>Système: Choisir une matière
    Administration->>Système: Choisir la discipline
    Système->>Système: Traitement des données
    alt Données correctes
        Système-->>Administration: Données enregistrées avec succès
    else En cas d'erreur
        Système-->>Administration: Erreur
    end

    Administration->>Système: Sélectionner la matière (ajout discipline)
    Administration->>Système: Saisie les informations des disciplines
    Système->>Système: Validation d'ajout
    Système->>Système: Traitement des données
    alt Matière existe
        alt Pas d'erreur
            Système-->>Administration: Succès
        else En cas d'erreur
            Système-->>Administration: Erreur
        end
    else Matière n'existe pas
        Administration->>Système: Saisie les informations de la nouvelle matière
        Administration->>Système: Saisie les informations concernant les disciplines
        Système->>Système: Validation d'ajout
        Système->>Système: Traitement des données
        alt Données correctes
            Système-->>Administration: Enregistrement avec succès
        else En cas d'erreur
            Système-->>Administration: Erreur
        end
    end
