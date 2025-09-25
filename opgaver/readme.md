## Eksempel: Associationsklasse (Actor–Movie med Role)

```mermaid
classDiagram
    class Actor {
      name: string
    }
    class Movie {
      title: string
    }
    class Role {
      name: string
    }

    %% Relationer
    Actor "1" -- "0..*" Role : plays
    Role "1" -- "1" Actor : played_by

    Movie "1" -- "0..*" Role : contains
    Role "0..1" -- "1" Movie : appears_in

