---
title: 显示实际执行计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f384e2d2752b7601fbb46b8ee7f7b56a2615651c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688846"
---
# <a name="display-an-actual-execution-plan"></a><span data-ttu-id="142d4-102">显示实际执行计划</span><span class="sxs-lookup"><span data-stu-id="142d4-102">Display an Actual Execution Plan</span></span>
  <span data-ttu-id="142d4-103">本主题介绍了如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]生成实际的图形化执行计划。</span><span class="sxs-lookup"><span data-stu-id="142d4-103">This topic describes how to generate actual graphical execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="142d4-104">生成实际执行计划后，将执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询或批处理。</span><span class="sxs-lookup"><span data-stu-id="142d4-104">When actual execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches execute.</span></span> <span data-ttu-id="142d4-105">生成的执行计划会显示 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 用于执行查询的实际查询执行计划。</span><span class="sxs-lookup"><span data-stu-id="142d4-105">The execution plan that is generated displays the actual query execution plan that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses to execute the queries.</span></span>  
  
 <span data-ttu-id="142d4-106">若要使用此功能，用户必须具有相应权限来执行要为其生成图形化执行计划的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询，并且对于查询所引用的所有数据库，用户必须被授予 SHOWPLAN 权限。</span><span class="sxs-lookup"><span data-stu-id="142d4-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a><span data-ttu-id="142d4-107">在查询执行中包括其执行计划</span><span class="sxs-lookup"><span data-stu-id="142d4-107">To include an execution plan for a query during execution</span></span>  
  
1.  <span data-ttu-id="142d4-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具栏中，单击 **“数据库引擎查询”** 。</span><span class="sxs-lookup"><span data-stu-id="142d4-108">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="142d4-109">通过单击 **“打开文件”** 工具栏按钮，再定位到该现有查询，也可以打开一个现有查询并显示估计的执行计划。</span><span class="sxs-lookup"><span data-stu-id="142d4-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="142d4-110">输入要显示其实际执行计划的查询。</span><span class="sxs-lookup"><span data-stu-id="142d4-110">Enter the query for which you would like to display the actual execution plan.</span></span>  
  
3.  <span data-ttu-id="142d4-111">在 "**查询**" 菜单上，单击 "**包括实际执行计划**" 或单击 "**包括实际执行计划**" 工具栏按钮</span><span class="sxs-lookup"><span data-stu-id="142d4-111">On the **Query** menu, click **Include Actual Execution Plan** or click the **Include Actual Execution Plan** toolbar button</span></span>  
  
4.  <span data-ttu-id="142d4-112">通过单击 **“执行”** 工具栏按钮执行查询。</span><span class="sxs-lookup"><span data-stu-id="142d4-112">Execute the query by clicking the **Execute** toolbar button.</span></span> <span data-ttu-id="142d4-113">查询优化器使用的计划将显示在结果窗格的 **“执行计划”** 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="142d4-113">The plan used by the query optimizer is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="142d4-114">将鼠标悬停在逻辑运算符和物理运算符上，显示的工具提示中将出现所选运算符的说明和属性。</span><span class="sxs-lookup"><span data-stu-id="142d4-114">Pause the mouse over the logical and physical operators to view the description and properties of the operators in the displayed ToolTip.</span></span>  
  
     <span data-ttu-id="142d4-115">另外，还可以在“属性”窗口中查看运算符属性。</span><span class="sxs-lookup"><span data-stu-id="142d4-115">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="142d4-116">如果“属性”不可见，请右键单击一个运算符并选择\*\*\*\*“属性”。</span><span class="sxs-lookup"><span data-stu-id="142d4-116">If Properties is not visible, right-click an operator and select **Properties**.</span></span> <span data-ttu-id="142d4-117">选择要查看其属性的运算符。</span><span class="sxs-lookup"><span data-stu-id="142d4-117">Select an operator to view its properties.</span></span>  
  
5.  <span data-ttu-id="142d4-118">可以通过右键单击执行计划并选择“放大”、“缩小”、“自定义显示比例”或“缩放到合适大小”来更改执行计划的显示。   </span><span class="sxs-lookup"><span data-stu-id="142d4-118">You can alter the display of the execution plan by right-clicking the execution plan and selecting **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="142d4-119">**“放大”** 和 **“缩小”** 可以放大或缩小执行计划， **“自定义显示比例”** 使您可以定义自己需要的显示比例，例如缩放到 80%。</span><span class="sxs-lookup"><span data-stu-id="142d4-119">**Zoom In** and **Zoom Out** allow you to zoom in or out on the execution plan, while **Custom Zoom** allows you to define your own zoom, such as zooming at 80 percent.</span></span> <span data-ttu-id="142d4-120">**“缩放到合适大小”** 会放大执行计划以适应结果窗格。</span><span class="sxs-lookup"><span data-stu-id="142d4-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
