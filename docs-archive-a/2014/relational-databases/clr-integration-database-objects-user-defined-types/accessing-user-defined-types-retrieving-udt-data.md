---
title: 正在检索 UDT 数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9133ea45069f76e7590f6b74d3c1e1cb98c7bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588578"
---
# <a name="retrieving-udt-data"></a><span data-ttu-id="9d9bc-102">检索 UDT 数据</span><span class="sxs-lookup"><span data-stu-id="9d9bc-102">Retrieving UDT Data</span></span>
  <span data-ttu-id="9d9bc-103">若要在客户端上创建用户定义类型 (UDT)，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中作为 UDT 注册的程序集必须可供客户端应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-103">In order to create a user-defined type (UDT) on the client, the assembly that was registered as a UDT in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database must be available to the client application.</span></span> <span data-ttu-id="9d9bc-104">UDT 程序集可位于该应用程序的相同目录中，也可以位于全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-104">The UDT assembly can be placed in the same directory with the application, or in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="9d9bc-105">还可以在项目中设置对该程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-105">You can also set a reference to the assembly in your project.</span></span>  
  
## <a name="requirements-for-using-udts-in-adonet"></a><span data-ttu-id="9d9bc-106">在 ADO.NET 中使用 UDT 的要求</span><span class="sxs-lookup"><span data-stu-id="9d9bc-106">Requirements for Using UDTs in ADO.NET</span></span>  
 <span data-ttu-id="9d9bc-107">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中加载的程序集和客户端上的程序集必须兼容，以便在该客户端上创建 UDT。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-107">The assembly loaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the assembly on the client must be compatible in order for the UDT to be created on the client.</span></span> <span data-ttu-id="9d9bc-108">对于采用 `Native` 序列化格式定义的 UDT，程序集必须在结构上兼容。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-108">For UDTs defined with the `Native` serialization format, the assemblies must be structurally compatible.</span></span> <span data-ttu-id="9d9bc-109">对于采用 `UserDefined` 格式定义的程序集，该程序集必须在客户端上可用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-109">For assemblies defined with the `UserDefined` format, the assembly must be available on the client.</span></span>  
  
 <span data-ttu-id="9d9bc-110">您无需在客户端上复制 UDT 程序集即可检索表中 UDT 列的原始数据。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-110">You do not need a copy of the UDT assembly on the client in order to retrieve the raw data from a UDT column in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d9bc-111">当 UDT 版本不匹配或其他问题时， **SqlClient**可能无法加载 udt。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-111">**SqlClient** may fail to load a UDT in the event of mismatched UDT versions or other problems.</span></span> <span data-ttu-id="9d9bc-112">在这种情况下，请使用常规故障排除机制确定调用应用程序无法找到包含 UDT 的程序集的原因。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-112">In this case, use regular troubleshooting mechanisms to determine why the assembly containing the UDT cannot be found by the calling application.</span></span> <span data-ttu-id="9d9bc-113">有关详细信息，请参阅 .NET Framework 文档中的“使用托管调试助手诊断错误”主题。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-113">For more information, read the topic titled "Diagnosing Errors with Managed Debugging Assistants" in the .NET Framework documentation.</span></span>  
  
## <a name="accessing-udts-with-a-sqldatareader"></a><span data-ttu-id="9d9bc-114">通过 SqlDataReader 访问 UDT</span><span class="sxs-lookup"><span data-stu-id="9d9bc-114">Accessing UDTs with a SqlDataReader</span></span>  
 <span data-ttu-id="9d9bc-115">可以从客户端代码使用 `System.Data.SqlClient.SqlDataReader` 检索包含 UDT 列的结果集，该列作为该对象的实例公开。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-115">A `System.Data.SqlClient.SqlDataReader` can be used from client code to retrieve a result set that contains a UDT column, which is exposed as an instance of the object.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9d9bc-116">示例</span><span class="sxs-lookup"><span data-stu-id="9d9bc-116">Example</span></span>  
 <span data-ttu-id="9d9bc-117">本示例演示如何使用 `Main` 方法新建 `SqlDataReader` 对象。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-117">This example shows how to use the `Main` method to create a new `SqlDataReader` object.</span></span> <span data-ttu-id="9d9bc-118">下面的操作是在代码示例中执行的：</span><span class="sxs-lookup"><span data-stu-id="9d9bc-118">The following actions occur within the code example:</span></span>  
  
1.  <span data-ttu-id="9d9bc-119">Main 方法新建 `SqlDataReader` 对象，并检索 Points 表中的值，该表具有一个命名为 Point 的 UDT 列。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-119">The Main method creates a new `SqlDataReader` object and retrieves the values from the Points table, which has a UDT column named Point.</span></span>  
  
2.  <span data-ttu-id="9d9bc-120">该 Point UDT 公开定义为整数的 X 和 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-120">The Point UDT exposes X and Y coordinates defined as integers.</span></span>  
  
3.  <span data-ttu-id="9d9bc-121">UDT 定义 `Distance` 方法和 `GetDistanceFromXY` 方法。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-121">The UDT defines a `Distance` method and a `GetDistanceFromXY` method.</span></span>  
  
4.  <span data-ttu-id="9d9bc-122">示例代码检索主键列和 UDT 列的值，以便显示 UDT 的功能。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-122">The sample code retrieves the values of the primary key and UDT columns in order to demonstrate the capabilities of the UDT.</span></span>  
  
5.  <span data-ttu-id="9d9bc-123">示例代码调用 `Point.Distance` 和 `Point.GetDistanceFromXY` 方法。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-123">The sample code calls the `Point.Distance` and `Point.GetDistanceFromXY` methods.</span></span>  
  
6.  <span data-ttu-id="9d9bc-124">结果将显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-124">The results are displayed in the console window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d9bc-125">应用程序必须已具有对 UDT 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-125">The application must already have a reference to the UDT assembly.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a><span data-ttu-id="9d9bc-126">以字节形式绑定 UDT</span><span class="sxs-lookup"><span data-stu-id="9d9bc-126">Binding UDTs as Bytes</span></span>  
 <span data-ttu-id="9d9bc-127">在某些情况下，您可能希望检索 UDT 列中的原始数据。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-127">In some situations, you may want to retrieve the raw data from the UDT column.</span></span> <span data-ttu-id="9d9bc-128">本地可能没有可用类型，或者您可能不希望实例化 UDT 实例。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-128">Perhaps the type is not available locally, or you do not wish to instantiate an instance of the UDT.</span></span> <span data-ttu-id="9d9bc-129">使用的**GetBytes**方法，可以将原始字节读入字节数组 `SqlDataReader` 。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-129">You can read the raw bytes into a byte array using the **GetBytes** method of a `SqlDataReader`.</span></span> <span data-ttu-id="9d9bc-130">该方法从指定的列偏移量将字节流作为数组从指定缓冲区偏移量开始读入缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-130">This method reads a stream of bytes from the specified column offset into the buffer of an array starting at a specified buffer offset.</span></span> <span data-ttu-id="9d9bc-131">另一种方法是使用**GetSqlBytes**或**GetSqlBinary**方法之一，并在一次操作中读取所有内容。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-131">Another option is to use one of the **GetSqlBytes** or **GetSqlBinary** methods and read all of the contents in a single operation.</span></span> <span data-ttu-id="9d9bc-132">无论何种情况，永远不会实例化 UDT 对象，因此，您无需在客户端程序集中设置对 UDT 的引用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-132">In either case, the UDT object is never instantiated, so you do not need to set a reference to the UDT in the client assembly.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9d9bc-133">示例</span><span class="sxs-lookup"><span data-stu-id="9d9bc-133">Example</span></span>  
 <span data-ttu-id="9d9bc-134">此示例演示如何使用将**点**数据作为原始字节检索到字节数组中 `SqlDataReader` 。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-134">This example shows how to retrieve the **Point** data as raw bytes into a byte array using a `SqlDataReader`.</span></span> <span data-ttu-id="9d9bc-135">以下代码使用 `System.Text.StringBuilder` 将原始字节转换为字符串表示形式，以便在控制台窗口中显示。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-135">The code uses a `System.Text.StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a><span data-ttu-id="9d9bc-136">使用 GetSqlBytes 的示例</span><span class="sxs-lookup"><span data-stu-id="9d9bc-136">Example Using GetSqlBytes</span></span>  
 <span data-ttu-id="9d9bc-137">此示例显示了如何使用**GetSqlBytes**方法在一次操作中使用原始字节检索**点**数据。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-137">This example shows how to retrieve the **Point** data as raw bytes in a single operation using the **GetSqlBytes** method.</span></span> <span data-ttu-id="9d9bc-138">以下代码使用 `StringBuilder` 将原始字节转换为字符串表示形式，以便在控制台窗口中显示。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-138">The code uses a `StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a><span data-ttu-id="9d9bc-139">使用 UDT 参数</span><span class="sxs-lookup"><span data-stu-id="9d9bc-139">Working with UDT Parameters</span></span>  
 <span data-ttu-id="9d9bc-140">可以在 ADO.NET 代码中将 UDT 作为输入参数和输出参数使用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-140">UDTs can be used as both input and output parameters in your ADO.NET code.</span></span>  
  
## <a name="using-udts-in-query-parameters"></a><span data-ttu-id="9d9bc-141">在查询参数中使用 UDT</span><span class="sxs-lookup"><span data-stu-id="9d9bc-141">Using UDTs in Query Parameters</span></span>  
 <span data-ttu-id="9d9bc-142">设置 `SqlParameter` 对象的 `System.Data.SqlClient.SqlCommand` 时可以将 UDT 用作参数值。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-142">UDTs can be used as parameter values when setting up a `SqlParameter` for a `System.Data.SqlClient.SqlCommand` object.</span></span> <span data-ttu-id="9d9bc-143">`SqlDbType.Udt` 对象的 `SqlParameter` 枚举用于指示对 `Add` 集合调用 `Parameters` 方法时参数为 UDT。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-143">The `SqlDbType.Udt` enumeration of a `SqlParameter` object is used to indicate that the parameter is a UDT when calling the `Add` method to the `Parameters` collection.</span></span> <span data-ttu-id="9d9bc-144">`UdtTypeName`对象的属性 `SqlCommand` 用于指定数据库中使用*schema_name OBJECT_NAME*语法的 UDT 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-144">The `UdtTypeName` property of a `SqlCommand` object is used to specify the fully qualified name of the UDT in the database using the *database.schema_name.object_name* syntax.</span></span> <span data-ttu-id="9d9bc-145">虽然这不是必需的，但使用完全限定名称可以避免代码出现混乱。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-145">Although it is not required, using the fully qualified name removes ambiguity from your code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d9bc-146">UDT 程序集的本地副本必须对客户端项目可用。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-146">A local copy of the UDT assembly must be available to the client project.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9d9bc-147">示例</span><span class="sxs-lookup"><span data-stu-id="9d9bc-147">Example</span></span>  
 <span data-ttu-id="9d9bc-148">本示例中的代码创建 `SqlCommand` 和 `SqlParameter` 对象，以将数据插入到表中的 UDT 列中。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-148">The code in this example creates `SqlCommand` and `SqlParameter` objects to insert data into a UDT column in a table.</span></span> <span data-ttu-id="9d9bc-149">该代码使用 `SqlDbType.Udt` 枚举指定数据类型，并使用 `UdtTypeName` 对象的 `SqlParameter` 属性指定数据库中的 UDT 的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="9d9bc-149">The code uses the `SqlDbType.Udt` enumeration to specify the data type, and the `UdtTypeName` property of the `SqlParameter` object to specify the fully qualified name of the UDT in the database.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      param.UdtTypeName = "TestPoint.dbo.Point"      param.Direction = ParameterDirection.Input      param.Value = New Point(5, 6)      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d9bc-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d9bc-150">See Also</span></span>  
 [<span data-ttu-id="9d9bc-151">在 ADO.NET 中访问用户定义类型</span><span class="sxs-lookup"><span data-stu-id="9d9bc-151">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
  
  
