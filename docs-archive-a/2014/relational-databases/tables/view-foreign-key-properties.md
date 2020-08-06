---
title: 查看外键属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5860a0cf26b983d75bab86862ee1e5fdd7737712
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578030"
---
# <a name="view-foreign-key-properties"></a><span data-ttu-id="6ed1f-102">查看外键属性</span><span class="sxs-lookup"><span data-stu-id="6ed1f-102">View Foreign Key Properties</span></span>
  <span data-ttu-id="6ed1f-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看关系的外键属性。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-103">You can view the foreign key attributes of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6ed1f-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="6ed1f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6ed1f-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6ed1f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6ed1f-106">安全性</span><span class="sxs-lookup"><span data-stu-id="6ed1f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6ed1f-107">**查看特定表的外键属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="6ed1f-107">**To view the foreign key attributes of a specific table, using:**</span></span>  
  
     [<span data-ttu-id="6ed1f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6ed1f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6ed1f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6ed1f-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6ed1f-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="6ed1f-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6ed1f-111">Security</span><span class="sxs-lookup"><span data-stu-id="6ed1f-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6ed1f-112">权限</span><span class="sxs-lookup"><span data-stu-id="6ed1f-112">Permissions</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="6ed1f-113">有关详细信息，请参阅 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-113">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6ed1f-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6ed1f-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="6ed1f-115">查看特定表中关系的外键属性</span><span class="sxs-lookup"><span data-stu-id="6ed1f-115">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="6ed1f-116">对于包含要查看的外键的表，打开表设计器，在表设计器中单击右键，然后从快捷菜单中选择“关系”  。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-116">Open the Table Designer for the table containing the foreign key you want to view, right-click in the Table Designer, and choose **Relationships** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="6ed1f-117">在 **“外键关系”** 对话框中，选择要查看其属性的关系。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-117">In the **Foreign Key Relationships** dialog box, select the relationship with properties you want to view.</span></span>  
  
 <span data-ttu-id="6ed1f-118">如果外键列与主键相关，则主键列在 **“表设计器”** 中将由行选择器中的主键符号进行标识。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-118">If the foreign key columns are related to a primary key, the primary key columns are identified in **Table Designer** by a primary key symbol in the row selector.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6ed1f-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6ed1f-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="6ed1f-120">查看特定表中关系的外键属性</span><span class="sxs-lookup"><span data-stu-id="6ed1f-120">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="6ed1f-121">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ed1f-122">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6ed1f-123">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6ed1f-124">此实例返回示例数据库中的表 `HumanResources.Employee` 的所有外键以及属性。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-124">The example returns all foreign keys and their properties for the table `HumanResources.Employee` in the sample database.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 <span data-ttu-id="6ed1f-125">有关详细信息，请参阅 [sys.foreign_keys (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) 和 [sys.foreign_key_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ed1f-125">For more information, see [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) and [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
