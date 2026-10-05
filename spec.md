## Attributes
  * Reader - Читач:
  	* reader_id - унікальний айді читача (PK, UUID)
  	* full_name - повний ПІБ (string)
  	* phone - контактні данні (string)
    * email - контактні данні (string)
  * Book - Книга:
  	* book_id - унікальний айді книги (PK, UUID)
  	* title - назва книги (string)
  	* isbn - міжнародний стандартний номер книги (string)
  	* publication_year - дата публікації (int)
  	* category_id - посилання на категорію (FK, UUID)
  * Category - Категорія:
  	* category_id - унікальний айді категорії (PK, UUID)
  	* category_name - назва категорії (string)
  * Author - Автор:
  	* author_id - унікальний айді автора (PK, UUID)
  	* author_name - ім’я автора (string)
  * BookCopy - Копія книги:
  	* copy_id - унікальний айді конкретної копії (PK, UUID)
  	* book_id - посилання на книгу (FK, UUID)
  	* status - поточний стан копії (string)
  * Loan - Видача:
  	* loan_id - унікалтний айді видачи (PK, UUID)
  	* reader_id - посилання на читача (FK, UUID)
  	* copy_id - посилання на копію (FK, UUID)
  	* issue_date - дата видачі книги (date)
  	* due_date - планованна дата повернення (date)
  	* return_date - фактична дата повернення (date, optional)

## Relationships
  * Category 1:N Book
  * Book N:M Author
  * Book 1:N BookCopy
  * Reader 1:N Loan
  * BookCopy 1:N Loan

## Acceptance Criteria
  * Normalisation:
    * Модель відповідає вимогам 3NF
    
  * Key Consistency:
    * Усі PK/FK мают UUID тип данних
    
  * No Junction Entities:
    * Book M:N Author прямий, без створення окремої таблиці
