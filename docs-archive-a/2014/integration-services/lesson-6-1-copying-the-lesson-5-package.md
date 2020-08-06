---
title: 步骤 1：复制第 5 课包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b30ec927084548a2371f22d857d5302e5dc84c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591481"
---
# <a name="step-1-copying-the-lesson-5-package"></a><span data-ttu-id="e7017-102">步骤 1：复制第 5 课包</span><span class="sxs-lookup"><span data-stu-id="e7017-102">Step 1: Copying the Lesson 5 Package</span></span>
  <span data-ttu-id="e7017-103">在本任务中，您将为第 5 课中创建的 Lesson 5.dtsx 包创建一个副本。</span><span class="sxs-lookup"><span data-stu-id="e7017-103">In this task, you will create a copy of the Lesson 5.dtsx package that you created in Lesson 5.</span></span> <span data-ttu-id="e7017-104">或者将本教程中附带的已完成的 Lesson 5 包添加到项目中，然后再对其进行复制。</span><span class="sxs-lookup"><span data-stu-id="e7017-104">Alternatively, you can add the completed lesson 5 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="e7017-105">您将使用这一新副本来完成第 6 课剩余部分。</span><span class="sxs-lookup"><span data-stu-id="e7017-105">You will use this new copy throughout the rest of Lesson 6.</span></span>  
  
### <a name="to-copy-the-lesson-5-package"></a><span data-ttu-id="e7017-106">复制 Lesson 5 包</span><span class="sxs-lookup"><span data-stu-id="e7017-106">To copy the Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="e7017-107">如果 SQL Server Data Tools 尚未打开，请单击“开始”，依次指向“所有程序”和“Microsoft SQL Server 2012”，然后单击“SQL Server Data Tools”。</span><span class="sxs-lookup"><span data-stu-id="e7017-107">If SQL Server Data Tools is not already open, click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Server Data Tools.</span></span>  
  
2.  <span data-ttu-id="e7017-108">在“文件”菜单中，单击“打开”，单击“项目/解决方案”，选择 SSIS Tutorial，再单击“打开”，然后双击 SSIS Tutorial.sln。</span><span class="sxs-lookup"><span data-stu-id="e7017-108">On the File menu, click Open, click Project/Solution, select SSIS Tutorial and click Open, and then double-click SSIS Tutorial.sln.</span></span>  
  
3.  <span data-ttu-id="e7017-109">在解决方案资源管理器中，右键单击“Lesson 5.dtsx”，然后单击“复制”。</span><span class="sxs-lookup"><span data-stu-id="e7017-109">In Solution Explorer, right-click Lesson 5.dtsx, and then click Copy.</span></span>  
  
4.  <span data-ttu-id="e7017-110">在解决方案资源管理器中，右键单击“SSIS 包”，再单击“粘贴”。</span><span class="sxs-lookup"><span data-stu-id="e7017-110">In Solution Explorer, right-click SSIS Packages, and then click Paste.</span></span>  
  
     <span data-ttu-id="e7017-111">默认情况下，复制的包命名为 Lesson 6.dtsx。</span><span class="sxs-lookup"><span data-stu-id="e7017-111">By default, the copied package is named Lesson 6.dtsx.</span></span>  
  
5.  <span data-ttu-id="e7017-112">在解决方案资源管理器中，双击“Lesson 6.dtsx”打开该包。</span><span class="sxs-lookup"><span data-stu-id="e7017-112">In the Solution Explorer, double-click Lesson 6.dtsx to open the package.</span></span>  
  
6.  <span data-ttu-id="e7017-113">右键单击“控制流”选项卡背景的任意位置，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="e7017-113">Right-click anywhere in the background of the Control Flow tab then click Properties.</span></span>  
  
7.  <span data-ttu-id="e7017-114">在“属性”窗口中，将 Name 属性更新为 Lesson 6。</span><span class="sxs-lookup"><span data-stu-id="e7017-114">In the Properties window, update the Name property to Lesson 6.</span></span>  
  
8.  <span data-ttu-id="e7017-115">依次单击“ID”属性框和下拉箭头，然后单击“ \<Generate New ID>”。</span><span class="sxs-lookup"><span data-stu-id="e7017-115">Click the box for the ID property, then click the dropdown arrow, and then click \<Generate New ID>.</span></span>  
  
### <a name="to-add-the-completed-lesson-5-package"></a><span data-ttu-id="e7017-116">添加已完成的 Lesson 5 包</span><span class="sxs-lookup"><span data-stu-id="e7017-116">To add the completed Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="e7017-117">依次打开 SQL Server Data Tools 和 SSIS Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="e7017-117">Open SQL Server Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="e7017-118">在解决方案资源管理器中，右键单击“SSIS 包”，再单击“添加现有包”。</span><span class="sxs-lookup"><span data-stu-id="e7017-118">In Solution Explorer, right-click SSIS Packages, and click Add Existing Package.</span></span>  
  
3.  <span data-ttu-id="e7017-119">在“添加现有包的副本”对话框的“包位置”中，选择“文件系统”。</span><span class="sxs-lookup"><span data-stu-id="e7017-119">In the Add Copy of Existing Package dialog box, in Package location, select File system.</span></span>  
  
4.  <span data-ttu-id="e7017-120">单击计算机上的 "浏览 ( ..." ) 按钮，.dtsx，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="e7017-120">Click the browse (...) button, Lesson 5.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="e7017-121">要下载此教程的所有课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e7017-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="e7017-122">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="e7017-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="e7017-123">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e7017-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="e7017-124">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="e7017-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="e7017-125">按先前过程中的步骤 3-8 中所述，复制并粘贴 Lesson 5 包。</span><span class="sxs-lookup"><span data-stu-id="e7017-125">Copy and paste the Lesson 5 package as described in steps 3-8 in the previous procedure.</span></span>  
  
     <span data-ttu-id="e7017-126">在复制 Lesson 5 包后，如果当前解决方案中有来自以前课程的包，请右键单击来自课程 1-5 的每个包并单击“从项目中排除”。</span><span class="sxs-lookup"><span data-stu-id="e7017-126">After copying the Lesson 5 package, if you currently have the packages from the previous lessons in your solution, right-click each package from lessons 1-5 and click Exclude From Project.</span></span> <span data-ttu-id="e7017-127">完成后，您的解决方案中应只有 Lesson 6.dtsx。</span><span class="sxs-lookup"><span data-stu-id="e7017-127">When done you should have only Lesson 6.dtsx in your solution.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e7017-128">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="e7017-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e7017-129">步骤 2：将项目转换为项目部署模型</span><span class="sxs-lookup"><span data-stu-id="e7017-129">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
  
