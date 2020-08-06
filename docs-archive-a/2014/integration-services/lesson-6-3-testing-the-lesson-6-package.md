---
title: 步骤 3：测试第 6 课包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3c7ab82e9b04fe0752252102374f745e311d830d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691799"
---
# <a name="step-3-testing-the-lesson-6-package"></a><span data-ttu-id="3ea2b-102">步骤 3：测试 Lesson 6 包</span><span class="sxs-lookup"><span data-stu-id="3ea2b-102">Step 3: Testing the Lesson 6 Package</span></span>
  <span data-ttu-id="3ea2b-103">在运行时，包从 VarFolderName 参数获取 Directory 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-103">At run time, your package will obtain the value for the Directory property from the VarFolderName parameter.</span></span>  
  
 <span data-ttu-id="3ea2b-104">若要验证该包在运行时是否使用新值更新了 Directory 属性，只需执行该包。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-104">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="3ea2b-105">由于只向新目录中复制了三个示例数据文件，因此该数据流将只运行三次，而不遍历原始文件夹中的 14 个文件。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-105">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="3ea2b-106">检查包布局</span><span class="sxs-lookup"><span data-stu-id="3ea2b-106">Checking the Package Layout</span></span>  
 <span data-ttu-id="3ea2b-107">测试包之前，应当确保 Lesson 6 包中的控制流和数据流包含下列关系图中显示的对象。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-107">Before you test the package you should verify that the control and data flows in the Lesson 6 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="3ea2b-108">控制流应与第 5 课中的控制流相同。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-108">The control flow should be identical to the control flow in lesson 5.</span></span> <span data-ttu-id="3ea2b-109">数据流应与第 5 课中的数据流相同。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-109">The data flow should be identical to the data flow in lesson 5.</span></span>  
  
 <span data-ttu-id="3ea2b-110">**控制流**</span><span class="sxs-lookup"><span data-stu-id="3ea2b-110">**Control Flow**</span></span>  
  
 <span data-ttu-id="3ea2b-111">![控制流](../../2014/tutorials/media/task3lesson6control.jpg "控制流")</span><span class="sxs-lookup"><span data-stu-id="3ea2b-111">![Control Flow](../../2014/tutorials/media/task3lesson6control.jpg "Control Flow")</span></span>  
  
 <span data-ttu-id="3ea2b-112">**数据流**</span><span class="sxs-lookup"><span data-stu-id="3ea2b-112">**Data Flow**</span></span>  
  
 <span data-ttu-id="3ea2b-113">![数据流](../../2014/tutorials/media/task3lesson6data.jpg "数据流")</span><span class="sxs-lookup"><span data-stu-id="3ea2b-113">![Data Flow](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")</span></span>  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a><span data-ttu-id="3ea2b-114">测试第 6 课教程包</span><span class="sxs-lookup"><span data-stu-id="3ea2b-114">TO test the Lesson 6 tutorial package</span></span>  
  
1.  <span data-ttu-id="3ea2b-115">在“调试”菜单上，单击“启动调试”。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-115">On the Debug menu, click Start Debugging.</span></span>  
  
2.  <span data-ttu-id="3ea2b-116">该包运行完成后，请在“调试”菜单上单击“停止调试”。</span><span class="sxs-lookup"><span data-stu-id="3ea2b-116">After the package has completed running, on the Debug menu, and then click Stop Debugging.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3ea2b-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="3ea2b-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3ea2b-118">步骤 4：部署第 6 课包</span><span class="sxs-lookup"><span data-stu-id="3ea2b-118">Step 4: Deploying the Lesson 6 Package</span></span>](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
