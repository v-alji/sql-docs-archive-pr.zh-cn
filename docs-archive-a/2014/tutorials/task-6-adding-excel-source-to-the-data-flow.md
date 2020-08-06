---
title: 任务6：将 Excel 源添加到数据流 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ae183dee04619a407655026a49b189f7bb3ac6fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589389"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a><span data-ttu-id="8c887-102">任务 6：将 Excel 源添加到数据流</span><span class="sxs-lookup"><span data-stu-id="8c887-102">Task 6: Adding Excel Source to the Data Flow</span></span>
  <span data-ttu-id="8c887-103">在本任务中，您向数据流添加 Excel 源，以便从源 Excel 文件读取供应商数据。</span><span class="sxs-lookup"><span data-stu-id="8c887-103">In this task, you add an Excel Source to the data flow to read supplier data from the source Excel file.</span></span> <span data-ttu-id="8c887-104">Excel 源从 Microsoft Excel 工作簿的工作表或范围中提取数据。</span><span class="sxs-lookup"><span data-stu-id="8c887-104">The Excel Source extracts data from worksheets or ranges in Microsoft Excel workbooks.</span></span> <span data-ttu-id="8c887-105">有关更多详细信息，请参阅[Excel 源](../integration-services/data-flow/excel-source.md)主题。</span><span class="sxs-lookup"><span data-stu-id="8c887-105">See [Excel Source](../integration-services/data-flow/excel-source.md) topic for more details.</span></span>

1.  <span data-ttu-id="8c887-106">将 " **Excel 源**" 从 **"SSIS 工具箱**" 中的**其他源**拖放到 "数据流 **" 选项卡**。</span><span class="sxs-lookup"><span data-stu-id="8c887-106">Drag-drop **Excel Source** from **Other Sources** in **SSIS Toolbox** to the **Data Flow** tab.</span></span>

2.  <span data-ttu-id="8c887-107">右键单击 "数据流 **" 选项卡**中的 " **Excel 源**"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="8c887-107">Right-click on **Excel Source** in the **Data Flow** tab, and click **Rename**.</span></span>

3.  <span data-ttu-id="8c887-108">键入 "**从 Excel 文件读取供应商数据**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="8c887-108">Type **Read Supplier Data from Excel File** and press **ENTER**.</span></span>

4.  <span data-ttu-id="8c887-109">双击 "**从 Excel 文件读取供应商数据**" 以启动 " **excel 源编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8c887-109">Double-click **Read Supplier Data from Excel File** to launch the **Excel Source Editor** dialog box.</span></span>

5.  <span data-ttu-id="8c887-110">在 " **Excel 源编辑器**" 对话框中，单击 "**新建**" 以创建 Excel 连接。</span><span class="sxs-lookup"><span data-stu-id="8c887-110">In the **Excel Source Editor** dialog box, click **New** to create an Excel connection.</span></span>

6.  <span data-ttu-id="8c887-111">在 " **Excel 连接管理器**" 对话框中，单击 "**浏览**"，然后选择**EIM 教程**文件夹中的**Suppliers.xls**文件。</span><span class="sxs-lookup"><span data-stu-id="8c887-111">In the **Excel Connection Manager** dialog box, click **Browse**, and then select the **Suppliers.xls** file in the **EIM Tutorial** folder.</span></span> <span data-ttu-id="8c887-112">确认在 " **Excel 版本**" 框中选择了 " **Microsoft Excel 97-2003** "，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="8c887-112">Confirm that **Microsoft Excel 97-2003** is selected in the **Excel Version** box and then click **OK**.</span></span>

     <span data-ttu-id="8c887-113">![“Excel 连接管理器”对话框](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "“Excel 连接管理器”对话框")</span><span class="sxs-lookup"><span data-stu-id="8c887-113">![Excel Connection Manager Dialog Box](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel Connection Manager Dialog Box")</span></span>

7.  <span data-ttu-id="8c887-114">在 " **Excel 源编辑器**" 对话框中，选择 " **excel 工作表**" 列表框名称中的 " **IncomingSuppliers $** "。</span><span class="sxs-lookup"><span data-stu-id="8c887-114">In the **Excel Source Editor** dialog box, select **IncomingSuppliers$** in the **Name of the Excel sheet** list box.</span></span>

     <span data-ttu-id="8c887-115">![Excel 工作表的名称 - 传入的供应商$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Excel 工作表的名称 - 传入的供应商$")</span><span class="sxs-lookup"><span data-stu-id="8c887-115">![Name of Excel Sheet - Incoming Suppliers$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Name of Excel Sheet - Incoming Suppliers$")</span></span>

8.  <span data-ttu-id="8c887-116">单击 "**预览**" 以预览 Excel 文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="8c887-116">Click **Preview** to preview the data in Excel file.</span></span>

9. <span data-ttu-id="8c887-117">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="8c887-117">Click **OK** to close the dialog box.</span></span>

10. <span data-ttu-id="8c887-118">将 " **SSIS 工具箱**" 中 "**其他转换**" 中的 " **DQS 清理**转换" 拖放到 "**从 Excel 文件读取供应商数据**" 下的 "**数据流**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8c887-118">Drag-drop **DQS Cleansing** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Read Supplier Data from Excel File**.</span></span> <span data-ttu-id="8c887-119">DQS 清理转换将通过 Data Quality Services (DQS) 应用知识库中已批准的规则来更正数据。</span><span class="sxs-lookup"><span data-stu-id="8c887-119">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data by applying approved rules in the knowledge base.</span></span> <span data-ttu-id="8c887-120">此转换在运行时会在 DQS 服务器上创建一个 DQS 清理项目。</span><span class="sxs-lookup"><span data-stu-id="8c887-120">This transform, at runtime, creates a DQS cleansing project on the DQS server.</span></span> <span data-ttu-id="8c887-121">有关更多详细信息，请参阅[DQS 清理转换](https://msdn.microsoft.com/library/ee677619.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="8c887-121">See [DQS Cleansing Transformation](https://msdn.microsoft.com/library/ee677619.aspx) topic for more details.</span></span>

## <a name="next-step"></a><span data-ttu-id="8c887-122">下一步</span><span class="sxs-lookup"><span data-stu-id="8c887-122">Next Step</span></span>

[<span data-ttu-id="8c887-123">任务 7：将 DQS 清理转换添加到数据流</span><span class="sxs-lookup"><span data-stu-id="8c887-123">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>](task-7-adding-dqs-cleansing-transform-to-the-data-flow.md)

### <a name="see-also"></a><span data-ttu-id="8c887-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c887-124">See Also</span></span>

[<span data-ttu-id="8c887-125">数据流</span><span class="sxs-lookup"><span data-stu-id="8c887-125">Data Flow</span></span>](../integration-services/data-flow/data-flow.md)
