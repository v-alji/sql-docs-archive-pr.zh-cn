---
title: 第 3 课：使用报表向导设计父报表 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3cb6a0972a2bb63e82e80c02b3ce90912ba01c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578713"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="00f45-102">第 3 课：使用报表向导设计父报表</span><span class="sxs-lookup"><span data-stu-id="00f45-102">Lesson 3: Design the Parent Report using the Report Wizard</span></span>
  <span data-ttu-id="00f45-103">创建用于父报表的数据连接和数据表后，接下来要使用报表设计器中的报表向导设计父报表。</span><span class="sxs-lookup"><span data-stu-id="00f45-103">After you create a data connection and a data table for the parent report, your next step is to design the parent report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="00f45-104">有关报表设计器的详细信息，请参阅[使用报表设计器设计报表 (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="00f45-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="00f45-105">使用报表向导设计父报表</span><span class="sxs-lookup"><span data-stu-id="00f45-105">To design the parent report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="00f45-106">确保在“解决方案资源管理器”中选择顶级网站  。</span><span class="sxs-lookup"><span data-stu-id="00f45-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="00f45-107">右键单击该网站，然后选择“添加新项”  。</span><span class="sxs-lookup"><span data-stu-id="00f45-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="00f45-108">在 "**添加新项**" 对话框中，选择 "**报表向导**"，输入报表文件的名称，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="00f45-108">In the **Add New Item** dialog box, select **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="00f45-109">随后将启动报表向导。</span><span class="sxs-lookup"><span data-stu-id="00f45-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="00f45-110">在“数据集属性”页上的“数据源”框中，选择在[第 2 课：定义用于父报表的数据连接和数据表](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)中创建的 DataSet1  。</span><span class="sxs-lookup"><span data-stu-id="00f45-110">On the **Dataset Properties** page, in the **Data source** box, select the **DataSet1** you created in [Lesson 2: Define a Data Connection and Data Table for Parent Report](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).</span></span>  
    <span data-ttu-id="00f45-111">随后将自动用你在上面创建的 DataTable 更新“可用数据集”框   。</span><span class="sxs-lookup"><span data-stu-id="00f45-111">The **Available datasets** box is automatically updated with the **DataTable** you created above.</span></span>  
  
5.  <span data-ttu-id="00f45-112">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="00f45-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="00f45-113">在“排列字段”页中，执行以下操作  ：</span><span class="sxs-lookup"><span data-stu-id="00f45-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="00f45-114">将“ProductID”、“Name”、“ProductNumber”、“SafetyStockLevel”和“ReorderLevel”从“可用字段”拖至“值”框中        。</span><span class="sxs-lookup"><span data-stu-id="00f45-114">Drag **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**, and **ReorderLevel** from **Available fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="00f45-115">单击\*\*sum (ProductID) \*\*， \*\*sum (SafetyStockLevel) \*\*， **sum (ReorderLevel) **并清除**sum**选项旁边的箭头。</span><span class="sxs-lookup"><span data-stu-id="00f45-115">Click the arrow next to **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="00f45-116">单击 "**下一步**" 两次，然后单击 "**完成**" 关闭**报表向导**。</span><span class="sxs-lookup"><span data-stu-id="00f45-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="00f45-117">现已创建 .rdlc 文件。</span><span class="sxs-lookup"><span data-stu-id="00f45-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="00f45-118">随后将在报表设计器中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="00f45-118">The file opens in Report Designer.</span></span> <span data-ttu-id="00f45-119">设计图面中现在显示由您设计的 tablix。</span><span class="sxs-lookup"><span data-stu-id="00f45-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="00f45-120">保存 .rdlc 文件。</span><span class="sxs-lookup"><span data-stu-id="00f45-120">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="00f45-121">下一个任务</span><span class="sxs-lookup"><span data-stu-id="00f45-121">Next Task</span></span>  
 <span data-ttu-id="00f45-122">您已成功地使用报表向导设计了父报表。</span><span class="sxs-lookup"><span data-stu-id="00f45-122">You have successfully designed the parent report using the Report Wizard.</span></span> <span data-ttu-id="00f45-123">接下来，将创建用于子报表的数据连接和数据表。</span><span class="sxs-lookup"><span data-stu-id="00f45-123">Next, you will create a data connection and a data table for the child report.</span></span>  
  
  
