## Opgave 6 – Sportsklub (to roller til samme klasse)

Tekst: En sportsklub organiserer hold og kampe. Et hold har navn og niveau (fx U15, senior). En spiller har navn, alder og spiller-id, og et hold har mange spillere. En kamp spilles mellem to hold på en bestemt dato. En dommer (navn, dommer-id) dømmer kampen.

Lav i draw.io:

Klasser: Hold, Spiller, Kamp, Dommer.

Vis at Kamp refererer til to forskellige Hold (hjemme/ude).

```mermaid
classDiagram
    class Hold {
      navn: string
      niveau: string
    }
    class Spiller {
      spillerId: string
      navn: string
      alder: int
    }
    class Kamp {
      kampId: string
      dato: date
    }
    class Dommer {
      dommerId: string
      navn: string
    }

    Hold "1" --> "0..*" Spiller : består_af
    Kamp "1" --> "1" Hold : hjemmehold
    Kamp "1" -- >"1" Hold : udehold
    Dommer "1" --> "0..*" Kamp : dømmer
