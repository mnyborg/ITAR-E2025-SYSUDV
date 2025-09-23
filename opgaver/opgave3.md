## Opgave 3 – Online butik (mange-til-mange via OrderLine)

Tekst: En online butik sælger produkter til kunder. Et produkt har navn, pris og produktnummer. En kunde har navn, adresse og email. En kunde kan have mange ordrer. En ordre har en dato og et ordrenummer. En ordre kan indeholde mange produkter, og et produkt kan være i mange ordrer.

Lav i draw.io:

Klasser: Kunde, Ordre, Produkt.

Indsæt en mellemklasse OrderLine til at løse mange-til-mange og holde antal og stykspris.

```mermaid
classDiagram
    class Kunde {
      navn: string
      adresse: string
      email: string
    }
    class Ordre {
      ordreNr: string
      dato: date
    }
    class Produkt {
      produktNr: string
      navn: string
      pris: decimal
    }
    class OrderLine {
      antal: int
      stykspris: decimal
    }

    Kunde "1" --> "0..*" Ordre : placerer
    Ordre "1" --> "1..*" OrderLine : indeholder
    Produkt "1" --> "0..*" OrderLine : refereres_af
