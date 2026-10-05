# Чому цей домен?
* Наявнысть розмежування між самою книгою та копіями
* Наявність зв'язку M:N
* Наявність історії видачи з чітким фіксуванням дати
  
# Чому 3NF
* Немає залежності між неключевими полями.

# Сінхронізація
| Сутність | spec.md | er-diagram.mmd |
| ----------- | ----------- | ----------- |
| Reader   | reader_id, full_name, phone, email   | reader_id, full_name, phone, email    |
| Book   | book_id, title, isbn, publication_year, category_id    | book_id, title, isbn, publication_year, category_id    |
| Category  | category_id, category_name    | category_id, category_name    |
| Author  | author_id, author_name     | author_id, author_name    |
| BookCopy   | copy_id, book_id, status    | copy_id, book_id, status    |
| Loan   | loan_id, reader_id, copy_id, issue_date, due_date, return_date    | loan_id, reader_id, copy_id, issue_date, due_date, return_date    |
| Типи  | PK/FK - UUID   | PK/FK - UUID    |
