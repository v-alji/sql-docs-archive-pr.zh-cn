---
title: 实现全文搜索 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8b797e2a38c9136c34b7058b539fca522e03229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682789"
---
# <a name="implementing-full-text-search"></a><span data-ttu-id="e5b4b-102">实现全文搜索</span><span class="sxs-lookup"><span data-stu-id="e5b4b-102">Implementing Full-Text Search</span></span>
  <span data-ttu-id="e5b4b-103">全文搜索对于每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例都可用且在 SMO 中由 <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> 对象来表示。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-103">Full-text search is available per instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and is represented in SMO by the <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> object.</span></span> <span data-ttu-id="e5b4b-104"><xref:Microsoft.SqlServer.Management.Smo.FullTextService> 对象位于 `Server` 对象下。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-104">The <xref:Microsoft.SqlServer.Management.Smo.FullTextService> object resides under the `Server` object.</span></span> <span data-ttu-id="e5b4b-105">它用于管理 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 全文搜索服务的配置选项。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-105">It is used to manage the configuration options for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Full Text Search service.</span></span> <span data-ttu-id="e5b4b-106"><xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> 对象属于 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象，并且它是表示为数据库定义的全文目录的 <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-106">The <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> object belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object and it is a collection of <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> objects that represent full-text catalogs defined for the database.</span></span> <span data-ttu-id="e5b4b-107">与普通索引不同，只能为每个表定义一个全文索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-107">You can only have one full-text index defined for each table, unlike normal indexes.</span></span> <span data-ttu-id="e5b4b-108">此索引由 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> 对象中的 <xref:Microsoft.SqlServer.Management.Smo.Table> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-108">This is represented by a <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object in the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="e5b4b-109">若要创建全文搜索服务，必须为数据库定义一个全文目录，并为数据库的其中一个表定义一个全文搜索索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-109">To create a full-text search service, you must have a full-text catalog defined on the database and a full-text search index defined on one of the tables in the database.</span></span>  
  
 <span data-ttu-id="e5b4b-110">首先，通过调用 <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> 构造函数并指定目录名称，为数据库创建全文目录。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-110">First, create a full-text catalog on the database by calling the <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> constructor and specifying the catalog name.</span></span> <span data-ttu-id="e5b4b-111">其次，通过调用该构造函数并指定要为其创建全文索引的表，创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-111">Then, create the full-text index by calling the constructor and specifying the table on which it is to be created.</span></span> <span data-ttu-id="e5b4b-112">接着，通过使用 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> 对象并提供表中列的名称，可以为全文索引添加索引列。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-112">You can then add index columns for the full-text index, by using the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object and providing the name of the column within the table.</span></span> <span data-ttu-id="e5b4b-113">然后，为已创建的目录设置 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-113">Then, set the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> property to the catalog you have created.</span></span> <span data-ttu-id="e5b4b-114">最后，调用 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> 方法并为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-114">Finally, call the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> method and create the full-text index on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b4b-115">示例</span><span class="sxs-lookup"><span data-stu-id="e5b4b-115">Example</span></span>  
 <span data-ttu-id="e5b4b-116">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-116">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="e5b4b-117">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-117">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a><span data-ttu-id="e5b4b-118">在 Visual Basic 中创建全文搜索服务</span><span class="sxs-lookup"><span data-stu-id="e5b4b-118">Creating a Full-Text Search Service in Visual Basic</span></span>  
 <span data-ttu-id="e5b4b-119">此代码示例为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 示例数据库中的 `ProductCategory` 表创建全文搜索目录。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-119">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="e5b4b-120">然后，它会为 `ProductCategory` 表中的 Name 列创建全文搜索索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-120">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="e5b4b-121">全文搜索索引要求已为该列定义唯一索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-121">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a><span data-ttu-id="e5b4b-122">在 Visual C# 中创建全文搜索服务</span><span class="sxs-lookup"><span data-stu-id="e5b4b-122">Creating a Full-Text Search Service in Visual C#</span></span>  
 <span data-ttu-id="e5b4b-123">此代码示例为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 示例数据库中的 `ProductCategory` 表创建全文搜索目录。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-123">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="e5b4b-124">然后，它会为 `ProductCategory` 表中的 Name 列创建全文搜索索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-124">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="e5b4b-125">全文搜索索引要求已为该列定义唯一索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-125">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a><span data-ttu-id="e5b4b-126">在 PowerShell 中创建全文搜索服务</span><span class="sxs-lookup"><span data-stu-id="e5b4b-126">Creating a Full-Text Search Service in PowerShell</span></span>  
 <span data-ttu-id="e5b4b-127">此代码示例为 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 示例数据库中的 `ProductCategory` 表创建全文搜索目录。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-127">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="e5b4b-128">然后，它会为 `ProductCategory` 表中的 Name 列创建全文搜索索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-128">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="e5b4b-129">全文搜索索引要求已为该列定义唯一索引。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-129">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = Get-Item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = Get-Item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -ArgumentList $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -ArgumentList $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -ArgumentList $fti, "Name"  
  
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
