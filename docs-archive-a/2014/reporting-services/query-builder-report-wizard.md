---
title: 查询生成器 (报表向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
- sql12.rtp.rptwizard.querybuilder.f1
helpviewer_keywords:
- Query Builder [Reporting Services]
ms.assetid: 1b0904ea-28c1-448e-b56c-c0fdfbc8b222
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34369bc72fadae75afbc93eb03c0e40509dd27a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577362"
---
# <a name="query-builder-report-wizard"></a><span data-ttu-id="cf1c1-102">查询生成器（报表向导）</span><span class="sxs-lookup"><span data-stu-id="cf1c1-102">Query Builder (Report Wizard)</span></span>
  <span data-ttu-id="cf1c1-103">使用查询生成器可以指定用于检索要在报表中使用的结果集的查询。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-103">Use the Query Builder to specify a query that retrieves a result set to use in a report.</span></span> <span data-ttu-id="cf1c1-104">您可以在两种查询生成器中进行选择：</span><span class="sxs-lookup"><span data-stu-id="cf1c1-104">You can choose between two query builders:</span></span>  
  
-   <span data-ttu-id="cf1c1-105">基于文本的查询生成器（默认情况下）提供一个用于指定查询和查看结果的简单工作区。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-105">The text-based query builder (default) provides a simple workspace for specifying a query and viewing the results.</span></span> <span data-ttu-id="cf1c1-106">您可以指定多个 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句，为自定义数据处理扩展插件指定查询或命令语法，还可以指定指定为表达式的查询。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-106">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="cf1c1-107">由于一般查询生成器不对查询进行预处理，并且适用于任何类型的查询语法，所以用作报表设计器的默认查询生成器工具。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-107">Because the generic query builder does not preprocess the query and can accommodate any kind of query syntax, it is the default query builder tool for Report Designer.</span></span>  
  
-   <span data-ttu-id="cf1c1-108">图形查询生成器为用户提供了更为丰富的视觉体验。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-108">The graphical query builder provides a richer visual experience.</span></span> <span data-ttu-id="cf1c1-109">该生成器用于 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的其他部分。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-109">It is used in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] and in other parts of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf1c1-110">如果您创建的不是表达式或多部分的 SQL 语句，则可以使用图形查询生成器。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-110">You can use the graphical query builder if you are not creating expressions or multi-part SQL statements.</span></span>  
  
     <span data-ttu-id="cf1c1-111">若要切换到图形查询生成器，请切换窗口左上角的 **“编辑为文本”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-111">To switch to the graphical query builder, toggle the **Edit As Text** button in the top left corner of the window.</span></span>  
  
 <span data-ttu-id="cf1c1-112">还可以从另一个报表导入查询。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-112">You can also import a query from another report.</span></span>  
  
## <a name="query-builder-options"></a><span data-ttu-id="cf1c1-113">查询生成器选项</span><span class="sxs-lookup"><span data-stu-id="cf1c1-113">Query Builder Options</span></span>  
 <span data-ttu-id="cf1c1-114">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="cf1c1-114">**Edit As Text**</span></span>  
 <span data-ttu-id="cf1c1-115">在基于文本的查询设计器和图形查询设计器之间切换（如果二者都适用于该查询）。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-115">Toggles between the text-based and graphical query designers, if both will work for the query.</span></span>  
  
 <span data-ttu-id="cf1c1-116">**导入**</span><span class="sxs-lookup"><span data-stu-id="cf1c1-116">**Import**</span></span>  
 <span data-ttu-id="cf1c1-117">打开“导入查询”\*\*\*\* 对话框，显示任何可用报表的 .rdl 和 .sql 文件。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-117">Opens the **Import Query** dialog box and displays .rdl and .sql files for any available report.</span></span> <span data-ttu-id="cf1c1-118">可以按原样使用导入的查询，也可以在查询生成器中进行修改。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-118">You can use the imported query as it is, or you can modify it in the query builder.</span></span>  
  
 <span data-ttu-id="cf1c1-119">\*\*! (运行) \*\*</span><span class="sxs-lookup"><span data-stu-id="cf1c1-119">**! (Run)**</span></span>  
 <span data-ttu-id="cf1c1-120">运行查询，并且在查询有效的情况下返回结果集。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-120">Runs the query and returns a result set if the query is valid.</span></span> <span data-ttu-id="cf1c1-121">请注意，如果查询是表达式，您将不能执行查询。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-121">Note that you cannot execute the query if it is an expression.</span></span> <span data-ttu-id="cf1c1-122">若要验证基于表达式的查询，您必须预览报表。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-122">To verify an expression-based query, you must preview the report.</span></span>  
  
 <span data-ttu-id="cf1c1-123">**命令类型**</span><span class="sxs-lookup"><span data-stu-id="cf1c1-123">**Command type**</span></span>  
 <span data-ttu-id="cf1c1-124">指定 Text、StoredProcedure 或 TableDirect。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-124">Specifies text, stored procedure, or table direct.</span></span> <span data-ttu-id="cf1c1-125">命令类型是否可用取决于您指定的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-125">Availability of a command type depends on the data processing extension you specified.</span></span>  
  
 <span data-ttu-id="cf1c1-126">**“查询”窗格**</span><span class="sxs-lookup"><span data-stu-id="cf1c1-126">**Query pane**</span></span>  
 <span data-ttu-id="cf1c1-127">键入查询。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-127">Type the query.</span></span>  
  
 <span data-ttu-id="cf1c1-128">**结果窗格**</span><span class="sxs-lookup"><span data-stu-id="cf1c1-128">**Result pane**</span></span>  
 <span data-ttu-id="cf1c1-129">显示查询返回的结果集。</span><span class="sxs-lookup"><span data-stu-id="cf1c1-129">Shows the result set returned from the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1c1-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf1c1-130">See Also</span></span>  
 <span data-ttu-id="cf1c1-131">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf1c1-131">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cf1c1-132">报表向导帮助</span><span class="sxs-lookup"><span data-stu-id="cf1c1-132">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
