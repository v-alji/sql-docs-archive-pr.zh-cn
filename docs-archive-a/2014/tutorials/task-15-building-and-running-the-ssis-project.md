---
title: 任务15：生成并运行 SSIS 项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 2a008cd848c95b48e6e22798b6ef903942b4d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690903"
---
# <a name="task-15-building-and-running-the-ssis-project"></a><span data-ttu-id="fff07-102">任务 15：生成和运行 SSIS 项目</span><span class="sxs-lookup"><span data-stu-id="fff07-102">Task 15: Building and Running the SSIS Project</span></span>

  <span data-ttu-id="fff07-103">在本任务中，您将生成并运行 SSIS 项目。</span><span class="sxs-lookup"><span data-stu-id="fff07-103">In this task, you build and run the SSIS project.</span></span> <span data-ttu-id="fff07-104">如果在计算机上安装了64位版本的 Excel 2010，则应将**Run64BitRuntime**的值设置为**False** ，以便 Excel 源工作。</span><span class="sxs-lookup"><span data-stu-id="fff07-104">If you have the 64-bit version of Excel 2010 installed on your computer, you should set the value of **Run64BitRuntime** to **False** for the Excel source to work.</span></span>  
  
1.  <span data-ttu-id="fff07-105">在 "**解决方案资源管理器**" 窗口中，单击菜单上的 "**项目**"，然后单击 " **CleanseAndCurateSuppliers 属性**"。</span><span class="sxs-lookup"><span data-stu-id="fff07-105">In the **Solution Explorer** window, click **Project** on the menu, and click **CleanseAndCurateSuppliers Properties**.</span></span>  
  
2.  <span data-ttu-id="fff07-106">在 "**属性**" 对话框中，展开左侧的 "**配置属性**"，然后单击 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="fff07-106">In the **Properties** dialog box, expand **Configuration Properties** on left, and click **Debugging**.</span></span>  
  
3.  <span data-ttu-id="fff07-107">将**Run64BitRuntime**设置为**False**。</span><span class="sxs-lookup"><span data-stu-id="fff07-107">Set **Run64BitRuntime** to **False**.</span></span>  
  
     <span data-ttu-id="fff07-108">![CleanseAndCurateSuppliers 项目属性](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers 项目属性")</span><span class="sxs-lookup"><span data-stu-id="fff07-108">![CleanseAndCurateSuppliers Project Properties](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers Project Properties")</span></span>  
  
4.  <span data-ttu-id="fff07-109">单击“确定”以关闭“属性”对话框 。</span><span class="sxs-lookup"><span data-stu-id="fff07-109">Click **OK** to close the **Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="fff07-110">单击菜单栏上的 "**生成**"，然后单击 "**生成 CleanseAndCurateSuppliers**"。</span><span class="sxs-lookup"><span data-stu-id="fff07-110">Click **Build** on menu bar and click **Build CleanseAndCurateSuppliers**.</span></span> <span data-ttu-id="fff07-111">确保没有生成错误。</span><span class="sxs-lookup"><span data-stu-id="fff07-111">Make sure that there are no build errors.</span></span>  
  
6.  <span data-ttu-id="fff07-112">单击菜单栏上的 "**调试**"，然后单击 "**启动调试**"。</span><span class="sxs-lookup"><span data-stu-id="fff07-112">Click **Debug** on the menu bar and click **Start Debugging**.</span></span>  
  
7.  <span data-ttu-id="fff07-113">查看 "**进度**" 窗口中的消息，并验证包是否已成功执行和结束。</span><span class="sxs-lookup"><span data-stu-id="fff07-113">Review messages in the **Progress** window and verify that package executed and ended successfully.</span></span>  
  
     <span data-ttu-id="fff07-114">![进度窗口的结果](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "进度窗口的结果")</span><span class="sxs-lookup"><span data-stu-id="fff07-114">![Results from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Results from Progress Window")</span></span>  
  
     <span data-ttu-id="fff07-115">![进度窗口的最终状态](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "进度窗口的最终状态")</span><span class="sxs-lookup"><span data-stu-id="fff07-115">![Final Status from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Final Status from Progress Window")</span></span>  
  
8.  <span data-ttu-id="fff07-116">单击菜单栏上的 "**调试**"，然后单击 "**停止调试**" 以停止调试会话。</span><span class="sxs-lookup"><span data-stu-id="fff07-116">Click **Debug** on menu bar and click **Stop Debugging** to stop the debugging session.</span></span> <span data-ttu-id="fff07-117">如果包失败，应启用数据查看器并查看数据在组件之间的流动方式。</span><span class="sxs-lookup"><span data-stu-id="fff07-117">If the package fails, you should enable data viewers and see how the data flows between components.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="fff07-118">下一步</span><span class="sxs-lookup"><span data-stu-id="fff07-118">Next Step</span></span>  
 [<span data-ttu-id="fff07-119">任务 16：使用主数据管理器进行验证</span><span class="sxs-lookup"><span data-stu-id="fff07-119">Task 16: Verifying with Master Data Manager</span></span>](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
