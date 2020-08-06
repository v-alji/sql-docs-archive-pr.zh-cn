---
title: 经过修改的功能（包含数据库）| Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc52821deeb879022881f838c61823b23c0c10c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693917"
---
# <a name="modified-features-contained-database"></a><span data-ttu-id="986ab-102">经过修改的功能（包含数据库）</span><span class="sxs-lookup"><span data-stu-id="986ab-102">Modified Features (Contained Database)</span></span>
  <span data-ttu-id="986ab-103">为了获得部分包含的数据库的支持，已对以下功能进行了修改。</span><span class="sxs-lookup"><span data-stu-id="986ab-103">The following features have been modified to be supported by a partially contained database.</span></span> <span data-ttu-id="986ab-104">经常会对功能进行修改，以便它们不会超出数据库范围。</span><span class="sxs-lookup"><span data-stu-id="986ab-104">Features are usually modified so they do not cross the database boundary.</span></span>  
  
 <span data-ttu-id="986ab-105">有关详细信息，请参阅 [Contained Databases](contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="986ab-105">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
## <a name="alter-database"></a><span data-ttu-id="986ab-106">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="986ab-106">ALTER DATABASE</span></span>  
  
### <a name="application-level"></a><span data-ttu-id="986ab-107">应用程序级别</span><span class="sxs-lookup"><span data-stu-id="986ab-107">Application Level</span></span>  
 <span data-ttu-id="986ab-108">在包含数据库内部使用 ALTER DATABASE 语句时，其语法不同于用于非包含数据库的语法。</span><span class="sxs-lookup"><span data-stu-id="986ab-108">When using the ALTER DATABASE statement from inside of a contained database, the syntax differs from that used for a non-contained database.</span></span> <span data-ttu-id="986ab-109">这种差异包括对语句元素的限制超出了数据库级别而作用于实例。</span><span class="sxs-lookup"><span data-stu-id="986ab-109">This difference includes restrictions of elements of the statement that extend beyond the database to the instance.</span></span> <span data-ttu-id="986ab-110">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="986ab-110">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="instance-level"></a><span data-ttu-id="986ab-111">实例级别</span><span class="sxs-lookup"><span data-stu-id="986ab-111">Instance Level</span></span>  
 <span data-ttu-id="986ab-112">在包含数据库外部使用时，ALTER DATABASE 的语法与用于非包含数据库时不同。</span><span class="sxs-lookup"><span data-stu-id="986ab-112">The syntax for the ALTER DATABASE when used outside of a contained database differs from that used for non-contained databases.</span></span> <span data-ttu-id="986ab-113">这些更改可防止超出数据库范围。</span><span class="sxs-lookup"><span data-stu-id="986ab-113">These changes prevent crossing the database boundary.</span></span> <span data-ttu-id="986ab-114">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="986ab-114">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="create-database"></a><span data-ttu-id="986ab-115">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="986ab-115">CREATE DATABASE</span></span>  
 <span data-ttu-id="986ab-116">包含数据库的 CREATE DATABASE 语法与非包含数据库的不同。</span><span class="sxs-lookup"><span data-stu-id="986ab-116">The CREATE DATABASE syntax for a contained database differs from that for a non-contained database.</span></span> <span data-ttu-id="986ab-117">有关新的语法要求和考虑事项的信息，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="986ab-117">See [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)for information about new syntax requirements and allowances.</span></span>  
  
## <a name="temporary-tables"></a><span data-ttu-id="986ab-118">临时表</span><span class="sxs-lookup"><span data-stu-id="986ab-118">Temporary Tables</span></span>  
 <span data-ttu-id="986ab-119">包含数据库中允许使用局部临时表，但它们的行为不同于非包含数据库中的局部临时表。</span><span class="sxs-lookup"><span data-stu-id="986ab-119">Local temporary tables are permitted within a contained database, but their behavior differs from those in non-contained databases.</span></span> <span data-ttu-id="986ab-120">在非包含数据库中，临时表数据是按照 **tempdb**的排序规则调整的。</span><span class="sxs-lookup"><span data-stu-id="986ab-120">In non-contained databases, temporary table data is collated in the collation of **tempdb**.</span></span> <span data-ttu-id="986ab-121">在包含数据库中，临时表数据是按照包含数据库的排序规则调整的。</span><span class="sxs-lookup"><span data-stu-id="986ab-121">In a contained database temporary table data is collated in the collation of the contained database.</span></span>  
  
 <span data-ttu-id="986ab-122">与临时表相关联的所有元数据（例如表名称和列名称、索引等）将在目录排序规则中。</span><span class="sxs-lookup"><span data-stu-id="986ab-122">All metadata associated with temporary tables (for example, table and column names, indexes, and so on) will be in the catalog collation.</span></span>  
  
 <span data-ttu-id="986ab-123">命名约束可能不在临时表中使用。</span><span class="sxs-lookup"><span data-stu-id="986ab-123">Named constraints may not be used in temporary tables.</span></span>  
  
 <span data-ttu-id="986ab-124">临时表可能不引用用户定义类型、XML 架构集合或用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="986ab-124">Temporary tables may not refer to user-defined types, XML schema collections, or user-defined functions.</span></span>  
  
## <a name="collation"></a><span data-ttu-id="986ab-125">排序规则</span><span class="sxs-lookup"><span data-stu-id="986ab-125">Collation</span></span>  
 <span data-ttu-id="986ab-126">非包含的数据库模型中有三种不同的排序规则：数据库排序规则、实例排序规则和 tempdb 排序规则。</span><span class="sxs-lookup"><span data-stu-id="986ab-126">In the non-contained database model, there are three separate types of collation: Database collation, Instance collation, and tempdb collation.</span></span> <span data-ttu-id="986ab-127">包含数据库只使用两种排序规则：数据库排序规则和新目录排序规则。</span><span class="sxs-lookup"><span data-stu-id="986ab-127">Contained databases use only two collations, database collation and the new catalog collation.</span></span> <span data-ttu-id="986ab-128">有关包含数据库排序规则的详细信息，请参阅 [Contained Database Collations](contained-database-collations.md) 。</span><span class="sxs-lookup"><span data-stu-id="986ab-128">See [Contained Database Collations](contained-database-collations.md) for more details on contained database collation.</span></span>  
  
## <a name="user-options"></a><span data-ttu-id="986ab-129">用户选项</span><span class="sxs-lookup"><span data-stu-id="986ab-129">User Options</span></span>  
 <span data-ttu-id="986ab-130">启用包含数据库时，对于 [的实例而言，](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) user options Option [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]必须设置为 0。</span><span class="sxs-lookup"><span data-stu-id="986ab-130">When enabling contained databases, the [user options Option](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) must be set to 0 for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986ab-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="986ab-131">See Also</span></span>  
 <span data-ttu-id="986ab-132">[包含数据库的排序规则](contained-database-collations.md) </span><span class="sxs-lookup"><span data-stu-id="986ab-132">[Contained Database Collations](contained-database-collations.md) </span></span>  
 [<span data-ttu-id="986ab-133">包含的数据库</span><span class="sxs-lookup"><span data-stu-id="986ab-133">Contained Databases</span></span>](contained-databases.md)  
  
  
