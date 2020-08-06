---
title: 显示估计的执行计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- zoom [SQL Server]
- estimated execution plan [SQL Server]
- displaying execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
- customizing execution plan display [SQL Server]
- modifying execution plan display
- custom zoom [SQL Server]
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79c0972661d40eb9e359cf43f7a1f0b1b2ae4b0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688840"
---
# <a name="display-the-estimated-execution-plan"></a><span data-ttu-id="20afd-102">显示估计的执行计划</span><span class="sxs-lookup"><span data-stu-id="20afd-102">Display the Estimated Execution Plan</span></span>
  <span data-ttu-id="20afd-103">本主题介绍了如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]生成图形化的估计的执行计划。</span><span class="sxs-lookup"><span data-stu-id="20afd-103">This topic describes how to generate graphical estimated execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="20afd-104">生成估计的执行计划时， [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询或批处理并不执行。</span><span class="sxs-lookup"><span data-stu-id="20afd-104">When estimated execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches do not execute.</span></span> <span data-ttu-id="20afd-105">生成的执行计划显示的是如果实际执行查询 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 最有可能使用的查询执行计划。</span><span class="sxs-lookup"><span data-stu-id="20afd-105">Instead, the execution plan that is generated displays the query execution plan that [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] would most probably use if the queries were actually executed.</span></span>  
  
 <span data-ttu-id="20afd-106">为了使用此功能，用户必须具有执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询（为其生成图形执行计划）的相应权限，并且用户必须获得了对查询引用的所有数据库的 SHOWPLAN 权限。</span><span class="sxs-lookup"><span data-stu-id="20afd-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-display-the-estimated-execution-plan-for-a-query"></a><span data-ttu-id="20afd-107">显示查询的估计的执行计划</span><span class="sxs-lookup"><span data-stu-id="20afd-107">To display the estimated execution plan for a query</span></span>  
  
1.  <span data-ttu-id="20afd-108">在工具栏上，单击 **“数据库引擎查询”** 。</span><span class="sxs-lookup"><span data-stu-id="20afd-108">On the toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="20afd-109">通过单击 **“打开文件”** 工具栏按钮，再定位到该现有查询，也可以打开一个现有查询并显示估计的执行计划。</span><span class="sxs-lookup"><span data-stu-id="20afd-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="20afd-110">输入您希望为其显示估计的执行计划的查询。</span><span class="sxs-lookup"><span data-stu-id="20afd-110">Enter the query for which you would like to display the estimated execution plan.</span></span>  
  
3.  <span data-ttu-id="20afd-111">在 **“查询”** 菜单上，单击 **“显示估计的执行计划”** ，或单击 **“显示估计的执行计划”** 工具栏按钮。</span><span class="sxs-lookup"><span data-stu-id="20afd-111">On the **Query** menu, click **Display Estimated Execution Plan** or click the **Display Estimated Execution Plan** toolbar button.</span></span> <span data-ttu-id="20afd-112">估计的执行计划在结果窗格中的 **“执行计划”** 选项卡上显示。</span><span class="sxs-lookup"><span data-stu-id="20afd-112">The estimated execution plan is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="20afd-113">若要查看其他信息，请将鼠标暂停在逻辑和物理运算符图标上，并查看显示的工具提示中有关运算符的说明和属性。</span><span class="sxs-lookup"><span data-stu-id="20afd-113">To view additional information, pause the mouse over the logical and physical operator icons and view the description and properties of the operator in the displayed ToolTip.</span></span> <span data-ttu-id="20afd-114">另外，还可以在“属性”窗口中查看运算符属性。</span><span class="sxs-lookup"><span data-stu-id="20afd-114">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="20afd-115">如果属性不可见，请右键单击一个运算符并单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="20afd-115">If Properties is not visible, right-click an operator and click **Properties**.</span></span> <span data-ttu-id="20afd-116">选择要查看其属性的运算符。</span><span class="sxs-lookup"><span data-stu-id="20afd-116">Select an operator to view its properties.</span></span>  
  
4.  <span data-ttu-id="20afd-117">若要更改执行计划的显示，请右键单击“执行计划”并选择“放大”、“缩小”、“自定义显示比例”或“缩放到合适大小”。</span><span class="sxs-lookup"><span data-stu-id="20afd-117">To alter the display of the execution plan, right-click the execution plan and select **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="20afd-118">“放大”和“缩小”允许你按固定量扩大或减小执行计划。</span><span class="sxs-lookup"><span data-stu-id="20afd-118">**Zoom In** and **Zoom Out** allow you to magnify or reduce the execution plan by fixed amounts.</span></span> <span data-ttu-id="20afd-119">“自定义缩放” 允许你定义自己的显示放大倍数，例如缩放到 80%。</span><span class="sxs-lookup"><span data-stu-id="20afd-119">**Custom Zoom** allows you to define your own display magnification, such as zooming at 80 percent.</span></span> <span data-ttu-id="20afd-120">**“缩放到合适大小”** 会放大执行计划以适应结果窗格。</span><span class="sxs-lookup"><span data-stu-id="20afd-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
