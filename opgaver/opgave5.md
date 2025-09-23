## Opgave 5 – Musikstreaming

Tekst: En bruger har mange playlister. En playliste har titel og beskrivelse. En sang har titel, varighed og tracknummer. En playliste kan indeholde mange sange, og en sang kan ligge i flere playlister. (Tip: brug en mellemklasse til at gemme rækkefølge/position.)

Lav i draw.io:

Klasser: Bruger, Playliste, Sang, + PlaylistEntry (position).

```mermaid
classDiagram
    class Bruger {
      navn: string
      email: string
    }
    class Playliste {
      titel: string
      beskrivelse: string
    }
    class Sang {
      titel: string
      varighedSek: int
      trackNr: int
    }
    class PlaylistEntry {
      position: int
      kommentar: string
    }

    Bruger "1" --> "0..*" Playliste : definerer
    Playliste "1" --> "1..*" PlaylistEntry : består_af
    Sang "1" --> "0..*" PlaylistEntry : indgår_i

