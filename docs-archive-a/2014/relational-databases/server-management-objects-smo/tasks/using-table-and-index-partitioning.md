---
title: 使用表和索引分区 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- partitions [SMO]
- storing data [SMO]
- partitioned tables [SQL Server], SMO
- partitioned indexes [SQL Server], SMO
ms.assetid: 0e682d7e-86c3-4d73-950d-aa692d46cb62
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e05087f63da163b8fa339befae039eb5e7e8245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579525"
---
# <a name="using-table-and-index-partitioning"></a><span data-ttu-id="c5910-102">使用表和索引分区</span><span class="sxs-lookup"><span data-stu-id="c5910-102">Using Table and Index Partitioning</span></span>
  <span data-ttu-id="c5910-103">可以使用 [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md)所提供的存储算法来存储数据。</span><span class="sxs-lookup"><span data-stu-id="c5910-103">Data can be stored by using the storage algorithms provided by [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md).</span></span> <span data-ttu-id="c5910-104">分区可以使大型表和索引更易于管理并且更灵活。</span><span class="sxs-lookup"><span data-stu-id="c5910-104">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
## <a name="index-and-table-partitioning"></a><span data-ttu-id="c5910-105">索引和表分区</span><span class="sxs-lookup"><span data-stu-id="c5910-105">Index and Table Partitioning</span></span>  
 <span data-ttu-id="c5910-106">通过该功能可以将索引和表数据分散到各个分区中的多个文件组。</span><span class="sxs-lookup"><span data-stu-id="c5910-106">The feature enables index and table data to be spread across multiple file groups in partitions.</span></span> <span data-ttu-id="c5910-107">分区函数定义如何根据某些列（称为分区依据列）中的值将表或索引的行映射到一组分区。</span><span class="sxs-lookup"><span data-stu-id="c5910-107">A partition function defines how the rows of a table or index are mapped to a set of partitions based on the values of certain columns, referred to as partitioning columns.</span></span> <span data-ttu-id="c5910-108">分区方案将分区函数指定的每个分区映射到一个文件组。</span><span class="sxs-lookup"><span data-stu-id="c5910-108">A partition scheme maps each partition specified by the partition function to a file group.</span></span> <span data-ttu-id="c5910-109">这样，您便可以制定相应存档策略，用以将表扩展到多个文件组，因而也可扩展到多个物理设备。</span><span class="sxs-lookup"><span data-stu-id="c5910-109">This lets you develop archiving strategies that enable tables to be scaled across file groups, and therefore physical devices.</span></span>  
  
 <span data-ttu-id="c5910-110"><xref:Microsoft.SqlServer.Management.Smo.Database> 对象包含表示已实现的分区函数的 <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> 对象的集合，以及描述如何将数据映射到文件组的 <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="c5910-110">The <xref:Microsoft.SqlServer.Management.Smo.Database> object contains a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> objects that represent the implemented partition functions and a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> objects that describe how data is mapped to file groups.</span></span>  
  
 <span data-ttu-id="c5910-111">每个 <xref:Microsoft.SqlServer.Management.Smo.Table> 和 <xref:Microsoft.SqlServer.Management.Smo.Index> 对象在 <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> 属性中指定其使用的分区方案，并在 <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection> 中指定列。</span><span class="sxs-lookup"><span data-stu-id="c5910-111">Each <xref:Microsoft.SqlServer.Management.Smo.Table> and <xref:Microsoft.SqlServer.Management.Smo.Index> object specifies which partition scheme it uses in the <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> property and specifies the columns in the <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5910-112">示例</span><span class="sxs-lookup"><span data-stu-id="c5910-112">Example</span></span>  
 <span data-ttu-id="c5910-113">对于下面的代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5910-113">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="c5910-114">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="c5910-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-basic"></a><span data-ttu-id="c5910-115">在 Visual Basic 中为表设置分区方案</span><span class="sxs-lookup"><span data-stu-id="c5910-115">Setting Up a Partition Scheme for a Table in Visual Basic</span></span>  
 <span data-ttu-id="c5910-116">此代码示例说明如何为 `TransactionHistory` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 表创建分区函数和分区方案。</span><span class="sxs-lookup"><span data-stu-id="c5910-116">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="c5910-117">这些分区是按日期划分的，这样做的目的是将以前的记录分离出来，放入 `TransactionHistoryArchive` 表中。</span><span class="sxs-lookup"><span data-stu-id="c5910-117">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBPartition1](SMO How to#SMO_VBPartition1)]  -->  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-c"></a><span data-ttu-id="c5910-118">在 Visual C# 中为表设置分区方案</span><span class="sxs-lookup"><span data-stu-id="c5910-118">Setting Up a Partition Scheme for a Table in Visual C#</span></span>  
 <span data-ttu-id="c5910-119">此代码示例说明如何为 `TransactionHistory` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 表创建分区函数和分区方案。</span><span class="sxs-lookup"><span data-stu-id="c5910-119">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="c5910-120">这些分区是按日期划分的，这样做的目的是将以前的记录分离出来，放入 `TransactionHistoryArchive` 表中。</span><span class="sxs-lookup"><span data-stu-id="c5910-120">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```csharp
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Define and create three new file groups on the database.   
FileGroup fg2;   
fg2 = new FileGroup(db, "Second");   
fg2.Create();   
FileGroup fg3;   
fg3 = new FileGroup(db, "Third");   
fg3.Create();   
FileGroup fg4;   
fg4 = new FileGroup(db, "Fourth");   
fg4.Create();   
//Define a partition function by supplying the parent database and name arguments in the constructor.   
PartitionFunction pf;   
pf = new PartitionFunction(db, "TransHistPF");   
//Add a partition function parameter that specifies the function uses a DateTime range type.   
PartitionFunctionParameter pfp;   
pfp = new PartitionFunctionParameter(pf, DataType.DateTime);   
pf.PartitionFunctionParameters.Add(pfp);   
//Specify the three dates that divide the data into four partitions.   
object[] val;   
val = new object[] {"1/1/2003", "1/1/2004", "1/1/2005"};   
pf.RangeValues = val;   
//Create the partition function.   
pf.Create();   
//Define a partition scheme by supplying the parent database and name arguments in the constructor.   
PartitionScheme ps;   
ps = new PartitionScheme(db, "TransHistPS");   
//Specify the partition function and the filegroups required by the partition scheme.   
ps.PartitionFunction = "TransHistPF";   
ps.FileGroups.Add("PRIMARY");   
ps.FileGroups.Add("second");   
ps.FileGroups.Add("Third");   
ps.FileGroups.Add("Fourth");   
//Create the partition scheme.   
ps.Create();   
}   
```  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-powershell"></a><span data-ttu-id="c5910-121">在 PowerShell 中为表设置分区方案</span><span class="sxs-lookup"><span data-stu-id="c5910-121">Setting Up a Partition Scheme for a Table in PowerShell</span></span>  
 <span data-ttu-id="c5910-122">此代码示例说明如何为 `TransactionHistory` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 表创建分区函数和分区方案。</span><span class="sxs-lookup"><span data-stu-id="c5910-122">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="c5910-123">这些分区是按日期划分的，这样做的目的是将以前的记录分离出来，放入 `TransactionHistoryArchive` 表中。</span><span class="sxs-lookup"><span data-stu-id="c5910-123">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
$db = $srv.Databases["AdventureWorks"]  
#Create four filegroups  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "First"  
$fg2 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Second"  
$fg3 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Third"  
$fg4 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Fourth"  
  
#Define a partition function by supplying the parent database and name arguments in the constructor.  
$pf =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunction -argumentlist $db, "TransHistPF"  
$T = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$T  
$T.GetType()  
#Add a partition function parameter that specifies the function uses a DateTime range type.  
$pfp =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunctionParameter -argumentlist $pf, $T  
  
#Specify the three dates that divide the data into four partitions.
#Create an array of type object to hold the partition data  
$val = "1/1/2003"."1/1/2004","1/1/2005"  
$pf.RangeValues = $val  
$pf  
#Create the partition function  
$pf.Create()  
  
#Create partition scheme  
$ps = New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionScheme -argumentlist $db, "TransHistPS"  
$ps.PartitionFunction = "TransHistPF"  
  
#add the filegroups to the scheme
$ps.FileGroups.Add("PRIMARY")  
$ps.FileGroups.Add("Second")  
$ps.FileGroups.Add("Third")  
$ps.FileGroups.Add("Fourth")  
  
#Create it at the server  
$ps.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5910-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5910-124">See Also</span></span>  
 [<span data-ttu-id="c5910-125">Partitioned Tables and Indexes</span><span class="sxs-lookup"><span data-stu-id="c5910-125">Partitioned Tables and Indexes</span></span>](../../partitions/partitioned-tables-and-indexes.md)  
