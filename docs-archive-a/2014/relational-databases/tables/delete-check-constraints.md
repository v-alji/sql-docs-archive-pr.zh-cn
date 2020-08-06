---
title: 删除 CHECK 约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28a7f72993cbf2ed0a8cc76534380090ef0d0a55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586575"
---
# <a name="delete-check-constraints"></a><span data-ttu-id="7b952-102">删除 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="7b952-102">Delete Check Constraints</span></span>
  <span data-ttu-id="7b952-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 删除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="7b952-103">You can delete a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7b952-104">删除 CHECK 约束将取消对在约束表达式中包含的一列或多列中可接受的数据值的限制。</span><span class="sxs-lookup"><span data-stu-id="7b952-104">Deleting check constraints removes the limitations on data values that are accepted in the column or columns included in the constraint expression.</span></span>  
  
 <span data-ttu-id="7b952-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7b952-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7b952-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7b952-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7b952-107">安全性</span><span class="sxs-lookup"><span data-stu-id="7b952-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7b952-108">**使用以下工具删除 CHECK 约束：**</span><span class="sxs-lookup"><span data-stu-id="7b952-108">**To delete a check constraint, using:**</span></span>  
  
     [<span data-ttu-id="7b952-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7b952-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7b952-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7b952-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7b952-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="7b952-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7b952-112">Security</span><span class="sxs-lookup"><span data-stu-id="7b952-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7b952-113">权限</span><span class="sxs-lookup"><span data-stu-id="7b952-113">Permissions</span></span>  
 <span data-ttu-id="7b952-114">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="7b952-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7b952-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7b952-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="7b952-116">删除 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="7b952-116">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="7b952-117">在 **“对象资源管理器”** 中，展开具有 CHECK 约束的表。</span><span class="sxs-lookup"><span data-stu-id="7b952-117">In **Object Explorer**, expand the table with the check constraint.</span></span>  
  
2.  <span data-ttu-id="7b952-118">展开  **“约束”** 。</span><span class="sxs-lookup"><span data-stu-id="7b952-118">Expand  **Constraints**.</span></span>  
  
3.  <span data-ttu-id="7b952-119">右键单击该约束，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="7b952-119">Right-click the constraint and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="7b952-120">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="7b952-120">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7b952-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7b952-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="7b952-122">删除 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="7b952-122">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="7b952-123">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="7b952-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b952-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7b952-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7b952-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="7b952-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="7b952-126">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7b952-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
