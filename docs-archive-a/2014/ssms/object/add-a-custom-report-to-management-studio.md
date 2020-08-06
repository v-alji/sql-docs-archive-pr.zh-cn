---
title: 向 Management Studio 添加自定义报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07263edfb9b255257e0c79733c2c34b279b61cd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576511"
---
# <a name="add-a-custom-report-to-management-studio"></a><span data-ttu-id="bad67-102">向 Management Studio 添加自定义报表</span><span class="sxs-lookup"><span data-stu-id="bad67-102">Add a Custom Report to Management Studio</span></span>
  <span data-ttu-id="bad67-103">本主题介绍如何创建简单的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表并将其保存为 .rdl 文件，然后将该 rdl 文件作为自定义报表添加到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="bad67-103">This topic describes how to create a simple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that is saved as an .rdl file, and then add that rdl file to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a custom report.</span></span> [!INCLUDE[ssRS](../../includes/ssrs.md)] <span data-ttu-id="bad67-104">可以创建各式各样的复杂报表。</span><span class="sxs-lookup"><span data-stu-id="bad67-104">can create a wide variety of sophisticated reports.</span></span> <span data-ttu-id="bad67-105">若要根据本主题创建报表，计算机上必须安装有 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bad67-105">To create a report by using this topic, you must have [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] installed on the computer.</span></span> <span data-ttu-id="bad67-106">不必在 [!INCLUDE[ssRS](../../includes/ssrs.md)] 上安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，即可使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]运行自定义报表。</span><span class="sxs-lookup"><span data-stu-id="bad67-106">You do not have to install [!INCLUDE[ssRS](../../includes/ssrs.md)] on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run a custom report using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a><span data-ttu-id="bad67-107">创建保存为 .rdl 文件的简单报表</span><span class="sxs-lookup"><span data-stu-id="bad67-107">To create a simple report saved as an .rdl file</span></span>  
  
1.  <span data-ttu-id="bad67-108">单击“开始”  ，依次指向“程序”  和 “Microsoft SQL Server”  ，然后单击“SQL Server Data Tools”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-108">Click **Start**, point to **Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="bad67-109">在 **“文件”** 菜单上，指向 **“新建”** ，再单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="bad67-109">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="bad67-110">在 **“项目类型”** 列表中，单击 **“商业智能项目”** 。</span><span class="sxs-lookup"><span data-stu-id="bad67-110">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="bad67-111">在“模板”  列表中，单击“报表服务器项目向导”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-111">In the **Templates** list, click **Report Server Project Wizard**.</span></span>  
  
5.  <span data-ttu-id="bad67-112">在“名称”  中键入**ConnectionsReport**，再单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-112">In **Name**, type **ConnectionsReport**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="bad67-113">在“报表向导”  简介页上，单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-113">On the **Report Wizard** introduction page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="bad67-114">在“选择数据源”  页上的“名称”框中，键入与 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的连接名称，再单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-114">On the **Select the Data Source** page, in the Name box type a name for this connection to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Edit**.</span></span>  
  
8.  <span data-ttu-id="bad67-115">在“连接属性”  对话框中的“服务器名称”  框中，键入 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="bad67-115">In the **Connection Properties** dialog box, in the **Server name** box, type the name of your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
9. <span data-ttu-id="bad67-116">在“选择或输入数据库名称”  框中，键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上任意数据库的名称（如 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]），再单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-116">In the **Select or enter a database name** box, type the name of any database on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
10. <span data-ttu-id="bad67-117">在“选择数据源”  页上，单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-117">On the **Select the Data Source** page, click **Next**.</span></span>  
  
11. <span data-ttu-id="bad67-118">在“设计查询”  页上的“查询字符串”  框中，键入以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以列出当前到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的连接，然后单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="bad67-118">On the **Design the Query** page, in the **Query string** box, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that lists the current connections to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span> <span data-ttu-id="bad67-119">报表向导的“查询字符串”框不接受报表参数。</span><span class="sxs-lookup"><span data-stu-id="bad67-119">The Report Wizard Query string box will not accept report parameters.</span></span> <span data-ttu-id="bad67-120">更为复杂的自定义报表必须以手动方式创建。</span><span class="sxs-lookup"><span data-stu-id="bad67-120">More complex custom reports must be created manually.</span></span>  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. <span data-ttu-id="bad67-121">在“选择报表类型”\*\*\*\* 页上，选择“表格”\*\*\*\*，再单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bad67-121">On the **Select the Report Type** page, select **Tabular**, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="bad67-122">在“完成向导”\*\*\*\* 页上的“报表名称”\*\*\*\* 框中，键入 **ConnectionsReport**，再单击“完成”\*\*\*\* 以创建并保存报表。</span><span class="sxs-lookup"><span data-stu-id="bad67-122">On the **Completing the Wizard** page, in the **Report name** box, type **ConnectionsReport**, and then click **Finish** to create and save the report.</span></span>  
  
14. <span data-ttu-id="bad67-123">关闭 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bad67-123">Close [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
15. <span data-ttu-id="bad67-124">将 **ConnectionsReport.rdl** 复制到数据库服务器上为自定义报表创建的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="bad67-124">Copy **ConnectionsReport.rdl** to a folder that you created on the database server for custom reports.</span></span>  
  
### <a name="to-add-a-report-to-management-studio"></a><span data-ttu-id="bad67-125">向 Management Studio 添加报表</span><span class="sxs-lookup"><span data-stu-id="bad67-125">To add a report to Management Studio</span></span>  
  
-   <span data-ttu-id="bad67-126">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，右键单击对象资源管理器中的节点，指向“报表”\*\*\*\*，再单击“自定义报表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bad67-126">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a node in Object Explorer, point to **Reports**, click **Custom Reports**.</span></span> <span data-ttu-id="bad67-127">在“打开文件”\*\*\*\* 对话框中，找到自定义报表文件夹并选择 **ConnectionsReport.rdl** 文件，再单击“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bad67-127">In the **Open File** dialog box, locate the custom reports folder and select the **ConnectionsReport.rdl** file, and then click **Open**.</span></span>  
  
     <span data-ttu-id="bad67-128">第一次从对象资源管理器节点打开新的自定义报表时，该报表将添加到该节点的快捷菜单上“自定义报表”\*\*\*\* 下最近使用的文件列表中。</span><span class="sxs-lookup"><span data-stu-id="bad67-128">When a new custom report is first opened from an Object Explorer node, the custom report is added to the most recently used list under **Custom Reports** on the shortcut menu of that node.</span></span> <span data-ttu-id="bad67-129">第一次打开标准报表时，该报表也将出现在“自定义报表”\*\*\*\* 下最近使用的文件列表中。</span><span class="sxs-lookup"><span data-stu-id="bad67-129">When a standard report is opened for the first time, it will also appear on the most recently used list under **Custom Reports**.</span></span> <span data-ttu-id="bad67-130">如果某个自定义报表文件已删除，则下一次选择该项时，系统将提示您从最近使用的文件列表中删除该项。</span><span class="sxs-lookup"><span data-stu-id="bad67-130">If a custom report file is deleted, the next time that the item is selected, a prompt will appear to delete the item from the most recently used list.</span></span>  
  
    1.  <span data-ttu-id="bad67-131">若要更改最近使用的文件列表中所显示的文件个数，请在“工具”\*\*\*\* 菜单上单击“选项”\*\*\*\*，展开“环境”\*\*\*\* 文件夹，再单击“常规”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bad67-131">To change the number of files that are displayed on the recently used list, on the **Tools** menu, click **Options,** expand the **Environment** folder, and then click **General**.</span></span>  
  
    2.  <span data-ttu-id="bad67-132">调整“显示最近使用列表中的文件”\*\*\*\* 的数量。</span><span class="sxs-lookup"><span data-stu-id="bad67-132">Adjust the number for **Display files in recently used list**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad67-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bad67-133">See Also</span></span>  
 <span data-ttu-id="bad67-134">[Management Studio 中的自定义报表](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="bad67-134">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="bad67-135">[将自定义报表与对象资源管理器节点属性一起使用](use-custom-reports-with-object-explorer-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bad67-135">[Use Custom Reports with Object Explorer Node Properties](use-custom-reports-with-object-explorer-node-properties.md) </span></span>  
 <span data-ttu-id="bad67-136">[取消运行自定义报表警告](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="bad67-136">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="bad67-137">Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="bad67-137">Reporting Services &#40;SSRS&#41;</span></span>](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
