using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Configuration;
using System.Data.SQLite;
using WindowsFormsApp5.Model;

namespace WindowsFormsApp5.Action
{
    public class ActionLogic
    {
        private static string Default = ConfigurationManager.ConnectionStrings["Default"].ConnectionString;
        private static ActionLogic _instancia = null;
        public ActionLogic()
        {

        }
        public static ActionLogic Instancia
        {
            get
            {
                if (_instancia == null)
                {
                    _instancia = new ActionLogic();
                }
                return _instancia;
            }
        }
        public bool Save(ActionModel obj)
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

        public bool Update(ActionModel obj)
        {
            bool answer = true;
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "update ActionModel set Customerid = @Customerid, Productid = @Productid, Product = @Product, CardN = @CardN";
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

        public bool Delete(ActionModel obj)
        {
            bool answer = true;
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "delete from ActionModel where Customerid = @Customerid";
                SQLiteCommand cmd = new SQLiteCommand(query, connection);
                cmd.CommandType = System.Data.CommandType.Text;

                if (cmd.ExecuteNonQuery() < 1)
                {
                    answer = false;
                }
            }
            return answer;
        }


        public List<ActionModel> Listar()
        {
            List<ActionModel> oLista = new List<ActionModel>();
            using (SQLiteConnection connection = new SQLiteConnection(Default))
            {
                connection.Open();
                string query = "select * from ActionModel";
                SQLiteCommand cmd = new SQLiteCommand(query, connection);
                cmd.CommandType = System.Data.CommandType.Text;
                using (SQLiteDataReader dr = cmd.ExecuteReader())
                {
                    while (dr.Read())
                    {
                        oLista.Add(new ActionModel()
                        {
                            Customerid = dr["Customerid"].ToString(),
                            Productid = dr["Productid"].ToString(),
                            Product = dr["Product"].ToString(),
                            CardN = dr["CardN"].ToString(),
                        });

                    }
                }
            }
            return oLista;
        }
    }
}
