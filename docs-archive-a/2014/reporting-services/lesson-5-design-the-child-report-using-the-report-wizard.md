---
title: 第 5 课：使用报表向导设计子报表 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f188a914fc2a2bb8370843191a31474a54c02aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578707"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="a4f92-102">第 5 课：使用报表向导设计子报表</span><span class="sxs-lookup"><span data-stu-id="a4f92-102">Lesson 5: Design the Child Report using the Report Wizard</span></span>
  <span data-ttu-id="a4f92-103">创建用于子报表的数据连接和数据表后，接下来要使用报表设计器中的报表向导设计子报表。</span><span class="sxs-lookup"><span data-stu-id="a4f92-103">After you create a data connection and data table for the child report, your next step is to design the child report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="a4f92-104">有关报表设计器的详细信息，请参阅[使用报表设计器设计报表 (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a4f92-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="a4f92-105">使用报表向导设计子报表</span><span class="sxs-lookup"><span data-stu-id="a4f92-105">To design the child report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="a4f92-106">确保在“解决方案资源管理器”中选择顶级网站  。</span><span class="sxs-lookup"><span data-stu-id="a4f92-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="a4f92-107">右键单击该网站，然后选择“添加新项”  。</span><span class="sxs-lookup"><span data-stu-id="a4f92-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="a4f92-108">在 "**添加新项**" 对话框中，单击 "**报表向导**"，输入报表文件的名称，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="a4f92-108">In the **Add New Item** dialog box, click **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a4f92-109">随后将启动报表向导。</span><span class="sxs-lookup"><span data-stu-id="a4f92-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="a4f92-110">在 "数据**集属性**" 页的 "**数据源**" 框中，单击**DataSet2**。</span><span class="sxs-lookup"><span data-stu-id="a4f92-110">In the **Dataset Properties** page, in the **Data source** box, click **DataSet2**.</span></span>  
  
     <span data-ttu-id="a4f92-111">随后将自动使用创建的 DataTable 更新“可用数据集”框  。</span><span class="sxs-lookup"><span data-stu-id="a4f92-111">The **Available datasets** box is automatically updated with the DataTable you created.</span></span>  
  
5.  <span data-ttu-id="a4f92-112">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a4f92-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a4f92-113">在“排列字段”页中，执行以下操作  ：</span><span class="sxs-lookup"><span data-stu-id="a4f92-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="a4f92-114">将 ProductID、PurchaseOrderID、PurchaseOrderDetailID、OrderQty、ReceivedQty、RejectedQty 和 StockedQty 从“可用字段”拖到“值”框中          。</span><span class="sxs-lookup"><span data-stu-id="a4f92-114">Drag **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**, and **StockedQty** from **Available Fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="a4f92-115">依次单击\*\*sum (ProductID) \*\*、Sum \*\* (PurchaseOrderID) \*\*、 \*\*sum (PurchaseOrderDetailID) \*\*、 \*\*Sum (OrderQty) \*\*、 \*\*sum (ReceivedQty) \*\*、 **Sum (RejectedQty) **和**sum (StockedQty) **并清除**sum**选项旁边的箭头。</span><span class="sxs-lookup"><span data-stu-id="a4f92-115">Click the arrow next to **Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)**, and **Sum(StockedQty)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="a4f92-116">单击 "**下一步**" 两次，然后单击 "**完成**" 关闭**报表向导**。</span><span class="sxs-lookup"><span data-stu-id="a4f92-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="a4f92-117">现已创建 .rdlc 文件。</span><span class="sxs-lookup"><span data-stu-id="a4f92-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="a4f92-118">随后将在报表设计器中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="a4f92-118">The file opens in Report Designer.</span></span> <span data-ttu-id="a4f92-119">设计图面中现在显示由您设计的 tablix。</span><span class="sxs-lookup"><span data-stu-id="a4f92-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="a4f92-120">打开 .rdlc 文件后，通过执行以下操作添加参数：</span><span class="sxs-lookup"><span data-stu-id="a4f92-120">With the .rdlc file open, add a parameter by doing the following:</span></span>  
  
    1.  <span data-ttu-id="a4f92-121">在 "**报表数据**" 窗格中单击 "**参数**"，然后单击 "**添加参数**"。</span><span class="sxs-lookup"><span data-stu-id="a4f92-121">Click **Parameters** in the **Report Data** pane, and then click **Add Parameters**.</span></span>  
  
    2.  <span data-ttu-id="a4f92-122">在“名称”框中输入“productid”   。</span><span class="sxs-lookup"><span data-stu-id="a4f92-122">Enter **productid** in the **Name** box.</span></span>  
  
    3.  <span data-ttu-id="a4f92-123">确认在“数据类型”列表框中选择了“整数”   。</span><span class="sxs-lookup"><span data-stu-id="a4f92-123">Confirm that **Integer** is selected in the **Data Type** list box.</span></span>  
  
    4.  <span data-ttu-id="a4f92-124">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="a4f92-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="a4f92-125">保存 .rdlc 文件。</span><span class="sxs-lookup"><span data-stu-id="a4f92-125">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="a4f92-126">下一个任务</span><span class="sxs-lookup"><span data-stu-id="a4f92-126">Next Task</span></span>  
 <span data-ttu-id="a4f92-127">您已成功地使用报表向导设计了子报表。</span><span class="sxs-lookup"><span data-stu-id="a4f92-127">You have successfully designed the child report by using the Report Wizard.</span></span> <span data-ttu-id="a4f92-128">接下来，将向网站应用程序添加 ReportViewer 控件。</span><span class="sxs-lookup"><span data-stu-id="a4f92-128">Next, you will add a ReportViewer control to the website application.</span></span>  
  
  
