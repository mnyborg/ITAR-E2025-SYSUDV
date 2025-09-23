## Opgave 2 – Skole og studerende

Tekst: En skole består af flere afdelinger. En afdeling har et navn og en adresse. En studerende har navn og studienummer. En underviser arbejder også på en afdeling og kan undervise mange studerende.

Lav i draw.io:

Klasser: Skole, Afdeling, Studerende, Underviser.

Relationer og multipliciteter (overvej om Underviser↔Studerende er mange-til-mange).

```mermaid
classDiagram
    class Skole {
      navn: string
    }
    class Afdeling {
      navn: string
      adresse: string
    }
    class Studerende {
      navn: string
      studienr: string
    }
    class Underviser {
      navn: string
      medarbejderNr: string
    }

    Skole "1" --> "1..*" Afdeling : består_af
    Afdeling "1" --> "0..*" Studerende : tilknytter
    Afdeling "1" --> "0..*" Underviser : ansætter
    Underviser "1" --> "0..*" Studerende : underviser

