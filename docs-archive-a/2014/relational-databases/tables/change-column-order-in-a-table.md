---
title: 更改表中的列顺序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d162f9dc793ceb9ea423d94922f7358f1729712e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586580"
---
# <a name="change-column-order-in-a-table"></a><span data-ttu-id="8b464-102">更改表中的列顺序</span><span class="sxs-lookup"><span data-stu-id="8b464-102">Change Column Order in a Table</span></span>
  <span data-ttu-id="8b464-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的表设计器中更改列顺序。</span><span class="sxs-lookup"><span data-stu-id="8b464-103">You can change the order of columns in Table Designer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8b464-104">更改表中的列顺序可能会影响依赖于特定列顺序的代码和应用程序。</span><span class="sxs-lookup"><span data-stu-id="8b464-104">Changing the column order of a table may affect code and applications that depend on the specific order of columns.</span></span> <span data-ttu-id="8b464-105">这些代码和应用程序包括查询、视图、存储过程、用户定义函数和客户端应用程序等。</span><span class="sxs-lookup"><span data-stu-id="8b464-105">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="8b464-106">请在需要对列顺序进行任何更改之前慎重考虑。</span><span class="sxs-lookup"><span data-stu-id="8b464-106">Carefully consider any changes you want to make to column order before making it.</span></span> <span data-ttu-id="8b464-107">最佳做法是指定在应用程序级别和查询级别返回列的顺序。</span><span class="sxs-lookup"><span data-stu-id="8b464-107">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="8b464-108">您不应依赖于使用 SELECT \* 基于在表中定义列的顺序以预期顺序返回所有列。</span><span class="sxs-lookup"><span data-stu-id="8b464-108">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="8b464-109">请始终按照您希望它们出现的顺序在您的查询和应用程序中按名称指定列。</span><span class="sxs-lookup"><span data-stu-id="8b464-109">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
 <span data-ttu-id="8b464-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="8b464-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8b464-111">**使用以下工具更改列顺序：**</span><span class="sxs-lookup"><span data-stu-id="8b464-111">**To change the column order, using:**</span></span>  
  
     [<span data-ttu-id="8b464-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8b464-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8b464-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8b464-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8b464-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8b464-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-column-order"></a><span data-ttu-id="8b464-115">更改列顺序</span><span class="sxs-lookup"><span data-stu-id="8b464-115">To change the column order</span></span>  
  
1.  <span data-ttu-id="8b464-116">在“对象资源管理器”  中，右键单击包含要重新排序的列的表，再单击“设计”  。</span><span class="sxs-lookup"><span data-stu-id="8b464-116">In **Object Explorer**, right-click the table with columns you want to reorder and click **Design**.</span></span>  
  
2.  <span data-ttu-id="8b464-117">选择要重新排序的列名称左侧的框。</span><span class="sxs-lookup"><span data-stu-id="8b464-117">Select the box to the left of the column name that you want to reorder.</span></span>  
  
3.  <span data-ttu-id="8b464-118">将列拖动到表中的另一个位置。</span><span class="sxs-lookup"><span data-stu-id="8b464-118">Drag the column to another location within the table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8b464-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8b464-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="8b464-120">**更改列顺序**</span><span class="sxs-lookup"><span data-stu-id="8b464-120">**To change the column order**</span></span>  
  
 <span data-ttu-id="8b464-121">无法使用 Transact-SQL 语句执行此任务。</span><span class="sxs-lookup"><span data-stu-id="8b464-121">This task cannot be performed using Transact-SQL statements.</span></span>  
  
###  <a name="TsqlExample"></a>  
