---
title: 创建和更新统计信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- statistical information [SMO]
ms.assetid: 47a0a172-a969-4deb-bca9-dd04401a0fe1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c61bb1b213e4b57c7fbae0b0ec7294c9401a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590676"
---
# <a name="creating-and-updating-statistics"></a><span data-ttu-id="18875-102">创建和更新统计信息</span><span class="sxs-lookup"><span data-stu-id="18875-102">Creating and Updating Statistics</span></span>
  <span data-ttu-id="18875-103">在 SMO 中，有关处理数据库中的查询的统计信息可以使用 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 对象进行收集。</span><span class="sxs-lookup"><span data-stu-id="18875-103">In SMO, statistical information about processing queries in the database can be collected by using the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object.</span></span>  
  
 <span data-ttu-id="18875-104">可以使用 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 对象创建任何列的统计信息。</span><span class="sxs-lookup"><span data-stu-id="18875-104">It is possible to create statistics for any column by using the <xref:Microsoft.SqlServer.Management.Smo.Statistic> and <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object.</span></span> <span data-ttu-id="18875-105">可以运行 <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> 方法以更新 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 对象中的统计信息。</span><span class="sxs-lookup"><span data-stu-id="18875-105">The <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> method can be run to update the statistics in the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object.</span></span> <span data-ttu-id="18875-106">可以在查询优化器中查看结果。</span><span class="sxs-lookup"><span data-stu-id="18875-106">The results can be viewed in the Query Optimizer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18875-107">示例</span><span class="sxs-lookup"><span data-stu-id="18875-107">Example</span></span>  
 <span data-ttu-id="18875-108">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="18875-108">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="18875-109">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="18875-109">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-and-update-statistics-in-visual-basic"></a><span data-ttu-id="18875-110">在 Visual Basic 中创建和更新统计信息</span><span class="sxs-lookup"><span data-stu-id="18875-110">Creating and Update Statistics in Visual Basic</span></span>  
 <span data-ttu-id="18875-111">此代码示例将对为其创建 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 对象和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 对象的现有数据库创建新表。</span><span class="sxs-lookup"><span data-stu-id="18875-111">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStatistics1](SMO How to#SMO_VBStatistics1)]  -->  
  
## <a name="creating-and-update-statistics-in-visual-c"></a><span data-ttu-id="18875-112">在 Visual C# 中创建和更新统计信息</span><span class="sxs-lookup"><span data-stu-id="18875-112">Creating and Update Statistics in Visual C#</span></span>  
 <span data-ttu-id="18875-113">此代码示例将对为其创建 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 对象和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 对象的现有数据库创建新表。</span><span class="sxs-lookup"><span data-stu-id="18875-113">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Reference the CreditCard table.   
  
           Table tb = db.Tables["CreditCard", "Sales"];  
            //Define a Statistic object by supplying the parent table and name   
            //arguments in the constructor.   
            Statistic stat = default(Statistic);  
            stat = new Statistic(tb, "Test_Statistics");  
            //Define a StatisticColumn object variable for the CardType column   
            //and add to the Statistic object variable.   
            StatisticColumn statcol = default(StatisticColumn);  
            statcol = new StatisticColumn(stat, "CardType");  
            stat.StatisticColumns.Add(statcol);  
            //Create the statistic counter on the instance of SQL Server.   
            stat.Create();  
        }  
```  
  
## <a name="creating-and-update-statistics-in-powershell"></a><span data-ttu-id="18875-114">在 PowerShell 中创建和更新统计信息</span><span class="sxs-lookup"><span data-stu-id="18875-114">Creating and Update Statistics in PowerShell</span></span>  
 <span data-ttu-id="18875-115">此代码示例将对为其创建 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 对象和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 对象的现有数据库创建新表。</span><span class="sxs-lookup"><span data-stu-id="18875-115">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
CD AdventureWorks2012\tables  
  
#Get a reference to the table  
$tb = get-item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -argumentlist $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -argumentlist $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index   
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -argumentlist $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
