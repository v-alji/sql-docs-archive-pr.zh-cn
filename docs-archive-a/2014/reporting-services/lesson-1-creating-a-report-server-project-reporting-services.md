---
title: 第 1 课：创建报表服务器项目 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a708e5114344e87edd620ef58bc50594a9b9ef8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694295"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a><span data-ttu-id="62594-102">第 1 课：创建报表服务器项目 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="62594-102">Lesson 1: Creating a Report Server Project (Reporting Services)</span></span>
  <span data-ttu-id="62594-103">若要在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中创建报表，必须先创建报表服务器项目以用于保存报表定义 (.rdl) 文件和报表所需的其他所有资源文件。</span><span class="sxs-lookup"><span data-stu-id="62594-103">To create a report in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you must first create a report server project where you will save your report definition (.rdl) file and any other resource files that you need for your report.</span></span> <span data-ttu-id="62594-104">然后，您将创建实际的报表定义文件、定义报表的数据源、定义数据集并定义报表布局。</span><span class="sxs-lookup"><span data-stu-id="62594-104">Then you will create the actual report definition file, define a data source for your report, define a dataset, and define the report layout.</span></span> <span data-ttu-id="62594-105">运行报表时，将检索实际数据并将其与布局相结合，然后呈现在屏幕上，以便执行导出、打印或保存操作。</span><span class="sxs-lookup"><span data-stu-id="62594-105">When you run the report, the actual data is retrieved and combined with the layout, and then rendered on your screen, from where you can export it, print it, or save it.</span></span>  
  
 <span data-ttu-id="62594-106">在本课中，您将学习如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中创建报表服务器项目。</span><span class="sxs-lookup"><span data-stu-id="62594-106">In this lesson, you will learn how to create a report server project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="62594-107">报表服务器项目用于创建在报表服务器中运行的报表。</span><span class="sxs-lookup"><span data-stu-id="62594-107">A report server project is used to create reports that run on a report server.</span></span>  
  
### <a name="to-create-a-report-server-project"></a><span data-ttu-id="62594-108">创建报表服务器项目</span><span class="sxs-lookup"><span data-stu-id="62594-108">To create a report server project</span></span>  
  
1.  <span data-ttu-id="62594-109">单击 "**开始**"，指向 "**所有程序**"，指向 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] ""，然后单击 " **SQL Server Data Tools**"。</span><span class="sxs-lookup"><span data-stu-id="62594-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools**.</span></span> <span data-ttu-id="62594-110">如果这是你首次打开 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，请单击 "默认环境设置" 的 "**商业智能设置**"。</span><span class="sxs-lookup"><span data-stu-id="62594-110">If this is the first time you have opened [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Business Intelligence Settings** for the default environment settings.</span></span>  
  
2.  <span data-ttu-id="62594-111">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="62594-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="62594-112">在“已安装的模板”\*\*\*\* 列表中，单击“商业智能”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62594-112">In the **Installed Templates** list, click **Business Intelligence**.</span></span>  
  
4.  <span data-ttu-id="62594-113">单击 "**报表服务器项目**"。</span><span class="sxs-lookup"><span data-stu-id="62594-113">Click **Report Server Project**.</span></span>  
  
5.  <span data-ttu-id="62594-114">在 "**名称**" 中键入 "**教程**"。</span><span class="sxs-lookup"><span data-stu-id="62594-114">In **Name**, type **Tutorial**.</span></span>  
  
6.  <span data-ttu-id="62594-115">单击“确定”以创建该项目  。</span><span class="sxs-lookup"><span data-stu-id="62594-115">Click **OK** to create the project.</span></span>  
  
     <span data-ttu-id="62594-116">解决方案资源管理器中将显示 Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="62594-116">The Tutorial project is displayed in Solution Explorer.</span></span>  
  
### <a name="to-create-a-new-report-definition-file"></a><span data-ttu-id="62594-117">创建新的报表定义文件</span><span class="sxs-lookup"><span data-stu-id="62594-117">To create a new report definition file</span></span>  
  
1.  <span data-ttu-id="62594-118">在解决方案资源管理器中，右键单击 "**报表**"，指向 "**添加**"，然后单击 "**新建项**"。</span><span class="sxs-lookup"><span data-stu-id="62594-118">In Solution Explorer, right-click **Reports**, point to **Add**, and click **New Item**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62594-119">如果“解决方案资源管理器”\*\*\*\* 窗口不可见，请单击“视图”\*\*\*\* 菜单中的“解决方案资源管理器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62594-119">If the **Solution Explorer** window is not visible, from the **View** menu, click **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="62594-120">在 "**添加新项**" 对话框中的 "**模板**" 下，单击 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="62594-120">In the **Add New Item** dialog box, under **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="62594-121">在“名称” \*\*\*\* 中，键入 **Sales Orders.rdl** ，再单击“添加” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62594-121">In **Name**, type **Sales Orders.rdl** and then click **Add**.</span></span>  
  
     <span data-ttu-id="62594-122">此时报表设计器将打开，并在“设计”视图中显示新的 .rdl 文件。</span><span class="sxs-lookup"><span data-stu-id="62594-122">Report Designer opens and displays the new .rdl file in Design view.</span></span>  
  
 <span data-ttu-id="62594-123">报表设计器是在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中运行的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]组件。</span><span class="sxs-lookup"><span data-stu-id="62594-123">Report Designer is a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] component that runs in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="62594-124">它包含两个视图：“设计” \*\*\*\* 和“预览” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62594-124">It has two views: **Design** and **Preview**.</span></span> <span data-ttu-id="62594-125">单击各个选项卡可更改视图。</span><span class="sxs-lookup"><span data-stu-id="62594-125">Click each tab to change views.</span></span>  
  
 <span data-ttu-id="62594-126">在“报表数据” \*\*\*\* 窗格中定义数据。</span><span class="sxs-lookup"><span data-stu-id="62594-126">You define your data in the **Report Data** pane.</span></span> <span data-ttu-id="62594-127">在“设计” \*\*\*\* 视图中定义报表布局。</span><span class="sxs-lookup"><span data-stu-id="62594-127">You define your report layout in **Design** view.</span></span> <span data-ttu-id="62594-128">可以在“预览” \*\*\*\* 视图中运行报表并查看其外观。</span><span class="sxs-lookup"><span data-stu-id="62594-128">You can run the report and see what it looks like in **Preview** view.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="62594-129">下一个任务</span><span class="sxs-lookup"><span data-stu-id="62594-129">Next Task</span></span>  
 <span data-ttu-id="62594-130">您已经成功创建了名为“Tutorial”的报表项目，并向该报表项目添加了报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="62594-130">You have successfully created a report project called "Tutorial" and added a report definition (.rdl) file to the report project.</span></span> <span data-ttu-id="62594-131">接下来，您将指定要用于报表的数据源。</span><span class="sxs-lookup"><span data-stu-id="62594-131">Next, you will specify a data source to use for the report.</span></span> <span data-ttu-id="62594-132">请参阅[第 2 课：指定连接信息 (Reporting Services)](lesson-2-specifying-connection-information-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="62594-132">See [Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62594-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62594-133">See Also</span></span>  
 [<span data-ttu-id="62594-134">创建基本表报表（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="62594-134">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
