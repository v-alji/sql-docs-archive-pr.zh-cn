---
title: 步骤 4：将数据流任务添加到包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4fda1de99e9fcaa683f9063e2feb1b71886a5cd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586832"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a><span data-ttu-id="4a7a2-102">步骤 4：将数据流任务添加到包</span><span class="sxs-lookup"><span data-stu-id="4a7a2-102">Step 4: Adding a Data Flow Task to the Package</span></span>
  <span data-ttu-id="4a7a2-103">为源数据和目标数据创建了连接管理器后，下一个任务是在包中添加一个数据流任务。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-103">After you have created the connection managers for the source and destination data, the next task is to add a Data Flow task to your package.</span></span> <span data-ttu-id="4a7a2-104">数据流任务将封装在源和目标之间移动数据的数据流引擎，并提供在移动数据时转换、清除和修改数据的功能。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-104">The Data Flow task encapsulates the data flow engine that moves data between sources and destinations, and provides the functionality for transforming, cleaning, and modifying data as it is moved.</span></span> <span data-ttu-id="4a7a2-105">大部分的数据提取、转换和加载 (ETL) 进程均在数据流任务中完成。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-105">The Data Flow task is where most of the work of an extract, transform, and load (ETL) process occurs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="4a7a2-106">将数据流 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 从控制流中分离出来。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates data flow from control flow.</span></span>  
  
### <a name="to-add-a-data-flow-task"></a><span data-ttu-id="4a7a2-107">添加一个数据流任务</span><span class="sxs-lookup"><span data-stu-id="4a7a2-107">To add a Data Flow task</span></span>  
  
1.  <span data-ttu-id="4a7a2-108">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-108">Click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="4a7a2-109">在“SSIS 工具箱”\*\*\*\* 中，展开“收藏夹”\*\*\*\*，并将一个“数据流任务”\*\*\*\* 拖到“控制流”\*\*\*\* 选项卡的设计图面上。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-109">In the **SSIS Toolbox**, expand **Favorites**, and drag a **Data Flow Task** onto the design surfaceof the **Control Flow** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a7a2-110">如果“SSIS 工具箱”不可用，请在主菜单中依次选择“SSIS”和“SSIS 工具箱”，以显示“SSIS 工具箱”。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-110">If the SSIS Toolbox isn't available, on the main menu select SSIS then SSIS Toolbox to display the SSIS Toolbox.</span></span>  
  
3.  <span data-ttu-id="4a7a2-111">在 "**控制流**" 设计图面上，右键单击新添加的 "数据流**任务**"，单击 "**重命名**"，然后将名称更改为 `Extract Sample Currency Data` 。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-111">On the **Control Flow** design surface, right-click the newly added **Data Flow Task**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
     <span data-ttu-id="4a7a2-112">好的做法是为添加到设计图面的所有组件提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-112">It is good practice to provide unique names to all components that you add to a design surface.</span></span> <span data-ttu-id="4a7a2-113">考虑到易用性和可维护性，名称应说明每个组件执行的功能。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-113">For ease of use and maintainability, the names should describe the function that each component performs.</span></span> <span data-ttu-id="4a7a2-114">按照这些命名指南， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包可以进行自我说明。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-114">Following these naming guidelines allows your [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to be self-documenting.</span></span> <span data-ttu-id="4a7a2-115">另一个说明包的方法是使用批注。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-115">Another way to document your packages is by using annotations.</span></span> <span data-ttu-id="4a7a2-116">有关批注的详细信息，请参阅[在包中使用批注](use-annotations-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-116">For more information about annotations, see [Use Annotations in Packages](use-annotations-in-packages.md).</span></span>  
  
4.  <span data-ttu-id="4a7a2-117">右键单击 "数据流任务"，单击 "**属性**"，然后在 "属性窗口中，验证 `LocaleID` 属性是否设置为"\*\*英语 (美国) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="4a7a2-117">Right-click the Data Flow task, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4a7a2-118">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="4a7a2-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4a7a2-119">步骤 5：添加并配置平面文件源</span><span class="sxs-lookup"><span data-stu-id="4a7a2-119">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="4a7a2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a7a2-120">See Also</span></span>  
 [<span data-ttu-id="4a7a2-121">数据流任务</span><span class="sxs-lookup"><span data-stu-id="4a7a2-121">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
