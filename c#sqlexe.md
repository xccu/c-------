c-------
========

c#数据库公共类
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Configuration;
using System.Data;
using System.Linq;
using System.Web.Security;
using System.Web.UI;
using System.Web.UI.HtmlControls;
using System.Web.UI.WebControls;
using System.Web.UI.WebControls.WebParts;
using System.Xml.Linq;
using System.Data.Sql;
using System.Data.SqlClient;
using System.ComponentModel;


/// <summary>
///sqlexe 的摘要说明
/// </summary>
public class sqlexe
{
    public string ssql;
    public string ConnStr;
    SqlConnection Conn;  //建立到指定资源的连接
    SqlCommand Cmd;//对一个数据源执行命令
    SqlDataReader Dr;//从一个数据源读取只进的只读数据流

    public sqlexe(string _ssql, string _ConnStr)
	{
        ssql = _ssql;
        ConnStr = _ConnStr;
	}

    public void exe()
    {
        int ret;
        Conn = new SqlConnection(ConnStr);
        Conn.Open();
        Cmd = new SqlCommand(ssql, Conn);
        ret = Cmd.ExecuteNonQuery();
        Conn.Close();
    }

  public SqlDataReader select()
    {
        Conn = new SqlConnection(ConnStr);
        Conn.Open();
        Cmd= new SqlCommand(ssql, Conn); 
        Dr =Cmd.ExecuteReader(); 
        return Dr;
    }
}

