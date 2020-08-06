---
title: 第 1 课：将表转换为层次结构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 196a546093786f9be4b88536763b3150ae750f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693235"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a><span data-ttu-id="7caa7-102">第 1 课：将表转换为层次结构</span><span class="sxs-lookup"><span data-stu-id="7caa7-102">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>
  <span data-ttu-id="7caa7-103">具有使用自联接表示层次结构关系的表的客户可以将本课程作为指南，将他们的表转换为层次结构。</span><span class="sxs-lookup"><span data-stu-id="7caa7-103">Customers who have tables using self joins to express hierarchical relationships can convert their tables to a hierarchical structure using this lesson as a guide.</span></span> <span data-ttu-id="7caa7-104">相对而言，从这种表示形式迁移为使用 `hierarchyid` 的表示形式较为容易。</span><span class="sxs-lookup"><span data-stu-id="7caa7-104">It is relatively easy to migrate from this representation to one using `hierarchyid`.</span></span> <span data-ttu-id="7caa7-105">迁移之后，用户将拥有一个精简且易于理解的层次结构表示形式，可以采用多种方式对其进行索引以进行有效查询。</span><span class="sxs-lookup"><span data-stu-id="7caa7-105">After migration, users will have a compact and easy to understand hierarchical representation, which can be indexed in several ways for efficient queries.</span></span>  
  
 <span data-ttu-id="7caa7-106">本课程将检查现有表、创建一个包含 `hierarchyid` 列的新表、使用源表中的数据填充此表，然后再演示三个索引策略。</span><span class="sxs-lookup"><span data-stu-id="7caa7-106">This lesson, examines an existing table, creates a new table containing a `hierarchyid` column, populates the table with the data from the source table, and then demonstrates three indexing strategies.</span></span> <span data-ttu-id="7caa7-107">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="7caa7-107">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="7caa7-108">检查 Employee 表的当前结构</span><span class="sxs-lookup"><span data-stu-id="7caa7-108">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [<span data-ttu-id="7caa7-109">使用现有层次结构数据填充表</span><span class="sxs-lookup"><span data-stu-id="7caa7-109">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [<span data-ttu-id="7caa7-110">优化 NewOrg 表</span><span class="sxs-lookup"><span data-stu-id="7caa7-110">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [<span data-ttu-id="7caa7-111">摘要：将表转换为层次结构</span><span class="sxs-lookup"><span data-stu-id="7caa7-111">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a><span data-ttu-id="7caa7-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="7caa7-112">Prerequisites</span></span>  
 <span data-ttu-id="7caa7-113">本课程需要使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="7caa7-113">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7caa7-114">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="7caa7-114">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7caa7-115">检查 Employee 表的当前结构</span><span class="sxs-lookup"><span data-stu-id="7caa7-115">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="7caa7-116">下一课</span><span class="sxs-lookup"><span data-stu-id="7caa7-116">Next Lesson</span></span>  
 [<span data-ttu-id="7caa7-117">第 2 课：创建和管理层次结构表中的数据</span><span class="sxs-lookup"><span data-stu-id="7caa7-117">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
