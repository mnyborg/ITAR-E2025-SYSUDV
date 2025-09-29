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
```
## Trin1:
```mermaid
classDiagram
    class School
    class Student
    class Class
    class Subject
    class Room
    class Teacher
    class Hour
```
## Trin2:
```mermaid
classDiagram
    class School
    class Student
    class Class
    class Subject
    class Room
    class Teacher
    class Hour

    School --> Student
    School --> Teacher
    School --> Class

    Class --> Student
    Class --> Hour

    Hour --> Subject
    Hour --> Room
    Hour --> Teacher
```
## Trin 3:

```mermaid
classDiagram
    class School {
    }

    class Student {
    }

    class Class {
    }

    class Subject {
    }

    class Room {
    }

    class Teacher {
    }

    class Hour {
    }

    School "1" --> "0..*" Student
    School "1" --> "0..*" Teacher
    School "1" --> "0..*" Class

    Class "1" --> "0..*" Student
    Class "1" --> "0..*" Hour

    Hour "1" --> "1" Subject
    Hour "1" --> "1" Room
    Hour "1" --> "1" Teacher

    Teacher "1" --> "0..*" Hour
    Subject "1" --> "0..*" Hour
    Room "1" --> "0..*" Hour
```
## Trin 4:
```mermaid
classDiagram
    class School {
      +schoolId: UUID
      +name: String
      +address: String
    }

    class Student {
      +studentId: UUID
      +fullName: String
      +email: String
      +enrollmentDate: Date
    }

    class Class {
      +classId: UUID
      +name: String        %% fx "1.A"
      +gradeLevel: Int     %% fx 1..9 eller årgang
      +year: Int           %% skoleår (fx 2025)
    }

    class Subject {
      +subjectCode: String %% fx "MATH"
      +title: String       %% fx "Mathematics"
      +ectsOrHours: Int    %% valgfrit felt til omfang
    }

    class Room {
      +roomCode: String    %% fx "B-201"
      +capacity: Int
      +building: String
    }

    class Teacher {
      +teacherId: UUID
      +fullName: String
      +email: String
      +hireDate: Date
    }

    class Hour {
      +hourId: UUID
      +dayOfWeek: Int      %% 1=Mon ... 7=Sun
      +startTime: Time
      +endTime: Time
      +weekNumber: Int     %% valgfrit, hvis relevant
    }

    %% Relationer med multiplicitet
    School "1" --> "0..*" Student
    School "1" --> "0..*" Teacher
    School "1" --> "0..*" Class

    Class "1" --> "0..*" Student
    Class "1" --> "0..*" Hour

    Hour "1" --> "1" Subject
    Hour "1" --> "1" Room
    Hour "1" --> "1" Teacher
```
"" Eksemel med identifikaitons af attributer.
```mermaid
classDiagram
    class Book {
      +bookId: UUID
      +isbn: String
      +title: String
    }

    class Author {
      +authorId: UUID
      +fullName: String
    }

    class Member {
      +memberId: UUID
      +fullName: String
      +email: String
      +joinedAt: Date
    }

    class Loan {
      +loanId: UUID
      +borrowedOn: Date
      +dueOn: Date
      +returnedOn: Date?   %% null => active
    }

    %% Relationships
    Member "1" --> "0..*" Loan
    Book "1" --> "0..*" Loan
    Book "0..*" -- "0..*" Author

