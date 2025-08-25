# Music-Store-Data-Analysis----SQL
This project presents a comprehensive SQL database designed for a music store. It covers essential entities and relationships needed to manage music inventory, sales, customers, employees, and business insights. The database includes tables for genres, media types, artists, albums, tracks, customers, employees, invoices, invoice lines, and playlists.

Through carefully crafted SQL queries, the project solves real-world business questions, such as identifying top customers, best-selling genres, and popular artists, making it a practical foundation for analytics and decision-making in the music retail industry.

### ER Diagram
<img width="2509" height="1248" alt="image" src="https://github.com/user-attachments/assets/25f008ec-1782-4c24-85c4-546e8beb2838" />

### Creating Tables
The project begins by creating structured tables for storing music store data, including information about genres, media types, employees, customers, artists, albums, tracks, invoices, and more. Primary and foreign keys are used to ensure data integrity and meaningful relationships between different entities.
<img width="868" height="933" alt="image" src="https://github.com/user-attachments/assets/e16255c4-ebb0-4495-bf00-a52e474cd94d" />

### Importing Data Into Tables
Data is imported into tables in an orderly manner using the LOAD DATA INFILE command for bulk data loads from CSV files, ensuring efficient population of large datasets like tracks. Additionally, the import wizard option in database management tools provides a user-friendly interface for importing data step-by-step, allowing customization and validation during the import process.
<img width="959" height="1080" alt="image" src="https://github.com/user-attachments/assets/aaf70176-dc53-4831-b18c-4e2819b263a3" />

### Challenges we face
There are actually 9 employees in total, but after importing the CSV file into the Employee table, we noticed it contained details for only 8 employees. Upon reviewing the entire CSV file, we decided to manually add the 9th employee's details into the Employee table.
<img width="1734" height="722" alt="image" src="https://github.com/user-attachments/assets/d5f3f2e7-bc07-4c6d-8517-f2956932e716" />

## QUERIES

#### 1. who is the senior most employee based on job title ?
SELECT employee_id , first_name ,  last_name , title , levels,hire_date
FROM employee
ORDER BY levels DESC , hire_date ASC
LIMIT 1 ;
<img width="2092" height="367" alt="image" src="https://github.com/user-attachments/assets/9ef3c99c-3d45-434e-b24f-9972a7675b0a" />

#### 2. Which countries have the most Invoices?
SELECT billing_country AS country , COUNT(*) AS invoice_count
FROM invoice 
GROUP BY billing_country
ORDER BY  invoice_count DESC ;
<img width="760" height="1163" alt="image" src="https://github.com/user-attachments/assets/402c9ac2-34ef-463c-82ac-5208dddd6d8c" />

#### 3. What are the top 3 values of total invoice?
SELECT DISTINCT total
FROM invoice 
ORDER BY total DESC LIMIT 3 ;
<img width="457" height="455" alt="image" src="https://github.com/user-attachments/assets/506b49ee-3c52-4aaa-8345-996fbaa0fbce" />

####  4. Which city has the best customers?
SELECT billing_city, SUM(total) AS total_revenue FROM invoice
 GROUP BY billing_city 
ORDER BY total_revenue DESC
LIMIT 1;
<img width="1016" height="281" alt="image" src="https://github.com/user-attachments/assets/52ca73d0-2c64-4400-a630-986fe333e0cd" />

####  5. Who is the best customer?
SELECT c.customer_id , c.first_name , c.last_name, SUM(i.total) AS total_spent
FROM customer c
JOIN invoice i on c.customer_id = i.customer_id 
GROUP BY c.customer_id 
ORDER BY total_spent DESC
LIMIT 1 ;
<img width="1700" height="246" alt="image" src="https://github.com/user-attachments/assets/83c74940-2e9a-4638-a01c-5509e9fabd32" />

####  6. Write a query to return the email, first name, last name, & Genre of all Rock Music listeners.
SELECT DISTINCT c.email , c.first_name , c.last_name , g.name AS genre FROM customer c
JOIN invoice i ON i.customer_id = c.customer_id
JOIN invoiceline il ON   il.invoice_id = i.invoice_id
JOIN track t ON t.track_id = il.track_id
JOIN genre g ON g.genre_id = t.genre_id
WHERE g.name = 'ROCK’
ORDER BY c.email ASC ;
<img width="1375" height="950" alt="image" src="https://github.com/user-attachments/assets/069f15fb-4133-4aef-983d-4056c5f416ad" />

#### 7. Let's invite the artists who have written the most rock music in our dataset. 
SELECT a.artist_id , a.name , COUNT(*) AS rock_track_count 
FROM artist a 
JOIN album al ON  al.artist_id = a.artist_id
JOIN track t ON t.album_id = al.album_id
JOIN genre g ON g.genre_id = t.genre_id 
WHERE g.name = 'ROCK’
GROUP BY a.artist_id , a.name
ORDER BY rock_track_count DESC , a.name
LIMIT 10 ;
<img width="1338" height="815" alt="image" src="https://github.com/user-attachments/assets/0ae93448-2aa7-4374-97f2-6804d29b7f0a" />






This project demonstrates how SQL empowers us to transform raw music store data into actionable business insights. By designing and querying a relational database, we can accurately identify which cities generate the most revenue, which customers are our top spenders, and which genres and artists are most popular. 
