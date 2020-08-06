---
title: 创建、更改和删除存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73e8313f3befd4c7c5cb20cdb6649c87ea72b037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590683"
---
# <a name="creating-altering-and-removing-stored-procedures"></a><span data-ttu-id="42d32-102">创建、更改和删除存储过程</span><span class="sxs-lookup"><span data-stu-id="42d32-102">Creating, Altering, and Removing Stored Procedures</span></span>
  <span data-ttu-id="42d32-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 中，存储过程由 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="42d32-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedures are represented by the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
 <span data-ttu-id="42d32-104">在 SMO 中创建 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 对象需要将 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> 属性设置为定义存储过程的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="42d32-104">Creating a <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object in SMO requires setting the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> property to the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script that defines the stored procedure.</span></span> <span data-ttu-id="42d32-105">参数需要 \@ 前缀，并且必须通过使用 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> 对象并将其添加到对象的集合中单独创建 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 。</span><span class="sxs-lookup"><span data-stu-id="42d32-105">Parameters require the \@ prefix and must be created individually by using <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> objects and adding to the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42d32-106">示例</span><span class="sxs-lookup"><span data-stu-id="42d32-106">Example</span></span>  
 <span data-ttu-id="42d32-107">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="42d32-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="42d32-108">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="42d32-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a><span data-ttu-id="42d32-109">在 Visual Basic 中创建、更改和删除存储过程</span><span class="sxs-lookup"><span data-stu-id="42d32-109">Creating, Altering, and Removing a Stored Procedure in Visual Basic</span></span>  
 <span data-ttu-id="42d32-110">此代码示例说明如何为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="42d32-110">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="42d32-111">如果提供了雇员的 ID 号，则将返回该雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="42d32-111">The example returns the last name of an employee when it is given the employee ID number.</span></span> <span data-ttu-id="42d32-112">存储过程需要一个输入参数来指定雇员的 ID 号，需要一个输出参数来返回该雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="42d32-112">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a><span data-ttu-id="42d32-113">在 Visual C# 中创建、更改和删除存储过程</span><span class="sxs-lookup"><span data-stu-id="42d32-113">Creating, Altering, and Removing a Stored Procedure in Visual C#</span></span>  
 <span data-ttu-id="42d32-114">此代码示例说明如何为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="42d32-114">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="42d32-115">如果提供了雇员的 ID 号 (`BusinessEntityID`)，则将返回该雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="42d32-115">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="42d32-116">存储过程需要一个输入参数来指定雇员的 ID 号，需要一个输出参数来返回该雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="42d32-116">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a><span data-ttu-id="42d32-117">在 PowerShell 中创建、更改和删除存储过程</span><span class="sxs-lookup"><span data-stu-id="42d32-117">Creating, Altering, and Removing a Stored Procedure in PowerShell</span></span>  
 <span data-ttu-id="42d32-118">此代码示例说明如何为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 数据库创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="42d32-118">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="42d32-119">如果提供了雇员的 ID 号 (`BusinessEntityID`)，则将返回该雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="42d32-119">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="42d32-120">存储过程需要一个输入参数来指定雇员的 ID 号，需要一个输出参数来返回该雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="42d32-120">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.
$sp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure -argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.
$sp.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="42d32-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42d32-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
