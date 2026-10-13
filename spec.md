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
  	* status - поточний стан копії (string) ("available", "borrowed", "damaged")
  * Loan - Видача:
  	* loan_id - унікалтний айді видачи (PK, UUID)
  	* reader_id - посилання на читача (FK, UUID)
  	* copy_id - посилання на копію (FK, UUID)
  	* issue_date - дата видачі книги (date)
  	* due_date - планованна дата повернення (date)
  	* return_date - фактична дата повернення (date, optional) (null якщо книга ще перебуває в читача та не повернуто)

## Relationships
  * Category 1:N Book (Категорія може існувати без книг, Книга обов'язково має належати чітко до однієї категорії)
  * Book N:M Author (Книга повинна мати хоча б одного автора. Автор може існувати в системі ще до прив'язки до книг, або мати багато виданих книг)
  * Book 1:N BookCopy (Запис про книгу може не мати жодного фізичного примірника на балансі. Кожна копія обов'язково прив'язана чітко до однієї книги)
  * Reader 1:N Loan (Читач може зареєструватися, але ще нічого не позичати. Кожен запис видачі обов'язково належить конкретному читачу)
  * BookCopy 1:N Loan (Новий примірник книги може ще жодного разу не видаватися. Кожен запис стосується чітко одного примірника книги)

## Acceptance Criteria
  * Normalisation:
    * Модель відповідає вимогам 3NF
    
  * Key Consistency:
    * Усі PK/FK мают UUID тип данних
    
  * No Junction Entities:
    * Book M:N Author прямий, без створення окремої таблиці
