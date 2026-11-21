# Слід взаємодії з AI для Завдання 3

## 1. Початковий промпт до AI
* "Склади 3 детальні Mermaid sequenceDiagram для трьох Gherkin-сценаріїв прецеденту 'Оформити видачу примірника читачу' (успішна видача, відмова через борги, відмова через пошкоджений примірник). Використай учасників Librarian, LoanService, BookCopyRepository, LoanRepository. Додай activation bars та фрагменти alt, opt, loop."

## 2. Сира відповідь
* закрив deactivate Service всередині першої гілки блоку alt (через що гілка else залишилася без активного бару);
* використав BookRepository замість BookCopyRepository для оновлення статусу примірника;
* у циклі loop не вказав перевірку returnDate == null.

## 3. Ручний аудит та виправлення
* Прийнято: Розподіл на 3 окремі діаграми під кожен Gherkin-сценарій, назви методів у стилі C# (issueBookCopy, getActiveLoansByReader, createLoan, updateStatus).
* Виправлено перед комітом:
  * Винесено deactivate Service за межі блоку alt, щоб activation bar охоплював усі гілки сценарію.
  * Замінено BookRepository на BookCopyRepository для узгодження з ER-моделлю із Завдання 1.
