---
title: 步骤 1：复制第 3 课包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fde3bd907e8a55b1ac9a164b2960268189b19392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581371"
---
# <a name="step-1-copying-the-lesson-3-package"></a><span data-ttu-id="7a94f-102">步骤 1：复制 Lesson 3 包</span><span class="sxs-lookup"><span data-stu-id="7a94f-102">Step 1: Copying the Lesson 3 Package</span></span>
  <span data-ttu-id="7a94f-103">在本任务中，将为第 3 课中创建的 Lesson 3.dtsx 包创建一个副本。</span><span class="sxs-lookup"><span data-stu-id="7a94f-103">In this task, you will create a copy of the Lesson 3.dtsx package that you created in Lesson 3.</span></span> <span data-ttu-id="7a94f-104">或者，如果未完成第 3 课，则可以向项目添加本教程中附带的已完成的第 3 课包，然后再对其进行复制以供使用。</span><span class="sxs-lookup"><span data-stu-id="7a94f-104">Alternatively, if you did not complete lesson 3, you can add the completed lesson 3 package that is included with the tutorial to the project, and then make a copy of it to work with.</span></span> <span data-ttu-id="7a94f-105">将使用这一新副本来完成第 4 课剩余部分。</span><span class="sxs-lookup"><span data-stu-id="7a94f-105">You will use this new copy throughout the rest of Lesson 4.</span></span>  
  
### <a name="to-create-the-lesson-4-package"></a><span data-ttu-id="7a94f-106">创建 Lesson 4 包</span><span class="sxs-lookup"><span data-stu-id="7a94f-106">To create the Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="7a94f-107">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未打开，请单击“开始”\*\*\*\*，依次指向“所有程序”\*\*\*\* 和“Microsoft SQL Server”\*\*\*\*，然后单击“SQL Server Data Tools”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a94f-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="7a94f-108">在“文件”\*\*\*\* 菜单中，依次单击“打开”\*\*\*\* 和“项目/解决方案”\*\*\*\*，选择“SSIS Tutorial”\*\*\*\*，单击“打开”\*\*\*\*，然后双击“SSIS Tutorial.sln”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a94f-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="7a94f-109">在解决方案资源管理器中，右键单击“Lesson 3.dtsx”\*\*\*\*，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a94f-109">In Solution Explorer, right-click **Lesson 3.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="7a94f-110">在解决方案资源管理器中，右键单击 " **SSIS 包**"，然后单击 "**粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="7a94f-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="7a94f-111">默认情况下，复制的包命名为 Lesson 4.dtsx。</span><span class="sxs-lookup"><span data-stu-id="7a94f-111">By default, the copied package is named Lesson 4.dtsx.</span></span>  
  
5.  <span data-ttu-id="7a94f-112">在解决方案资源管理器中，双击 " **.dtsx** " 以打开包。</span><span class="sxs-lookup"><span data-stu-id="7a94f-112">In Solution Explorer, double-click **Lesson 4.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="7a94f-113">右键单击“控制流”\*\*\*\* 选项卡背景的任意位置，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a94f-113">Right-click anywhere in the background of the **Control Flow** tab and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="7a94f-114">在属性窗口中，将 `Name` 属性更新为 `Lesson 4` 。</span><span class="sxs-lookup"><span data-stu-id="7a94f-114">In the Properties window, update the `Name` property to `Lesson 4`.</span></span>  
  
8.  <span data-ttu-id="7a94f-115">单击“ID”\*\*\*\* 属性框，然后在列表中，单击“\<Generate New ID>”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a94f-115">Click the box for the **ID** property, and then in the list, click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-3-package"></a><span data-ttu-id="7a94f-116">添加已完成的 Lesson 3 包</span><span class="sxs-lookup"><span data-stu-id="7a94f-116">To add the completed Lesson 3 package</span></span>  
  
1.  <span data-ttu-id="7a94f-117">依次打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 SSIS Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="7a94f-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="7a94f-118">在解决方案资源管理器中，右键单击 " **SSIS 包**"，然后单击 "**添加现有包**"。</span><span class="sxs-lookup"><span data-stu-id="7a94f-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="7a94f-119">在“添加现有包的副本”  对话框的“包位置”  中，选择“文件系统”  。</span><span class="sxs-lookup"><span data-stu-id="7a94f-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="7a94f-120">单击 "浏览\*\* ( ..." ) **按钮，导航到计算机上的第 .dtsx 课，并单击 "**打开\*\*"。</span><span class="sxs-lookup"><span data-stu-id="7a94f-120">Click the browse **(...)** button, navigate to Lesson 3.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="7a94f-121">要下载此教程的所有课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7a94f-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="7a94f-122">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="7a94f-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="7a94f-123">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7a94f-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="7a94f-124">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="7a94f-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="7a94f-125">按先前过程中的步骤 3-8 中所述，复制并粘贴 Lesson 3 包。</span><span class="sxs-lookup"><span data-stu-id="7a94f-125">Copy and paste the Lesson 3 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7a94f-126">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="7a94f-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7a94f-127">步骤 2：创建损坏的文件</span><span class="sxs-lookup"><span data-stu-id="7a94f-127">Step 2: Creating a Corrupted File</span></span>](lesson-4-2-creating-a-corrupted-file.md)  
  
  