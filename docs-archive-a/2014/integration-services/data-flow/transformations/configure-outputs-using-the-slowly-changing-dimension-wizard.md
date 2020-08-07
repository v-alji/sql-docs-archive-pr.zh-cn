---
title: 使用渐变维度向导配置输出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Slowly Changing Dimension transformation
- slowly changing dimensions
- Slowly Changing Dimension Wizard
ms.assetid: da111731-1ffa-49b9-bcaa-3c93fd0eb619
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ec3dfb34de8eb7e20b255ce485ee506f070749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587942"
---
# <a name="configure-outputs-using-the-slowly-changing-dimension-wizard"></a><span data-ttu-id="e73a0-102">使用渐变维度向导配置输出</span><span class="sxs-lookup"><span data-stu-id="e73a0-102">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="e73a0-103">渐变维度向导所起作用相当于渐变维度转换的编辑器。</span><span class="sxs-lookup"><span data-stu-id="e73a0-103">The Slowly Changing Dimension Wizard functions as the editor for the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="e73a0-104">为渐变维度数据生成和配置数据流可能是一项复杂的任务。</span><span class="sxs-lookup"><span data-stu-id="e73a0-104">Building and configuring the data flow for slowly changing dimension data can be a complex task.</span></span> <span data-ttu-id="e73a0-105">渐变维度向导提供了为渐变维度转换输出生成数据流的最简便方法，指导您逐步完成映射列、选择业务键列、设置列更改属性以及配置对推断维度成员的支持。</span><span class="sxs-lookup"><span data-stu-id="e73a0-105">The Slowly Changing Dimension Wizard offers the simplest method of building the data flow for the Slowly Changing Dimension transformation outputs by guiding you through the steps of mapping columns, selecting business key columns, setting column change attributes, and configuring support for inferred dimension members.</span></span>

 <span data-ttu-id="e73a0-106">必须在维度表中选择至少一个业务键列，并将其映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="e73a0-106">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="e73a0-107">业务键的值将源中的一条记录链接到维度表中的一条记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-107">The value of the business key links a record in the source to a record in the dimension table.</span></span> <span data-ttu-id="e73a0-108">转换使用此映射在维度表中定位该记录，并确定某条记录是新的还是更改过的。</span><span class="sxs-lookup"><span data-stu-id="e73a0-108">The transformation uses this mapping to locate the record in the dimension table and to determine whether a record is new or changing.</span></span> <span data-ttu-id="e73a0-109">业务键通常是源中的主键。如果业务键唯一标识一条记录而且其值不改变，则它也可以作为备用键。</span><span class="sxs-lookup"><span data-stu-id="e73a0-109">The business key is typically the primary key in the source, but it can be an alternate key as long as it uniquely identifies a record and its value does not change.</span></span> <span data-ttu-id="e73a0-110">业务键还可以是由多列构成的组合键。</span><span class="sxs-lookup"><span data-stu-id="e73a0-110">The business key can also be a composite key, consisting of multiple columns.</span></span> <span data-ttu-id="e73a0-111">维度表中的主键通常是代理键，它表示标识列或自定义解决方案（如脚本）自动生成的数值。</span><span class="sxs-lookup"><span data-stu-id="e73a0-111">The primary key in the dimension table is usually a surrogate key, which means a numeric value generated automatically by an identity column or by a custom solution such as a script.</span></span>

 <span data-ttu-id="e73a0-112">必须向数据流添加源和渐变维度转换，再将源的输出连接到渐变维度转换的输入，然后才能运行渐变维度向导。</span><span class="sxs-lookup"><span data-stu-id="e73a0-112">Before you can run the Slowly Changing Dimension Wizard, you must add a source and a Slowly Changing Dimension transformation to the data flow, and then connect the output from the source to the input of the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="e73a0-113">数据流还可以在数据源和渐变维度转换之间包含其他转换。</span><span class="sxs-lookup"><span data-stu-id="e73a0-113">Optionally, the data flow can include other transformations between the data source and the Slowly Changing Dimension transformation.</span></span>

 <span data-ttu-id="e73a0-114">若要在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中打开渐变维度向导，请双击渐变维度转换。</span><span class="sxs-lookup"><span data-stu-id="e73a0-114">To open the Slowly Changing Dimension Wizard in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, double-click the Slowly Changing Dimension transformation.</span></span>

## <a name="creating-slowly-changing-dimension-outputs"></a><span data-ttu-id="e73a0-115">创建渐变维度输出</span><span class="sxs-lookup"><span data-stu-id="e73a0-115">Creating Slowly Changing Dimension Outputs</span></span>

#### <a name="to-create-slowly-changing-dimension-transformation-outputs"></a><span data-ttu-id="e73a0-116">创建渐变维度转换输出</span><span class="sxs-lookup"><span data-stu-id="e73a0-116">To create Slowly Changing Dimension transformation outputs</span></span>

1.  <span data-ttu-id="e73a0-117">选择连接管理器，以便访问包含要更新的维度表的数据源。</span><span class="sxs-lookup"><span data-stu-id="e73a0-117">Choose the connection manager to access the data source that contains the dimension table that you want to update.</span></span>

     <span data-ttu-id="e73a0-118">可以从包所包含的连接管理器列表中选择。</span><span class="sxs-lookup"><span data-stu-id="e73a0-118">You can select from a list of connection managers that the package includes.</span></span>

2.  <span data-ttu-id="e73a0-119">选择要更新的维度表或视图。</span><span class="sxs-lookup"><span data-stu-id="e73a0-119">Choose the dimension table or view you want to update.</span></span>

     <span data-ttu-id="e73a0-120">选择连接管理器后，可以从数据源选择表或视图。</span><span class="sxs-lookup"><span data-stu-id="e73a0-120">After you select the connection manager, you can select the table or view from the data source.</span></span>

3.  <span data-ttu-id="e73a0-121">设置列的键属性，并将输入列映射到维度表中的列。</span><span class="sxs-lookup"><span data-stu-id="e73a0-121">Set key attributes on columns and map input columns to columns in the dimension table.</span></span>

     <span data-ttu-id="e73a0-122">必须在维度表中选择至少一个业务键列，并将其映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="e73a0-122">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="e73a0-123">其他输入列可以作为非键映射映射到维度表中的列。</span><span class="sxs-lookup"><span data-stu-id="e73a0-123">Other input columns can be mapped to columns in the dimension table as non-key mappings.</span></span>

4.  <span data-ttu-id="e73a0-124">选择每列的更改类型。</span><span class="sxs-lookup"><span data-stu-id="e73a0-124">Choose the change type for each column.</span></span>

    -   <span data-ttu-id="e73a0-125">**“变化的属性”** 覆盖记录中的现有值。</span><span class="sxs-lookup"><span data-stu-id="e73a0-125">**Changing attribute** overwrites existing values in records.</span></span>

    -   <span data-ttu-id="e73a0-126">**“历史属性”** 创建新记录而不更新现有记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-126">**Historical attribute** creates new records instead of updating existing records.</span></span>

    -   <span data-ttu-id="e73a0-127">**“固定的属性”** 指示列值不得更改。</span><span class="sxs-lookup"><span data-stu-id="e73a0-127">**Fixed attribute** indicates that the column value must not change.</span></span>

5.  <span data-ttu-id="e73a0-128">设置固定和变化的属性选项。</span><span class="sxs-lookup"><span data-stu-id="e73a0-128">Set fixed and changing attribute options.</span></span>

     <span data-ttu-id="e73a0-129">如果将列配置为使用 **“固定的属性”** 更改类型，则可以指定在这些列中检测到更改时渐变维度转换是否失败。</span><span class="sxs-lookup"><span data-stu-id="e73a0-129">If you configure columns to use the **Fixed attribute** change type, you can specify whether the Slowly Changing Dimension transformation fails when changes are detected in these columns.</span></span> <span data-ttu-id="e73a0-130">如果将列配置为使用 **“变化的属性”** 更改类型，则可以指定是否更新包括过期记录在内所有匹配的记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-130">If you configure columns to use the **Changing attribute** change type, you can specify whether all matching records, including outdated records, are updated.</span></span>

6.  <span data-ttu-id="e73a0-131">设置历史属性选项。</span><span class="sxs-lookup"><span data-stu-id="e73a0-131">Set historical attribute options.</span></span>

     <span data-ttu-id="e73a0-132">如果将列配置为使用 **“历史属性”** 更改类型，则必须选择如何区分当前记录和过期记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-132">If you configure columns to use the **Historical attribute** change type, you must choose how to distinguish between current and expired records.</span></span> <span data-ttu-id="e73a0-133">可以使用一个当前行指示器列或两个日期列来标识当前行和过期行。</span><span class="sxs-lookup"><span data-stu-id="e73a0-133">You can use a current row indicator column or two date columns to identify current and expired rows.</span></span> <span data-ttu-id="e73a0-134">如果使用当前行指示器列，则可以将其设置成当行是当前行时为 **“当前”** 或 **True** ，而当行是过期行时为 **“过期”** 或 **False** 。</span><span class="sxs-lookup"><span data-stu-id="e73a0-134">If you use the current row indicator column, you can set it to **Current**, **True** when current and **Expired,** or **False** when expired.</span></span> <span data-ttu-id="e73a0-135">也可以输入自定义值。</span><span class="sxs-lookup"><span data-stu-id="e73a0-135">You can also enter custom values.</span></span> <span data-ttu-id="e73a0-136">如果使用两个日期列（开始日期和结束日期），则可以输入日期或选择系统变量然后使用其值，从而指定设置日期列值时要使用的日期。</span><span class="sxs-lookup"><span data-stu-id="e73a0-136">If you use two date columns, a start date and an end date, you can specify the date to use when setting the date column values by typing a date or by selecting a system variable and then using its value.</span></span>

7.  <span data-ttu-id="e73a0-137">指定对推断成员的支持，并选择推断成员记录所包含的列。</span><span class="sxs-lookup"><span data-stu-id="e73a0-137">Specify support for inferred members and choose the columns that the inferred member record contains.</span></span>

     <span data-ttu-id="e73a0-138">向事实数据表中加载度量值时，可以为尚不存在的推断成员创建最小记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-138">When loading measures into a fact table, you can create minimal records for inferred members that do not yet exist.</span></span> <span data-ttu-id="e73a0-139">以后出现有意义的数据时，可以更新维度记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-139">Later, when meaningful data is available, the dimension records can be updated.</span></span> <span data-ttu-id="e73a0-140">可以创建以下类型的最小记录：</span><span class="sxs-lookup"><span data-stu-id="e73a0-140">The following types of minimal records can be created:</span></span>

    -   <span data-ttu-id="e73a0-141">其中所有带更改类型的列中的记录均为空。</span><span class="sxs-lookup"><span data-stu-id="e73a0-141">A record in which all columns with change types are null.</span></span>

    -   <span data-ttu-id="e73a0-142">其中有布尔值列指示该记录为推断成员的记录。</span><span class="sxs-lookup"><span data-stu-id="e73a0-142">A record in which a Boolean column indicates the record is an inferred member.</span></span>

8.  <span data-ttu-id="e73a0-143">检查渐变维度向导生成的配置。</span><span class="sxs-lookup"><span data-stu-id="e73a0-143">Review the configurations that the Slowly Changing Dimension Wizard builds.</span></span> <span data-ttu-id="e73a0-144">根据所支持的更改类型，将不同的数据流组件集添加到包。</span><span class="sxs-lookup"><span data-stu-id="e73a0-144">Depending on which change types are supported, different sets of data flow components are added to the package.</span></span>

     <span data-ttu-id="e73a0-145">下列关系图所示的示例数据流支持固定的属性更改、变化的属性更改以及历史属性更改、推断成员和对匹配记录的更改。</span><span class="sxs-lookup"><span data-stu-id="e73a0-145">The following diagram shows an example of a data flow that supports fixed attribute, changing attribute, and historical attribute changes, inferred members, and changes to matching records.</span></span>

     <span data-ttu-id="e73a0-146">![渐变维度向导的数据流](../../media/dimensionwizard.gif "渐变维度向导的数据流")</span><span class="sxs-lookup"><span data-stu-id="e73a0-146">![Data flow from Slowly Changing Dimension Wizard](../../media/dimensionwizard.gif "Data flow from Slowly Changing Dimension Wizard")</span></span>

## <a name="updating-slowly-changing-dimension-outputs"></a><span data-ttu-id="e73a0-147">更新渐变维度输出</span><span class="sxs-lookup"><span data-stu-id="e73a0-147">Updating Slowly Changing Dimension Outputs</span></span>
 <span data-ttu-id="e73a0-148">更新渐变维度转换输出配置的最简单方法就是重新运行渐变维度向导并从向导页修改属性。</span><span class="sxs-lookup"><span data-stu-id="e73a0-148">The simplest way to update the configuration of the Slowly Changing Dimension transformation outputs is to rerun the Slowly Changing Dimension Wizard and modify properties from the wizard pages.</span></span> <span data-ttu-id="e73a0-149">也可以使用 **“高级编辑器”** 对话框或以编程方式更新渐变维度转换。</span><span class="sxs-lookup"><span data-stu-id="e73a0-149">You can also update the Slowly Changing Dimension transformation using the **Advanced Editor** dialog box or programmatically.</span></span>

## <a name="see-also"></a><span data-ttu-id="e73a0-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e73a0-150">See Also</span></span>
 [<span data-ttu-id="e73a0-151">渐变维度转换</span><span class="sxs-lookup"><span data-stu-id="e73a0-151">Slowly Changing Dimension Transformation</span></span>](slowly-changing-dimension-transformation.md)


