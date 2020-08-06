---
title: 列出作业类别信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 924e2b064980b2ea7068230610414262995da1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691498"
---
# <a name="list-job-category-information"></a><span data-ttu-id="497bc-102">列出作业类别信息</span><span class="sxs-lookup"><span data-stu-id="497bc-102">List Job Category Information</span></span>
  <span data-ttu-id="497bc-103">如何 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用或 SQL Server 管理对象列出中的作业类别信息 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="497bc-103">How to list job category information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  

  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="497bc-104">Security</span><span class="sxs-lookup"><span data-stu-id="497bc-104">Security</span></span>  
 <span data-ttu-id="497bc-105">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="497bc-105">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="497bc-106">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="497bc-106">Using Transact-SQL</span></span>  
  
#### <a name="to-list-job-category-information"></a><span data-ttu-id="497bc-107">列出作业类别信息</span><span class="sxs-lookup"><span data-stu-id="497bc-107">To list job category information</span></span>  
  
1.  <span data-ttu-id="497bc-108">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="497bc-108">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="497bc-109">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="497bc-109">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="497bc-110">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="497bc-110">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 <span data-ttu-id="497bc-111">有关详细信息，请参阅[&#40;transact-sql&#41;sp_help_category ](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="497bc-111">For more information, see [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).</span></span>  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="497bc-112">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="497bc-112">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="497bc-113">**列出作业类别信息**</span><span class="sxs-lookup"><span data-stu-id="497bc-113">**To list job category information**</span></span>  
  
 <span data-ttu-id="497bc-114">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobCategory` 类。</span><span class="sxs-lookup"><span data-stu-id="497bc-114">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell..</span></span> <span data-ttu-id="497bc-115">有关详细信息，请参阅[SQL Server 管理对象 &#40;SMO&#41; 编程指南](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="497bc-115">For more information, see [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).</span></span>  
