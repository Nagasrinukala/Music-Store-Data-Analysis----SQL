# Music-Store-Data-Analysis----SQL
This project presents a comprehensive SQL database designed for a music store. It covers essential entities and relationships needed to manage music inventory, sales, customers, employees, and business insights. The database includes tables for genres, media types, artists, albums, tracks, customers, employees, invoices, invoice lines, and playlists.

Through carefully crafted SQL queries, the project solves real-world business questions, such as identifying top customers, best-selling genres, and popular artists, making it a practical foundation for analytics and decision-making in the music retail industry.

### ER Diagram
<img width="2509" height="1248" alt="image" src="https://github.com/user-attachments/assets/25f008ec-1782-4c24-85c4-546e8beb2838" />

### Creating Tables
The project begins by creating structured tables for storing music store data, including information about genres, media types, employees, customers, artists, albums, tracks, invoices, and more. Primary and foreign keys are used to ensure data integrity and meaningful relationships between different entities.

### Importing Data Into Tables
Data is imported into tables in an orderly manner using the LOAD DATA INFILE command for bulk data loads from CSV files, ensuring efficient population of large datasets like tracks. Additionally, the import wizard option in database management tools provides a user-friendly interface for importing data step-by-step, allowing customization and validation during the import process.

### Challenges we face
There are actually 9 employees in total, but after importing the CSV file into the Employee table, we noticed it contained details for only 8 employees. Upon reviewing the entire CSV file, we decided to manually add the 9th employee's details into the Employee table.
<img width="1734" height="722" alt="image" src="https://github.com/user-attachments/assets/d5f3f2e7-bc07-4c6d-8517-f2956932e716" />

## Conclusion
This project demonstrates how SQL empowers us to transform raw music store data into actionable business insights. By designing and querying a relational database, we can accurately identify which cities generate the most revenue, which customers are our top spenders, and which genres and artists are most popular. These findings guide strategic decisions, such as selecting optimal locations for marketing campaigns or music festivals and targeting our best customers for promotions.Additionally, the process offers valuable hands-on experience with complex SQL techniques—including joins, subqueries, window functions, and Common Table Expressions (CTEs)—beyond basic SELECT statements. Ultimately, this analytical approach ensures informed decision-making, supports business growth, and enhances our ability to respond dynamically to customer preferences and trends in the music industry.

