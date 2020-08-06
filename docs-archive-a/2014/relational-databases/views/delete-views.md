---
title: 删除视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3e05724f7d6384d0407e915207ad60a1cdfb01b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577459"
---
# <a name="delete-views"></a><span data-ttu-id="b5fa9-102">删除视图</span><span class="sxs-lookup"><span data-stu-id="b5fa9-102">Delete Views</span></span>
  <span data-ttu-id="b5fa9-103">可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中删除视图 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5fa9-103">You can delete (drop) views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b5fa9-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="b5fa9-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b5fa9-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b5fa9-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b5fa9-106">删除视图时，将从系统目录中删除视图的定义和有关视图的其他信息。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-106">When you drop a view, the definition of the view and other information about the view is deleted from the system catalog.</span></span> <span data-ttu-id="b5fa9-107">还将删除视图的所有权限。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-107">All permissions for the view are also deleted.</span></span>  
  
-   <span data-ttu-id="b5fa9-108">使用 `DROP TABLE` 删除的表上的任何视图都必须使用 `DROP VIEW`显式删除。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-108">Any view on a table that is dropped by using `DROP TABLE` must be dropped explicitly by using `DROP VIEW`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b5fa9-109">Security</span><span class="sxs-lookup"><span data-stu-id="b5fa9-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b5fa9-110">权限</span><span class="sxs-lookup"><span data-stu-id="b5fa9-110">Permissions</span></span>  
 <span data-ttu-id="b5fa9-111">需要对 SCHEMA 的 ALTER 权限或对 OBJECT 的 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-111">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b5fa9-112">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5fa9-112">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="b5fa9-113">从数据库中删除视图</span><span class="sxs-lookup"><span data-stu-id="b5fa9-113">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="b5fa9-114">在 **“对象资源管理器”** 中，展开包含要删除的视图的数据库，然后展开 **“视图”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-114">In **Object Explorer**, expand the database that contains the view you want to delete, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="b5fa9-115">右键单击要删除的视图，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-115">Right-click the view you want to delete and click **Delete**.</span></span>  
  
3.  <span data-ttu-id="b5fa9-116">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-116">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b5fa9-117">单击“删除对象”\*\*\*\* 对话框中的“显示依赖关系”\*\*\*\*，打开__“view_name 依赖关系”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-117">Click **Show Dependencies** in the **Delete Object** dialog box to open the _view_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="b5fa9-118">这将显示依赖于该视图的所有对象和该视图依赖的所有对象。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-118">This will show all of the objects that depend on the view and all of the objects on which the view depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b5fa9-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5fa9-119">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="b5fa9-120">从数据库中删除视图</span><span class="sxs-lookup"><span data-stu-id="b5fa9-120">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="b5fa9-121">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5fa9-122">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b5fa9-123">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b5fa9-124">仅在视图存在时，该示例才删除指定的视图。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-124">The example deletes the specified view only if the view already exists.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 <span data-ttu-id="b5fa9-125">有关详细信息，请参阅 [DROP VIEW (Transact-SQL)](/sql/t-sql/statements/drop-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fa9-125">For more information, see [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
  
