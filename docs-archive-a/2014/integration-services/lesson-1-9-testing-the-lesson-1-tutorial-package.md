---
title: 步骤 9：测试第 1 课教程包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff1132489c1683430b1003e88f5037664b11983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586818"
---
# <a name="step-9-testing-the-lesson-1-tutorial-package"></a><span data-ttu-id="db36c-102">步骤 9：测试 Lesson 1 教程包</span><span class="sxs-lookup"><span data-stu-id="db36c-102">Step 9: Testing the Lesson 1 Tutorial Package</span></span>
  <span data-ttu-id="db36c-103">在本课中，已经完成了下列任务：</span><span class="sxs-lookup"><span data-stu-id="db36c-103">In this lesson, you have done the following tasks:</span></span>  
  
-   <span data-ttu-id="db36c-104">创建了一个新的 [!INCLUDE[ssIS](../includes/ssis-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="db36c-104">Created a new [!INCLUDE[ssIS](../includes/ssis-md.md)] project.</span></span>  
  
-   <span data-ttu-id="db36c-105">配置了包连接到源数据和目标数据所需的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="db36c-105">Configured the connection managers that the package needs to connect to the source and destination data.</span></span>  
  
-   <span data-ttu-id="db36c-106">添加了一个数据流，该数据流从平面文件源提取数据，对数据执行必要的查找转换，并为目标配置数据。</span><span class="sxs-lookup"><span data-stu-id="db36c-106">Added a data flow that takes the data from a flat file source, performs the necessary Lookup transformations on the data, and configures the data for the destination.</span></span>  
  
 <span data-ttu-id="db36c-107">包现在已经完成了！</span><span class="sxs-lookup"><span data-stu-id="db36c-107">Your package is now complete!</span></span> <span data-ttu-id="db36c-108">该对包进行测试了。</span><span class="sxs-lookup"><span data-stu-id="db36c-108">It is time to test your package.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="db36c-109">检查包布局</span><span class="sxs-lookup"><span data-stu-id="db36c-109">Checking the Package Layout</span></span>  
 <span data-ttu-id="db36c-110">测试包之前，应当确保 Lesson 1 包中的控制流和数据流包含下列关系图中显示的对象。</span><span class="sxs-lookup"><span data-stu-id="db36c-110">Before you test the package you should verify that the control and data flows in the Lesson 1 package contain the objects shown in the following diagrams.</span></span>  
  
 <span data-ttu-id="db36c-111">**控制流**</span><span class="sxs-lookup"><span data-stu-id="db36c-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="db36c-112">![包中的控制流](../../2014/tutorials/media/task9lesson1control.gif "包中的控制流")</span><span class="sxs-lookup"><span data-stu-id="db36c-112">![Control flow in package](../../2014/tutorials/media/task9lesson1control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="db36c-113">**数据流**</span><span class="sxs-lookup"><span data-stu-id="db36c-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="db36c-114">![包中的数据流](../../2014/tutorials/media/task9lesson1data.gif "包中的数据流")</span><span class="sxs-lookup"><span data-stu-id="db36c-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a><span data-ttu-id="db36c-115">运行 Lesson 1 教程包</span><span class="sxs-lookup"><span data-stu-id="db36c-115">To run the Lesson 1 tutorial package</span></span>  
  
1.  <span data-ttu-id="db36c-116">在“调试”菜单上，单击“开始调试”。</span><span class="sxs-lookup"><span data-stu-id="db36c-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="db36c-117">包将开始运行，结果有 1097 个行被成功添加到 **AdventureWorksDW2012** 中的 **FactCurrency**事实数据表中。</span><span class="sxs-lookup"><span data-stu-id="db36c-117">The package will run, resulting in 1097 rows successfully added into the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span>  
  
2.  <span data-ttu-id="db36c-118">当包运行完毕后，在 **“调试”** 菜单中，单击 **“停止调试”**。</span><span class="sxs-lookup"><span data-stu-id="db36c-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="db36c-119">下一课</span><span class="sxs-lookup"><span data-stu-id="db36c-119">Next Lesson</span></span>  
 [<span data-ttu-id="db36c-120">第 2 课：添加循环</span><span class="sxs-lookup"><span data-stu-id="db36c-120">Lesson 2: Adding Looping</span></span>](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a><span data-ttu-id="db36c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db36c-121">See Also</span></span>  
 [<span data-ttu-id="db36c-122">项目和包的执行</span><span class="sxs-lookup"><span data-stu-id="db36c-122">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
