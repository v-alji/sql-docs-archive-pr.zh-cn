---
title: 步骤 1：复制第 4 课包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1140c0e7d26f11f79e18d42143c1ed084c4ff144
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590913"
---
# <a name="step-1-copying-the-lesson-4-package"></a><span data-ttu-id="c385a-102">步骤 1：复制 Lesson 4 包</span><span class="sxs-lookup"><span data-stu-id="c385a-102">Step 1: Copying the Lesson 4 Package</span></span>
  <span data-ttu-id="c385a-103">在本任务中，将为第 4 课中创建的 Lesson 4.dtsx 包创建一个副本。</span><span class="sxs-lookup"><span data-stu-id="c385a-103">In this task, you will create a copy of the Lesson 4.dtsx package that you created in Lesson 4.</span></span> <span data-ttu-id="c385a-104">或者将本教程中附带的已完成的 Lesson 4 包添加到项目中，然后再对其进行复制。</span><span class="sxs-lookup"><span data-stu-id="c385a-104">Alternatively, you can add the completed lesson 4 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="c385a-105">将使用这一新副本来完成第 5 课剩余部分。</span><span class="sxs-lookup"><span data-stu-id="c385a-105">You will use this new copy throughout the rest of Lesson 5.</span></span>  
  
### <a name="to-copy-the-lesson-4-package"></a><span data-ttu-id="c385a-106">复制 Lesson 4 包</span><span class="sxs-lookup"><span data-stu-id="c385a-106">To copy the Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="c385a-107">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未打开，请单击“开始”\*\*\*\*，依次指向“所有程序”\*\*\*\* 和“Microsoft SQL Server 2012”\*\*\*\*，然后单击“SQL Server Data Tools”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c385a-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="c385a-108">在“文件”\*\*\*\* 菜单中，依次单击“打开”\*\*\*\* 和“项目/解决方案”\*\*\*\*，选择“SSIS Tutorial”\*\*\*\*，单击“打开”\*\*\*\*，然后双击“SSIS Tutorial.sln”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c385a-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="c385a-109">在解决方案资源管理器中，右键单击“Lesson 4.dtsx”\*\*\*\*，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c385a-109">In Solution Explorer, right-click **Lesson 4.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="c385a-110">在解决方案资源管理器中，右键单击 " **SSIS 包**"，然后单击 "**粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="c385a-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="c385a-111">默认情况下，复制的包命名为 Lesson 5.dtsx。</span><span class="sxs-lookup"><span data-stu-id="c385a-111">By default, the copied package is named Lesson 5.dtsx.</span></span>  
  
5.  <span data-ttu-id="c385a-112">在解决方案资源管理器中，双击“Lesson 5.dtsx”\*\*\*\* 打开该包。</span><span class="sxs-lookup"><span data-stu-id="c385a-112">In the Solution Explorer, double-click **Lesson 5.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="c385a-113">右键单击 "**控制流**" 选项卡背景中的任意位置，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="c385a-113">Right-click anywhere in the background of the **Control Flow** tab then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="c385a-114">在属性窗口中，将 `Name` 属性更新为 `Lesson 5` 。</span><span class="sxs-lookup"><span data-stu-id="c385a-114">In the Properties window, update the `Name` property to `Lesson 5`.</span></span>  
  
8.  <span data-ttu-id="c385a-115">单击**ID**属性的框，然后单击下拉箭头，然后单击 **\<Generate New ID>** 。</span><span class="sxs-lookup"><span data-stu-id="c385a-115">Click the box for the **ID** property, then click the dropdown arrow, and then click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-4-package"></a><span data-ttu-id="c385a-116">添加已完成的 Lesson 4 包</span><span class="sxs-lookup"><span data-stu-id="c385a-116">To add the completed Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="c385a-117">依次打开 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 和 SSIS Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="c385a-117">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="c385a-118">在解决方案资源管理器中，右键单击 " **SSIS 包**"，然后单击 "**添加现有包**"。</span><span class="sxs-lookup"><span data-stu-id="c385a-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="c385a-119">在“添加现有包的副本”  对话框的“包位置”  中，选择“文件系统”  。</span><span class="sxs-lookup"><span data-stu-id="c385a-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="c385a-120">单击 "浏览\*\* ( ..." ) **按钮，导航到计算机上的**第 .dtsx 课**，并单击 "**打开\*\*"。</span><span class="sxs-lookup"><span data-stu-id="c385a-120">Click the browse **(...)** button, navigate to **Lesson 4.dtsx** on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="c385a-121">要下载此教程的所有课程包，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c385a-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="c385a-122">导航到 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="c385a-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="c385a-123">单击 "**下载**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c385a-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="c385a-124">单击 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="c385a-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="c385a-125">按先前过程中的步骤 3-8 中所述，复制并粘贴 Lesson 4 包。</span><span class="sxs-lookup"><span data-stu-id="c385a-125">Copy and paste the Lesson 4 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c385a-126">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c385a-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c385a-127">步骤 2：启用和配置包配置</span><span class="sxs-lookup"><span data-stu-id="c385a-127">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
  
