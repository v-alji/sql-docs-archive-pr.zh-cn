---
title: 任务13：添加 OLE DB 目标以便将数据写入 MDS 临时表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77799782518a3be2441b4c461467e3132781298d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689169"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a><span data-ttu-id="f78ce-102">任务 13：添加 OLE DB 目标以便将数据写入 MDS 临时表</span><span class="sxs-lookup"><span data-stu-id="f78ce-102">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>
  <span data-ttu-id="f78ce-103">将**ImportType**和**BatchTag**值添加到所有记录后，便可以将它们发送到 MDS 进行过渡。</span><span class="sxs-lookup"><span data-stu-id="f78ce-103">Now that you have added **ImportType** and **BatchTag** values to all records, you are ready to send them over to MDS for staging.</span></span> <span data-ttu-id="f78ce-104">在此任务中，将使用 OLE DB 目标将数据写入 stg.<name 临时表中**supplier_Leaf。**</span><span class="sxs-lookup"><span data-stu-id="f78ce-104">In this task, you use the OLE DB Destination to write the data into **stg.supplier_Leaf** staging table.</span></span>  
  
1.  <span data-ttu-id="f78ce-105">将 " **SSIS 工具箱**" 中的 "**其他目标**" **OLE DB "目标**" 拖到 **"数据流" 选项卡**，并将其放在 "**添加 MDS 所需的列**" 下</span><span class="sxs-lookup"><span data-stu-id="f78ce-105">Drag **OLE DB Destination** from **Other Destinations** section in the **SSIS Toolbox** to the **Data Flow** tab and drop it under **Add Columns Required by MDS**.</span></span>  
  
2.  <span data-ttu-id="f78ce-106">右键单击 "**数据流**" 选项卡中**OLE DB "目标**"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="f78ce-106">Right-click **OLE DB Destination** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="f78ce-107">键入 "**将供应商数据写入 MDS 临时表**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="f78ce-107">Type **Write Supplier Data to MDS Staging Table** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="f78ce-108">使用蓝色连接器连接**Mds 所需的 "添加列**" 将**供应商数据写入 mds 临时表**。</span><span class="sxs-lookup"><span data-stu-id="f78ce-108">Connect the **Add Columns Required by MDS** to **Write Supplier Data to MDS Staging Table** using the blue connector.</span></span>  
  
4.  <span data-ttu-id="f78ce-109">双击 **"数据流" 选项**卡上的 "**将供应商数据写入 MDS 临时表**"。</span><span class="sxs-lookup"><span data-stu-id="f78ce-109">Double-click **Write Supplier Data to MDS Staging Table** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="f78ce-110">在 " **OLE DB 目标编辑器**" 对话框中，确保\*\* (本地) \*\* (或**localhost。** 为 " **OLE DB 连接管理器**" 字段选择 MDS) 。</span><span class="sxs-lookup"><span data-stu-id="f78ce-110">In the **OLE DB Destination Editor** Dialog box, make sure that **(local).MDS** (or **localhost.MDS**) is selected for the **OLE DB Connection Manager** field.</span></span>  
  
6.  <span data-ttu-id="f78ce-111">选择**stg.<name。** 从**表或视图的名称**列表中 Supplier_Leaf 表。</span><span class="sxs-lookup"><span data-stu-id="f78ce-111">Select **stg.Supplier_Leaf** table from the list of **Name of the table or the view**.</span></span>  
  
     <span data-ttu-id="f78ce-112">![OLEDB 目标编辑器](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB 目标编辑器")</span><span class="sxs-lookup"><span data-stu-id="f78ce-112">![OLEDB Destination Editor](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB Destination Editor")</span></span>  
  
7.  <span data-ttu-id="f78ce-113">单击左侧菜单上的 "**映射**"，切换到 "**映射**" 页。</span><span class="sxs-lookup"><span data-stu-id="f78ce-113">Switch to the **Mappings** page by clicking **Mapping** on the menu on left.</span></span>  
  
8.  <span data-ttu-id="f78ce-114">映射**输入**列和**目标**列，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="f78ce-114">Map **input** and **destination** columns as shown in the following table.</span></span>  
  
     <span data-ttu-id="f78ce-115">![OLEDB 目标编辑器 - 映射](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB 目标编辑器 - 映射")</span><span class="sxs-lookup"><span data-stu-id="f78ce-115">![OLEDB Destination Editor - Mappings](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB Destination Editor - Mappings")</span></span>  
  
9. <span data-ttu-id="f78ce-116">确认您使用的是输入列 **_Output**列，而不是 **_Status**或 **_Source**列。</span><span class="sxs-lookup"><span data-stu-id="f78ce-116">Confirm that you are using **_Output** columns for Input Columns, not the **_Status** or **_Source** columns.</span></span> <span data-ttu-id="f78ce-117">**_Output**列包含 DQS 清理中的输出值。</span><span class="sxs-lookup"><span data-stu-id="f78ce-117">**_Output** columns contain the output values from DQS Cleansing.</span></span>  
  
10. <span data-ttu-id="f78ce-118">单击 **"确定"** 以关闭 " **OLE DB 目标编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="f78ce-118">Click **OK** to close the **OLE DB Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="f78ce-119">数据流应如下图所示。</span><span class="sxs-lookup"><span data-stu-id="f78ce-119">The data flow should like the following image.</span></span>  
  
     <span data-ttu-id="f78ce-120">![已完成的数据流](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "已完成的数据流")</span><span class="sxs-lookup"><span data-stu-id="f78ce-120">![Completed Data Flow](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Completed Data Flow")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f78ce-121">下一步</span><span class="sxs-lookup"><span data-stu-id="f78ce-121">Next Step</span></span>  
 [<span data-ttu-id="f78ce-122">任务 14：将执行 SQL 任务添加到控制流以运行 MDS 的存储过程</span><span class="sxs-lookup"><span data-stu-id="f78ce-122">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
