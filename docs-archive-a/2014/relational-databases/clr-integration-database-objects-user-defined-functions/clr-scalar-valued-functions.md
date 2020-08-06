---
title: CLR 标量值函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
ms.openlocfilehash: be8f9616fb285d6a68d6734924874ded06fb3bd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688949"
---
# <a name="clr-scalar-valued-functions"></a><span data-ttu-id="48477-102">CLR 标量值函数</span><span class="sxs-lookup"><span data-stu-id="48477-102">CLR Scalar-Valued Functions</span></span>
  <span data-ttu-id="48477-103">标量值函数 (SVF) 返回单个值，例如字符串、整数或位值。您可以使用任何 .NET Framework 编程语言以托管代码形式创建标量值用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="48477-103">A scalar-valued function (SVF) returns a single value, such as a string, integer, or bit value.You can create scalar-valued user-defined functions in managed code using any .NET Framework programming language.</span></span> <span data-ttu-id="48477-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] 或其他托管代码可访问这些函数。</span><span class="sxs-lookup"><span data-stu-id="48477-104">These functions are accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span> <span data-ttu-id="48477-105">有关 CLR 集成的优点以及如何在托管代码和之间进行选择的信息 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，请参阅[Clr 集成概述](../clr-integration/clr-integration-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="48477-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a><span data-ttu-id="48477-106">CLR 标量值函数的要求</span><span class="sxs-lookup"><span data-stu-id="48477-106">Requirements for CLR Scalar-Valued Functions</span></span>  
 <span data-ttu-id="48477-107">在 .NET Framework 程序集中 .NET Framework  SVF 将实现为类的方法。</span><span class="sxs-lookup"><span data-stu-id="48477-107">.NET Framework SVFs are implemented as methods on a class in a .NET Framework assembly.</span></span> <span data-ttu-id="48477-108">输入参数和从 SVF 返回的类型可以是支持的任何标量数据类型，但、、、、、、、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `varchar` `char` 或除外 `rowversion` `text` `ntext` `image` `timestamp` `table` `cursor` 。</span><span class="sxs-lookup"><span data-stu-id="48477-108">The input parameters and the type returned from a SVF can be any of the scalar data types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except `varchar`, `char`, `rowversion`, `text`, `ntext`, `image`, `timestamp`, `table`, or `cursor`.</span></span> <span data-ttu-id="48477-109">SVF 必须确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型和实现方法的返回数据类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="48477-109">SVFs must ensure a match between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and the return data type of the implementation method.</span></span> <span data-ttu-id="48477-110">有关类型转换的详细信息，请参阅[映射 CLR 参数数据](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)。</span><span class="sxs-lookup"><span data-stu-id="48477-110">For more information about type conversions, see [Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
 <span data-ttu-id="48477-111">使用 .NET Framework 语言实现 .NET Framework SVF 时，可以指定 `SqlFunction` 自定义属性以包括有关此函数的其他信息。</span><span class="sxs-lookup"><span data-stu-id="48477-111">When implementing a .NET Framework SVF in a .NET Framework language, the `SqlFunction` custom attribute can be specified to include additional information about the function.</span></span> <span data-ttu-id="48477-112">`SqlFunction` 属性可以指示该函数是否访问或修改数据、是否为确定性函数以及是否涉及浮点运算。</span><span class="sxs-lookup"><span data-stu-id="48477-112">The `SqlFunction` attribute indicates whether or not the function accesses or modifies data, if it is deterministic, and if the function involves floating point operations.</span></span>  
  
 <span data-ttu-id="48477-113">标量值用户定义函数可以是确定性函数也可以是不确定性函数。</span><span class="sxs-lookup"><span data-stu-id="48477-113">Scalar-valued user-defined functions may be deterministic or non-deterministic.</span></span> <span data-ttu-id="48477-114">如果使用一组特定的输入参数调用某个确定性函数，则该确定性函数始终返回相同的结果。</span><span class="sxs-lookup"><span data-stu-id="48477-114">A deterministic function always returns the same result when it is called with a specific set of input parameters.</span></span> <span data-ttu-id="48477-115">如果使用一组特定的输入参数调用某个不确定性函数，则该不确定性函数返回的结果可能会不同。</span><span class="sxs-lookup"><span data-stu-id="48477-115">A non-deterministic function may return different results when it is called with a specific set of input parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48477-116">在输入值相同且数据库状态相同的情况下，如果某函数并不总是产生相同的输出值，请不要将该函数标记为确定性函数。</span><span class="sxs-lookup"><span data-stu-id="48477-116">Do not mark a function as deterministic if the function does not always produces the same output values, given the same input values and the same database state.</span></span> <span data-ttu-id="48477-117">如果函数不具备真正的确定性而将其标记为确定性函数，将可能产生损坏的索引视图和计算列。</span><span class="sxs-lookup"><span data-stu-id="48477-117">Marking a function as deterministic, when the function isn't truly deterministic can result in corrupted indexed views and computed columns.</span></span> <span data-ttu-id="48477-118">通过将 `IsDeterministic` 属性设置为 true 可将函数标记为确定性函数。</span><span class="sxs-lookup"><span data-stu-id="48477-118">You mark a function as deterministic by setting the `IsDeterministic` property to true.</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="48477-119">表值参数</span><span class="sxs-lookup"><span data-stu-id="48477-119">Table-Valued Parameters</span></span>  
 <span data-ttu-id="48477-120">表值参数 (TVP) 即传递到某一过程或函数的用户定义表类型，它提供了一种将多行数据传递到服务器的高效方法。</span><span class="sxs-lookup"><span data-stu-id="48477-120">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="48477-121">TVP 提供与参数数组类似的功能，但灵活性更高并且与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的集成更紧密。</span><span class="sxs-lookup"><span data-stu-id="48477-121">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="48477-122">它们还提供提升性能的潜力。</span><span class="sxs-lookup"><span data-stu-id="48477-122">They also provide the potential for better performance.</span></span> <span data-ttu-id="48477-123">TVP 还有助于减少到服务器的往返次数。</span><span class="sxs-lookup"><span data-stu-id="48477-123">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="48477-124">可以将数据作为 TVP 发送到服务器，而不是向服务器发送多个请求（例如，对于标量参数列表）。</span><span class="sxs-lookup"><span data-stu-id="48477-124">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="48477-125">用户定义表类型不能作为表值参数传递到在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程中执行的托管存储过程或函数，也不能从这些存储过程或函数中返回。</span><span class="sxs-lookup"><span data-stu-id="48477-125">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="48477-126">有关 Tvp 的详细信息，请参阅[&#40;数据库引擎使用表值参数&#41;](../tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="48477-126">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="example-of-a-clr-scalar-valued-function"></a><span data-ttu-id="48477-127">CLR 标量值函数示例</span><span class="sxs-lookup"><span data-stu-id="48477-127">Example of a CLR Scalar-Valued Function</span></span>  
 <span data-ttu-id="48477-128">下面是访问数据并返回一个整数值的 SVF 示例：</span><span class="sxs-lookup"><span data-stu-id="48477-128">Here is a simple SVF that accesses data and returns an integer value:</span></span>  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 <span data-ttu-id="48477-129">代码的第一行引用 `Microsoft.SqlServer.Server` 以访问属性并引用 `System.Data.SqlClient` 以访问 ADO.NET 命名空间。</span><span class="sxs-lookup"><span data-stu-id="48477-129">The first line of code references `Microsoft.SqlServer.Server` to access attributes and `System.Data.SqlClient` to access the ADO.NET namespace.</span></span> <span data-ttu-id="48477-130">（此命名空间包含 `SqlClient`，即 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。）</span><span class="sxs-lookup"><span data-stu-id="48477-130">(This namespace contains `SqlClient`, the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="48477-131">接下来，该函数收到 `SqlFunction` 自定义属性，它位于 `Microsoft.SqlServer.Server` 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="48477-131">Next, the function receives the `SqlFunction` custom attribute, which is found in the `Microsoft.SqlServer.Server` namespace.</span></span> <span data-ttu-id="48477-132">该自定义属性指示用户定义函数 (UDF) 是否使用进程内访问接口来读取服务器中的数据。</span><span class="sxs-lookup"><span data-stu-id="48477-132">The custom attribute indicates whether or not the user-defined function (UDF) uses the in-process provider to read data in the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48477-133">不允许 UDF 更新、插入或删除数据。</span><span class="sxs-lookup"><span data-stu-id="48477-133">does not allow UDFs to update, insert, or delete data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48477-134">可以优化执行不使用进程内访问接口的 UDF。</span><span class="sxs-lookup"><span data-stu-id="48477-134">can optimize execution of a UDF that does not use the in-process provider.</span></span> <span data-ttu-id="48477-135">它是通过将 `DataAccessKind` 设置为 `DataAccessKind.None` 来指示的。</span><span class="sxs-lookup"><span data-stu-id="48477-135">This is indicated by setting `DataAccessKind` to `DataAccessKind.None`.</span></span> <span data-ttu-id="48477-136">在下一行中，目标方法为公共静态方法（在 Visual Basic .NET 中为 shared）。</span><span class="sxs-lookup"><span data-stu-id="48477-136">On the next line, the target method is a public static (shared in Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="48477-137">然后，`SqlContext` 类（位于 `Microsoft.SqlServer.Server` 命名空间中）可以通过已建立的与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例间的连接访问 `SqlCommand` 对象。</span><span class="sxs-lookup"><span data-stu-id="48477-137">The `SqlContext` class, located in the `Microsoft.SqlServer.Server` namespace, can then access a `SqlCommand` object with a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is already set up.</span></span> <span data-ttu-id="48477-138">虽然这里未使用当前事务上下文，但它也可通过 `System.Transactions` 应用程序编程接口 (API) 获取。</span><span class="sxs-lookup"><span data-stu-id="48477-138">Although not used here, the current transaction context is also available through the `System.Transactions` application programming interface (API).</span></span>  
  
 <span data-ttu-id="48477-139">开发人员如果编写过使用 `System.Data.SqlClient` 命名空间中所含类型的客户端应用程序，对函数体中大部分代码行应较熟悉。</span><span class="sxs-lookup"><span data-stu-id="48477-139">Most of the lines of code in the function body should look familiar to developers who have written client applications that use the types found in the `System.Data.SqlClient` namespace.</span></span>  
  
 <span data-ttu-id="48477-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="48477-140">[C#]</span></span>  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 <span data-ttu-id="48477-141">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="48477-141">[Visual Basic]</span></span>  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 <span data-ttu-id="48477-142">通过初始化 `SqlCommand` 对象指定相应的命令文本。</span><span class="sxs-lookup"><span data-stu-id="48477-142">The appropriate command text is specified by initializing the `SqlCommand` object.</span></span> <span data-ttu-id="48477-143">上面的示例将计算出表 `SalesOrderHeader` 中的行数。</span><span class="sxs-lookup"><span data-stu-id="48477-143">The previous example counts the number of rows in table `SalesOrderHeader`.</span></span> <span data-ttu-id="48477-144">接下来，将调用 `ExecuteScalar` 对象的 `cmd` 方法。</span><span class="sxs-lookup"><span data-stu-id="48477-144">Next, the `ExecuteScalar` method of the `cmd` object is called.</span></span> <span data-ttu-id="48477-145">它将根据查询返回类型为 `int` 的值。</span><span class="sxs-lookup"><span data-stu-id="48477-145">This returns a value of type `int` based on the query.</span></span> <span data-ttu-id="48477-146">最后，将订单计数返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="48477-146">Finally, the order count is returned to the caller.</span></span>  
  
 <span data-ttu-id="48477-147">如果此代码保存在名为 FirstUdf.cs 的文件中，则它将能够编译到如下的程序集中：</span><span class="sxs-lookup"><span data-stu-id="48477-147">If this code is saved in a file called FirstUdf.cs, it could be compiled into as assembly as follows:</span></span>  
  
 <span data-ttu-id="48477-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="48477-148">[C#]</span></span>  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 <span data-ttu-id="48477-149">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="48477-149">[Visual Basic]</span></span>  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  <span data-ttu-id="48477-150">`/t:library` 指示应生成一个库，而非可执行程序。</span><span class="sxs-lookup"><span data-stu-id="48477-150">`/t:library` indicates that a library, rather than an executable, should be produced.</span></span> <span data-ttu-id="48477-151">可执行程序无法在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中进行注册。</span><span class="sxs-lookup"><span data-stu-id="48477-151">Executables cannot be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48477-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不再支持执行使用 `/clr:pure` 编译的 Visual C++ 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="48477-152">Visual C++ database objects compiled with `/clr:pure` are not supported for execution on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="48477-153">例如，此类数据库对象包含标量值函数。</span><span class="sxs-lookup"><span data-stu-id="48477-153">For example, such database objects include scalar-valued functions.</span></span>  
  
 <span data-ttu-id="48477-154">用于注册程序集和 UDF 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询及示例调用如下：</span><span class="sxs-lookup"><span data-stu-id="48477-154">The [!INCLUDE[tsql](../../includes/tsql-md.md)] query and a sample invocation to register the assembly and UDF are:</span></span>  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 <span data-ttu-id="48477-155">请注意，[!INCLUDE[tsql](../../includes/tsql-md.md)] 中显示的函数名称不需要与目标公共静态方法的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="48477-155">Note that the function name as exposed in [!INCLUDE[tsql](../../includes/tsql-md.md)] does not need to match the name of the target public static method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48477-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48477-156">See Also</span></span>  
 <span data-ttu-id="48477-157">[映射 CLR 参数数据](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span><span class="sxs-lookup"><span data-stu-id="48477-157">[Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span></span>  
 <span data-ttu-id="48477-158">[CLR 集成自定义特性概述](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="48477-158">[Overview of CLR Integration Custom Attributes](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span></span>  
 <span data-ttu-id="48477-159">[用户定义函数](../user-defined-functions/user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="48477-159">[User-Defined Functions](../user-defined-functions/user-defined-functions.md) </span></span>  
 [<span data-ttu-id="48477-160">从 CLR 数据库对象进行数据访问</span><span class="sxs-lookup"><span data-stu-id="48477-160">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
