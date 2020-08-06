---
title: 处理插入、更新和删除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],processing data
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67f016aaf4f7f83c0fa506966c4e78f5b8fadef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577775"
---
# <a name="process-inserts-updates-and-deletes"></a><span data-ttu-id="95f34-102">处理插入、更新和删除</span><span class="sxs-lookup"><span data-stu-id="95f34-102">Process Inserts, Updates, and Deletes</span></span>
  <span data-ttu-id="95f34-103">在用于执行变更数据的增量加载的 Integration Services 包的数据流中，第二个任务是分隔插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="95f34-103">In the data flow of an Integration Services package that performs an incremental load of change data, the second task is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="95f34-104">然后，可以使用相应的命令将它们应用到目标。</span><span class="sxs-lookup"><span data-stu-id="95f34-104">Then, you can use appropriate commands to apply them to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95f34-105">为执行变更数据增量加载的包设计数据流的过程中，第一个任务是配置用于运行查询以检索变更数据的源组件。</span><span class="sxs-lookup"><span data-stu-id="95f34-105">The first task in designing the data flow of a package that performs an incremental load of change data is to configure the source component that runs the query that retrieves the change data.</span></span> <span data-ttu-id="95f34-106">有关此组件的详细信息，请参阅 [检索和了解变更数据](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="95f34-106">For more information about this component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span> <span data-ttu-id="95f34-107">有关创建用于执行变更数据增量加载的包的完整过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="95f34-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="associating-friendly-values-to-separate-inserts-updates-and-deletes"></a><span data-ttu-id="95f34-108">关联友好值以分隔插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="95f34-108">Associating Friendly Values to Separate Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="95f34-109">在检索变更数据的示例查询中，**cdc.fn_cdc_get_net_changes_<capture_instance>** 函数仅返回名为 **__$operation** 的元数据列。</span><span class="sxs-lookup"><span data-stu-id="95f34-109">In the example query that retrieves change data, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns only the column of metadata named **__$operation**.</span></span> <span data-ttu-id="95f34-110">此元数据列包含一个序号值，该值指示哪个操作导致更改。</span><span class="sxs-lookup"><span data-stu-id="95f34-110">This metadata column contains an ordinal value that indicates which operation caused the change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95f34-111">有关使用和调用 **cdc.fn_cdc_get_net_changes_<capture_instance>** 函数的查询的详细信息，请参阅[创建函数以检索变更数据](create-the-function-to-retrieve-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="95f34-111">For more information about the query that uses calls the **cdc.fn_cdc_get_net_changes_<capture_instance>** function, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
 <span data-ttu-id="95f34-112">将序号值与其相应的操作匹配，不像使用操作的助记键那样容易。</span><span class="sxs-lookup"><span data-stu-id="95f34-112">Matching an ordinal value to its corresponding operation is not as easy as using a mnemonic of the operation.</span></span> <span data-ttu-id="95f34-113">例如，D 可以简便地表示删除操作，而 I 则可表示插入操作。</span><span class="sxs-lookup"><span data-stu-id="95f34-113">For example, 'D' can easily represent a delete operation and 'I' represent an insert operation.</span></span> <span data-ttu-id="95f34-114">在主题 [创建函数以检索变更数据](create-the-function-to-retrieve-the-change-data.md)中创建的示例查询执行了此转换，即将序号值转换为新列中返回的友好字符串值。</span><span class="sxs-lookup"><span data-stu-id="95f34-114">The example query that was created in the topic, [Creating the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md), makes this conversion from an ordinal value to a friendly string value that is returned in a new column.</span></span> <span data-ttu-id="95f34-115">下面的代码段显示了此转换：</span><span class="sxs-lookup"><span data-stu-id="95f34-115">The following segment of code shows this conversion:</span></span>  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## <a name="configuring-a-conditional-split-transformation-to-direct-inserts-updates-and-deletes"></a><span data-ttu-id="95f34-116">配置有条件拆分转换以定向插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="95f34-116">Configuring a Conditional Split Transformation to Direct Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="95f34-117">若要将变更数据行定向到三个输出中的一个输出，有条件拆分转换是理想的选择。</span><span class="sxs-lookup"><span data-stu-id="95f34-117">To direct rows of change data to one of three outputs, the Conditional Split transformation is ideal.</span></span> <span data-ttu-id="95f34-118">该转换只是检索各行中 **CDC_OPERATION** 列的值，并确定该变更是插入操作、更新操作还是删除操作。</span><span class="sxs-lookup"><span data-stu-id="95f34-118">The transformation just checks the value of the **CDC_OPERATION** column in each row and determines whether that change was an insert, update, or delete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95f34-119">CDC_OPERATION 列包含一个从 **__$operation** 列中的数值派生的友好字符串值。</span><span class="sxs-lookup"><span data-stu-id="95f34-119">The CDC_OPERATION column contains a friendly string value derived from the numeric value in the **__$operation** column.</span></span>  
  
#### <a name="to-split-inserts-updates-and-deletes-for-processing-by-using-a-conditional-split-transformation"></a><span data-ttu-id="95f34-120">使用有条件拆分转换拆分要进行处理的插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="95f34-120">To split inserts, updates, and deletes for processing by using a Conditional Split transformation</span></span>  
  
1.  <span data-ttu-id="95f34-121">在 **“数据流”** 选项卡上，添加一个有条件拆分转换。</span><span class="sxs-lookup"><span data-stu-id="95f34-121">On the **Data Flow** tab, add a Conditional Split transformation.</span></span>  
  
2.  <span data-ttu-id="95f34-122">将 OLE DB 源的输出连接到有条件拆分转换。</span><span class="sxs-lookup"><span data-stu-id="95f34-122">Connect the output of the OLE DB source to the Conditional Split transformation.</span></span>  
  
3.  <span data-ttu-id="95f34-123">在 **“有条件拆分转换编辑器”** 的下部窗格中，输入下面三行以指定三个输出</span><span class="sxs-lookup"><span data-stu-id="95f34-123">In the **Conditional Split Transformation Editor**, in the lower pane of the editor, enter the following three lines to designate the three outputs</span></span>  
  
    1.  <span data-ttu-id="95f34-124">输入条件为 `CDC_OPERATION == "I"` 的行，以将已插入的行定向到插入操作的输出。</span><span class="sxs-lookup"><span data-stu-id="95f34-124">Enter a line with the condition `CDC_OPERATION == "I"` to direct inserted rows to the output for inserts.</span></span>  
  
    2.  <span data-ttu-id="95f34-125">输入条件为 `CDC_OPERATION == "U"` 的行，以将已更新的行定向到更新操作的输出。</span><span class="sxs-lookup"><span data-stu-id="95f34-125">Enter a line with the condition `CDC_OPERATION == "U"` to direct updated rows to the output for updates.</span></span>  
  
    3.  <span data-ttu-id="95f34-126">输入条件为 `CDC_OPERATION == "D"` 的行，以将已删除的行定向到删除操作的输出。</span><span class="sxs-lookup"><span data-stu-id="95f34-126">Enter a line with the condition `CDC_OPERATION == "D"` to direct deleted rows to the output for deletes.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="95f34-127">下一步</span><span class="sxs-lookup"><span data-stu-id="95f34-127">Next Step</span></span>  
 <span data-ttu-id="95f34-128">在拆分要处理的行之后，下一步是将更改应用到目标中。</span><span class="sxs-lookup"><span data-stu-id="95f34-128">After you split the rows for processing, the next step is to apply the changes to the destination.</span></span>  
  
 <span data-ttu-id="95f34-129">**下一个主题：** [将变更应用到目标](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="95f34-129">**Next topic:** [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f34-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95f34-130">See Also</span></span>  
 <span data-ttu-id="95f34-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="95f34-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span></span>  
 [<span data-ttu-id="95f34-132">使用有条件拆分转换拆分数据集</span><span class="sxs-lookup"><span data-stu-id="95f34-132">Split a Dataset by Using the Conditional Split Transformation</span></span>](../data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
