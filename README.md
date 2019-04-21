# Java
java with oracle



```  
  /**  *
  * @author VIK
  * Create Connection with Oracle server
  */
  
  
  
 import java.sql.*;
 
 public class ConnTest {
 
     public static void main(String... args) throws Exception {
         Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
         Connection con = DriverManager.getConnection("jdbc:odbc:excelDB","","");//vikku", "", "");
         if (con == null) {
             System.out.println("Access denied...");
         } else {
             System.out.println("Connection Successful...");
         }
         Statement st = con.createStatement();
         ResultSet rs = st.executeQuery("select * from [student$]");
         ResultSetMetaData rsmd = rs.getMetaData();
         int colcount = rsmd.getColumnCount();           
         while (rs.next()) {
             System.out.println("");
             for (int i = 1; i < colcount; i++) {
                 System.out.print("\t" + rs.getString(i));
             }
         }
         rs.close();
         st.close();
         con.close();
     }
 }
```
