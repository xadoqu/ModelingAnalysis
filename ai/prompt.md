## 1. ER DIAGRAM
> "Згенеруй концептуальну ER-модель для системи управління бібліотекою на основі специфікації spec.md у синтаксисі Mermaid erDiagram. Не використовуй проміжні таблиці для N:M."

Reader:
reader_id (PK, UUID)
full_name (string)
phone (string)
email (string)

Book:
book_id (PK, UUID)
title (string)
isbn (string)
publication_year (int)
category_id (FK, UUID)

Category:
category_id (PK, UUID)
category_name (string)

Author:
author_id (PK, UUID)
author_name (string)

BookCopy:
copy_id (PK, UUID)
book_id (FK, UUID)
status (string)

Loan:
loan_id (PK, UUID)
reader_id (FK, UUID)
copy_id (FK, UUID)
issue_date (date)
due_date (date)
return_date (date, optional)

Category 1:N Book
Book N:M Author
Book 1:N BookCopy
Reader 1:N Loan
BookCopy 1:N Loan

## Що відхилено або виправлено:
  1. Початково AI запропонував поле publish_year замість publication_year. Відхилено, повернуто publication_year згідно зі spec.
  2. Початково AI згенерував відсутність відображення обов'язковості для return_date. Уточнено бізнес-логіку: return_date є optional (null).
  3. Перевірено сутність Loan - залишено як асоціативну сутність, оскільки вона має власні часові атрибути.

## 2. Сира відповідь AI
```
erDiagram
    CATEGORY ||--o{ BOOK : "categorizes"
    BOOK }|--|{ AUTHOR : "written_by"
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
        string status
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
        date return_date
    }
```
