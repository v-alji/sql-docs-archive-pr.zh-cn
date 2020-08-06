---
title: 将变更应用到目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],applying changes
ms.assetid: 338a56db-cb14-4784-a692-468eabd30f41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dd7ab93a299ffaab2259c3d462a5c0a69160ad5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591494"
---
# <a name="apply-the-changes-to-the-destination"></a><span data-ttu-id="aa778-102">将变更应用到目标</span><span class="sxs-lookup"><span data-stu-id="aa778-102">Apply the Changes to the Destination</span></span>
  <span data-ttu-id="aa778-103">在用于执行变更数据增量加载的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的数据流中，第三个任务（即最后一个任务）是将变更应用到目标。</span><span class="sxs-lookup"><span data-stu-id="aa778-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to apply the changes to your destination.</span></span> <span data-ttu-id="aa778-104">您将需要一个组件应用插入操作、一个组件应用更新操作以及一个组件应用删除操作。</span><span class="sxs-lookup"><span data-stu-id="aa778-104">You will need one component to apply inserts, one to apply updates, and one to apply deletes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa778-105">为用于执行变更数据增量加载的包设计数据流的过程中，第二个任务是分隔插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="aa778-105">The second task in designing the data flow of a package that performs an incremental load of change data is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="aa778-106">有关此组件的详细信息，请参阅 [处理插入、更新和删除](process-inserts-updates-and-deletes.md)。</span><span class="sxs-lookup"><span data-stu-id="aa778-106">For more information about this component, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span> <span data-ttu-id="aa778-107">有关创建用于执行变更数据增量加载的包的完整过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="aa778-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="applying-inserts"></a><span data-ttu-id="aa778-108">应用插入操作</span><span class="sxs-lookup"><span data-stu-id="aa778-108">Applying Inserts</span></span>  
 <span data-ttu-id="aa778-109">若要应用插入操作，请使用 OLE DB 目标，因为新行不需要任何特殊处理。</span><span class="sxs-lookup"><span data-stu-id="aa778-109">To apply inserts, you use an OLE DB destination because the new rows do not require any special handling.</span></span>  
  
#### <a name="to-process-inserts-by-using-an-ole-db-destination"></a><span data-ttu-id="aa778-110">使用 OLE DB 目标处理插入操作</span><span class="sxs-lookup"><span data-stu-id="aa778-110">To process inserts by using an OLE DB Destination</span></span>  
  
1.  <span data-ttu-id="aa778-111">在 **“数据流”** 选项卡上，添加 OLE DB 目标。</span><span class="sxs-lookup"><span data-stu-id="aa778-111">On the **Data flow** tab, add an OLE DB destination.</span></span>  
  
2.  <span data-ttu-id="aa778-112">将包含来自有条件拆分转换的插入操作的输出连接到 OLE DB 目标。</span><span class="sxs-lookup"><span data-stu-id="aa778-112">Connect the output that contains inserts from the Conditional Split transformation to the OLE DB destination.</span></span>  
  
3.  <span data-ttu-id="aa778-113">在 **“OLE DB 目标编辑器”** 的 **“连接管理器”** 页上，选择下列选项：</span><span class="sxs-lookup"><span data-stu-id="aa778-113">In the **OLE DB Destination Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="aa778-114">为目标数据库选择或创建一个 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="aa778-114">Select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
    2.  <span data-ttu-id="aa778-115">选择 **“数据访问模式”** 选项，然后选择包含目标列的目标表或输入包含目标列的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="aa778-115">Select a **Data access mode** option, and then select the destination table or enter a SQL statement that contains the destination columns.</span></span>  
  
4.  <span data-ttu-id="aa778-116">在编辑器的 **“映射”** 页上，将变更数据的相应列映射到目标表。</span><span class="sxs-lookup"><span data-stu-id="aa778-116">On the **Mappings** page of the editor, map the appropriate columns from the change data to the destination table.</span></span>  
  
## <a name="applying-updates"></a><span data-ttu-id="aa778-117">应用更新操作</span><span class="sxs-lookup"><span data-stu-id="aa778-117">Applying Updates</span></span>  
 <span data-ttu-id="aa778-118">若要应用更新操作，请使用 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-118">To apply updates, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="aa778-119">因为您必须通过参数化的 UPDATE 语句使用新的列值一次更新一行，所以要使用此转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-119">You use this transformation because you have to use a parameterized UPDATE statement to update one row at a time with the new column values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa778-120">还可以使用目标组件来应用更新操作。</span><span class="sxs-lookup"><span data-stu-id="aa778-120">You can also use destination components to apply updates.</span></span> <span data-ttu-id="aa778-121">如果使用此方法，则将使用目标组件将行保存到为此而创建的临时表中。</span><span class="sxs-lookup"><span data-stu-id="aa778-121">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="aa778-122">然后，使用执行 SQL 任务根据临时表对目标执行大容量更新和大容量删除操作。</span><span class="sxs-lookup"><span data-stu-id="aa778-122">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-updates-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="aa778-123">使用 OLE DB 命令转换处理更新操作</span><span class="sxs-lookup"><span data-stu-id="aa778-123">To process updates by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="aa778-124">在 **“数据流”** 选项卡上，添加 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-124">On the **Data flow** tab, add an OLE DB Command transformation.</span></span>  
  
2.  <span data-ttu-id="aa778-125">将包含来自有条件拆分转换的更新操作的输出连接到 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-125">Connect the output that contains updates from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="aa778-126">在 **“OLE DB 命令的高级编辑器”** 的 **“连接管理器”** 选项卡上，为目标数据库选择或创建一个 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="aa778-126">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
4.  <span data-ttu-id="aa778-127">在 **“OLE DB 命令的高级编辑器”** 的 **“组件属性”** 选项卡上，对于 **SqlCommand**，输入参数化的 UPDATE 语句。</span><span class="sxs-lookup"><span data-stu-id="aa778-127">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab, for **SqlCommand**, enter a parameterized UPDATE statement.</span></span>  
  
     <span data-ttu-id="aa778-128">例如，Customer 表的 UPDATE 语句可能具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="aa778-128">For example, an UPDATE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    update CDCSample.Customer  
    set TerritoryID  = ?,  
        CustomerType  = ?,  
        rowguid  = ?,  
        ModifiedDate  = ?  
    where CustomerID = ?  
  
    ```  
  
5.  <span data-ttu-id="aa778-129">在编辑器的 **“列映射”** 选项卡上，将变更数据的相应列映射到 UPDATE 语句中的参数。</span><span class="sxs-lookup"><span data-stu-id="aa778-129">On the **Column Mappings** tab of the editor, map the appropriate columns from the change data to the parameters in the UPDATE statement.</span></span>  
  
## <a name="applying-deletes"></a><span data-ttu-id="aa778-130">应用删除操作</span><span class="sxs-lookup"><span data-stu-id="aa778-130">Applying Deletes</span></span>  
 <span data-ttu-id="aa778-131">若要应用删除操作，请使用 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-131">To apply deletes, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="aa778-132">因为您必须通过参数化的 DELETE 语句使用唯一标识行的列值一次删除一行，所以要使用此转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-132">You use this transformation because you have to use a parameterized DELETE statement that deletes a single row at a time based on the column value that uniquely identifies the row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa778-133">还可以使用目标组件来应用删除操作。</span><span class="sxs-lookup"><span data-stu-id="aa778-133">You can also use destination components to apply deletes.</span></span> <span data-ttu-id="aa778-134">如果使用此方法，则将使用目标组件将行保存到为此而创建的临时表中。</span><span class="sxs-lookup"><span data-stu-id="aa778-134">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="aa778-135">然后，使用执行 SQL 任务根据临时表对目标执行大容量更新和大容量删除操作。</span><span class="sxs-lookup"><span data-stu-id="aa778-135">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-deletes-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="aa778-136">使用 OLE DB 命令转换处理删除操作</span><span class="sxs-lookup"><span data-stu-id="aa778-136">To process deletes by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="aa778-137">在 **“数据流”** 选项卡上，向数据流中添加 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-137">On the **Data flow** tab, add an OLE DB Command transformation to the data flow.</span></span>  
  
2.  <span data-ttu-id="aa778-138">将包含来自有条件拆分转换的删除操作的输出连接到 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-138">Connect the output that contains deletes from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="aa778-139">打开“高级编辑器”以配置该转换。</span><span class="sxs-lookup"><span data-stu-id="aa778-139">Open the Advanced Editor to configure the transformation.</span></span>  
  
4.  <span data-ttu-id="aa778-140">在 **“OLE DB 命令的高级编辑器”** 的 **“连接管理器”** 选项卡上，为目标数据库选择或创建一个 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="aa778-140">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
5.  <span data-ttu-id="aa778-141">在 **“OLE DB 命令的高级编辑器”** 的 **“组件属性”** 选项卡上，对于 **SqlCommand**，输入参数化的 DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="aa778-141">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab of the editor, for **SqlCommand**, enter a parameterized DELETE statement.</span></span>  
  
     <span data-ttu-id="aa778-142">例如，Customer 表的 DELETE 语句可能具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="aa778-142">For example, a DELETE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    delete from Customer where CustomerID = ?  
  
    ```  
  
6.  <span data-ttu-id="aa778-143">在编辑器的 **“列映射”** 选项卡上，将变更数据的相应列映射到 DELETE 语句中的参数。</span><span class="sxs-lookup"><span data-stu-id="aa778-143">On the **Column Mappings** tab of the editor, map the appropriate column from the change data to the parameter in the DELETE statement.</span></span>  
  
## <a name="optimizing-inserts-and-updates-by-using-merge-functionality"></a><span data-ttu-id="aa778-144">使用 MERGE 功能优化插入和更新操作</span><span class="sxs-lookup"><span data-stu-id="aa778-144">Optimizing Inserts and Updates by Using MERGE Functionality</span></span>  
 <span data-ttu-id="aa778-145">可以通过将特定的变更数据捕获选项与 Transact-SQL MERGE 关键字结合使用，来优化插入操作和更新操作的处理。</span><span class="sxs-lookup"><span data-stu-id="aa778-145">You can optimize the processing of inserts and updates by combining certain change data capture options with the use of the Transact-SQL MERGE keyword.</span></span> <span data-ttu-id="aa778-146">有关 MERGE 关键字的详细信息，请参阅[ MERGE (Transact-SQL)](/sql/t-sql/statements/merge-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa778-146">For more information about the MERGE keyword, see [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql).</span></span>  
  
 <span data-ttu-id="aa778-147">在用于检索变更数据的 Transact-SQL 语句中，调用 **cdc.fn_cdc_get_net_changes_<capture_instance>** 函数时可以将 all with merge 指定为 row_filter_option 参数的值 。</span><span class="sxs-lookup"><span data-stu-id="aa778-147">In the Transact-SQL statement that retrieves the change data, you can specify *all with merge* as the value of the *row_filter_option* parameter when you call the **cdc.fn_cdc_get_net_changes_<capture_instance>** function.</span></span> <span data-ttu-id="aa778-148">当此变更数据捕获函数不需要执行用于区分插入操作和更新操作的额外处理时，它的操作效率会大大提高。</span><span class="sxs-lookup"><span data-stu-id="aa778-148">This change data capture function operates more efficiently when it does not have to perform the extra processing that is required to distinguish inserts from updates.</span></span> <span data-ttu-id="aa778-149">将 all with merge 指定为参数值时，对于删除操作来说，变更数据的 **__$operation** 值为 1，而对于插入操作或更新操作引起的变更来说，该值为 5。</span><span class="sxs-lookup"><span data-stu-id="aa778-149">When you specify the *all with merge* parameter value, the **__$operation** value of the change data is 1 for deletes or 5 for changes that were caused by inserts or updates.</span></span> <span data-ttu-id="aa778-150">有关用于检索变更数据的 Transact-SQL 函数的详细信息，请参阅[检索和了解变更数据](retrieve-and-understand-the-change-data.md)。使用 all with merge 参数值检索变更之后，可以应用删除操作，并将剩余行输出到临时表或中间临时表中  。</span><span class="sxs-lookup"><span data-stu-id="aa778-150">For more information about the Transact-SQL function that is used to retrieve the change data, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).After retrieving changes with the *all with merge* parameter value, you can apply deletes, and output the remaining rows to a temporary table or a staging table.</span></span> <span data-ttu-id="aa778-151">然后，在下游执行 SQL 任务中，可以使用一个 MERGE 语句将所有插入操作或更新操作从中间临时表应用到目标中。</span><span class="sxs-lookup"><span data-stu-id="aa778-151">Then, in a downstream Execute SQL Task, you can use a single MERGE statement to apply all the inserts or updates from the staging table to the destination.</span></span>  
  
  
