# 0. Чому цей домен?
* Наявнысть розмежування між самою книгою та копіями
* Наявність зв'язку M:N
* Наявність історії видачи з чітким фіксуванням дати

# 1. Що просили в AI
Усі промпти, відповіді та мої правки збережено в ai/prompt. Завданням було згенерувати Mermaid-діаграму за специфікацією без зайвих сполучних таблиць.
  
# 2. Чому 3NF
* Немає залежності між неключевими полями.

# 3. Топ-3 виправлених розбіжностей (spec - модель)

Провів аудит моделі та відкоригував розбіжності через оновлення специфікації та окремі коміти:

| № | Що було не так | Як виправив |
| :- | :--- | :--- |
| 1 | Різні назви поля року видання (publish_year та publication_year). | Виправив на publication_year у spec.md та діаграмі. | 
| 2 | Поля phone та email йшли в один рядок у специфікації. | Розділив на два окремих атрибути для атомарності. | 
| 3 | У spec не було розписано обов'язковість зв'язків та опціональність return_date. | Додав детальний опис кардинальності та обов'язковості в spec.md. | 
SHA: 89c9f55 

# 4. Сінхронізація
| Сутність | spec.md | er-diagram.mmd |
| ----------- | ----------- | ----------- |
| Reader   | reader_id, full_name, phone, email   | reader_id, full_name, phone, email    |
| Book   | book_id, title, isbn, publication_year, category_id    | book_id, title, isbn, publication_year, category_id    |
| Category  | category_id, category_name    | category_id, category_name    |
| Author  | author_id, author_name     | author_id, author_name    |
| BookCopy   | copy_id, book_id, status    | copy_id, book_id, status    |
| Loan   | loan_id, reader_id, copy_id, issue_date, due_date, return_date    | loan_id, reader_id, copy_id, issue_date, due_date, return_date    |
| Типи  | PK/FK - UUID   | PK/FK - UUID    |
