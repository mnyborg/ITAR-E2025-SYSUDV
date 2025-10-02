## Beskrivelse af en brugerrejse (eksempel: Glemt at tjekke ud med rejsekort)  

**Persona:** Sofie, 23 år, studerende, rejser ofte med tog og bus.

Brugerrejse:
Forberedelse
- Sofie har penge på sit rejsekort og skal tage toget hjem fra studie.

Check ind
- Hun checker ind på stationen og finder en plads i toget.

Rejsen
- Hun læser på sin telefon og snakker med en ven.

Ankomst
- Da toget når frem, skynder hun sig ud for at nå bussen videre.

Problem – glemt check ud
- Sofie glemmer at checke ud på stationen.
- Næste dag opdager hun, at hun er blevet trukket for en kontrolafgift (maksimumpris).

Efterfølgende handling
- Hun logger på rejsekort.dk for at klage og få refunderet beløbet.
- Hun synes processen er besværlig og langsommelig.

## Ord-/begrebsanalyse af brugerrejsebeskrivelsen

- Aktører/roller: Sofie (bruger), DSB, Rejsekort-system, kundeservice
- Handlinger (verber): checke ind, rejse, læse, snakke, stå af, glemme, opdage, logge på, klage
- Touchpoints: check-ind stander, togstation, rejsekort.dk, kundeservice
- Problemer/pains: glemt check-ud, makspris, besværlig klageproces
- Gains: nem indcheckning, fleksibel rejse, mulighed for refundering
- Moments of truth:  
  - Om Sofie husker at checke ud
  - Om hun kan få en rimelig og hurtig løsning ved fejl

## Forslag til domænemodel (i Mermaid)  
```mermaid
classDiagram
    class Bruger {
        +id : int
        +navn : String
        +email : String
    }

    class Rejsekort {
        +kortId : int
        +saldo : double
    }

    class Rejse {
        +rejseId : int
        +startTid : datetime
        +slutTid : datetime
        +pris : double
        +status : String  // fx "afsluttet", "glemt check ud"
    }

    class Station {
        +stationId : int
        +navn : String
    }

    class Klage {
        +klageId : int
        +dato : datetime
        +status : String
    }

    Bruger "1" --> "1" Rejsekort
    Rejsekort "1" --> "*" Rejse
    Rejse "1" --> "1" Station : start
    Rejse "1" --> "1" Station : slut
    Bruger "1" --> "*" Klage
    Klage "*" --> "1" Rejse
```
## Journey-diagram (oplevelse pr. fase)
```mermaid
journey
    title Brugerrejse: Glemt at checke ud (Rejsekort)
    section Forberedelse
      Tjekker saldo i app : Sofie: 4
      Finder rejseplan : Sofie: 4
    section Check ind
      Checker ind på stationens stander : Sofie: 5
      Feedback (lys/lyd) bekræfter check ind : Sofie: 5
    section Rejsen
      Sætter sig i toget og skifter til bus : Sofie: 4
      Opmærksomheden rettes mod beskeder/samtale : Sofie: 3
    section Ankomst
      Skynder sig ud for at nå bussen : Sofie: 3
      Glemmer at checke ud : Sofie: 1
    section Efter rejsen
      Opdager makspris i transaktionsoversigt : Sofie: 2
      Forsøger refundering via rejsekort.dk : Sofie: 2
      Får svar/refusion (langsom proces) : Sofie: 3
```
## Flowchart med touchpoints, pains & gains
```mermaid
flowchart TD
    %% Aktører & systemer
    U[Sofie (bruger)]
    CI[Check-ind stander]
    TOG[Tog/bus (transport)]
    ST[Station (ankomst)]
    APP[Rejsekort app / kontooversigt]
    WEB[Rejsekort.dk (refundering)]
    KS[Kundeservice]

    %% Rejsens forløb
    U -->|tjekker saldo| APP
    U -->|ankommer| CI
    CI -->|lys/lyd bekræfter| U
    U -->|rejser| TOG
    U -->|ankommer| ST
    ST -->|mange stimuli/tidspres| U
    U -.->|glemmer check ud (pain)| ST

    %% Efter rejsen
    U -->|opdager makspris (pain)| APP
    U -->|anmoder om refundering| WEB
    WEB -->|kræver oplysninger/begrundelse (pain)| U
    WEB -->|status/opdatering| U
    U -->|kontakter ved behov| KS
    KS -->|vejledning/afgørelse| U

    %% Pains
    P1[[Pain: Tidspres ved ankomst → glemt check-ud]]
    P2[[Pain: Makspris udløst]]
    P3[[Pain: Besværlig/uklar refundering]]
    ST -. trigger .-> P1
    APP -. viser .-> P2
    WEB -. formular/ventetid .-> P3

    %% Gains
    G1[[Gain: Hurtig, enkel check-ind feedback]]
    G2[[Gain: Oversigt over transaktioner]]
    G3[[Gain: Mulighed for refusion ved fejl]]
    CI -. positiv feedback .-> G1
    APP -. transparens .-> G2
    WEB -. mulighed .-> G3

    %% Moments of Truth
    M1{{MoT: Check ind bekræftes tydeligt}}
    M2{{MoT: Check ud gennemføres eller glemmes}}
    M3{{MoT: Retfærdig og hurtig refusion}}
    CI --> M1
    ST --> M2
    WEB --> M3
```


