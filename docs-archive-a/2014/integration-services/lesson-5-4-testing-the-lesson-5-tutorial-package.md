---
title: 步骤 4：测试第 5 课教程包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 76e4692de4daa9ddd6ed0e418bed5cda74ec7650
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579628"
---
# <a name="step-4-testing-the-lesson-5-tutorial-package"></a><span data-ttu-id="a798e-102">步骤 4：测试第 5 课教程包</span><span class="sxs-lookup"><span data-stu-id="a798e-102">Step 4: Testing the Lesson 5 Tutorial Package</span></span>
  <span data-ttu-id="a798e-103">在运行时，包从运行时更新的变量中获取 `Directory` 属性的值，而不是使用在创建包时指定的原始目录名。</span><span class="sxs-lookup"><span data-stu-id="a798e-103">At run time, your package will obtain the value for the `Directory` property from a variable updated at run time, rather than using the original directory name that you specified when you created the package.</span></span> <span data-ttu-id="a798e-104">该变量的值由 SSISTutorial.dtsConfig 文件填充。</span><span class="sxs-lookup"><span data-stu-id="a798e-104">The value of the variable is populated by the SSISTutorial.dtsConfig file.</span></span>  
  
 <span data-ttu-id="a798e-105">若要验证该包在运行时是否使用新值更新了 Directory 属性，只需执行该包。</span><span class="sxs-lookup"><span data-stu-id="a798e-105">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="a798e-106">由于只向新目录中复制了三个示例数据文件，因此该数据流将只运行三次，而不遍历原始文件夹中的 14 个文件。</span><span class="sxs-lookup"><span data-stu-id="a798e-106">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="a798e-107">检查包布局</span><span class="sxs-lookup"><span data-stu-id="a798e-107">Checking the Package Layout</span></span>  
 <span data-ttu-id="a798e-108">测试程序包之前，应确保第 5 课包中的控制流和数据流包含显示在下列关系图中的对象。</span><span class="sxs-lookup"><span data-stu-id="a798e-108">Before you test the package you should verify that the control and data flows in the Lesson 5 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="a798e-109">控制流应与第 4 课中的控制流相同。</span><span class="sxs-lookup"><span data-stu-id="a798e-109">The control flow should be identical to the control flow in lesson 4.</span></span> <span data-ttu-id="a798e-110">数据流应与第 4 课中的数据流相同。</span><span class="sxs-lookup"><span data-stu-id="a798e-110">The data flow should be identical to the data flow in lessons 4.</span></span>  
  
 <span data-ttu-id="a798e-111">**控制流**</span><span class="sxs-lookup"><span data-stu-id="a798e-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="a798e-112">![包中的控制流](../../2014/tutorials/media/task4lesson2control.gif "包中的控制流")</span><span class="sxs-lookup"><span data-stu-id="a798e-112">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="a798e-113">**数据流**</span><span class="sxs-lookup"><span data-stu-id="a798e-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="a798e-114">![包中的数据流](../../2014/tutorials/media/task9lesson1data.gif "包中的数据流")</span><span class="sxs-lookup"><span data-stu-id="a798e-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a><span data-ttu-id="a798e-115">测试 Lesson 5 教程包</span><span class="sxs-lookup"><span data-stu-id="a798e-115">To test the Lesson 5 tutorial package</span></span>  
  
1.  <span data-ttu-id="a798e-116">在“调试”菜单上，单击“开始调试”。</span><span class="sxs-lookup"><span data-stu-id="a798e-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="a798e-117">包完成运行后，在 "**调试**" 菜单上，然后单击 "**停止调试**"。</span><span class="sxs-lookup"><span data-stu-id="a798e-117">After the package has completed running, on the **Debug** menu, and then click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="a798e-118">下一课</span><span class="sxs-lookup"><span data-stu-id="a798e-118">Next Lesson</span></span>  
 [<span data-ttu-id="a798e-119">第 6 课：对项目部署模型使用参数</span><span class="sxs-lookup"><span data-stu-id="a798e-119">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
