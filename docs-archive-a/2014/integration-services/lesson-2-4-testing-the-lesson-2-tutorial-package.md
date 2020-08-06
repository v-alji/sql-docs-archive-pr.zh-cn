---
title: 步骤 4：测试第 2 课教程包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c055f80cbe9e6748b82569204e3a2d82e2f437e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578303"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a><span data-ttu-id="f6028-102">步骤 4：测试第 2 课教程包</span><span class="sxs-lookup"><span data-stu-id="f6028-102">Step 4: Testing the Lesson 2 Tutorial Package</span></span>
  <span data-ttu-id="f6028-103">使用现在配置的 Foreach 循环容器和平面文件连接管理器，Lesson 2 包可以迭代遍历示例数据文件夹中由 14 个平面文件组成的集合。</span><span class="sxs-lookup"><span data-stu-id="f6028-103">With the Foreach Loop container and the Flat File connection manager now configured, the Lesson 2 package can iterate through the collection of 14 flat files in the Sample Data folder.</span></span> <span data-ttu-id="f6028-104">每次找到与指定的文件名条件匹配的文件名时，Foreach 循环容器都将用该文件名填充用户定义的变量。</span><span class="sxs-lookup"><span data-stu-id="f6028-104">Each time a file name is found that matches the specified file name criteria, the Foreach Loop container populates the user-defined variable with the file name.</span></span> <span data-ttu-id="f6028-105">该变量又会更新平面文件连接管理器的 ConnectionString 属性，并与新平面文件建立连接。</span><span class="sxs-lookup"><span data-stu-id="f6028-105">This variable, in turn, updates the ConnectionString property of the Flat File connection manager, and a connection to the new flat file is made.</span></span> <span data-ttu-id="f6028-106">然后，在连接到文件夹中的下一个文件之前，Foreach 循环容器将对新平面文件中的数据运行未修改的数据流任务。</span><span class="sxs-lookup"><span data-stu-id="f6028-106">The Foreach Loop container then runs the unmodified data flow task against the data in the new flat file before connecting to the next file in the folder.</span></span>  
  
 <span data-ttu-id="f6028-107">使用以下过程可以测试已添加到包中的新循环功能。</span><span class="sxs-lookup"><span data-stu-id="f6028-107">Use the following procedure to test the new looping functionality that you have added to your package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6028-108">如果您已运行第 1 课中的包，则在运行本课中的该包之前，您需要从 AdventureWorksDW2012 的 dbo.FactCurrency 中删除记录，否则包将失败，并出现指示主键约束冲突的错误。</span><span class="sxs-lookup"><span data-stu-id="f6028-108">If you ran the package from Lesson 1, you will need to delete the records from dbo.FactCurrency in AdventureWorksDW2012 before you run the package from this lesson or the package will fail with errors indicating a Violation of Primary Key constraint.</span></span> <span data-ttu-id="f6028-109">如果您通过选择“调试”/“启动调试”（或按 F5）来运行包，则由于第 1 课和第 2 课都将运行该包，因此您会收到相同的错误。</span><span class="sxs-lookup"><span data-stu-id="f6028-109">You will receive the same errors if you run the package by selecting Debug/Start Debugging (or press F5) because both Lesson 1 and Lesson 2 will run.</span></span> <span data-ttu-id="f6028-110">第 2 课将尝试插入第 1 课中已插入的记录。</span><span class="sxs-lookup"><span data-stu-id="f6028-110">Lesson 2 will attempt to insert records already inserted in Lesson 1.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="f6028-111">检查包布局</span><span class="sxs-lookup"><span data-stu-id="f6028-111">Checking the Package Layout</span></span>  
 <span data-ttu-id="f6028-112">测试包之前，应当确保第 2 课包中的控制流和数据流包含下列关系图中显示的对象。</span><span class="sxs-lookup"><span data-stu-id="f6028-112">Before you test the package you should verify that the control and data flows in the Lesson 2 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="f6028-113">数据流应与第 1 课中的数据流相同。</span><span class="sxs-lookup"><span data-stu-id="f6028-113">The data flow should be identical to the data flow in lesson 1.</span></span>  
  
 <span data-ttu-id="f6028-114">**控制流**</span><span class="sxs-lookup"><span data-stu-id="f6028-114">**Control Flow**</span></span>  
  
 <span data-ttu-id="f6028-115">![包中的控制流](../../2014/tutorials/media/task4lesson2control.gif "包中的控制流")</span><span class="sxs-lookup"><span data-stu-id="f6028-115">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="f6028-116">**数据流**</span><span class="sxs-lookup"><span data-stu-id="f6028-116">**Data Flow**</span></span>  
  
 <span data-ttu-id="f6028-117">![包中的数据流](../../2014/tutorials/media/task9lesson1data.gif "包中的数据流")</span><span class="sxs-lookup"><span data-stu-id="f6028-117">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a><span data-ttu-id="f6028-118">测试第 2 课教程包</span><span class="sxs-lookup"><span data-stu-id="f6028-118">To test the Lesson 2 tutorial package</span></span>  
  
1.  <span data-ttu-id="f6028-119">在 **“解决方案资源管理器”** 中，右键单击 **“Lesson 2.dtsx”** ，然后单击 **“执行包”**。</span><span class="sxs-lookup"><span data-stu-id="f6028-119">In **Solution Explorer**, right-click **Lesson 2.dtsx** and click **Execute Package**.</span></span>  
  
     <span data-ttu-id="f6028-120">包将运行。</span><span class="sxs-lookup"><span data-stu-id="f6028-120">The package will run.</span></span> <span data-ttu-id="f6028-121">可以在 "输出" 窗口中或通过单击 "**进度**" 选项卡来验证每个循环的状态。例如，可以看到从文件 Currency_VEB.txt 向目标表添加了1097行。</span><span class="sxs-lookup"><span data-stu-id="f6028-121">You can verify the status of each loop in the Output window, or by clicking on the **Progress** tab. For example, you can see that 1097 lines were added to the destination table from the file Currency_VEB.txt.</span></span>  
  
2.  <span data-ttu-id="f6028-122">当包运行完毕后，在 **“调试”** 菜单中，单击 **“停止调试”**。</span><span class="sxs-lookup"><span data-stu-id="f6028-122">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="f6028-123">下一课</span><span class="sxs-lookup"><span data-stu-id="f6028-123">Next Lesson</span></span>  
 [<span data-ttu-id="f6028-124">第 5 课：添加包部署模型的包配置</span><span class="sxs-lookup"><span data-stu-id="f6028-124">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6028-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6028-125">See Also</span></span>  
 [<span data-ttu-id="f6028-126">项目和包的执行</span><span class="sxs-lookup"><span data-stu-id="f6028-126">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
