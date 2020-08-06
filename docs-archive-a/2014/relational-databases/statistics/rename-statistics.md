---
title: 重命名统计信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- renaming statistics
- statistics [SQL Server], renaming
ms.assetid: a3bed7b7-3dc5-4b33-b1c6-67c27f573764
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1528dcec50a662524531065d597b004fe7f59e5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590111"
---
# <a name="rename-statistics"></a><span data-ttu-id="95a11-102">重命名统计信息</span><span class="sxs-lookup"><span data-stu-id="95a11-102">Rename Statistics</span></span>
  <span data-ttu-id="95a11-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 重命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a11-103">You can rename a statistics object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="95a11-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="95a11-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="95a11-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="95a11-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="95a11-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="95a11-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="95a11-107">安全性</span><span class="sxs-lookup"><span data-stu-id="95a11-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="95a11-108">**若要重命名统计信息对象，请使用：**</span><span class="sxs-lookup"><span data-stu-id="95a11-108">**To rename a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="95a11-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95a11-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="95a11-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="95a11-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="95a11-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="95a11-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="95a11-112">默认情况下，创建索引将在该索引的键列上创建统计信息。</span><span class="sxs-lookup"><span data-stu-id="95a11-112">By default, creating an index creates a statistic on the key columns of that index.</span></span> <span data-ttu-id="95a11-113">因此，重命名索引将自动重命名统计信息对象，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="95a11-113">Therefore, renaming the index automatically renames the statistics object, and vice versa.</span></span>  
  
 <span data-ttu-id="95a11-114">更改对象名的任一部分都可能破坏脚本和存储过程。</span><span class="sxs-lookup"><span data-stu-id="95a11-114">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="95a11-115">我们建议您删除统计信息对象，然后使用新名称重新创建它，而不是重命名视图。</span><span class="sxs-lookup"><span data-stu-id="95a11-115">Instead of renaming, we recommend that you drop the statistics object and re-create it with the new name.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95a11-116">Security</span><span class="sxs-lookup"><span data-stu-id="95a11-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95a11-117">权限</span><span class="sxs-lookup"><span data-stu-id="95a11-117">Permissions</span></span>  
 <span data-ttu-id="95a11-118">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="95a11-118">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="95a11-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95a11-119">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-statistics-object"></a><span data-ttu-id="95a11-120">重命名统计信息对象</span><span class="sxs-lookup"><span data-stu-id="95a11-120">To rename a statistics object</span></span>  
  
1.  <span data-ttu-id="95a11-121">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="95a11-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="95a11-122">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="95a11-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="95a11-123">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="95a11-123">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename N'AK_Employee_LoginID', N'AK_Emp_Login', N'STATISTICS';   
    GO  
    ```  
  
 <span data-ttu-id="95a11-124">有关详细信息，请参阅 [sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="95a11-124">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
