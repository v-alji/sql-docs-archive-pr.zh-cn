---
title: 任务5：将清理结果导出到 Excel 文件 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dbdc1bef348e03e211e4933132985ea2c089b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589394"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a><span data-ttu-id="6f9f0-102">任务 5：将清理结果导出到 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="6f9f0-102">Task 5: Exporting Cleansing Results to an Excel File</span></span>
  <span data-ttu-id="6f9f0-103">在本任务中，您将清理活动的结果导出到 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-103">In this task, you export results from the cleansing activity to an Excel file.</span></span> <span data-ttu-id="6f9f0-104">有关更多详细信息，请参阅[导出阶段](https://msdn.microsoft.com/library/hh213061.aspx#Export)主题。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-104">See [Export Stage](https://msdn.microsoft.com/library/hh213061.aspx#Export) topic for more details.</span></span>  
  
1.  <span data-ttu-id="6f9f0-105">在右侧窗格中，选择 " **Excel** " 作为**目标类型**。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-105">In the right pane, select **Excel** for the **Destination Type**.</span></span>  
  
2.  <span data-ttu-id="6f9f0-106">单击 "**浏览**"，将输出文件名指定为**清理供应商 List.xls**，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-106">Click **Browse**, specify the output file name as **Cleansed Supplier List.xls**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="6f9f0-107">仅选择 "要导出的**数据**" 作为**输出**格式，以便只导出清理的数据。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-107">Select **Data Only** for the **Output** format to export just the cleansed data.</span></span> <span data-ttu-id="6f9f0-108">第二个选项 "**数据和清理信息**" 允许您导出清理活动详细信息以及清理数据。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-108">The second option, **Data and Cleansing Info**, lets you export cleansing activity details along with the cleansed data.</span></span> <span data-ttu-id="6f9f0-109">使用 "**标准化格式**" 选项，您可以将域中定义的任何输出格式应用于该域的值。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-109">The **Standardize Format** option lets you apply any output formats you define on a domain to the values of that domain.</span></span> <span data-ttu-id="6f9f0-110">在本教程中，您尚未在任何域上定义输出格式。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-110">You have not defined an output format on any domain in the tutorial.</span></span>  
  
     <span data-ttu-id="6f9f0-111">![“导出清理结果”页](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "“导出清理结果”页")</span><span class="sxs-lookup"><span data-stu-id="6f9f0-111">![Export Cleansing Results Page](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Export Cleansing Results Page")</span></span>  
  
4.  <span data-ttu-id="6f9f0-112">单击 "**导出**" 以导出数据。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-112">Click **Export** to export the data.</span></span> <span data-ttu-id="6f9f0-113">不要单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-113">Do not click **Finish** yet.</span></span>  
  
5.  <span data-ttu-id="6f9f0-114">单击 "**导出**" 对话框中的 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-114">Click **Close** on the **Exporting** dialog box.</span></span>  
  
6.  <span data-ttu-id="6f9f0-115">单击 "**完成**" 完成活动。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-115">Click **Finish** to finish the activity.</span></span> <span data-ttu-id="6f9f0-116">如果您在单击 "**完成**" 之前忘了导出结果，请在 " **DQS 客户端**" 的主页中单击 "**打开数据质量项目**"，从项目列表中选择 "**清理供应商列表**"，然后单击屏幕底部的 "**下一步**" 以再次转到清理过程的**导出**阶段。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-116">If you forgot to export results before clicking **Finish**, click **Open Data Quality Project** in the main page of **DQS Client**, select **Cleanse Supplier List** from the list of projects, and click **Next** at the bottom of the screen to get to the **Export** stage of cleansing process again.</span></span> <span data-ttu-id="6f9f0-117">还可以通过单击 "**后退**" 按钮切换到 "**管理和查看结果**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-117">You can also switch to **Manage and View Results** tab by clicking **Back** button.</span></span>  
  
7.  <span data-ttu-id="6f9f0-118">打开**清理供应商 List.xls**并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6f9f0-118">Open the **Cleansed Supplier List.xls** and do the following:</span></span>  
  
    1.  <span data-ttu-id="6f9f0-119">通过在工作表中搜索 adventure-work.com，确保不存在以 adventure-work.com (的电子邮件地址，但没有字符 ' ) 。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-119">Ensure that there are no email addresses that end with adventure-work.com (without character 's') by searching for adventure-work.com in the worksheet.</span></span>  
  
    2.  <span data-ttu-id="6f9f0-120">请注意，"**国家/地区**" 列中没有任何**USA**值。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-120">See that there is no **USA** value in the **Country** column.</span></span>  
  
    3.  <span data-ttu-id="6f9f0-121">搜索洛杉矶 **，并看到**"**状态**" 设置为 " **CA**"。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-121">Search for **Los Angeles** and see that the **State** is set to **CA**.</span></span>  
  
    4.  <span data-ttu-id="6f9f0-122">确认没有术语 " **Co**"、" **Corp**" 和 " **inc.**"。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-122">Confirm that there are no terms **Co.**, **Corp.**, and **Inc.**.</span></span>  
  
    5.  <span data-ttu-id="6f9f0-123">从电子表格中删除**地址验证**列，并保存该 excel 文件。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-123">Delete the **Address Validation** column from the spreadsheet and save the excel file.</span></span> <span data-ttu-id="6f9f0-124">此额外列对应于“地址验证”复合域。</span><span class="sxs-lookup"><span data-stu-id="6f9f0-124">This additional column corresponds to the Address Validation composite domain.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="6f9f0-125">下一步</span><span class="sxs-lookup"><span data-stu-id="6f9f0-125">Next Step</span></span>  
 [<span data-ttu-id="6f9f0-126">任务 6：从 Cleanse Supplier List 项目导入值</span><span class="sxs-lookup"><span data-stu-id="6f9f0-126">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
