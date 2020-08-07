---
title: 教程：使用 hierarchyid 数据类型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
author: stevestein
ms.author: sstein
ms.openlocfilehash: a735b4c2b51e1c680c8129647733ce1efd9f9984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580105"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a><span data-ttu-id="51e59-102">教程：使用 hierarchyid 数据类型</span><span class="sxs-lookup"><span data-stu-id="51e59-102">Tutorial: Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="51e59-103">本教程面向有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用经验但对 `hierarchyid` 数据类型还很陌生的用户。</span><span class="sxs-lookup"><span data-stu-id="51e59-103">This tutorial is intended for users who are experienced with [!INCLUDE[tsql](../../includes/tsql-md.md)], but are new to the `hierarchyid` data type.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="51e59-104">学习内容</span><span class="sxs-lookup"><span data-stu-id="51e59-104">What You Will Learn</span></span>  
 <span data-ttu-id="51e59-105">本教程分为两课：</span><span class="sxs-lookup"><span data-stu-id="51e59-105">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="51e59-106">第 1 课：将表转换为层次结构</span><span class="sxs-lookup"><span data-stu-id="51e59-106">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
 <span data-ttu-id="51e59-107">在本课程中，您采用以父级/子级层次结构方式构建的现有雇员表，然后将数据移到使用 `hierarchyid` 数据类型表示层次结构的新表中。</span><span class="sxs-lookup"><span data-stu-id="51e59-107">In this lesson, you take an existing employee table that is structured as a parent/child hierarchy and move the data into a new table that represents the hierarchy by using the `hierarchyid` data type.</span></span> <span data-ttu-id="51e59-108">本课程需要使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="51e59-108">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [<span data-ttu-id="51e59-109">第 2 课：创建和管理层次结构表中的数据</span><span class="sxs-lookup"><span data-stu-id="51e59-109">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
 <span data-ttu-id="51e59-110">在本课程中，您通过使用 `hierarchyid` 数据类型创建表来表示层次结构。</span><span class="sxs-lookup"><span data-stu-id="51e59-110">In this lesson, you create a table by using the `hierarchyid` data type to represent the hierarchy structure.</span></span> <span data-ttu-id="51e59-111">然后，您通过使用分层方法处理表中的数据。</span><span class="sxs-lookup"><span data-stu-id="51e59-111">Then, you manipulate the data in the table by using the hierarchical methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e59-112">要求</span><span class="sxs-lookup"><span data-stu-id="51e59-112">Requirements</span></span>  
 <span data-ttu-id="51e59-113">您的系统必须安装以下软件：</span><span class="sxs-lookup"><span data-stu-id="51e59-113">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="51e59-114">任何版本的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="51e59-114">Any edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="51e59-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="51e59-115">Either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.</span></span>  
  
-   <span data-ttu-id="51e59-116">Internet Explorer 6 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="51e59-116">Internet Explorer 6 or a later version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e59-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51e59-117">See Also</span></span>  
 <span data-ttu-id="51e59-118">[教程：入门与数据库引擎](../tutorial-getting-started-with-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="51e59-118">[Tutorial: Getting Started with the Database Engine](../tutorial-getting-started-with-the-database-engine.md) </span></span>  
 <span data-ttu-id="51e59-119">[教程：编写 Transact-sql 语句](../../t-sql/tutorial-writing-transact-sql-statements.md) </span><span class="sxs-lookup"><span data-stu-id="51e59-119">[Tutorial: Writing Transact-SQL Statements](../../t-sql/tutorial-writing-transact-sql-statements.md) </span></span>  
 <span data-ttu-id="51e59-120">[hierarchyid 数据类型方法引用](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="51e59-120">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="51e59-121">[分层数据 &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="51e59-121">[Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span></span>  
 [<span data-ttu-id="51e59-122">hierarchyid (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="51e59-122">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
