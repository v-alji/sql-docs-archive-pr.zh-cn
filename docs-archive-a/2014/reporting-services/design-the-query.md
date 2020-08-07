---
title: 设计查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b56d99ec11b50ce53ef223a01eb5fc2766238ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691121"
---
# <a name="design-the-query"></a><span data-ttu-id="6fc4d-102">设计查询</span><span class="sxs-lookup"><span data-stu-id="6fc4d-102">Design the Query</span></span>
  <span data-ttu-id="6fc4d-103">使用报表向导的此页来创建查询，可以手动键入查询，使用查询生成器来交互生成查询，或从另一个表中导入查询。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-103">Use this page of the Report Wizard to create a query by typing the query manually, by using Query Builder to interactively build a query, or by importing a query from another report.</span></span>  
  
 <span data-ttu-id="6fc4d-104">您在“选择数据源”页（报表向导中的上一页）中选择的数据源类型决定了您可以在此页中输入的查询。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-104">The data source type you chose on the Select the Data Source page, a previous page in the Report Wizard, determines the query you can enter on this page.</span></span> <span data-ttu-id="6fc4d-105">例如，如果数据源类型为 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，则可以输入 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句或存储过程名称。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-105">For example, if the data source type is [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements or stored procedure names.</span></span> <span data-ttu-id="6fc4d-106">如果数据源类型为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，则 "查询" 窗格将被禁用，并且您不能直接输入查询。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-106">If the data source type is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], the Query pane is disabled and you cannot enter a query directly.</span></span> <span data-ttu-id="6fc4d-107">可以使用“查询生成器”来指定查询。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-107">You can specify the query by using Query Builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6fc4d-108">选项</span><span class="sxs-lookup"><span data-stu-id="6fc4d-108">Options</span></span>  
 <span data-ttu-id="6fc4d-109">**查询字符串**</span><span class="sxs-lookup"><span data-stu-id="6fc4d-109">**Query string**</span></span>  
 <span data-ttu-id="6fc4d-110">键入用于检索要在报表中使用的数据的查询。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-110">Type a query that retrieves the data you want to use in your report.</span></span>  
  
 <span data-ttu-id="6fc4d-111">**查询生成器**</span><span class="sxs-lookup"><span data-stu-id="6fc4d-111">**Query Builder**</span></span>  
 <span data-ttu-id="6fc4d-112">单击“查询生成器”\*\*\*\* 打开数据源的查询设计器，或从另一个表中导入查询。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-112">Click **Query Builder** to open a query designer for the data source, or to import a query from another report.</span></span>  
  
 <span data-ttu-id="6fc4d-113">有关查询设计器的详细信息，请参阅 [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-113">For more information about query designers, see [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc4d-114">示例</span><span class="sxs-lookup"><span data-stu-id="6fc4d-114">Example</span></span>  
 <span data-ttu-id="6fc4d-115">对于数据源类型**Microsoft SQL Server**，下面的查询将从数据库表中检索姓氏列表 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `Person` 。</span><span class="sxs-lookup"><span data-stu-id="6fc4d-115">For the data source type **Microsoft SQL Server**, the following query retrieves a list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Person` table.</span></span>  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 <span data-ttu-id="6fc4d-116">对于数据源类型**Microsoft SQL Server**，下面的查询将 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 为标识号为1的员工运行存储过程 `uspGetEmployeeManagers` ：</span><span class="sxs-lookup"><span data-stu-id="6fc4d-116">For the data source type **Microsoft SQL Server**, the following query runs the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` for the employee with identification number 1:</span></span>  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fc4d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fc4d-117">See Also</span></span>  
 <span data-ttu-id="6fc4d-118">[报表向导帮助](../../2014/reporting-services/report-wizard-help.md) </span><span class="sxs-lookup"><span data-stu-id="6fc4d-118">[Report Wizard Help](../../2014/reporting-services/report-wizard-help.md) </span></span>  
 <span data-ttu-id="6fc4d-119">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6fc4d-119">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6fc4d-120">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6fc4d-120">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
