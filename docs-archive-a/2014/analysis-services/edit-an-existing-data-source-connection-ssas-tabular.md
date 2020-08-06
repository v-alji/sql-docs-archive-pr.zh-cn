---
title: " (SSAS 表格) 编辑现有数据源连接 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.selexistconn.f1
ms.assetid: 97e63f18-a01d-4c91-a411-e7e6d40a0647
author: minewiskan
ms.author: owend
ms.openlocfilehash: 675a0d1119e25a92231d3e74a79739cb2e96b6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589941"
---
# <a name="edit-an-existing-data-source-connection-ssas-tabular"></a><span data-ttu-id="81068-102">编辑现有数据源连接（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="81068-102">Edit an Existing Data Source Connection (SSAS Tabular)</span></span>
  <span data-ttu-id="81068-103">本主题介绍如何编辑表格模型中现有数据源连接的属性。</span><span class="sxs-lookup"><span data-stu-id="81068-103">This topic describes how to edit the properties of an existing data source connection in a tabular model.</span></span>  
  
 <span data-ttu-id="81068-104">在创建与外部数据源的连接后，可以通过以下方式修改该连接：</span><span class="sxs-lookup"><span data-stu-id="81068-104">After you have created a connection to an external data source, you can later modify that connection in these ways:</span></span>  
  
-   <span data-ttu-id="81068-105">可以更改连接信息，其中包括：用作源的文件、馈送或数据库，其属性或其他特定于访问接口的连接选项。</span><span class="sxs-lookup"><span data-stu-id="81068-105">You can change the connection information, including the file, feed, or database used as a source, its properties, or other provider-specific connection options.</span></span>  
  
-   <span data-ttu-id="81068-106">可以更改表和列映射，删除不再使用的列引用。</span><span class="sxs-lookup"><span data-stu-id="81068-106">You can change table and column mappings, and remove references to columns that are no longer used.</span></span>  
  
-   <span data-ttu-id="81068-107">可以更改从外部数据源获取的表、视图或列。</span><span class="sxs-lookup"><span data-stu-id="81068-107">You can change the tables, views, or columns that you get from the external data source.</span></span>  
  
## <a name="modify-a-connection"></a><span data-ttu-id="81068-108">修改连接</span><span class="sxs-lookup"><span data-stu-id="81068-108">Modify a Connection</span></span>  
 <span data-ttu-id="81068-109">此过程介绍如何修改数据库的数据源连接。</span><span class="sxs-lookup"><span data-stu-id="81068-109">This procedure describes how to modify a database data source connection.</span></span> <span data-ttu-id="81068-110">使用数据源的某些选项将根据数据源类型而有所不同；但是，您应该能够轻松地标识这些差异。</span><span class="sxs-lookup"><span data-stu-id="81068-110">Some options for working with data sources differ depending on the data source type; however, you should be able to easily identify those differences.</span></span>  
  
#### <a name="to-change-the-external-data-source-used-by-a-current-connection"></a><span data-ttu-id="81068-111">更改当前连接使用的外部数据源</span><span class="sxs-lookup"><span data-stu-id="81068-111">To change the external data source used by a current connection</span></span>  
  
1.  <span data-ttu-id="81068-112">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="81068-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="81068-113">选择您要修改的数据源连接，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="81068-113">Select the data source connection you want to modify, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="81068-114">在 **“编辑连接”** 对话框中，单击 **“浏览”** 找到类型相同但名称或位置不同的其他数据库。</span><span class="sxs-lookup"><span data-stu-id="81068-114">In the **Edit Connection** dialog box, click **Browse** to locate another database of the same type but with a different name or location.</span></span>  
  
     <span data-ttu-id="81068-115">更改数据库文件后，将立即显示一条消息，指示您需要保存和刷新表以便查看新数据。</span><span class="sxs-lookup"><span data-stu-id="81068-115">As soon as you change the database file, a message appears indicating that you need to save and refresh the tables in order to see the new data.</span></span>  
  
4.  <span data-ttu-id="81068-116">单击 **“保存”**，然后单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="81068-116">Click **Save**, and then click **Close**.</span></span>  
  
5.  <span data-ttu-id="81068-117">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，依次单击 **“模型”**、 **“处理”** 和 **“全部处理”**。</span><span class="sxs-lookup"><span data-stu-id="81068-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model**, click **Process**, and then click **Process All**.</span></span>  
  
     <span data-ttu-id="81068-118">将使用新数据源重新处理表，但保留原有的数据选择。</span><span class="sxs-lookup"><span data-stu-id="81068-118">The tables are re-processed using the new data source, but with the original data selections.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81068-119">如果新数据源包含原始数据源中不存在的任何附加表，您必须重新打开已更改的连接并添加这些表。</span><span class="sxs-lookup"><span data-stu-id="81068-119">If the new data source contains any additional tables that were not present in the original data source, you must re-open the changed connection and add the tables.</span></span>  
  
## <a name="edit-table-and-column-mappings-bindings"></a><span data-ttu-id="81068-120">编辑表和列映射（绑定）</span><span class="sxs-lookup"><span data-stu-id="81068-120">Edit Table and Column Mappings (Bindings)</span></span>  
 <span data-ttu-id="81068-121">此过程说明如何在更改数据源之后编辑映射。</span><span class="sxs-lookup"><span data-stu-id="81068-121">This procedure describes how to edit the mappings after you change a data source.</span></span>  
  
#### <a name="to-edit-column-mappings-when-a-data-source-changes"></a><span data-ttu-id="81068-122">在数据源发生更改时编辑列映射</span><span class="sxs-lookup"><span data-stu-id="81068-122">To edit column mappings when a data source changes</span></span>  
  
1.  <span data-ttu-id="81068-123">在模型设计器中，选择某个表。</span><span class="sxs-lookup"><span data-stu-id="81068-123">In the model designer, select a table.</span></span>  
  
2.  <span data-ttu-id="81068-124">单击 **“表”** 菜单，然后单击 **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="81068-124">Click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
     <span data-ttu-id="81068-125">**“表名”** 框中将显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="81068-125">The name of the selected table is displayed in the **Table Name** box.</span></span> <span data-ttu-id="81068-126">**“源名称”** 框包含外部数据源中的表的名称。</span><span class="sxs-lookup"><span data-stu-id="81068-126">The **Source Name** box contains the name of the table in the external data source.</span></span> <span data-ttu-id="81068-127">如果源和模型中对列的命名方式不同，则可通过选择 **“源”** 或 **“模型”** 选项在这两组列名之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="81068-127">If columns are named differently in the source and in the model, you can toggle between the two sets of column names by selecting the options **Source** or **Model**.</span></span>  
  
3.  <span data-ttu-id="81068-128">若要更改用作数据源的表，请为 **“源名称”** 选择当前表之外的其他表。</span><span class="sxs-lookup"><span data-stu-id="81068-128">To change the table that is used as a data source, for **Source Name**, select a different table than the current one.</span></span>  
  
4.  <span data-ttu-id="81068-129">在需要时更改列映射：</span><span class="sxs-lookup"><span data-stu-id="81068-129">Change column mappings if needed:</span></span>  
  
    1.  <span data-ttu-id="81068-130">若要添加源中存在但模型中不存在的列，请选中列名旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="81068-130">To add columns that are present in the source but not in the model, select the checkbox beside the column name.</span></span>  
  
         <span data-ttu-id="81068-131">实际数据将在下次进行刷新时加载到模型中。</span><span class="sxs-lookup"><span data-stu-id="81068-131">The actual data will be loaded into the model the next time you refresh.</span></span>  
  
    2.  <span data-ttu-id="81068-132">如果模型中有些列在当前数据源中不再可用，将在通知区域显示一条消息，其中列出无效的列。</span><span class="sxs-lookup"><span data-stu-id="81068-132">If some columns in the model are no longer available in the current data source, a message appears in the notification area that lists the invalid columns.</span></span> <span data-ttu-id="81068-133">您无需执行任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="81068-133">You do not need to do anything else.</span></span>  
  
5.  <span data-ttu-id="81068-134">单击 **“保存”** 将更改应用于源。</span><span class="sxs-lookup"><span data-stu-id="81068-134">Click **Save** to apply the changes to your model.</span></span>  
  
     <span data-ttu-id="81068-135">在您保存当前的一组表属性时，可能会显示一条消息，指示您需要处理表。</span><span class="sxs-lookup"><span data-stu-id="81068-135">When you save the current set of table properties, a message may appear indicating that you need to process the tables.</span></span> <span data-ttu-id="81068-136">单击 **“处理”** 可将更新的数据加载到模型中。</span><span class="sxs-lookup"><span data-stu-id="81068-136">Click **Process** to load updated data into your model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81068-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81068-137">See Also</span></span>  
 <span data-ttu-id="81068-138">[&#40;SSAS 表格&#41;处理数据](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="81068-138">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="81068-139">支持的数据源（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="81068-139">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
