---
title: 创建、更改和删除架构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- schemas [SMO]
ms.assetid: 3e3619de-c6a2-4280-b2be-4ec9924608fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 390a70c48d442b52a6aa29185880de67467c0cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588956"
---
# <a name="creating-altering-and-removing-schemas"></a><span data-ttu-id="fc45d-102">创建、更改和删除架构</span><span class="sxs-lookup"><span data-stu-id="fc45d-102">Creating, Altering, and Removing Schemas</span></span>
  <span data-ttu-id="fc45d-103"><xref:Microsoft.SqlServer.Management.Smo.Schema> 对象表示数据库对象的所有权上下文。</span><span class="sxs-lookup"><span data-stu-id="fc45d-103">The <xref:Microsoft.SqlServer.Management.Smo.Schema> object represents an ownership context for database object.</span></span> <span data-ttu-id="fc45d-104"><xref:Microsoft.SqlServer.Management.Smo.Database.Schemas%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Database> 属性表示 <xref:Microsoft.SqlServer.Management.Smo.Schema> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="fc45d-104">The <xref:Microsoft.SqlServer.Management.Smo.Database.Schemas%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Database> object represents a collection of <xref:Microsoft.SqlServer.Management.Smo.Schema> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc45d-105">示例</span><span class="sxs-lookup"><span data-stu-id="fc45d-105">Example</span></span>  
 <span data-ttu-id="fc45d-106">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="fc45d-106">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="fc45d-107">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="fc45d-107">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-schema-in-visual-basic"></a><span data-ttu-id="fc45d-108">在 Visual Basic 中创建、更改和删除架构</span><span class="sxs-lookup"><span data-stu-id="fc45d-108">Creating, Altering, and Removing a Schema in Visual Basic</span></span>  
 <span data-ttu-id="fc45d-109">此代码示例说明如何创建架构并将其分配给数据库对象。</span><span class="sxs-lookup"><span data-stu-id="fc45d-109">This code example demonstrates how to create a schema and assign it to a database object.</span></span> <span data-ttu-id="fc45d-110">接着，程序向用户授予权限，然后在该架构中创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="fc45d-110">The program then grants permission to a user, and then creates a new table in the schema.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSchemas1](SMO How to#SMO_VBSchemas1)]  -->  
  
## <a name="creating-altering-and-removing-a-schema-in-visual-c"></a><span data-ttu-id="fc45d-111">在 Visual C# 中创建、更改和删除架构</span><span class="sxs-lookup"><span data-stu-id="fc45d-111">Creating, Altering, and Removing a Schema in Visual C#</span></span>  
 <span data-ttu-id="fc45d-112">此代码示例说明如何创建架构并将其分配给数据库对象。</span><span class="sxs-lookup"><span data-stu-id="fc45d-112">This code example demonstrates how to create a schema and assign it to a database object.</span></span> <span data-ttu-id="fc45d-113">接着，程序向用户授予权限，然后在该架构中创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="fc45d-113">The program then grants permission to a user, and then creates a new table in the schema.</span></span>  
  
```csharp
{  
         //Connect to the local, default instance of SQL Server.   
         Server srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db = srv.Databases["AdventureWorks2012"];   
        //Define a Schema object variable by supplying the parent database and name arguments in the constructor.   
        Schema sch = new Schema(db, "MySchema1");   
        sch.Owner = "dbo";   
  
        //Create the schema on the instance of SQL Server.   
        sch.Create();   
  
        //Define an ObjectPermissionSet that contains the Update and Select object permissions.   
        ObjectPermissionSet obperset = new ObjectPermissionSet();   
        obperset.Add(ObjectPermission.Select);   
        obperset.Add(ObjectPermission.Update);   
  
        //Grant the set of permissions on the schema to the guest account.   
        sch.Grant(obperset, "guest");   
  
        //Define a Table object variable by supplying the parent database, name and schema arguments in the constructor.   
        Table tb = new Table(db, "MyTable", "MySchema1");   
       Column mycol = new Column(tb, "Date", DataType.DateTime);   
        tb.Columns.Add(mycol);   
        tb.Create();   
  
        //Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.   
        sch.Owner = "guest";   
        sch.Alter();   
  
        //Run the Drop method for the table and the schema to remove them.   
        tb.Drop();   
        sch.Drop();   
}  
```  
  
## <a name="creating-altering-and-removing-a-schema-in-powershell"></a><span data-ttu-id="fc45d-114">在 PowerShell 中创建、更改和删除架构</span><span class="sxs-lookup"><span data-stu-id="fc45d-114">Creating, Altering, and Removing a Schema in PowerShell</span></span>  
 <span data-ttu-id="fc45d-115">此代码示例说明如何创建架构并将其分配给数据库对象。</span><span class="sxs-lookup"><span data-stu-id="fc45d-115">This code example demonstrates how to create a schema and assign it to a database object.</span></span> <span data-ttu-id="fc45d-116">接着，程序向用户授予权限，然后在该架构中创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="fc45d-116">The program then grants permission to a user, and then creates a new table in the schema.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a schema object variable by supplying the parent database and name arguments in the constructor.
$sch  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Schema -argumentlist $db, "MySchema1"  
  
# Set schema owner  
$sch.Owner = "dbo"
  
# Create the schema on the instance of SQL Server.
$sch.Create()  
  
# Define an ObjectPermissionSet that contains the Update and Select object permissions.
$obperset  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.ObjectPermissionSet  
$obperset.Add([Microsoft.SqlServer.Management.SMO.ObjectPermission]::Select)  
$obperset.Add([Microsoft.SqlServer.Management.SMO.ObjectPermission]::Update)  
  
# Grant the set of permissions on the schema to the guest account.
$sch.Grant($obperset, "guest")  
  
#Create a SMO Table with one column and add it to the database  
$tb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Table -argumentlist $db, "MyTable", "MySchema1"  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$mycol =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Date", $Type  
$tb.Columns.Add($mycol)  
$tb.Create()
  
# Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.
$sch.Owner = "guest"  
$sch.Alter()  
  
# Run the Drop method for the table and the schema to remove them.
$tb.Drop()  
$sch.Drop()  
```
