---
title: 任务12：添加派生列转换以添加 MDS 所需的列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a4a70dd4d288e425beb2821f6b2aaf440b1d1930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690914"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a><span data-ttu-id="b1e07-102">任务 12：添加派生列转换以添加 MDS 所需的列</span><span class="sxs-lookup"><span data-stu-id="b1e07-102">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>
  <span data-ttu-id="b1e07-103">在本任务中，您将向数据流添加派生列转换。</span><span class="sxs-lookup"><span data-stu-id="b1e07-103">In this task, you add the Derive Column Transform to the data flow.</span></span> <span data-ttu-id="b1e07-104">将两个派生列**ImportType**和**BatchTag**添加到传递给此转换的记录。</span><span class="sxs-lookup"><span data-stu-id="b1e07-104">You add two derived columns, **ImportType** and **BatchTag**, to the records passed to this transform.</span></span> <span data-ttu-id="b1e07-105">您应该在将数据上载到 MDS 中的临时表之前添加这些列。</span><span class="sxs-lookup"><span data-stu-id="b1e07-105">You should add these columns before uploading the data to staging tables in MDS.</span></span> <span data-ttu-id="b1e07-106">这两列是 MDS 中的临时表所必需的列。</span><span class="sxs-lookup"><span data-stu-id="b1e07-106">These two are required columns for the staging tables in MDS.</span></span> <span data-ttu-id="b1e07-107">有关更多详细信息，请参阅[叶成员临时表](../master-data-services/leaf-member-staging-table-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e07-107">See [Leaf Member Staging Tables](../master-data-services/leaf-member-staging-table-master-data-services.md) for more details.</span></span>  
  
1.  <span data-ttu-id="b1e07-108">将从 " **SSIS 工具箱**" 中的 "**公共**" 部分拖放到 **"数据流" 选项卡**的**派生列转换**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-108">Drag-drop **Derived Column transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="b1e07-109">右键**单击 "数据流**" 选项卡中的 "**派生列**转换"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="b1e07-109">Right-click **Derived Column** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="b1e07-110">键入 "**添加 MDS 所需的列**"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-110">Type **Add Columns Required by MDS** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="b1e07-111">使用蓝色连接器连接**筛选器重复项**以**添加 MDS 所需的列**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-111">Connect **Filter Duplicates** to **Add Columns Required by MDS** using the blue connector.</span></span> <span data-ttu-id="b1e07-112">应会看到 "**输入输出选择**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b1e07-112">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="b1e07-113">在 "**输入输出选择**" 对话框中，选择 "**唯一记录**"，并单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-113">In the **Input Output Selection** dialog box, select **Unique Records**, and click **OK**.</span></span>  
  
     <span data-ttu-id="b1e07-114">![“选择输入输出”对话框](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "“选择输入输出”对话框")</span><span class="sxs-lookup"><span data-stu-id="b1e07-114">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="b1e07-115">单击菜单栏上的 " **SSIS** "，然后单击 "**变量**"。</span><span class="sxs-lookup"><span data-stu-id="b1e07-115">Click **SSIS** on the menu bar and click **Variables**.</span></span>  
  
6.  <span data-ttu-id="b1e07-116">在 "**变量**" 窗口中，单击工具栏上的 "**添加变量**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b1e07-116">In the **Variables** window, click **Add Variable** button on the toolbar.</span></span>  
  
     <span data-ttu-id="b1e07-117">![SSIS 变量窗口](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS 变量窗口")</span><span class="sxs-lookup"><span data-stu-id="b1e07-117">![SSIS Variables Window](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS Variables Window")</span></span>  
  
7.  <span data-ttu-id="b1e07-118">键入**ImportType**作为**名称**，键入**2**作为**值**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-118">Type **ImportType** for the **Name** and **2** for the **value**.</span></span> <span data-ttu-id="b1e07-119">您将该值指定为 2，因为您想要向 MDS 中的实体添加新成员。</span><span class="sxs-lookup"><span data-stu-id="b1e07-119">You specify the value as 2 because you want to add new members to an entity in MDS.</span></span> <span data-ttu-id="b1e07-120">有关此参数的详细信息，请参阅[叶成员临时表](../master-data-services/leaf-member-staging-table-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e07-120">For details about this parameter, see [Leaf Member Staging Table](../master-data-services/leaf-member-staging-table-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="b1e07-121">再次单击 "**添加变量**" 工具栏按钮。</span><span class="sxs-lookup"><span data-stu-id="b1e07-121">Click **Add Variable** toolbar button again.</span></span>  
  
9. <span data-ttu-id="b1e07-122">键入 " **BatchTag** " 作为 "**名称**"，选择 "**字符串**" 作为 "**数据类型**"，并选择 " **EIMBatch** " 作为**值**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-122">Type **BatchTag** for the **Name**, select **String** for the **Data type**, and **EIMBatch** for the **Value**.</span></span> <span data-ttu-id="b1e07-123">**BatchTag**只是要提交到 MDS 的批处理的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="b1e07-123">**BatchTag** is just a unique name for the batch you will be submitting to MDS.</span></span>  
  
10. <span data-ttu-id="b1e07-124">在 "**数据流" 选项卡**中，双击 "**添加 MDS 所需的列**"。</span><span class="sxs-lookup"><span data-stu-id="b1e07-124">In the **Data Flow** tab, double-click **Add Columns Required by MDS**.</span></span>  
  
11. <span data-ttu-id="b1e07-125">在 "**派生列转换编辑器**" 对话框的**底部窗格的列表框**中，键入**ImportType**作为**派生列名称**。</span><span class="sxs-lookup"><span data-stu-id="b1e07-125">In the **Derived Column Transformation Editor** dialog box, in the **list box in the bottom pane**, type **ImportType** for the **Derived Column Name**.</span></span>  
  
12. <span data-ttu-id="b1e07-126">展开左上方窗格中的 "**变量和参数**"，将**User：： ImportType**拖放到**Expression**列。</span><span class="sxs-lookup"><span data-stu-id="b1e07-126">Expand **Variables and Parameters** in the top-left pane, drag-drop **User::ImportType** to the **Expression** column.</span></span>  
  
     <span data-ttu-id="b1e07-127">![派生列转换编辑器](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "派生列转换编辑器")</span><span class="sxs-lookup"><span data-stu-id="b1e07-127">![Derived Column Transformation Editor](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "Derived Column Transformation Editor")</span></span>  
  
13. <span data-ttu-id="b1e07-128">在 "**派生列名称**" 的下一行中键入**BatchTag** 。</span><span class="sxs-lookup"><span data-stu-id="b1e07-128">Type **BatchTag** in the next row for the **Derived Column Name**.</span></span>  
  
14. <span data-ttu-id="b1e07-129">将**User：： BatchTag**从**Variables 和 Parameters**拖放到**Expression**列。</span><span class="sxs-lookup"><span data-stu-id="b1e07-129">Drag-drop **User::BatchTag** from **Variables and Parameters** to the **Expression** column.</span></span>  
  
15. <span data-ttu-id="b1e07-130">单击 **"确定"** 以关闭 "**派生列转换**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b1e07-130">Click **OK** to close the **Derived Column Transformation** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b1e07-131">下一步</span><span class="sxs-lookup"><span data-stu-id="b1e07-131">Next Step</span></span>  
 [<span data-ttu-id="b1e07-132">任务 13：添加 OLE DB 目标以便将数据写入 MDS 临时表</span><span class="sxs-lookup"><span data-stu-id="b1e07-132">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
