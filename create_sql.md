//Create Main Buy Action Table
CREATE TABLE "ActionModel" (
	"Customerid"	TEXT NOT NULL UNIQUE,
	"Productid"	TEXT NOT NULL UNIQUE,
	"Product"	TEXT,
	"CardN"	TEXT NOT NULL,
	PRIMARY KEY("Customerid","Productid")
);

//Create Book Table
CREATE TABLE "Book" (
	"Productid"	TEXT NOT NULL UNIQUE,
	"ISBN"	TEXT NOT NULL UNIQUE,
	"Title"	TEXT NOT NULL,
	"Author"	TEXT,
	"Year"	INTEGER NOT NULL,
	PRIMARY KEY("Productid","ISBN")
);

//Create Video Table
CREATE TABLE "Video" (
	"Productid"	TEXT NOT NULL UNIQUE,
	"Title"	TEXT NOT NULL,
	"StarName"	TEXT,
	"Year"	INTEGER,
	PRIMARY KEY("Productid")
);

//Create Customer Table
CREATE TABLE "Customer" (
	"Customerid"	TEXT NOT NULL UNIQUE,
	"FirstName"	TEXT NOT NULL,
	"LastName"	TEXT NOT NULL,
	"Phone"	INTEGER NOT NULL,
	"CardN"	INTEGER NOT NULL,
	PRIMARY KEY("Customerid")
);
