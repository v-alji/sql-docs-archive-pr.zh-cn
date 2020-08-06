---
title: 定义 UDT 表和列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: aa9596629ed8b4877b1793fa0c56956c52989499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591910"
---
# <a name="defining-udt-tables-and-columns"></a><span data-ttu-id="792af-102">定义 UDT 表和列</span><span class="sxs-lookup"><span data-stu-id="792af-102">Defining UDT Tables and Columns</span></span>
  <span data-ttu-id="792af-103">一旦包含用户定义类型的程序集已在数据库中注册 (UDT) 定义 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，就可以在列定义中使用。</span><span class="sxs-lookup"><span data-stu-id="792af-103">Once the assembly containing the user-defined type (UDT) definition has been registered in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, it can be used in a column definition.</span></span>  
  
## <a name="creating-tables-with-udts"></a><span data-ttu-id="792af-104">使用 UDT 创建表</span><span class="sxs-lookup"><span data-stu-id="792af-104">Creating Tables with UDTs</span></span>  
 <span data-ttu-id="792af-105">没有用于在表中创建 UDT 列的特殊语法。</span><span class="sxs-lookup"><span data-stu-id="792af-105">There is no special syntax for creating a UDT column in a table.</span></span> <span data-ttu-id="792af-106">您可以在某一列定义中使用 UDT 的名称，就像它是某一内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型一样。</span><span class="sxs-lookup"><span data-stu-id="792af-106">You can use the name of the UDT in a column definition as though it were one of the intrinsic [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="792af-107">下面的 CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将创建一个名为**Points**的表，其中包含一个名为 **"ID"** 的列，该列定义为 `int` 标识列和表的主键。</span><span class="sxs-lookup"><span data-stu-id="792af-107">The following CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates a table named **Points**, with a column named **ID,** which is defined as an `int` identity column and \ the primary key for the table.</span></span> <span data-ttu-id="792af-108">第二列的名称为**PointValue**，数据类型为**Point**。</span><span class="sxs-lookup"><span data-stu-id="792af-108">The second column is named **PointValue**, with a data type of **Point**.</span></span> <span data-ttu-id="792af-109">本示例中使用的架构名称为**dbo**。</span><span class="sxs-lookup"><span data-stu-id="792af-109">The schema name used in this example is **dbo**.</span></span> <span data-ttu-id="792af-110">请注意，您必须具有指定架构名称所需的权限。</span><span class="sxs-lookup"><span data-stu-id="792af-110">Note that you must have the necessary permissions to specify a schema name.</span></span> <span data-ttu-id="792af-111">如果省略架构名称，将使用数据库用户的默认架构。</span><span class="sxs-lookup"><span data-stu-id="792af-111">If you omit the schema name, the default schema for the database user is used.</span></span>  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a><span data-ttu-id="792af-112">对 UDT 列创建索引</span><span class="sxs-lookup"><span data-stu-id="792af-112">Creating Indexes on UDT Columns</span></span>  
 <span data-ttu-id="792af-113">有两个用于为 UDT 列编制索引的选项：</span><span class="sxs-lookup"><span data-stu-id="792af-113">There are two options for indexing a UDT column:</span></span>  
  
-   <span data-ttu-id="792af-114">为整个值编制索引。</span><span class="sxs-lookup"><span data-stu-id="792af-114">Index the full value.</span></span> <span data-ttu-id="792af-115">在此情况下，如果 UDT 是二进制排序的，则可以通过使用 CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句对整个 UDT 列创建索引。</span><span class="sxs-lookup"><span data-stu-id="792af-115">In this case, if the UDT is binary ordered, you can create an index over the entire UDT column by using the CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="792af-116">对 UDT 表达式编制索引。</span><span class="sxs-lookup"><span data-stu-id="792af-116">Index UDT expressions.</span></span> <span data-ttu-id="792af-117">您可以对 UDT 表达式在持久计算列上创建索引。</span><span class="sxs-lookup"><span data-stu-id="792af-117">You can create indexes on persisted computed columns over UDT expressions.</span></span> <span data-ttu-id="792af-118">该 UDT 表达式可以是 UDT 的某一字段、方法或属性。</span><span class="sxs-lookup"><span data-stu-id="792af-118">The UDT expression can be a field, method, or property of a UDT.</span></span> <span data-ttu-id="792af-119">该表达式必须是确定性的并且不得执行数据访问。</span><span class="sxs-lookup"><span data-stu-id="792af-119">The expression must be deterministic and must not perform data access.</span></span>  
  
 <span data-ttu-id="792af-120">有关详细信息，请参阅[CLR 用户定义类型](clr-user-defined-types.md)和[CREATE INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="792af-120">For more information, see [CLR User-Defined Types](clr-user-defined-types.md) and [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792af-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="792af-121">See Also</span></span>  
 [<span data-ttu-id="792af-122">使用 SQL Server 中的用户定义类型</span><span class="sxs-lookup"><span data-stu-id="792af-122">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
