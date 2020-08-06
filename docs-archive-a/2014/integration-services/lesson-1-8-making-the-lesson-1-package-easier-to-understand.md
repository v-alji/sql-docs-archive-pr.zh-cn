---
title: 步骤 8：使第 1 课包更易于理解 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fb8e2adb9062b5b777acc14df0ddc5b45884ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586823"
---
# <a name="step-8-making-the-lesson-1-package-easier-to-understand"></a><span data-ttu-id="8f1d6-102">步骤 8：使 Lesson 1 包更易理解</span><span class="sxs-lookup"><span data-stu-id="8f1d6-102">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>
  <span data-ttu-id="8f1d6-103">因为您已完成了 Lesson 1 包的配置，所以整理包布局是很必要的。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-103">Now that you have completed the configuration of the Lesson 1 package, it is a good idea to tidy up the package layout.</span></span> <span data-ttu-id="8f1d6-104">如果控制流和数据流布局中的形状大小不一，或者如果形状未对齐或未进行分组，则可能很难理解包功能。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-104">If the shapes in the control and data flow layouts are random sizes, or if the shapes are not aligned or grouped, the functionality of package can be more difficult to understand.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="8f1d6-105">Data Tools 提供了可轻松、快速设置包布局格式的工具。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-105">Data Tools provides tools that make it easy and quick to format the package layout.</span></span> <span data-ttu-id="8f1d6-106">格式设置功能包括使形状大小统一，对齐各个形状，并控制形状之间的水平间距和垂直间距。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-106">The formatting features include the ability to make shapes the same size, align shapes, and manipulate the horizontal and vertical spacing between shapes.</span></span>  
  
 <span data-ttu-id="8f1d6-107">另一种增进对包功能的了解的方式是添加描述包功能的批注。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-107">Another way to improve the understanding of package functionality is to add annotations that describe package functionality.</span></span>  
  
 <span data-ttu-id="8f1d6-108">在本任务中，您将使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 中的格式设置功能改善数据流的布局并向数据流中添加批注。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-108">In this task, you will use the formatting features in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools to improve the layout of the data flow and also add an annotation to the data flow.</span></span>  
  
### <a name="to-format-the-layout-of-the-data-flow"></a><span data-ttu-id="8f1d6-109">设置数据流布局的格式</span><span class="sxs-lookup"><span data-stu-id="8f1d6-109">To format the layout of the data flow</span></span>  
  
1.  <span data-ttu-id="8f1d6-110">如果尚未打开 Lesson 1 包，则请在解决方案资源管理器中双击 Lesson 1.dtsx。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-110">If the Lesson 1 package is not already open, double-click Lesson 1.dtsx in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="8f1d6-111">单击 **“数据流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-111">Click the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="8f1d6-112">将游标置于 Extract Sample Currency 转换的右上方，单击并将游标拖过所有的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-112">Place the cursor to the top and to the right of the Extract Sample Currency transformation, click, and then drag the cursor across all the data flow components.</span></span>  
  
4.  <span data-ttu-id="8f1d6-113">在 **“格式”** 菜单中，指向 **“使大小相同”**，再单击 **“两者”**。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-113">On the **Format** menu, point to **Make Same Size**, and then click **Both**.</span></span>  
  
5.  <span data-ttu-id="8f1d6-114">选定数据流对象后，在 **“格式”** 菜单中，指向 **“对齐”**，再单击 **“左对齐”**。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-114">With the data flow objects selected, on the **Format** menu, point to **Align**, and then click **Lefts**.</span></span>  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a><span data-ttu-id="8f1d6-115">向数据流中添加批注</span><span class="sxs-lookup"><span data-stu-id="8f1d6-115">To add an annotation to the data flow</span></span>  
  
1.  <span data-ttu-id="8f1d6-116">右键单击数据流设计图面背景的任意位置，再单击 **“添加批注”**。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-116">Right-click anywhere in the background of the data flow design surface and then click **Add Annotation**.</span></span>  
  
2.  <span data-ttu-id="8f1d6-117">在批注框中键入或粘贴以下文本。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-117">Type or paste the following text in the annotation box.</span></span>  
  
     <span data-ttu-id="8f1d6-118">**The data flow extracts data from a file, looks up values in the CurrencyKey column in the DimCurrency table and the DateKey column in the DimDate table, and writes the data to the NewFactCurrencyRate table.**</span><span class="sxs-lookup"><span data-stu-id="8f1d6-118">**The data flow extracts data from a file, looks up values in the CurrencyKey column in the DimCurrency table and the DateKey column in the DimDate table, and writes the data to the NewFactCurrencyRate table.**</span></span>  
  
     <span data-ttu-id="8f1d6-119">若要在批注框中使文本换行，请将游标置于要开始新行的位置，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-119">To wrap the text in the annotation box, place the cursor where you want to start a new line and press the Enter key.</span></span>  
  
     <span data-ttu-id="8f1d6-120">如果未将文本添加到批注框，则当您在批注框外部单击时，该文本便会消失。</span><span class="sxs-lookup"><span data-stu-id="8f1d6-120">If you do not add text to the annotation box, it disappears when you click outside the box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f1d6-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8f1d6-121">Next Steps</span></span>  
 [<span data-ttu-id="8f1d6-122">步骤 9：测试 Lesson 1 教程包</span><span class="sxs-lookup"><span data-stu-id="8f1d6-122">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
