---
title: 代码大纲显示
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], outlining code
- Query Editor [SQL Server Management Studio], hiding code
ms.assetid: 556c7dfe-7bc8-4cab-a36f-2b753a05d3f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a142ca8fbdcdfcfbfd1b71de06c0b0fd4c5339c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580650"
---
# <a name="code-outlining"></a><span data-ttu-id="c5833-102">代码大纲显示</span><span class="sxs-lookup"><span data-stu-id="c5833-102">Code Outlining</span></span>
  <span data-ttu-id="c5833-103">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中的大纲显示功能可在编辑查询时有选择地隐藏代码，</span><span class="sxs-lookup"><span data-stu-id="c5833-103">You can use the outlining feature in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] query editors to selectively hide code when you edit queries.</span></span> <span data-ttu-id="c5833-104">从而可以更加方便地查看您正在处理的代码，尤其是大型查询文件中的代码。</span><span class="sxs-lookup"><span data-stu-id="c5833-104">This enables you to more easily view the code you are working on, especially in large query files.</span></span>

## <a name="outlining-overview"></a><span data-ttu-id="c5833-105">大纲显示概述</span><span class="sxs-lookup"><span data-stu-id="c5833-105">Outlining Overview</span></span>
 <span data-ttu-id="c5833-106">默认情况下，打开查询编辑器窗口时所有代码均可见。</span><span class="sxs-lookup"><span data-stu-id="c5833-106">By default, all code is visible when you open a query editor window.</span></span> <span data-ttu-id="c5833-107">可将代码区域折叠起来以便在视图中隐藏该区域。</span><span class="sxs-lookup"><span data-stu-id="c5833-107">Regions of the code can be collapsed to hide it from view.</span></span> <span data-ttu-id="c5833-108">编辑器窗口左侧边缘的竖线使用一个方块和一个减号 (-) 来标识每个可折叠代码区域的起点。</span><span class="sxs-lookup"><span data-stu-id="c5833-108">A vertical line on the left edge of the editor window uses a square with a minus sign (-) to identify the start of each collapsible code region.</span></span> <span data-ttu-id="c5833-109">单击减号时，代码区域的文本将更换为一个含有三个句点 (...) 的框，且减号将变为加号 (+)。</span><span class="sxs-lookup"><span data-stu-id="c5833-109">When you click a minus sign, the text of the code region is replaced with a box that contains three periods (...), and the minus sign changes to a plus sign (+).</span></span> <span data-ttu-id="c5833-110">单击加号时，将显示折叠的代码，且加号将变为减号。</span><span class="sxs-lookup"><span data-stu-id="c5833-110">When you click a plus sign, the collapsed code appears and the plus sign changes to a minus sign.</span></span> <span data-ttu-id="c5833-111">将指针移动到含有三个句点的框上方时，该处出现工具提示，显示折叠部分包含的代码。</span><span class="sxs-lookup"><span data-stu-id="c5833-111">When you move the pointer over a box that has three periods, a tooltip appears that shows the code in the collapsed section.</span></span>

## <a name="system-outline-regions"></a><span data-ttu-id="c5833-112">系统大纲区域</span><span class="sxs-lookup"><span data-stu-id="c5833-112">System Outline Regions</span></span>
 <span data-ttu-id="c5833-113">每个 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 编辑器均生成一组默认的系统定义的大纲区域。</span><span class="sxs-lookup"><span data-stu-id="c5833-113">Each [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] editor generates a set of default, system-defined outline regions.</span></span>

 <span data-ttu-id="c5833-114">MDX 和 DMX 代码编辑器可为每个多行语句创建大纲区域。</span><span class="sxs-lookup"><span data-stu-id="c5833-114">The MDX and DMX code editors create outline regions for each multiline statement.</span></span> <span data-ttu-id="c5833-115">这是以上编辑器支持的唯一大纲显示级别。</span><span class="sxs-lookup"><span data-stu-id="c5833-115">This is the only level of outlining that these editors support.</span></span>

### <a name="analysis-services-xmla-query-editor-regions"></a><span data-ttu-id="c5833-116">Analysis Services XMLA 查询编辑器区域</span><span class="sxs-lookup"><span data-stu-id="c5833-116">Analysis Services XMLA Query Editor Regions</span></span>
 <span data-ttu-id="c5833-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA 查询编辑器为每个多行 XML 属性生成大纲区域。</span><span class="sxs-lookup"><span data-stu-id="c5833-117">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query Editor generates an outline region for each multiline XML attribute.</span></span> <span data-ttu-id="c5833-118">该编辑器可为嵌套标签嵌套大纲区域。</span><span class="sxs-lookup"><span data-stu-id="c5833-118">The editor nests the outline regions for nested tags.</span></span> <span data-ttu-id="c5833-119">例如，XMLA 编辑器为以下文件创建三个大纲区域。</span><span class="sxs-lookup"><span data-stu-id="c5833-119">For example, the XMLA Editor creates three outline regions for the following document.</span></span>

 <span data-ttu-id="c5833-120">![显示大纲的 XML 代码](../../database-engine/media/editoutlinexmlfull.gif "显示大纲的 XML 代码")</span><span class="sxs-lookup"><span data-stu-id="c5833-120">![XML code showing outlining](../../database-engine/media/editoutlinexmlfull.gif "XML code showing outlining")</span></span>

 <span data-ttu-id="c5833-121">当单击行上的减号时 \<InnerTag> ，只会折叠 InnerTag，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c5833-121">When you click the minus sign on the \<InnerTag> line, just the InnerTag is collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="c5833-122">![隐藏内部节点的 XML 代码](../../database-engine/media/editoutlinexmlinnercol.gif "隐藏内部节点的 XML 代码")</span><span class="sxs-lookup"><span data-stu-id="c5833-122">![XML code with inner node hidden](../../database-engine/media/editoutlinexmlinnercol.gif "XML code with inner node hidden")</span></span>

 <span data-ttu-id="c5833-123">将指针移动到含有三个句点 (...) 的框上方时，折叠区域中的代码将出现在工具提示中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c5833-123">When you move the pointer over the box that has the three periods (...), the code in the collapsed region appears in a tooltip, as shown in the following illustration.</span></span>

 <span data-ttu-id="c5833-124">![带有显示隐藏代码的工具提示的 XML 代码](../../database-engine/media/editoutlinexmlmouse.gif "带有显示隐藏代码的工具提示的 XML 代码")</span><span class="sxs-lookup"><span data-stu-id="c5833-124">![XML code with tooltip showing hidden code](../../database-engine/media/editoutlinexmlmouse.gif "XML code with tooltip showing hidden code")</span></span>

 <span data-ttu-id="c5833-125">当单击行上的减号时 \<MiddleTag> ，MiddleTag 和 InnerTag 都是折叠的，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c5833-125">When you click the minus sign on the \<MiddleTag> line, both the MiddleTag and InnerTag are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="c5833-126">![隐藏内部和中间标记的 XML 代码](../../database-engine/media/editoutlinexmlmiddlecol.gif "隐藏内部和中间标记的 XML 代码")</span><span class="sxs-lookup"><span data-stu-id="c5833-126">![XML code with inner and middle tags hidden](../../database-engine/media/editoutlinexmlmiddlecol.gif "XML code with inner and middle tags hidden")</span></span>

 <span data-ttu-id="c5833-127">当单击行上的减号时 \<OuterTag> ，所有三行均折叠起来，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c5833-127">When you click the minus sign on the \<OuterTag> line, all three lines are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="c5833-128">![显示所有三个隐藏标记的 XML 代码](../../database-engine/media/editoutlinexmloutercol.gif "显示所有三个隐藏标记的 XML 代码")</span><span class="sxs-lookup"><span data-stu-id="c5833-128">![XML code showing all three tags hidden](../../database-engine/media/editoutlinexmloutercol.gif "XML code showing all three tags hidden")</span></span>

### <a name="database-engine-query-editor-regions"></a><span data-ttu-id="c5833-129">数据库引擎查询编辑器区域</span><span class="sxs-lookup"><span data-stu-id="c5833-129">Database Engine Query Editor Regions</span></span>
 <span data-ttu-id="c5833-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 查询编辑器为以下层次结构中的每个元素生成大纲区域：</span><span class="sxs-lookup"><span data-stu-id="c5833-130">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor generates outline regions for each element in the following hierarchy:</span></span>

1.  <span data-ttu-id="c5833-131">批处理。</span><span class="sxs-lookup"><span data-stu-id="c5833-131">Batches.</span></span> <span data-ttu-id="c5833-132">第一个批处理是从文件开头到第一个 GO 命令或没有 GO 命令时到文件结尾的代码。</span><span class="sxs-lookup"><span data-stu-id="c5833-132">The first batch is the code from the start of the file to either the first GO command or the end of the file when there are no GO commands.</span></span> <span data-ttu-id="c5833-133">在第一个 GO 命令后面，从每个 GO 命令到下一个 GO 命令或文件结尾均有一个批处理。</span><span class="sxs-lookup"><span data-stu-id="c5833-133">After the first GO, there is one batch from each GO command to either the next GO command or the end of the file.</span></span>

2.  <span data-ttu-id="c5833-134">块由以下关键字分隔：</span><span class="sxs-lookup"><span data-stu-id="c5833-134">Blocks delimited by the following keywords:</span></span>

    -   <span data-ttu-id="c5833-135">BEGIN - END</span><span class="sxs-lookup"><span data-stu-id="c5833-135">BEGIN - END</span></span>

    -   <span data-ttu-id="c5833-136">BEGIN TRY - END TRY</span><span class="sxs-lookup"><span data-stu-id="c5833-136">BEGIN TRY - END TRY</span></span>

    -   <span data-ttu-id="c5833-137">BEGIN CATCH - END CATCH</span><span class="sxs-lookup"><span data-stu-id="c5833-137">BEGIN CATCH - END CATCH</span></span>

3.  <span data-ttu-id="c5833-138">多行语句。</span><span class="sxs-lookup"><span data-stu-id="c5833-138">Multiline statements.</span></span>

 <span data-ttu-id="c5833-139">例如， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 查询编辑器为以下查询创建三个大纲区域：</span><span class="sxs-lookup"><span data-stu-id="c5833-139">For example, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor creates three outline regions for the following query:</span></span>

```
CREATE PROCEDURE Sales.SampleProc --Outline region 1
AS
BEGIN --Outline region 2 
  SELECT GETDATE() AS TimeOfQuery;
  SELECT * --Outline region 3
  FROM sys.transmission_queue;
  SELECT @@VERSION;
END;
GO
```

 <span data-ttu-id="c5833-140">若仅折叠该 `SELECT *` 语句，请单击 `SELECT` 行上的减号。</span><span class="sxs-lookup"><span data-stu-id="c5833-140">You can click the minus sign on the `SELECT *` line to collapse just that `SELECT` statement.</span></span> <span data-ttu-id="c5833-141">若要折叠整个 `BEGIN - END` 块，请单击 `BEGIN` 行上的减号。</span><span class="sxs-lookup"><span data-stu-id="c5833-141">To collapse the whole `BEGIN - END` block, click the minus sign on the `BEGIN` line.</span></span> <span data-ttu-id="c5833-142">若要将整个批处理折叠到 `GO` 命令，请单击 `CREATE PROCEDURE` 行上的减号。</span><span class="sxs-lookup"><span data-stu-id="c5833-142">To collapse the whole batch to the `GO` command, click the minus sign on the `CREATE PROCEDURE` line.</span></span> <span data-ttu-id="c5833-143">由于 `SELECT GETDATE()` 或 `SELECT @@VERSION` 行为单行语句且不具有大纲区域，因此不能将这两行分别单独折叠起来。</span><span class="sxs-lookup"><span data-stu-id="c5833-143">You cannot collapse the `SELECT GETDATE()` or `SELECT @@VERSION` lines individually because they are single line statements and do not get outlining regions.</span></span>


