---
title: 删除外键关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], deleting
- removing foreign keys
- deleting foreign keys
ms.assetid: 9c9e9ae4-9e03-4137-acb6-b18928a0c4ca
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ae466b9fce53073bfc0645c753246023ff3269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586573"
---
# <a name="delete-foreign-key-relationships"></a><span data-ttu-id="53b22-102">删除外键关系</span><span class="sxs-lookup"><span data-stu-id="53b22-102">Delete Foreign Key Relationships</span></span>
  <span data-ttu-id="53b22-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除外键约束。</span><span class="sxs-lookup"><span data-stu-id="53b22-103">You can delete a foreign key constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="53b22-104">删除外键约束时，将删除强制引用完整性的要求。</span><span class="sxs-lookup"><span data-stu-id="53b22-104">Deleting a foreign key constraint removes the requirement to enforce referential integrity.</span></span>  
  
 <span data-ttu-id="53b22-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="53b22-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="53b22-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="53b22-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="53b22-107">安全性</span><span class="sxs-lookup"><span data-stu-id="53b22-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="53b22-108">**删除外键约束，使用：**</span><span class="sxs-lookup"><span data-stu-id="53b22-108">**To delete a foreign key constraint, using:**</span></span>  
  
     [<span data-ttu-id="53b22-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="53b22-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="53b22-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="53b22-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="53b22-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="53b22-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="53b22-112">Security</span><span class="sxs-lookup"><span data-stu-id="53b22-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="53b22-113">权限</span><span class="sxs-lookup"><span data-stu-id="53b22-113">Permissions</span></span>  
 <span data-ttu-id="53b22-114">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="53b22-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="53b22-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="53b22-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-foreign-key-constraint"></a><span data-ttu-id="53b22-116">删除外键约束</span><span class="sxs-lookup"><span data-stu-id="53b22-116">To delete a foreign key constraint</span></span>  
  
1.  <span data-ttu-id="53b22-117">在 **“对象资源管理器”** 中，展开具有约束的表，再展开 **“键”** 。</span><span class="sxs-lookup"><span data-stu-id="53b22-117">In **Object Explorer**, expand the table with the constraint and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="53b22-118">右键单击该约束，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="53b22-118">Right-click the constraint and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="53b22-119">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="53b22-119">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="53b22-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="53b22-120">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-foreign-key-constraint"></a><span data-ttu-id="53b22-121">删除外键约束</span><span class="sxs-lookup"><span data-stu-id="53b22-121">To delete a foreign key constraint</span></span>  
  
1.  <span data-ttu-id="53b22-122">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="53b22-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="53b22-123">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="53b22-123">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="53b22-124">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="53b22-124">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.DocExe   
    DROP CONSTRAINT FK_Column_B;   
    GO  
    ```  
  
 <span data-ttu-id="53b22-125">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="53b22-125">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
