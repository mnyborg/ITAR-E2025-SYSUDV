## Opgave 1 – Bibliotekssystem (opvarmning)

Tekst: Et bibliotek udlåner bøger til lånere. En bog har en titel og et ISBN-nummer. En låner har et navn og et låner-id. En låner kan låne mange bøger, men en bog kan højst være udlånt til én låner ad gangen.

Lav i draw.io:

Klasser: Låner, Bog.

Attributter.

Relation med multiplicitet.

```mermaid
classDiagram
    class Laaner {
      navn: string
      laanerId: string
    }
    class Bog {
      titel: string
      isbn: string
    }
    Laaner "1" -- "0..*" Bog : låner
    Bog "0..1" -- "1" Laaner : udlånt_til
