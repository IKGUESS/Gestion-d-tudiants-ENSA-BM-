# Diagramme de Classes

```mermaid
classDiagram
    class Responsable {
        idRespo: int
    }

    class Administrateur {
        idAdmin: int
    }

    class Personne {
        CIN: String
        nom: String
        prenom: String
        dateNaissance: Date
        telephone: String
        email: String
        nationalite: String
        ville: String
        sexe: String
        statut: String
        login: String
        password: String
    }

    class Professeur {
        idProf: int
    }

    class Etudiant {
        idEtud: int
    }

    class Inscription {
        idInscrip: int
        anneeUniversitaire: Date
        statutInscrip: String
    }

    class Presence {
        idPres: int
        nbAbsences: int
        nbRetards: int
    }

    class Note {
        idNote: int
        noteControle: double
        noteTp: double
        noteExam: double
        session: String
    }

    class Filiere {
        codeFil: String
        designation: String
    }

    class SectionFiliere {
        idSecFil: int
    }

    class Niveau {
        codeNiv: String
        designation: String
    }

    class NiveauEtude {
        codeNivSco: String
        designation: String
    }

    class Section {
        codeSec: String
        designation: String
    }

    class Module {
        codeMod: String
        nomMod: String
        nbControles: int
        nbTps: int
        nbExams: int
        coeffControles: double
        coeffTps: double
        coeffExams: double
    }

    Responsable "1" -- "1" Administrateur : gerer
    Administrateur "1" -- "1..*" Personne
    Professeur "1..*" --|> Personne
    Etudiant "1..*" --|> Personne
    Etudiant "1" -- "0..*" Inscription : s'inscrire
    Inscription "1..*" -- "1" Filiere : admettre
    Filiere "1..*" -- "1" Niveau : appartenir
    Niveau "1..*" -- "1" NiveauEtude : avoir
    Filiere "1" -- "1..*" SectionFiliere : contient
    SectionFiliere "1..*" -- "1" Section : contient
    Etudiant "1" -- "0..*" Presence : présenter
    Etudiant "1" -- "0..*" Note : noter
    Professeur "1" -- "1..*" Module : enseigner
    Section "1" -- "0..*" Module : contenir

      
  
      
