---
title: 将脚本另存为项目或解决方案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fade3900c8859f211bb0c66820dc97792262481
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690272"
---
# <a name="save-scripts-as-projects-or-solutions"></a><span data-ttu-id="c9782-102">将脚本另存为项目或解决方案</span><span class="sxs-lookup"><span data-stu-id="c9782-102">Save Scripts as Projects or Solutions</span></span>
  <span data-ttu-id="c9782-103">熟悉 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 的开发人员会喜欢使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的解决方案资源管理器。</span><span class="sxs-lookup"><span data-stu-id="c9782-103">Developers familiar with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio will welcome Solution Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c9782-104">您可以将支持您业务的脚本分组为多个脚本项目，然后将各个脚本项目作为一个解决方案进行集中管理。</span><span class="sxs-lookup"><span data-stu-id="c9782-104">The scripts that support your business can be grouped into script projects, and the script projects can be managed together as a solution.</span></span> <span data-ttu-id="c9782-105">将脚本置于脚本项目和解决方案中后，便可将其视为一个组同时打开，或者同时保存到 Visual SourceSafe 之类的源代码管理产品中。</span><span class="sxs-lookup"><span data-stu-id="c9782-105">When scripts are placed in script projects and solutions they can be opened together as a group, or saved together to a source control product such as Visual SourceSafe.</span></span> <span data-ttu-id="c9782-106">脚本项目包括可使脚本正确执行的连接信息，还包括非脚本文件，例如支持文本文件。</span><span class="sxs-lookup"><span data-stu-id="c9782-106">Script projects include the connection information for the scripts to execute properly, and can include non-script files such as a supporting text file.</span></span>  
  
 <span data-ttu-id="c9782-107">以下练习将创建一个可查询 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的短脚本，该脚本被置于脚本项目和解决方案中。</span><span class="sxs-lookup"><span data-stu-id="c9782-107">The following practice creates a short script that queries the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, placed in a script project and solution.</span></span>  
  
## <a name="using-script-projects-and-solutions"></a><span data-ttu-id="c9782-108">使用脚本项目和解决方案</span><span class="sxs-lookup"><span data-stu-id="c9782-108">Using Script Projects and Solutions</span></span>  
  
#### <a name="to-create-a-script-project-and-solution"></a><span data-ttu-id="c9782-109">创建脚本项目和解决方案</span><span class="sxs-lookup"><span data-stu-id="c9782-109">To create a script project and solution</span></span>  
  
1.  <span data-ttu-id="c9782-110">打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，然后使用对象资源管理器连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="c9782-110">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and connect to a server with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="c9782-111">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="c9782-111">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="c9782-112">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="c9782-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="c9782-113">在“名称”\*\*\*\* 文本框中，键入 **StatusCheck**，在“模板”\*\*\*\* 中单击“SQL Server 脚本”\*\*\*\*，再单击“确定”\*\*\*\* 以打开新的解决方案和脚本项目。</span><span class="sxs-lookup"><span data-stu-id="c9782-113">In the **Name** text box, type **StatusCheck**, click **SQL Server Scripts** in **Templates**, and then click **OK** to open a new solution and script project.</span></span>  
  
4.  <span data-ttu-id="c9782-114">在解决方案资源管理器中，右键单击“连接”\*\*\*\*，再单击“新建连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9782-114">In Solution Explorer, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="c9782-115">将打开“连接到服务器”对话框。</span><span class="sxs-lookup"><span data-stu-id="c9782-115">The **Connect to Server** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="c9782-116">在“服务器名称”\*\*\*\* 列表框中，键入服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="c9782-116">In the **Server name** list box, type the name of your server.</span></span>  
  
6.  <span data-ttu-id="c9782-117">单击“选项”\*\*\*\*，再单击“连接属性”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c9782-117">Click **Options**, and then click the **Connection Properties** tab.</span></span>  
  
7.  <span data-ttu-id="c9782-118">在“连接到数据库”\*\*\*\* 框中，浏览服务器，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库，再单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9782-118">In the **Connect to database** box, browse the server, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then click **Connect**.</span></span> <span data-ttu-id="c9782-119">包括数据库的连接信息便添加到了项目中。</span><span class="sxs-lookup"><span data-stu-id="c9782-119">The connection information including the database is added to the project.</span></span>  
  
8.  <span data-ttu-id="c9782-120">如果未显示“属性”窗口，请单击解决方案资源管理器中的新连接，然后按 F4。</span><span class="sxs-lookup"><span data-stu-id="c9782-120">If the Properties window is not displayed, click the new connection in Solution Explorer, and then press F4.</span></span> <span data-ttu-id="c9782-121">连接属性将随即显示，并显示有关连接的信息，其中包括作为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 的“初始数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9782-121">The properties for the connection appear, and show information about the connection including the **Initial Database** as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
9. <span data-ttu-id="c9782-122">在解决方案资源管理器中，右键单击“连接”，再单击“新建查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9782-122">In Solution Explorer, right-click the connection, and then click **New Query**.</span></span> <span data-ttu-id="c9782-123">系统将创建一个名为 **SQLQuery1.sql** 的新查询，该查询连接到你的服务器上的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库并添加到脚本项目中。</span><span class="sxs-lookup"><span data-stu-id="c9782-123">A new query called **SQLQuery1.sql** is created, connected to the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database on your server, and added to your script project.</span></span>  
  
10. <span data-ttu-id="c9782-124">在查询编辑器中，键入以下查询来确定有多少工作订单的结束日期早于开始日期。</span><span class="sxs-lookup"><span data-stu-id="c9782-124">In Query Editor, type the following query to determine how many work orders have due dates, before the work order starting dates.</span></span> <span data-ttu-id="c9782-125">（您可以从“教程”窗口中复制和粘贴代码。）</span><span class="sxs-lookup"><span data-stu-id="c9782-125">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9782-126">如果需要更多的空间来键入查询，请按 Shift+Alt+Enter 切换到全屏显示模式。</span><span class="sxs-lookup"><span data-stu-id="c9782-126">If you need more room to type your query, press SHIFT+ALT+ENTER, to switch to full-screen mode.</span></span>  
  
11. <span data-ttu-id="c9782-127">在解决方案资源管理器中，右键单击 **SQLQuery1**，再单击“重命名”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9782-127">In Solution Explorer, right-click **SQLQuery1**, and then click **Rename**.</span></span> <span data-ttu-id="c9782-128">键入 "检查是否有**sql** " 作为查询的新名称，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="c9782-128">Type **Check Workorders.sql** as the new name for the query and press ENTER.</span></span>  
  
12. <span data-ttu-id="c9782-129">若要保存解决方案和脚本项目，请在“文件”\*\*\*\* 菜单中，单击“全部保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9782-129">To save your solution and script project, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c9782-130">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c9782-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c9782-131">摘要：解决方案和脚本项目</span><span class="sxs-lookup"><span data-stu-id="c9782-131">Summary: Solutions and Script Projects</span></span>](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
