[//]: # (A flask web app to manage library data)
# ddl-library-web Report

## Outline of the Web Application
The application consists of two main parts. One is a public access for borrowers to search for books' availibility, the other one 
is for staff to manage borrowers and loans.

### Home Page
Home page extends base.html which has the top navigation bar, the home page can be accessed by default route(/). On the home page, there is a navigation bar on the header, the main body inludes library information on the left area, an big library pictureon the right area. Cantact and location will display on footer.

<img src="images/home_page.PNG" width="400px" alt="home"></img>

### Public Search Page
The public Search Book function is on the right of the navigation bar. Its route is /searchbooks, its template is search_book.html. The route will display a search box for people to enter book title or book author to search. After clicking search button, the template search_book_result.html will pass the book search result data to route /search-book-result. Search result data will display all the bookcopies including book title, book author, year of publication, status(availible or on loan), if it's on loan, display the due date.
On this page, List All Books can display the avalibility of all the bookcopies, pass the data from the template search_book_result.html to route /list-all-books.

<img src="images/public_search.PNG" width="400px" alt="publicsearch"></img> 

### Staff Page
Staff can access the Staff Page by the route /staff. There is a side bar on the right of the main body. The functions are all listed on the side bar, they are Search Book, Issue Book, Return Book, Search Borrower, Update Borrower, Add New Borrower, Overdue Books, Loan Summary, Borrower Summary. 

<img src="images/staff.PNG" width="800px" alt="staff"></img>

Search Book function displays on the staff main page, after staff finishing searching, the template staff_search_book_result.html will pass the book search result data to route /staff-search-book-result. Search result data will display the details of the bookkcopies including id, book title, book author, year of publication, status(availible or on loan), if it's on loan, display the due date. On this page, List All Books can display the avalibility of all the bookcopies, pass the data from the template staff_search_book_result.html to route /staff-list-all-books.

<img src="images/staff_search_book.PNG" width="400px" alt="staffsearchbook"></img>

Issue Book and Return Book function both have a dropdown select form which also accept text input, so staff can search the information quickly. The template staff_issue_book_to_borrower.html and staff_return_book.html pass bookcopy and boorower data to route /staff-issue-book and staff-return-book.
After Issue book successfully, the loans table in the database will be inserted one loan data. After Returning book successfully, the loans table in the database will be updated on the Returned column. A List All Loans function provided for staff to check the updated data. A template current_loans.html will pass the latest loans to route /currentloans.

Search Borrower function is similar with the Search Book function, the template staff_search_borrower_result.html pass searched borrower details to route /search-boroower-result.
Apart form checking the borrower details, an Update function is provided on each borrower, staff can edit borrower from here directly. 

<img src="images/search_borrower.PNG" width="400px" alt="searchborrower"></img>

Update Borrower function needs staff to search borrower first, and then update the searched borrower, or staff can use List All Borrowers to list all the borrower and find the one to update.
After clicking Update, the staff_update_borrower will pass the exact borrower detail to route /update_borrower/&lt;borrowerid>;, staff submit changes after editting any information, and then the borrowers table will updated by the change.

<img src="images/update_borrower.PNG" width="400px" alt="updateborrower"></img>

Add Borrower function displays a empty form for staff to input all the information of a new borrower, after finishing inputting the template staff_add_new_borrower passes the data to route /borrower/add,  and then the borrowers table inserts a new borrower.

Overdue Books function lists all the overdue books which have been on loan longer than 35 days. The template staff_list_overdue_books.html passes overdue bookcopies data to route /list-overdue-books.

Loan Summary function lists the loans data, including bookid, bookcopyid, book title, book format and the number of times each book has been loaned on total. The template staff_list_loan_summary.html passes loans data to route /list-loan-summary.

Borrower Summary function lists the borrower information including boorowerid, borrower full name, and the number of loans each borrower has had. The template staff_list_borrower_summary.html passes borrower data to route /list-borrower-summary.
