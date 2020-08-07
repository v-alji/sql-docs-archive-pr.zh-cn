---
title: 定义维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb7a695ffc2c0588396a4a9ea655983c26cc719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577026"
---
# <a name="defining-a-dimension"></a><span data-ttu-id="a353e-102">定义维度</span><span class="sxs-lookup"><span data-stu-id="a353e-102">Defining a Dimension</span></span>
  <span data-ttu-id="a353e-103">在以下任务中，将使用维度向导生成“日期”维度。</span><span class="sxs-lookup"><span data-stu-id="a353e-103">In the following task, you will use the Dimension Wizard to build a Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a353e-104">本课要求您已完成课程 1 中的所有课程。</span><span class="sxs-lookup"><span data-stu-id="a353e-104">This lesson requires that you have completed all the procedures in Lesson 1.</span></span>  
  
### <a name="to-define-a-dimension"></a><span data-ttu-id="a353e-105">定义维度</span><span class="sxs-lookup"><span data-stu-id="a353e-105">To define a dimension</span></span>  
  
1.  <span data-ttu-id="a353e-106">在解决方案资源管理器中（在 Microsoft Visual Studio 的右侧），右键单击“维度”\*\*\*\* 文件夹，然后单击“新建维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a353e-106">In Solution Explorer (on the right side of Microsoft Visual Studio), right-click **Dimensions**, and then click **New Dimension**.</span></span> <span data-ttu-id="a353e-107">将显示维度向导。</span><span class="sxs-lookup"><span data-stu-id="a353e-107">The Dimension Wizard appears.</span></span>  
  
2.  <span data-ttu-id="a353e-108">在“欢迎使用维度向导”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a353e-108">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="a353e-109">在“选择创建方法”\*\*\*\* 页上，确保选中“使用现有表”\*\*\*\* 选项，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a353e-109">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="a353e-110">在“指定源信息”\*\*\*\* 页上，确保选中“Adventure Works DW 2012”\*\*\*\* 数据源视图。</span><span class="sxs-lookup"><span data-stu-id="a353e-110">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="a353e-111">在“主表”\*\*\*\* 列表中，选择“日期”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a353e-111">In the **Main table** list, select **Date**.</span></span>  
  
6.  <span data-ttu-id="a353e-112">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a353e-112">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="a353e-113">在“选择维度属性”\*\*\*\* 页上，选中下列属性旁的复选框：</span><span class="sxs-lookup"><span data-stu-id="a353e-113">On the **Select Dimension Attributes** page, select the check boxes next to the following attributes:</span></span>  
  
    -   <span data-ttu-id="a353e-114">**日期键**</span><span class="sxs-lookup"><span data-stu-id="a353e-114">**Date Key**</span></span>  
  
    -   <span data-ttu-id="a353e-115">**完整日期备用键**</span><span class="sxs-lookup"><span data-stu-id="a353e-115">**Full Date Alternate Key**</span></span>  
  
    -   <span data-ttu-id="a353e-116">**英文月份名称**</span><span class="sxs-lookup"><span data-stu-id="a353e-116">**English Month Name**</span></span>  
  
    -   <span data-ttu-id="a353e-117">**日历季度**</span><span class="sxs-lookup"><span data-stu-id="a353e-117">**Calendar Quarter**</span></span>  
  
    -   <span data-ttu-id="a353e-118">**日历年**</span><span class="sxs-lookup"><span data-stu-id="a353e-118">**Calendar Year**</span></span>  
  
    -   <span data-ttu-id="a353e-119">**Calendar Semester**</span><span class="sxs-lookup"><span data-stu-id="a353e-119">**Calendar Semester**</span></span>  
  
8.  <span data-ttu-id="a353e-120">将“完整日期备用键”\*\*\*\* 属性的“属性类型”\*\*\*\* 列的设置从“常规”\*\*\*\* 更改为“日期”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a353e-120">Change the setting of the **Full Date Alternate Key** attribute's **Attribute Type** column from **Regular** to **Date**.</span></span> <span data-ttu-id="a353e-121">为此，请单击“属性类型”\*\*\*\* 列中的“常规”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a353e-121">To do this, click **Regular** in the **Attribute Type** column.</span></span> <span data-ttu-id="a353e-122">然后单击箭头展开选项。</span><span class="sxs-lookup"><span data-stu-id="a353e-122">Then click the arrow to expand the options.</span></span> <span data-ttu-id="a353e-123">接下来，单击 "**日期**  >  **日历**  >  **日期**"。</span><span class="sxs-lookup"><span data-stu-id="a353e-123">Next, click **Date** > **Calendar** > **Date**.</span></span> <span data-ttu-id="a353e-124">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="a353e-124">Click **OK**.</span></span> <span data-ttu-id="a353e-125">重复这些步骤，更改属性的属性类型，具体如下所示：</span><span class="sxs-lookup"><span data-stu-id="a353e-125">Repeat these steps to change the attribute type of the attributes as follows:</span></span>  
  
    -   <span data-ttu-id="a353e-126">“英文月份名称”\*\*\*\* 更改为“月份”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a353e-126">**English Month Name** to **Month**</span></span>  
  
    -   <span data-ttu-id="a353e-127">“日历季度”\*\*\*\* 更改为“季度”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a353e-127">**Calendar Quarter** to **Quarter**</span></span>  
  
    -   <span data-ttu-id="a353e-128">“日历年”\*\*\*\* 更改为“年”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a353e-128">**Calendar Year** to **Year**</span></span>  
  
    -   <span data-ttu-id="a353e-129">“日历半期”\*\*\*\* 更改为“半年”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a353e-129">**Calendar Semester** to **Half Year**</span></span>  
  
9. <span data-ttu-id="a353e-130">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a353e-130">Click **Next**.</span></span>  
  
10. <span data-ttu-id="a353e-131">在“完成向导”\*\*\*\* 页的“预览”窗格中，可以看到“日期”\*\*\*\* 维度及其属性。</span><span class="sxs-lookup"><span data-stu-id="a353e-131">On the **Completing the Wizard** page, in the Preview pane, you can see the **Date** dimension and its attributes.</span></span>  
  
11. <span data-ttu-id="a353e-132">单击 **“完成”** 以完成向导。</span><span class="sxs-lookup"><span data-stu-id="a353e-132">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="a353e-133">在解决方案资源管理器的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目中，“日期”维度将在“维度”\*\*\*\* 文件夹中显示。</span><span class="sxs-lookup"><span data-stu-id="a353e-133">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the Date dimension appears in the **Dimensions** folder.</span></span> <span data-ttu-id="a353e-134">在开发环境的中央，维度设计器显示“日期”维度。</span><span class="sxs-lookup"><span data-stu-id="a353e-134">In the center of the development environment, Dimension Designer displays the Date dimension.</span></span>  
  
12. <span data-ttu-id="a353e-135">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="a353e-135">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a353e-136">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="a353e-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a353e-137">定义多维数据集</span><span class="sxs-lookup"><span data-stu-id="a353e-137">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="a353e-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a353e-138">See Also</span></span>  
 <span data-ttu-id="a353e-139">[多维模型中的维度](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a353e-139">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="a353e-140">[使用现有表创建维度](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="a353e-140">[Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="a353e-141">使用维度向导创建维度</span><span class="sxs-lookup"><span data-stu-id="a353e-141">Create a Dimension Using the Dimension Wizard</span></span>](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
