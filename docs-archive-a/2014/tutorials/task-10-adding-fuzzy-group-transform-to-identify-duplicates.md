---
title: 任务10：添加模糊分组转换以确定重复项 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 086625197850fdfd6381e9c0a4a7deac8ce3ae45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689178"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a><span data-ttu-id="42d9d-102">任务 10：添加模糊分组转换以确定重复项</span><span class="sxs-lookup"><span data-stu-id="42d9d-102">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>
  <span data-ttu-id="42d9d-103">在本任务中，您向数据流添加模糊分组转换。</span><span class="sxs-lookup"><span data-stu-id="42d9d-103">In this task, you add a Fuzzy Group Transform to the data flow.</span></span> <span data-ttu-id="42d9d-104">模糊分组转换可有助于标识源数据中的重复项。</span><span class="sxs-lookup"><span data-stu-id="42d9d-104">The Fuzzy Group transformation can help identify duplicates in the source data.</span></span> <span data-ttu-id="42d9d-105">有关更多详细信息，请参阅[模糊分组转换](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="42d9d-105">See [Fuzzy Grouping Transformation](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) for more details.</span></span>  
  
1.  <span data-ttu-id="42d9d-106">将 " **SSIS 工具箱**" 中**其他转换**中的 "**模糊组**转换" 拖放到 **"数据流" 选项卡**下的 "**合并正确和已更正的记录**"。</span><span class="sxs-lookup"><span data-stu-id="42d9d-106">Drag-drop **Fuzzy Group** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Combine Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="42d9d-107">右键单击 **"数据流" 选项卡**中的 "**模糊组**转换"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="42d9d-107">Right-click **Fuzzy Group** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="42d9d-108">键入**组具有匹配 id 的供应商**，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="42d9d-108">Type **Group Suppliers with matching IDs** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="42d9d-109">连接结合使用蓝色连接器将**正确和更正的记录合并**到**具有匹配 Id 的组供应商**。</span><span class="sxs-lookup"><span data-stu-id="42d9d-109">Connect **Combine Correct and Corrected Records** to **Group Suppliers with matching IDs** using the blue connector.</span></span>  
  
     <span data-ttu-id="42d9d-110">![连接到具有匹配 ID 的组供应商](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "连接到具有匹配 ID 的组供应商")</span><span class="sxs-lookup"><span data-stu-id="42d9d-110">![Connection to Group Suppliers with Matching IDs](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Connection to Group Suppliers with Matching IDs")</span></span>  
  
4.  <span data-ttu-id="42d9d-111">双击 "**组具有匹配 id 的供应商**"。</span><span class="sxs-lookup"><span data-stu-id="42d9d-111">Double-click **Group Suppliers with matching IDs**.</span></span>  
  
5.  <span data-ttu-id="42d9d-112">在 "**模糊分组转换编辑器**" 中，单击 " **OLE DB 连接管理器" 下拉列表**旁边的 "**新建**" 以启动 "**配置 OLE DB 连接管理器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="42d9d-112">In the **Fuzzy Group Transformation Editor**, click **New** next to **OLE DB Connection Manager drop-down list** to launch **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
6.  <span data-ttu-id="42d9d-113">在对话框中，单击 "**新建**" 以启动 "**连接管理器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="42d9d-113">In the dialog box, click **New** to launch **Connection Manager** dialog box.</span></span>  
  
7.  <span data-ttu-id="42d9d-114">为服务器名称键入 " \*\* (本地) \*\* " 或 "**句点** (" ) 。</span><span class="sxs-lookup"><span data-stu-id="42d9d-114">Type **(local)** or **period** (.) for the Server name.</span></span>  
  
8.  <span data-ttu-id="42d9d-115">选择 " **MDS** "，**选择或输入数据库名称**字段。</span><span class="sxs-lookup"><span data-stu-id="42d9d-115">Select **MDS** for **Select or enter a database name** field.</span></span> <span data-ttu-id="42d9d-116">将使用 MDS 数据库作为**模糊组转换**的临时存储。</span><span class="sxs-lookup"><span data-stu-id="42d9d-116">You will use the MDS database as the temporary storage for the **Fuzzy Group Transform**.</span></span> <span data-ttu-id="42d9d-117">**模糊分组**转换要求与 SQL Server 的实例建立连接，以创建转换算法完成其工作所需的临时 SQL Server 表。</span><span class="sxs-lookup"><span data-stu-id="42d9d-117">The **Fuzzy Grouping** transformation requires a connection to an instance of SQL Server to create the temporary SQL Server tables that the transformation algorithm requires to do its work.</span></span> <span data-ttu-id="42d9d-118">您可以为此目的创建一个数据库或使用其他现有数据库。</span><span class="sxs-lookup"><span data-stu-id="42d9d-118">You can create a database or use another existing database for this purpose.</span></span>  
  
9. <span data-ttu-id="42d9d-119">单击 "**测试连接**" 以测试连接，然后在消息框上单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="42d9d-119">Click **Test Connection** to test the connection and click **OK** on the message box.</span></span>  
  
10. <span data-ttu-id="42d9d-120">在 "**连接管理器**" 对话框中，单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="42d9d-120">In the **Connection Manager** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="42d9d-121">选择\*\* (本地) \*\* " (或" **localhost "。MDS**) 的**数据连接列表**中，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="42d9d-121">Select **(local).MDS** (or **localhost.MDS**) from the **list of Data Connections** and click **OK**.</span></span>  
  
12. <span data-ttu-id="42d9d-122">在 "**模糊分组转换编辑器**" 中，确认\*\* (本地) \*\* "或" 本地**主机 "。** 选择了 MDS 作为**OLE DB 连接管理器**。</span><span class="sxs-lookup"><span data-stu-id="42d9d-122">In the **Fuzzy Grouping Transformation Editor**, confirm that **(local).MDS** or **localhost.MDS** is selected for the **OLE DB Connection Manager**.</span></span>  
  
13. <span data-ttu-id="42d9d-123">切换到 "**列**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="42d9d-123">Switch to the **Columns** tab.</span></span>  
  
14. <span data-ttu-id="42d9d-124">从**可用输入列**列表中选择 " (" 复选框) " **SupplierID_Output** "。</span><span class="sxs-lookup"><span data-stu-id="42d9d-124">Select (check box) **SupplierID_Output** from the list of **Available Input Columns**.</span></span> <span data-ttu-id="42d9d-125">为了配置该转换，请选择在标识重复项时要使用的输入列。</span><span class="sxs-lookup"><span data-stu-id="42d9d-125">To configure the transformation, select the input columns to use when identifying duplicates.</span></span> <span data-ttu-id="42d9d-126">为简单易懂，您在此步骤中仅使用 SupplierID。</span><span class="sxs-lookup"><span data-stu-id="42d9d-126">To keep it simple, you only use the SupplierID in this step.</span></span>  
  
     <span data-ttu-id="42d9d-127">![模糊分组转换编辑器](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "模糊分组转换编辑器")</span><span class="sxs-lookup"><span data-stu-id="42d9d-127">![Fuzzy Grouping Transformation Editor](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Fuzzy Grouping Transformation Editor")</span></span>  
  
15. <span data-ttu-id="42d9d-128">单击 **"确定"** 以关闭 "**模糊组转换编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="42d9d-128">Click **OK** to close the **Fuzzy Group Transformation Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="42d9d-129">下一步</span><span class="sxs-lookup"><span data-stu-id="42d9d-129">Next Step</span></span>  
 [<span data-ttu-id="42d9d-130">任务 11：添加有条件拆分转换以筛选重复项</span><span class="sxs-lookup"><span data-stu-id="42d9d-130">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
