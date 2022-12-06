//Database Description: This database models an online shopping store of books and videos. There are 4 tables. 

-->The First Table, Action Model, is just the Action of buying an item. It has the following attributes:

  "Customerid"	TEXT NOT NULL UNIQUE,
  "Productid"	TEXT NOT NULL UNIQUE,
  "Product"	TEXT,
  "CardN"	TEXT NOT NULL,
  PRIMARY KEY("Customerid","Productid")
  
//Basically, a customer, with their customerid, just like a WSU ID, they input their customer id, which is unique to every customer,
they also input a Productid, which is also unique to every product, the Product which can either be a "Book" or a " Video" and input their CardN to pay. They are all strings
"Customerid" and "Productid" are Primary Keys.  The constaints are that Productid in Table Action must be equal to some Productid in Table Book or Table Video.
Another Constraint is that Customerid in table Action must be equal to Customerid in Table Customer

//SAMPLE DATA

Action("1","232","book","532125657")

-->The Second Table, Book has 4 attributes:

  "Productid"	TEXT NOT NULL UNIQUE,
	"ISBN"	TEXT NOT NULL UNIQUE,
	"Title"	TEXT NOT NULL,
	"Author"	TEXT,
	"Year"	INTEGER NOT NULL,
	PRIMARY KEY("Productid","ISBN")
  
  //Here, a book has a Productid, ISBN, Title, Author and Year. Productid is a ForeignKey. 
  //The constaints are that Productid in Table Action must be equal to some Productid in Table Book or Table Video.
  //SAMPLE DATA
  
  Book("321", "A-324153","Harry Potter","JK ROWLING","2000")
  
-->The Third Table, Video has 4 attributes:
  
    "Productid"	TEXT NOT NULL UNIQUE,
	  "Title"	TEXT NOT NULL,
	  "StarName"	TEXT,
	  "Year"	INTEGER,
	  PRIMARY KEY("Productid")
    
   //Similarly, a video will contain information such as the ProductId, the title, the StarName of the video, and the year of the video. The Foreign Key is ProductId.
   //The constaints are that Productid in Table Action must be equal to some Productid in Table Book or Table Video.
   //SAMPLE DATA
   
   Video("531","The Great Gatsby","Leonardo Di Caprio", 2013,)
   
-->The Last Table is Customer, which has 5 attributes:
   
   "Customerid"	TEXT NOT NULL UNIQUE,
	"FirstName"	TEXT NOT NULL,
	"LastName"	TEXT NOT NULL,
	"Phone"	INTEGER NOT NULL,
	"CardN"	INTEGER NOT NULL,
	PRIMARY KEY("Customerid")
  
  //The customer table contains information on the CustomersId, which is unique, along with its FirstName, LastName, Phone and CardN
  //Another Constraint is that Customerid in table Action must be equal to Customerid in Table Customer
  //SAMPLE DATA
  
  Customer("3","John", "Adams","3124233390","532125657")
  
  
  
