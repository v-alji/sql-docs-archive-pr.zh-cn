---
title: 修改统计信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6dd44da6d1a80050f37f08e49773f95af0e5a339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590112"
---
# <a name="modify-statistics"></a><span data-ttu-id="f7b6d-102">修改统计信息</span><span class="sxs-lookup"><span data-stu-id="f7b6d-102">Modify Statistics</span></span>
  <span data-ttu-id="f7b6d-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的现有统计信息。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-103">You can modify existing statistics in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f7b6d-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f7b6d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f7b6d-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f7b6d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f7b6d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="f7b6d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f7b6d-107">**若要修改统计信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f7b6d-107">**To modify statistics, using:**</span></span>  
  
     [<span data-ttu-id="f7b6d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f7b6d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f7b6d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f7b6d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f7b6d-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="f7b6d-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f7b6d-111">Security</span><span class="sxs-lookup"><span data-stu-id="f7b6d-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f7b6d-112">权限</span><span class="sxs-lookup"><span data-stu-id="f7b6d-112">Permissions</span></span>  
 <span data-ttu-id="f7b6d-113">要求：</span><span class="sxs-lookup"><span data-stu-id="f7b6d-113">Requires that:</span></span>  
  
-   <span data-ttu-id="f7b6d-114">用户对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-114">The user has ALTER permission on the table or view.</span></span>  
  
-   <span data-ttu-id="f7b6d-115">用户是表或索引视图所有者，或者是以下角色之一的成员： **sysadmin** 固定服务器角色、 **db_owner** 固定数据库角色或 **db_ddladmin** 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-115">The user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f7b6d-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f7b6d-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-statistics"></a><span data-ttu-id="f7b6d-117">修改统计信息</span><span class="sxs-lookup"><span data-stu-id="f7b6d-117">To modify statistics</span></span>  
  
1.  <span data-ttu-id="f7b6d-118">在 **“对象资源管理器”** 中，单击加号以便展开要修改统计信息的数据库。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-118">In **Object Explorer**, click the plus sign to expand the database in which you want to modify a statistic.</span></span>  
  
2.  <span data-ttu-id="f7b6d-119">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="f7b6d-120">单击加号以便展开要修改统计信息的表。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-120">Click the plus sign to expand the table in which you want to modify a statistic.</span></span>  
  
4.  <span data-ttu-id="f7b6d-121">单击加号以便展开 **“统计信息”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="f7b6d-122">右键单击要修改的统计信息对象，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-122">Right-click the statistics object that you wish to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="f7b6d-123">在“统计信息属性 - statistics_name”对话框中的“常规”页面上，单击“添加”、“删除”、“上移”、“下移”或上述任何组合，以更改统计信息的属性     。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-123">In the **Statistics Properties -** *statistics_name* dialog box, on the **General** page, click **Add**, **Remove**, **Move Up**, or **Move Down**, or any combination, to alter the properties of the statistics.</span></span> <span data-ttu-id="f7b6d-124">请记住，某一列在“统计信息列”网格内的位置可能会显著影响统计信息的有用性。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-124">Remember that a column's location within the **Statistics Columns** grid can substantially impact the usefulness of the statistics.</span></span>  
  
7.  <span data-ttu-id="f7b6d-125">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-125">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f7b6d-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f7b6d-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="f7b6d-127">**修改统计信息**</span><span class="sxs-lookup"><span data-stu-id="f7b6d-127">**To modify statistics**</span></span>  
  
 <span data-ttu-id="f7b6d-128">无法使用 Transact-SQL 语句执行此任务。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-128">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="f7b6d-129">若要使用 Transact-SQL 修改统计信息，必须首先删除现有的统计信息，然后使用新属性重新创建统计信息。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-129">To modify statistics using Transact-SQL, you must first delete the existing statistic and then re-create it with new attributes.</span></span>  
  
 <span data-ttu-id="f7b6d-130">详细信息，请参阅 [DROP STATISTICS (Transact SQL)](/sql/t-sql/statements/drop-statistics-transact-sql) 和 [CREATE STATISTICS (Transact SQL)](/sql/t-sql/statements/create-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f7b6d-130">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) and [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
