---
title: 步骤 1：复制第 1 课包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e117d82983bdaca8959fe7af8940d248ded97b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586808"
---
# <a name="step-1-copying-the-lesson-1-package"></a><span data-ttu-id="57434-102">步骤 1：复制 Lesson 1 包</span><span class="sxs-lookup"><span data-stu-id="57434-102">Step 1: Copying the Lesson 1 Package</span></span>
  <span data-ttu-id="57434-103">在本任务中，将为第 1 课中创建的 Lesson 1.dtsx 包创建一个副本。</span><span class="sxs-lookup"><span data-stu-id="57434-103">In this task, you will create a copy of the Lesson 1.dtsx package that you created in Lesson 1.</span></span> <span data-ttu-id="57434-104">如果未完成第 1 课的学习，则可以向项目添加本教程中附带的已完成 Lesson 1 包，然后再对其进行复制。</span><span class="sxs-lookup"><span data-stu-id="57434-104">If you did not complete Lesson 1, you can add the completed lesson 1 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="57434-105">将使用这一新副本来完成第 2 课剩余部分。</span><span class="sxs-lookup"><span data-stu-id="57434-105">You will use this new copy throughout the rest of Lesson 2.</span></span>  
  
### <a name="to-create-the-lesson-2-package"></a><span data-ttu-id="57434-106">创建 Lesson 2 包</span><span class="sxs-lookup"><span data-stu-id="57434-106">To create the Lesson 2 package</span></span>  
  
1.  <span data-ttu-id="57434-107">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未打开，请单击“开始”\*\*\*\*，依次指向“所有程序”\*\*\*\* 和“Microsoft SQL Server 2012”\*\*\*\*，然后单击“SQL Server Data Tools”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="57434-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="57434-108">在“文件”\*\*\*\* 菜单中，依次单击“打开”\*\*\*\*、“项目/解决方案”\*\*\*\*、“SSIS Tutorial”\*\*\*\* 文件夹，然后再次单击“打开”\*\*\*\*，最后双击“SSIS Tutorial.sln”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="57434-108">On the **File** menu, click **Open**, click **Project/Solution**, click the **SSIS Tutorial** folder and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="57434-109">在解决方案资源管理器中，右键单击“Lesson 1.dtsx”\*\*\*\*，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="57434-109">In Solution Explorer, right-click **Lesson 1.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="57434-110">在解决方案资源管理器中，右键单击 " **SSIS 包**"，然后单击 "**粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="57434-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="57434-111">默认情况下，复制的包将命名为 Lesson 2.dtsx。</span><span class="sxs-lookup"><span data-stu-id="57434-111">By default, the copied package will be named Lesson 2.dtsx.</span></span>  
  
5.  <span data-ttu-id="57434-112">在解决方案资源管理器中，双击 " **.dtsx** " 以打开包</span><span class="sxs-lookup"><span data-stu-id="57434-112">In Solution Explorer, double-click **Lesson 2.dtsx** to open the package</span></span>  
  
6.  <span data-ttu-id="57434-113">右键单击“控制流”\*\*\*\* 设计图面背景的任意位置，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="57434-113">Right-click anywhere in the background of the **Control Flow** design surface and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="57434-114">在属性窗口中，将 `Name` 属性更新为 `Lesson 2` 。</span><span class="sxs-lookup"><span data-stu-id="57434-114">In the Properties window, update the `Name` property to `Lesson 2`.</span></span>  
  
8.  <span data-ttu-id="57434-115">依次单击“ID”\*\*\*\* 属性框和下拉箭头，然后单击“\<Generate New ID>”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="57434-115">Click the box for the **ID** property, click the dropdown arrow and then click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-1-package"></a><span data-ttu-id="57434-116">添加已完成的 Lesson 1 包</span><span class="sxs-lookup"><span data-stu-id="57434-116">To add the completed Lesson 1 package</span></span>  
  
1.  <span data-ttu-id="57434-117">依次打开 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 和 SSIS Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="57434-117">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="57434-118">在解决方案资源管理器中，右键单击 " **SSIS 包**"，然后单击 "**添加现有包**"。</span><span class="sxs-lookup"><span data-stu-id="57434-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="57434-119">在“添加现有包的副本”  对话框的“包位置”  中，选择“文件系统”  。</span><span class="sxs-lookup"><span data-stu-id="57434-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="57434-120">单击“浏览(…)”按钮，导航到计算机上的“Lesson 1.dtsx”，然后单击“打开”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="57434-120">Click the browse **(...)** button, navigate to **Lesson 1.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="57434-121">要下载此教程的所有课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="57434-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="57434-122">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="57434-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="57434-123">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="57434-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="57434-124">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="57434-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="57434-125">按先前过程中的步骤 3-8 中所述，复制并粘贴 Lesson 1 包。</span><span class="sxs-lookup"><span data-stu-id="57434-125">Copy and paste the Lesson 1 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="57434-126">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="57434-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="57434-127">步骤 2：添加和配置 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="57434-127">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
  
