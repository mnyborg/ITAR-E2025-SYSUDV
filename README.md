# ITAR-E2025-SYSUDV

```mermaid
classDiagram
direction LR

%% --- Entiteter ---
class Studerende {
  +id: UUID
  +navn: String
  +email: String
  +studienummer: String
}

class Underviser {
  +id: UUID
  +navn: String
  +email: String
}

class Kursus {
  +id: UUID
  +titel: String
  +ects: int
}

class Hold {
  +id: UUID
  +kapacitet: int
}

class Lokale {
  +id: String
  +betegnelse: String
  +bygning: String
}

class Tilmelding {
  +id: UUID
  +status: String
  +oprettetTid: DateTime
}

%% --- Value object (modelleret som almindelig klasse) ---
class TimeSlot {
  +ugedag: String
  +start: LocalTime
  +slut: LocalTime
}

%% --- "Enum"-klasser uden stereotyper ---
class Status {
  +ANSØGT
  +OPTAGET
  +AFMELDT
}

class Ugedag {
  +MAN
  +TIR
  +ONS
  +TOR
  +FRE
  +LØR
  +SØN
}

%% --- Relationer og multipliciteter ---
Studerende "1" --> "0..*" Tilmelding : tilmelder sig
Kursus "1" --> "0..*" Tilmelding
Kursus "1" --> "1..*" Hold : har >
Hold "1" --> "1" Lokale : afvikles i >
Hold "1" --> "1" TimeSlot : afholdes på >
Underviser "1" --> "0..*" Kursus : udbyder >

```mermaid
classDiagram
direction LR

class School
class Student
class Teacher
class Class
class Subject
class Hours
class Room

%% Relationer (som set i dit diagram)
School "1" --> "0..*" Student : har >
School "1" --> "0..*" Teacher : ansætter >
School "1" --> "0..*" Class : organiserer >

Class "1" --> "0..*" Student : indeholder >
Class "1" --> "1..*" Subject : underviser i >
Class "1" --> "1" Room : foregår i >
Class "1" --> "1..*" Teacher : undervises af >
Class "1" --> "1" Hours : har >

Subject "1" --> "0..*" Teacher : undervises af >

