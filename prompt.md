# ER-Diagram
Сгенерувати ER-діаграму на мові Mermaid за атрибутами та зв'язками:
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
