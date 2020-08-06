---
title: 创建、更改和删除视图 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd8d75e413b1871ce4b8784f5087cb08ed08da73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590677"
---
# <a name="creating-altering-and-removing-views"></a><span data-ttu-id="72c23-102">创建、更改和删除视图</span><span class="sxs-lookup"><span data-stu-id="72c23-102">Creating, Altering, and Removing Views</span></span>
  <span data-ttu-id="72c23-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 中，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 视图由 <xref:Microsoft.SqlServer.Management.Smo.View> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="72c23-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] views are represented by the <xref:Microsoft.SqlServer.Management.Smo.View> object.</span></span>  
  
 <span data-ttu-id="72c23-104"><xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.View> 属性可定义视图。</span><span class="sxs-lookup"><span data-stu-id="72c23-104">The <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.View> object defines the view.</span></span> <span data-ttu-id="72c23-105">它与创建视图的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 语句等效。</span><span class="sxs-lookup"><span data-stu-id="72c23-105">It is the equivalent of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statement for creating a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c23-106">示例</span><span class="sxs-lookup"><span data-stu-id="72c23-106">Example</span></span>  
 <span data-ttu-id="72c23-107">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="72c23-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="72c23-108">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="72c23-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a><span data-ttu-id="72c23-109">在 Visual Basic 中创建、更改和删除视图</span><span class="sxs-lookup"><span data-stu-id="72c23-109">Creating, Altering, and Removing a View in Visual Basic</span></span>  
 <span data-ttu-id="72c23-110">此代码示例显示如何使用内部联接创建两个表的视图。</span><span class="sxs-lookup"><span data-stu-id="72c23-110">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="72c23-111">该视图是使用文本模式创建的，因此必须设置 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="72c23-111">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a><span data-ttu-id="72c23-112">在 Visual C# 中创建、更改和删除视图</span><span class="sxs-lookup"><span data-stu-id="72c23-112">Creating, Altering, and Removing a View in Visual C#</span></span>  
 <span data-ttu-id="72c23-113">此代码示例显示如何使用内部联接创建两个表的视图。</span><span class="sxs-lookup"><span data-stu-id="72c23-113">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="72c23-114">该视图是使用文本模式创建的，因此必须设置 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="72c23-114">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```csharp
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a><span data-ttu-id="72c23-115">在 PowerShell 中创建、更改和删除视图</span><span class="sxs-lookup"><span data-stu-id="72c23-115">Creating, Altering, and Removing a View in PowerShell</span></span>  
 <span data-ttu-id="72c23-116">此代码示例显示如何使用内部联接创建两个表的视图。</span><span class="sxs-lookup"><span data-stu-id="72c23-116">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="72c23-117">该视图是使用文本模式创建的，因此必须设置 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="72c23-117">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View -argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.
$myview.Create()  
  
# Remove the view
$myview.Drop();  
```  
  
## <a name="see-also"></a><span data-ttu-id="72c23-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72c23-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
