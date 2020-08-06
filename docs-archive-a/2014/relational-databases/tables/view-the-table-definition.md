---
title: 查看表定义 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53170a78a104bfce4b4e4177015461f2eb9093e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591821"
---
# <a name="view-the-table-definition"></a><span data-ttu-id="8e185-102">查看表定义</span><span class="sxs-lookup"><span data-stu-id="8e185-102">View the Table Definition</span></span>
  <span data-ttu-id="8e185-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 显示 [!INCLUDE[tsql](../../includes/tsql-md.md)]中某个表的属性。</span><span class="sxs-lookup"><span data-stu-id="8e185-103">You can display properties for a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8e185-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="8e185-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8e185-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="8e185-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8e185-106">安全性</span><span class="sxs-lookup"><span data-stu-id="8e185-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8e185-107">**使用以下工具显示表属性：**</span><span class="sxs-lookup"><span data-stu-id="8e185-107">**To display table properties, using:**</span></span>  
  
     [<span data-ttu-id="8e185-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e185-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8e185-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e185-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8e185-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="8e185-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8e185-111">Security</span><span class="sxs-lookup"><span data-stu-id="8e185-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8e185-112">权限</span><span class="sxs-lookup"><span data-stu-id="8e185-112">Permissions</span></span>  
 <span data-ttu-id="8e185-113">如果您拥有某个表或者已对该表授予权限，则只能查看该表中的属性。</span><span class="sxs-lookup"><span data-stu-id="8e185-113">You can only see properties in a table if you either own the table or have been granted permissions to that table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8e185-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e185-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a><span data-ttu-id="8e185-115">在“属性”窗口中显示表属性</span><span class="sxs-lookup"><span data-stu-id="8e185-115">To show table properties in the Properties window</span></span>  
  
1.  <span data-ttu-id="8e185-116">在对象资源管理器中，选择要显示其属性的表。</span><span class="sxs-lookup"><span data-stu-id="8e185-116">In Object Explorer, select the table for which you want to show properties.</span></span>  
  
2.  <span data-ttu-id="8e185-117">右键单击该表，然后从快捷菜单中选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="8e185-117">Right-click the table and choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="8e185-118">有关详细信息，请参阅 [Table Properties](table-properties-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="8e185-118">For more information, see [Table Properties](table-properties-ssms.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8e185-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e185-119">Using Transact-SQL</span></span>  
  
#### <a name="to-show-table-properties"></a><span data-ttu-id="8e185-120">显示表属性</span><span class="sxs-lookup"><span data-stu-id="8e185-120">To show table properties</span></span>  
  
1.  <span data-ttu-id="8e185-121">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="8e185-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8e185-122">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="8e185-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8e185-123">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="8e185-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8e185-124">此示例返回指定对象的 `sys.tables` 目录视图中的所有列。</span><span class="sxs-lookup"><span data-stu-id="8e185-124">The example returns all columns from the `sys.tables` catalog view for the specified object.</span></span>  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 <span data-ttu-id="8e185-125">有关详细信息，请参阅 [sys.tables (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8e185-125">For more information, see [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
