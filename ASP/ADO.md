增删查：都是返回受影响的行数

查询：

- 多行多表的结果集合：表接收 
- 单个值：变量

##### 为什么学ADO.NET

- 搭建一个界面（winform，asp）方便不懂sql语句的普通用户操作数据库中的数据

##### 什么是ADO.NET

- 一组类库，通过这组类库可以让我们以程序的方式访问数据库
- 帮助开发人员在程序中使用SQL语句来操作数据库,将SQL语句交给ADO.NET的相关对象,由该对象负责与数据库进行沟通来执行相关的操作.



## ADO.NET的组成

- ##### 第一部分：数据源提供程序（常用）

  - **Connection**(连接通道)，用来连接数据库
  - **Command**(命令对象)，用来执行SQL语句（增删改，查单个值）
  - **DataReader**(数据读取器)，返回一个对象，只读、只进的结果集，一条条读取数据（需要循环）
  - DataAdapter(数据适配器)：封装了上面三个对象的对象

- ##### 第二部分：数据集（DataSet）,临时数据库-内存

  - 断开式数据操作

### SqlDataReader数据读取器

- 只读,不能更新数据
- 一次只处理一条记录
- 查询结果可包含多条记录,但在读取过程中,只能从前向后依次把每一行查询结果调入内存(**Read()方法**)

#### 创建

- 通过SqlCommand对象的ExecuteReader方法创建

```c#
SqlConnection conn = new SqlConnection(connStr);
conn.Open();
string sql="";
SqlCommand comm = new SqlCommand(sql, conn);
SqlDataReader reader = comm.ExecuteReader();
while(reader.Read()){   //循环读取数据 
                    //索引的两种读取方式
                   MessageBox.Show(reader[0] + " " + reader["classname"]);
                }
conn.Close();
```



##### ADO.NET访问数据库的方式

- 方式一
  - 1.Connection
  - 2.Command
  - 3.执行完毕后将结果一条条返回，DataReader

- 方式二
  - DataAdapter+DataSet，其本质还是通过Connection、Command、DataReader将数据全部取出然后放到DataSDet中

 ExecuteReader()：返回一个对象，适用于的到具体数据的值，不是父盒条件的个数，不是聚合函数，单个值

ExecuteNonQuery：返回受影响的行数

ExecuteScalar()：返回满足条件的个数或者第一行的第一列值，返回类型**object**时需要做强制类型的转换（Convert）

SQL注入漏洞

- 一般在登录的场景下；使用一些特殊的字符进行对数据库进行攻击
- 采用sql参数化，SqlParameter



#### SqlDataAdapter数据访问适配器

适配了数据库和应用程序之间的隔阂

- 连接数据库后，一次性将表中的数据加入到C#内存中，然后关闭连接（自动打开连接数据库）

- 将SqlServer表适配成C#应用程序的DataSet、DataTable
- 不适合从数据库加载大量的数据

![](C:\Users\Administrator\Documents\FullStack\C#\pic\sqldatareader.png)

### DataSet数据集

- 数据的集合，临时数据仓库，一个被复制到内存的数据库副本

- 不带sql不用引命名空间
- DataSet包含若干表DataTable，DataTable包含若干行DataROW

##### 断开式数据库操作

```c#
string connStr="连接字符串";
string sql="sql语句";
//创建数据适配器
SqlDataAdapter da = new SqlDataAdapter(sql,connStr);
//根据返回的结果集创建对应的结构接收

//1.如果是一个结果集，则创建DataTable接收
DataTable dt = new DataTable();
//将结果集存储到自己指定的表中
da.Fill(dt);
//此时数据已经在内存中了，可以指定数据源了
this.dataGridView.DataSource = dt;

//2.如果是多个结果集，就创建数据集做接收
DataSet ds = new Data Set();
da.Fill(dt);
this.dataGridView.DataSource = dt.Tables[0];


```

##### 手动创建数据集

```c#
//1.创建数据集
DataSet ds = new DataSet();
//2.创建数据表
DataTable dt = new DataTable("grade");
//3.1创建好表的结构（由列决定）
DataColumn c1 = new DataColumn("class",typeof(int));
c1.AutoIncrement = true;//设置标识列
c1.AutoIncrementSeed = 1;//标识种子
c1.AutoIncrementStep = 1;//标识增量
c1.AllowDBnull = falss;//不允许为空
//3.2将创建好的列添加到表的列集合中
dt.Columns.Add(c1)；
//3.3设置表主键
dt.PrimaryKey = new DataColumn[]{c1};
//4.创建表的数据行,不能通过new创建，行要根据表的结构生成
//手动添加数据行，写死的方式 
DataRow row = dt.NewRow();
row[0]=1;
dt.Rows.Add(row);

//将生成的表添加到数据集
ds.Tables.Add(dt);
this.DataGridView = ds.Tables[0];
```

##### 分页操作

通过DataAdapter填充DataSet.Fill()也可也分页，但是并不高效，会在服务端数据库存储所有的数据，然后用DataReader跳过前面的数据，只取后面的数据，真正的分页应该是在数据库中就只查询当前页的数据

#### SqlDataReader

- 建立连接后，一致保持连接状态。数据都在数据库中，只有用到哪个数据才会读取哪个（在线读）
- 其查询结果并不是存放在程序中，而是在数据库中，一旦断开连接就不能再读取
- 通过comm对象的ExecuteReader()方法创建
- 优点是无论查询结果有多少条，对程序占用的内存都几乎没有影响

```c#
SqlDataReader reader=cmd.ExecuteReader();
//reader是一个指针指向了数据库的数据，即真正从数据库中获取数据
reader["UserId"]	

```

