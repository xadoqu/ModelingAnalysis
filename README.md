## Name:
  * Library Managment System
## Desciption:
  * Моделювання роботи бібліотеки: облік книжкового фонду, категорій та авторів, відстеження копій книжок, реєстрація видач книжок відвідувчам та контролем їх терміну.
## Structure:
  * spec.md - специфікація сутностей, атрибутів, зв'язків та критерій прийняття
  * er-diagram.mmd - Mermaid ER-діаграмма
  * ai/prompt.md - Архів використанних промптів 
  * DEFENSE.md - Обгрунтування нормалізації, вибору домену та таблиця відповідності
  * adr/0001-separate-book-and-bookcopy.md - Архітектурне рішення про розділення книги та копії

# ER-Diagram
```mermaid
erDiagram
    CATEGORY ||--o{ BOOK : "categorizes"
    BOOK }o--|{ AUTHOR : "written_by"
    BOOK ||--o{ BOOK_COPY : "has_copies"
    READER ||--o{ LOAN : "borrows"
    BOOK_COPY ||--o{ LOAN : "is_borrowed_in"

    CATEGORY {
        UUID category_id PK
        string category_name
    }

    BOOK {
        UUID book_id PK
        UUID category_id FK
        string title
        string isbn
        int publication_year
    }

    AUTHOR {
        UUID author_id PK
        string author_name
    }

    BOOK_COPY {
        UUID copy_id PK
        UUID book_id FK
        string status "available|borrowed|damaged"
    }

    READER {
        UUID reader_id PK
        string full_name
        string phone
        string email
    }

    LOAN {
        UUID loan_id PK
        UUID reader_id FK
        UUID copy_id FK
        date issue_date
        date due_date
        date return_date "nullable"
    }
