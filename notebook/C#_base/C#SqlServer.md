# C# SqlServer

## 1 安装依赖

* visual Studio ➡ 工具 ➡ NuGet包管理器 ➡ 管理解决方案的NuGet程序包

* 安装System.Data.SqlClient包

  ![](.\images\01.png)

## 2 导入依赖

```c#
using System.Data.SqlClient;
```

## 3 连接与关闭SqlServer

```c#
# 使用windows验证
String connStr = "Server=DESKTOP-TB29AIU;DataBase=emarket;integrated security=SSPI";
# 使用用户密码验证
String connStr = "Server=DESKTOP-TB29AIU;DataBase=emarket;uid=sa;pwd=123456";
# 创建SqlConnection对象用于连接
SqlConnection conn = new SqlConnection(connStr);
# 连接
conn.Open();
# 关闭
conn.Close();
```

## 4 基础操作

```c#
using System;
using System.Data;
using System.Data.SqlClient;

namespace SQLServerTest
{
    class Database
    {
        private SqlConnection conn;
        //服务器
        private string server;
        //数据库
        private string dataBase;
        //用户名
        private string uid;
        //密码
        private string pwd;
        //直接通过url连接
        public Database(string url) 
        {
            conn = new SqlConnection(url);
        }
        //通过用户名、密码连接
        public Database(string server, string dataBase, string uid, string pwd)
        {
            this.server = server;
            this.dataBase = dataBase;
            this.uid = uid;
            this.pwd = pwd;
            string url = "Server=" + server + ";DataBase=" + dataBase + ";uid=" + uid + ";pwd=" + pwd;
            conn = new SqlConnection(url);
        }
        //通过windows连接
        public Database(string server, string dataBase)
        {
            this.server = server;
            this.dataBase = dataBase;
            string url = "Server=" + server + ";DataBase=" + dataBase + ";integrated security=SSPI";
            conn = new SqlConnection(url);
        }

        //查询
        public DataSet Query(string sql)
        {
            DataSet ds = new DataSet();
            try
            {
                conn.Open();
                SqlDataAdapter adp = new SqlDataAdapter(sql, conn);
                adp.Fill(ds);
            }
            catch
            {
                throw new Exception("Database Query error.");
            }
            finally
            {
                conn.Close();
            }

            return ds;
        }

        //增删改
        public int executeNoneQuery(string sql)
        {
            SqlCommand command = new SqlCommand(sql, conn);
            try
            {
                conn.Open();
                command.ExecuteNonQuery();
            }
            catch(Exception e)
            {
                Console.WriteLine(e.Message.ToString());
                return 0;
            }
            finally
            {
                conn.Close();
            }
            return 1;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Database database = new Database("Server=DESKTOP-TB29AIU;DataBase=emarket;uid=sa;pwd=123456");

            DataSet ds =database.Query(@"SELECT * FROM sys_user");

            foreach(DataTable dt in ds.Tables)
            {
                foreach(DataRow dr in dt.Rows)
                {
                    foreach(DataColumn dc in dt.Columns)
                    {
                        Console.WriteLine("{0}, {1}", dc.ColumnName, dr[dc]);
                    }
                }
            }
        }
    }
}
```

