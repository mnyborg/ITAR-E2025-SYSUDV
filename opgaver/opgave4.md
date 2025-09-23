## Opgave 4 – Transport (per-tur relationer)

Tekst: Et busselskab har mange busser. Hver bus har et registreringsnummer og antal sæder. Hver bus kører på en bestemt rute (rutenummer, start- og slutdestination). En chauffør kan køre mange forskellige busser, men kun én chauffør ad gangen på en given tur.

Lav i draw.io:

Klasser: Busselskab, Bus, Rute, Chauffør.

For at udtrykke “én chauffør pr. tur” modelleres en Tur (dato/tidsrum), som forbinder Bus, Rute og Chauffør.

```mermaid
classDiagram
    class Busselskab {
      navn: string
    }
    class Bus {
      regNr: string
      saedeAntal: int
    }
    class Rute {
      ruteNr: string
      start: string
      slut: string
    }
    class Chauffor {
      chaufforId: string
      navn: string
    }
    class Tur {
      dato: date
      startTid: time
      slutTid: time
    }

    Busselskab "1" --> "1..*" Bus : ejer
    Bus "1" --> "0..*" Tur : kører
    Chauffor "1" --> "0..*" Tur : bemander
    Rute "1" --> "0..*" Tur : foregår_på

