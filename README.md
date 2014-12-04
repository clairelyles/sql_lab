#SQL Lab


##Getting Started

To get started we'll need to import the booktown.sql file.

1. open terminal
2. use the command `psql -f booktown.sql`
3. type `sql` to open your psql console
4. type \list to ensure the booktown database was successfully completed

##Instructions
Provide the follow sql statements below each question.

##Order
1. Find all subjects sorted by subject
	SELECT * FROM subjects ORDER BY subject;

2. Find all subjects sorted by location
	SELECT * FROM subjects ORDER by location;


##Where
1. Find the book "Little Women"
	SELECT * FROM books WHERE title = 'Little Women';

2. Find all books containing the word "Python"
	SELECT * FROM books WHERE title LIKE '%Python%';

3. Find all subjects with the location "Main St" sort them by subject
	SELECT subject FROM subjects WHERE location 'Main St';

##Joins

1. Find all books about Computers list ONLY book title
	SELECT title FROM books JOIN subjects ON books.subject_id = subjects.id WHERE subject = 'Computers';

* Find all books and display ONLY
	SELECT title, last_name, first_name, subject FROM books JOIN authors ON books.author_id = authors.id JOIN subjects ON books.subject_id = subjects.id;


* Find all books that are listed in the stock table
	SELECT title, retail FROM books JOIN editions ON books.id = editions.book_id JOIN stock ON editions.isbn = stock.isbn ORDER BY retail ASC;


* Find the book "Dune" and display ONLY
	SELECT title, editions.isbn, publishers.name, stock.retail FROM books JOIN editions ON books.id = editions.book_id JOIN publishers ON editions.publisher_id = publishers.id JOIN stock ON editions.isbn = stock.isbn WHERE books.title = 'Dune';

	* Book title
	books - book.id

	* ISBN number
	editions - books_id isbn publisher_id

	* Publisher name
	publishers - publishers.name

	* Retail price
	stock - isbn retail


* Find all shipments sorted by ship date display ONLY:
	SELECT customers.first_name, customers.last_name, shipments.ship_date, title FROM books JOIN editions ON books.id = editions.book_id JOIN shipments ON editions.isbn = shipments.isbn JOIN customers ON shipments.customer_id = customers.id;

	* Customer first name
	customers - id, last_name, first_name

	* Customer last name
	customers - id, last_name, first_name

	* ship date
	shipments - customer_id and shipments.id and isbn and ship_date

	* book title
	books - id, author_id and subject_id
	editions - book_id and isbn

* Find all books that have either a 2nd or 3rd edition associated to it display ONLY:
	SELECT title, first_name || ' ' || last_name, edition FROM books JOIN authors ON books.author_id = authors.id JOIN editions ON books.id = editions.book_id WHERE edition=3 OR edition=2 ORDER BY title, edition;

	* Book title
	Books - id, title, author_id

	* Book Author
	authors - id

	* Edition Number
	editions - book_id, edition

