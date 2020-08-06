---
title: 创建、更改和删除用户定义函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9ff6d1b6e675d41e96f26fc24e6e0dd4ba69454
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590678"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a><span data-ttu-id="44173-102">创建、更改和删除用户定义函数</span><span class="sxs-lookup"><span data-stu-id="44173-102">Creating, Altering, and Removing User-Defined Functions</span></span>
  <span data-ttu-id="44173-103"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>对象提供允许用户以编程方式管理中用户定义的函数的功能 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44173-103">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object provides functionality that lets users programmatically manage user-defined functions in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="44173-104">用户定义函数支持输入和输出参数，还支持对表列的直接引用。</span><span class="sxs-lookup"><span data-stu-id="44173-104">User-defined functions support input and output parameters, and also support direct references to table columns.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="44173-105">要求先在数据库中注册程序集，然后才能在存储过程、用户定义函数、触发器和用户定义数据类型中使用这些程序集。</span><span class="sxs-lookup"><span data-stu-id="44173-105">requires assemblies to be registered within a database before these can be used inside stored procedures, user defined functions, triggers, and user defined data types.</span></span> <span data-ttu-id="44173-106">SMO 使用 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 对象支持此项功能。</span><span class="sxs-lookup"><span data-stu-id="44173-106">SMO supports this feature with the <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object.</span></span>  
  
 <span data-ttu-id="44173-107"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 对象使用 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> 属性来引用 .NET 程序集。</span><span class="sxs-lookup"><span data-stu-id="44173-107">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references the .NET assembly with the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> properties.</span></span>  
  
 <span data-ttu-id="44173-108">当 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 对象引用 .NET 程序集时，您必须通过创建 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 对象并将其添加到 <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> 对象（属于 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象）来注册该程序集。</span><span class="sxs-lookup"><span data-stu-id="44173-108">When the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references a .NET assembly, you must register the assembly by creating a <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object and adding it to the <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> object, which belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44173-109">示例</span><span class="sxs-lookup"><span data-stu-id="44173-109">Example</span></span>  
 <span data-ttu-id="44173-110">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="44173-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="44173-111">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="44173-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a><span data-ttu-id="44173-112">在 Visual Basic 中创建标量用户定义函数</span><span class="sxs-lookup"><span data-stu-id="44173-112">Creating a Scalar User-Defined Function in Visual Basic</span></span>  
 <span data-ttu-id="44173-113">此代码示例说明如何在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中创建和删除具有 <xref:System.DateTime> 输入对象参数和整数返回类型的标量用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="44173-113">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="44173-114">此用户定义函数是对 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库创建的。</span><span class="sxs-lookup"><span data-stu-id="44173-114">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="44173-115">该示例创建了用户定义函数 ISOweek，此函数带有一个日期参数，用于计算 ISO 周号。</span><span class="sxs-lookup"><span data-stu-id="44173-115">The example creates a user-defined function, ISOweek, which takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="44173-116">要使此函数能正确计算，必须在调用此函数之前将数据库 DATEFIRST 选项设置为 1。</span><span class="sxs-lookup"><span data-stu-id="44173-116">For this function to calculate correctly, the database DATEFIRST option must be set to 1 before the function is called.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a><span data-ttu-id="44173-117">在 Visual C# 中创建标量用户定义函数</span><span class="sxs-lookup"><span data-stu-id="44173-117">Creating a Scalar User-Defined Function in Visual C#</span></span>  
 <span data-ttu-id="44173-118">此代码示例说明如何在 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 中创建和删除具有 <xref:System.DateTime> 输入对象参数和整数返回类型的标量用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="44173-118">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="44173-119">此用户定义函数是对 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库创建的。</span><span class="sxs-lookup"><span data-stu-id="44173-119">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="44173-120">该示例将创建用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="44173-120">The example creates the user-defined function.</span></span> <span data-ttu-id="44173-121">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="44173-121">`ISOweek`.</span></span> <span data-ttu-id="44173-122">此函数使用日期参数来计算 ISO 周数。</span><span class="sxs-lookup"><span data-stu-id="44173-122">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="44173-123">要使此函数能正确计算，必须在调用此函数之前将数据库 `DATEFIRST` 选项设置为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="44173-123">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a><span data-ttu-id="44173-124">在 PowerShell 中创建标量用户定义函数</span><span class="sxs-lookup"><span data-stu-id="44173-124">Creating a Scalar User-Defined Function in PowerShell</span></span>  
 <span data-ttu-id="44173-125">此代码示例说明如何在 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 中创建和删除具有 <xref:System.DateTime> 输入对象参数和整数返回类型的标量用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="44173-125">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="44173-126">此用户定义函数是对 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库创建的。</span><span class="sxs-lookup"><span data-stu-id="44173-126">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="44173-127">该示例将创建用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="44173-127">The example creates the user-defined function.</span></span> <span data-ttu-id="44173-128">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="44173-128">`ISOweek`.</span></span> <span data-ttu-id="44173-129">此函数使用日期参数来计算 ISO 周数。</span><span class="sxs-lookup"><span data-stu-id="44173-129">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="44173-130">要使此函数能正确计算，必须在调用此函数之前将数据库 `DATEFIRST` 选项设置为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="44173-130">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction -argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter -argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.
$udf.Create()  
  
# Remove the user-defined function.
$udf.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="44173-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44173-131">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
