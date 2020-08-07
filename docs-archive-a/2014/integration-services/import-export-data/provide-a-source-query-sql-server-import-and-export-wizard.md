---
title: 提供源查询（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b21100f51c279e9ba764c8f82565af9d6e391ef3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588623"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="0ca6d-102">提供源查询（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="0ca6d-102">Provide a Source Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="0ca6d-103">使用 "**提供源查询**" 页可以键入将生成要从数据源复制到目标的数据的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-103">Use the **Provide a Source Query** page to type the SQL statement that will generate the data to copy from the data source to the destination.</span></span>  
  
 <span data-ttu-id="0ca6d-104">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="0ca6d-105">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="0ca6d-106">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="0ca6d-107">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="0ca6d-108">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="0ca6d-109">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ca6d-110">选项</span><span class="sxs-lookup"><span data-stu-id="0ca6d-110">Options</span></span>  
 <span data-ttu-id="0ca6d-111">**SQL 语句**</span><span class="sxs-lookup"><span data-stu-id="0ca6d-111">**SQL statement**</span></span>  
 <span data-ttu-id="0ca6d-112">键入查询语句，以便从源数据库中检索所选的数据行。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-112">Type a query statement to retrieve selected rows of data from the source database.</span></span> <span data-ttu-id="0ca6d-113">例如，以下查询语句可以从 AdventureWorks 数据库中检索提成比例超过 1.5% 的销售人员的 **SalesPersonID**、 **SalesQuota**和 **SalesYTD** 。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-113">For example, the following query statement retrieves the **SalesPersonID**, **SalesQuota**, and **SalesYTD** from the AdventureWorks database for sales persons whose commission percentage is more than 1.5 percent.</span></span>  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 <span data-ttu-id="0ca6d-114">Parse</span><span class="sxs-lookup"><span data-stu-id="0ca6d-114">**Parse**</span></span>  
 <span data-ttu-id="0ca6d-115">检查“SQL 语句”\*\*\*\* 文本框中 SQL 语句的语法。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-115">Checks the syntax of the SQL statement in the **SQL statement** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ca6d-116">如果检查语句的语法所需的时间超过超时值（30 秒），则将停止分析并生成错误。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-116">If the time that is required to check the syntax of the statement exceeds the time-out value of 30 seconds, parsing stops and generates an error.</span></span> <span data-ttu-id="0ca6d-117">在成功完成分析之前，您将无法跳过向导的这一页。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-117">You will not be able to move past this page of the wizard until parsing succeeds.</span></span> <span data-ttu-id="0ca6d-118">一种解决方案是基于查询创建数据库视图，然后从向导查询该视图，而不是直接输入查询文本。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-118">One solution is to create a database view based on the query, and to query the view from the wizard, instead of entering the query text directly.</span></span>  
  
 <span data-ttu-id="0ca6d-119">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="0ca6d-119">**Browse**</span></span>  
 <span data-ttu-id="0ca6d-120">使用 "**打开**" 对话框选择包含 SQL 语句的文件。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-120">Select a file containing a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="0ca6d-121">选择一个文件可以将该文件中的文本复制到 **“查询语句”** 文本框中。</span><span class="sxs-lookup"><span data-stu-id="0ca6d-121">Selecting a file copies the text from the file into the **Query statement** text box.</span></span>  
  
  
