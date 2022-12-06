using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Configuration;
using System.Data.SQLite;
using WindowsFormsApp5.Model;

//Here we have the insert to populate all tables.

namespace WindowsFormsApp5.Action
{
        //Populate Table Action
        public bool Insert_Action(ActionModel obj)
        {
            bool answer = true;
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "insert into ActionModel (Customerid, Productid, Product, CardN) values (@Customerid, @Productid, @Product, @CardN)";
                SQLiteCommand cmd = new SQLiteCommand(query, connection);
                cmd.Parameters.Add(new SQLiteParameter("@Customerid", obj.Customerid));
                cmd.Parameters.Add(new SQLiteParameter("@Productid", obj.Productid));
                cmd.Parameters.Add(new SQLiteParameter("@Product", obj.Product));
                cmd.Parameters.Add(new SQLiteParameter("@CardN", obj.CardN));
                cmd.CommandType = System.Data.CommandType.Text;
                if (cmd.ExecuteNonQuery() < 1)
                {
                    answer = false;
                }
            }
            return answer;
        }
        //Populate Table Book
         public bool Insert_Book(BookModel obj)
        {
            bool answer = true;
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "insert into ActionModel (ISBN, Productid, Title, Author, Year) values (@ISBN, @Productid, @title, @author, @year)";
                SQLiteCommand cmd = new SQLiteCommand(query, connection);
                cmd.Parameters.Add(new SQLiteParameter("@ISBN", obj.ISBN));
                cmd.Parameters.Add(new SQLiteParameter("@Productid", obj.Productid));
                cmd.Parameters.Add(new SQLiteParameter("@title", obj.title));
                cmd.Parameters.Add(new SQLiteParameter("@author", obj.author));
                cmd.Parameters.Add(new SQLiteParameter("@year", obj.year));
                cmd.CommandType = System.Data.CommandType.Text;
                if (cmd.ExecuteNonQuery() < 1)
                {
                    answer = false;
                }
            }
            return answer;
        } 
        //Populate Table Customer
        public bool Insert_Customer(CustomerModel obj)
        {
            bool answer = true;
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "insert into ActionModel (Customerid, FirstName, LastName, Phone, CardN) values (@Customerid, @FirstName, @LastName, @Phone, @CardN)";
                SQLiteCommand cmd = new SQLiteCommand(query, connection);
                cmd.Parameters.Add(new SQLiteParameter("@Customerid", obj.Customerid));
                cmd.Parameters.Add(new SQLiteParameter("@FirstName", obj.FirstName));
                cmd.Parameters.Add(new SQLiteParameter("@LastName", obj.LastName));
                cmd.Parameters.Add(new SQLiteParameter("@Phone", obj.Phone));
                cmd.Parameters.Add(new SQLiteParameter("@CardN", obj.CardN));
                cmd.CommandType = System.Data.CommandType.Text;
                if (cmd.ExecuteNonQuery() < 1)
                {
                    answer = false;
                }
            }
            return answer;
        } 
        //Populate Table Video
        public bool Insert_Video(ActionModel obj)
        {
            bool answer = true;
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "insert into ActionModel (Productid, Title, StarName, Year) values (@Productid, @Title, @StarName, @Year)";
                SQLiteCommand cmd = new SQLiteCommand(query, connection);
                cmd.Parameters.Add(new SQLiteParameter("@Productid", obj.Productid));
                cmd.Parameters.Add(new SQLiteParameter("@Title", obj.Title));
                cmd.Parameters.Add(new SQLiteParameter("@StarName", obj.StarName));
                cmd.Parameters.Add(new SQLiteParameter("@Year", obj.Year));
                cmd.CommandType = System.Data.CommandType.Text;
                if (cmd.ExecuteNonQuery() < 1)
                {
                    answer = false;
                }
            }
            return answer;
        }
    }
}
