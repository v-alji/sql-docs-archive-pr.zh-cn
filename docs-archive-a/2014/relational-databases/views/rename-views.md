---
title: 重命名视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc76ced033a69788270c3fa9277bcca6972e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687723"
---
# <a name="rename-views"></a><span data-ttu-id="a51c3-102">重命名视图</span><span class="sxs-lookup"><span data-stu-id="a51c3-102">Rename Views</span></span>
  <span data-ttu-id="a51c3-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重命名视图。</span><span class="sxs-lookup"><span data-stu-id="a51c3-103">You can rename a view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a51c3-104">如果重命名视图，则依赖于该视图的代码和应用程序可能会出错。</span><span class="sxs-lookup"><span data-stu-id="a51c3-104">If you rename a view, code and applications that depend on the view may fail.</span></span> <span data-ttu-id="a51c3-105">这些代码和应用程序包括其他视图、查询、存储过程、用户定义函数和客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="a51c3-105">These include other views, queries, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="a51c3-106">注意，这些错误会级联发生。</span><span class="sxs-lookup"><span data-stu-id="a51c3-106">Note that these failures will cascade.</span></span>  
  
 <span data-ttu-id="a51c3-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a51c3-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a51c3-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a51c3-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a51c3-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="a51c3-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="a51c3-110">安全性</span><span class="sxs-lookup"><span data-stu-id="a51c3-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a51c3-111">**重命名视图，使用：**</span><span class="sxs-lookup"><span data-stu-id="a51c3-111">**To rename a view, using:**</span></span>  
  
     [<span data-ttu-id="a51c3-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a51c3-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a51c3-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a51c3-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a51c3-114">**跟进：** [在重命名视图之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a51c3-114">**Follow Up:**  [After renaming a view](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a51c3-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="a51c3-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="a51c3-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="a51c3-116">Prerequisites</span></span>  
 <span data-ttu-id="a51c3-117">获取视图的所有依赖关系的列表。</span><span class="sxs-lookup"><span data-stu-id="a51c3-117">Obtain a list of all dependencies on the view.</span></span> <span data-ttu-id="a51c3-118">必须修改引用视图的任何对象、脚本或应用程序，以反映新的视图名称。</span><span class="sxs-lookup"><span data-stu-id="a51c3-118">Any objects, scripts or applications that reference the view must be modified to reflect the new name of the view.</span></span> <span data-ttu-id="a51c3-119">有关详细信息，请参阅 [Get Information About a View](get-information-about-a-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a51c3-119">For more information, see [Get Information About a View](get-information-about-a-view.md).</span></span> <span data-ttu-id="a51c3-120">我们建议您删除视图，然后使用新名称重新创建它，而不是重命名视图。</span><span class="sxs-lookup"><span data-stu-id="a51c3-120">We recommend that you drop the view and recreate it with a new name instead of renaming the view.</span></span> <span data-ttu-id="a51c3-121">通过重新创建视图，您可以更新视图中引用的对象的依赖关系信息。</span><span class="sxs-lookup"><span data-stu-id="a51c3-121">By recreating the view, you update the dependency information for the objects that are referenced in the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a51c3-122">Security</span><span class="sxs-lookup"><span data-stu-id="a51c3-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a51c3-123">权限</span><span class="sxs-lookup"><span data-stu-id="a51c3-123">Permissions</span></span>  
 <span data-ttu-id="a51c3-124">需要对 SCHEMA 的 ALTER 权限或对 OBJECT 的 CONTROL 权限，以及数据库中的 CREATE VIEW 权限。</span><span class="sxs-lookup"><span data-stu-id="a51c3-124">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT is required, and CREATE VIEW permission in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a51c3-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a51c3-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-view"></a><span data-ttu-id="a51c3-126">重命名视图</span><span class="sxs-lookup"><span data-stu-id="a51c3-126">To rename a view</span></span>  
  
1.  <span data-ttu-id="a51c3-127">在 **“对象资源管理器”** 中，展开包含要重命名的视图的数据库，然后展开 **“视图”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a51c3-127">In **Object Explorer**, expand the database that contains the view you wish to rename and then expand the **View** folder.</span></span>  
  
2.  <span data-ttu-id="a51c3-128">右键单击要重命名的视图，然后选择 **“重命名”** 。</span><span class="sxs-lookup"><span data-stu-id="a51c3-128">Right-click the view you wish to rename and select **Rename**.</span></span>  
  
3.  <span data-ttu-id="a51c3-129">输入视图的新名称。</span><span class="sxs-lookup"><span data-stu-id="a51c3-129">Enter the view's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a51c3-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a51c3-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="a51c3-131">**重命名视图**</span><span class="sxs-lookup"><span data-stu-id="a51c3-131">**To rename a view**</span></span>  
  
 <span data-ttu-id="a51c3-132">尽管可以使用 **sp_rename** 更改视图的名称，但是我们建议你删除现有视图，然后使用新名称重新创建它。</span><span class="sxs-lookup"><span data-stu-id="a51c3-132">While you can use **sp_rename** to change the name of the view, we recommend that you delete the existing view and then re-create it with the new name.</span></span>  
  
 <span data-ttu-id="a51c3-133">有关详细信息，请参阅 [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) 和 [DROP VIEW (Transact-SQL)](/sql/t-sql/statements/drop-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a51c3-133">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) and [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a> <span data-ttu-id="a51c3-134">跟进：在重命名视图之后</span><span class="sxs-lookup"><span data-stu-id="a51c3-134">Follow Up: After Renaming a View</span></span>  
 <span data-ttu-id="a51c3-135">确保引用视图的旧名称的所有对象、脚本和应用程序现在都使用新名称。</span><span class="sxs-lookup"><span data-stu-id="a51c3-135">Ensure that all objects, scripts, and applications that reference the view's old name now use the new name.</span></span>  
  
  
