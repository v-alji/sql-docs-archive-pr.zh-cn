---
title: 第 6 课：将 ReportViewer 控件添加到应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb04008fa47801f0500de711592a3cec45ca3dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590576"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="f57a6-102">第 6 课：将 ReportViewer 控件添加到应用程序</span><span class="sxs-lookup"><span data-stu-id="f57a6-102">Lesson 6: Add a ReportViewer Control to the Application</span></span>
  <span data-ttu-id="f57a6-103">使用报表向导设计子报表后，接下来要向网站应用程序添加 ReportViewer 控件。</span><span class="sxs-lookup"><span data-stu-id="f57a6-103">After you design the child report by using the Report Wizard, your next step is to add a ReportViewer control to the website application.</span></span>  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="f57a6-104">向应用程序添加 ReportViewer 控件</span><span class="sxs-lookup"><span data-stu-id="f57a6-104">To add a ReportViewer control to the application</span></span>  
  
1.  <span data-ttu-id="f57a6-105">在“解决方案资源管理器”中，右键单击 Default.aspx，然后单击“视图设计器”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f57a6-105">In **Solution Explorer**, right-click **Default.aspx**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="f57a6-106">从 "**工具箱**" 窗口的 " **AJAX 扩展**" 组中，将一个**ScriptManager**控件拖到设计图面。</span><span class="sxs-lookup"><span data-stu-id="f57a6-106">From the **AJAX Extensions** group in the **Toolbox** window, drag a **ScriptManager** control to the design surface.</span></span>  
  
3.  <span data-ttu-id="f57a6-107">从“报表”组中，将一个 ReportViewer 控件拖到设计图面上的 ScriptManager 控件下\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f57a6-107">From the **Reporting** group, drag a **ReportViewer** control to the design surface below the **ScriptManager** control.</span></span>  
  
4.  <span data-ttu-id="f57a6-108">通过单击 **ReportViewer** 控件右上角的箭头，打开 **ReportViewer Tasks** 窗口。</span><span class="sxs-lookup"><span data-stu-id="f57a6-108">Open the **ReportViewer Tasks** window by clicking the arrow in the top right-hand corner of the **ReportViewer** control.</span></span>  
  
5.  <span data-ttu-id="f57a6-109">在 "**选择报表**" 框中，选择您创建的父报表。</span><span class="sxs-lookup"><span data-stu-id="f57a6-109">In the **Choose Report** box, select Parent report you created.</span></span>  
  
     <span data-ttu-id="f57a6-110">选择某个报表后，将自动创建在该报表中使用的数据源的实例。</span><span class="sxs-lookup"><span data-stu-id="f57a6-110">When you select a report, instances of data sources used in the report are created automatically.</span></span> <span data-ttu-id="f57a6-111">并将生成代码以使每个 DataTable（及其 [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) 容器）实例化。</span><span class="sxs-lookup"><span data-stu-id="f57a6-111">Code is generated to instantiate each DataTable (and its [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) container).</span></span> <span data-ttu-id="f57a6-112">向设计图面添加 [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) 控件，对应于报表中使用的每个数据源。</span><span class="sxs-lookup"><span data-stu-id="f57a6-112">An [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) control is added to the design surface, corresponding to each data source used in the report.</span></span> <span data-ttu-id="f57a6-113">此数据源控件为自动配置。</span><span class="sxs-lookup"><span data-stu-id="f57a6-113">This data source control is configured automatically.</span></span>  
  
     <span data-ttu-id="f57a6-114">如果使用 Microsoft Visual Studio 2012，请确保在 "**选择业务对象**" 下拉列表框中列出了完全限定名称的情况下，使用完全限定了 "项目命名空间" 的 DataSet1 绑定了 ObjectDataSource 控件 (例如，到用 projectnamespace.dataset1tableadapters.producttableadapter) 。</span><span class="sxs-lookup"><span data-stu-id="f57a6-114">If you're using Microsoft Visual Studio 2012, make sure that the ObjectDataSource control is bound with DataSet1 that is fully qualified with the project namespace, if the fully qualified name is listed in the **Choose your business object** drop-down list box (for example, Projectnamespace.DataSet1TableAdapters.ProductTableAdapter).</span></span> <span data-ttu-id="f57a6-115">通过右键单击 "ObjectDataSource"，然后单击 "**配置数据源**"，访问该列表框。</span><span class="sxs-lookup"><span data-stu-id="f57a6-115">You access the list box by right-clicking ObjectDataSource, and then clicking **Configure Data Source**.</span></span>  
  
6.  <span data-ttu-id="f57a6-116">在“生成”菜单上，单击“生成网站”。</span><span class="sxs-lookup"><span data-stu-id="f57a6-116">On the Build menu, click Build website.</span></span>  
  
     <span data-ttu-id="f57a6-117">该报表随即进行编译，并在“错误列表”区域中显示任何错误（例如报表表达式中的语法错误）  。</span><span class="sxs-lookup"><span data-stu-id="f57a6-117">The report is compiled and any errors such as a syntax error in a report expression appear in the **Error List** area.</span></span> <span data-ttu-id="f57a6-118">单击 Visual Studio 窗口底部的“错误列表”以显示“错误列表”区域   。</span><span class="sxs-lookup"><span data-stu-id="f57a6-118">Click **Error List** at the bottom of the Visual Studio window to display the **Error List** area.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="f57a6-119">下一个任务</span><span class="sxs-lookup"><span data-stu-id="f57a6-119">Next Task</span></span>  
 <span data-ttu-id="f57a6-120">您已成功地将 ReportViewer 控件添加到网站应用程序。</span><span class="sxs-lookup"><span data-stu-id="f57a6-120">You have successfully added a ReportViewer control to the website application.</span></span> <span data-ttu-id="f57a6-121">接下来，将在父报表上添加钻取操作。</span><span class="sxs-lookup"><span data-stu-id="f57a6-121">Next, you will add a drillthrough action on the parent report.</span></span>  
  
  
