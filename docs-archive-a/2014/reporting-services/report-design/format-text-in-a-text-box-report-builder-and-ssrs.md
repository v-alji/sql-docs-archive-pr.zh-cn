---
title: 设置文本框中文本的格式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df0794b5-96b0-4034-bd17-1be7f31e29db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 522bc420f77b2e5e9d2163c28d3d688b7c47883c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580579"
---
# <a name="format-text-in-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="97fe3-102">设置文本框中文本的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97fe3-102">Format Text in a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="97fe3-103">可以单独设置文本框中任何一部分文本的格式，并在一个文本框中混合使用占位符文本和静态文本。</span><span class="sxs-lookup"><span data-stu-id="97fe3-103">You can format any part of the text within a text box independently, and mix placeholder text and static text in one text box.</span></span> <span data-ttu-id="97fe3-104">这种混合格式并添加占位符文本的功能可使您能够为报表中的文本创建邮件合并或模板。</span><span class="sxs-lookup"><span data-stu-id="97fe3-104">This ability to mix formats and add placeholder text enables you to create mail merges or templates for text in your report.</span></span> <span data-ttu-id="97fe3-105">使用占位符可以单独定义任何表达式并设置其格式。</span><span class="sxs-lookup"><span data-stu-id="97fe3-105">Any expression can be defined and formatted separately using a placeholder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-combine-multiple-formats-in-a-text-box"></a><span data-ttu-id="97fe3-106">在一个文本框中组合多种格式</span><span class="sxs-lookup"><span data-stu-id="97fe3-106">To combine multiple formats in a text box</span></span>  
  
1.  <span data-ttu-id="97fe3-107">在 **“插入”** 选项卡上，单击 **“文本框”** 。</span><span class="sxs-lookup"><span data-stu-id="97fe3-107">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="97fe3-108">单击设计图面，然后拖动鼠标根据所需大小创建一个文本框。</span><span class="sxs-lookup"><span data-stu-id="97fe3-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
2.  <span data-ttu-id="97fe3-109">在文本框内，选择要为其设置格式的文本。</span><span class="sxs-lookup"><span data-stu-id="97fe3-109">Inside the text box, select the text you want to format.</span></span>  
  
3.  <span data-ttu-id="97fe3-110">右键单击所选文本，然后单击“文本属性”  。</span><span class="sxs-lookup"><span data-stu-id="97fe3-110">Right-click the selected text, and click **Text Properties**.</span></span>  
  
4.  <span data-ttu-id="97fe3-111">设置格式设置选项。</span><span class="sxs-lookup"><span data-stu-id="97fe3-111">Set formatting options.</span></span> <span data-ttu-id="97fe3-112">例如，在 **“常规”** 选项卡上：</span><span class="sxs-lookup"><span data-stu-id="97fe3-112">For example, on the **General** tab:</span></span>  
  
    -   <span data-ttu-id="97fe3-113">**工具提示** 键入文本或计算结果为工具提示的表达式。</span><span class="sxs-lookup"><span data-stu-id="97fe3-113">**Tooltip** Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="97fe3-114">当用户将鼠标指针停在报表中该项的上方时，便会显示此工具提示</span><span class="sxs-lookup"><span data-stu-id="97fe3-114">The ToolTip appears when the user pauses the pointer over the item in a report</span></span>  
  
    -   <span data-ttu-id="97fe3-115">**标记类型** 选择一个选项以指示所选文本的呈现方式：</span><span class="sxs-lookup"><span data-stu-id="97fe3-115">**Markup type** Select an option to indicate how the selected text will be rendered:</span></span>  
  
         <span data-ttu-id="97fe3-116">**纯文本** ：将所选文本显示为简单文本。</span><span class="sxs-lookup"><span data-stu-id="97fe3-116">**Plain Text** Display the selected text as simple text.</span></span> <span data-ttu-id="97fe3-117">HTML 将被视为文字文本。</span><span class="sxs-lookup"><span data-stu-id="97fe3-117">HTML will be treated as literal text.</span></span>  
  
         <span data-ttu-id="97fe3-118">**HTML**  ：将所选文本显示为 HTML。</span><span class="sxs-lookup"><span data-stu-id="97fe3-118">**HTML**  Display the selected text as HTML.</span></span> <span data-ttu-id="97fe3-119">如果占位符的表达式值包含有效的 HTML 标记，则这些标记将呈现为 HTML。</span><span class="sxs-lookup"><span data-stu-id="97fe3-119">If the expression value of the placeholder contains valid HTML tags, these tags will be rendered as HTML.</span></span> <span data-ttu-id="97fe3-120">有关详细信息，请参阅[将 HTML 导入报表（报表生成器和 SSRS）](importing-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="97fe3-120">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="97fe3-121">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="97fe3-121">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="97fe3-122">对要为其设置格式的其余文本，重复步骤 2 到步骤 5。</span><span class="sxs-lookup"><span data-stu-id="97fe3-122">Repeat steps 2 through 5 for the remaining text you want to format.</span></span>  
  
### <a name="to-format-text-and-placeholders-differently-in-the-same-text-box"></a><span data-ttu-id="97fe3-123">在同一文本框中以不同方式设置文本和占位符的格式</span><span class="sxs-lookup"><span data-stu-id="97fe3-123">To format text and placeholders differently in the same text box</span></span>  
  
1.  <span data-ttu-id="97fe3-124">在 **“插入”** 选项卡上，单击 **“列表”** 。</span><span class="sxs-lookup"><span data-stu-id="97fe3-124">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="97fe3-125">单击设计图面，然后拖动鼠标根据所需大小创建一个文本框。</span><span class="sxs-lookup"><span data-stu-id="97fe3-125">Click the design surface, and then drag to create a box that is the size you want.</span></span> <span data-ttu-id="97fe3-126">此时将打开 **“数据集属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="97fe3-126">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="97fe3-127">可以使用共享数据集或嵌入在报表中的数据集。</span><span class="sxs-lookup"><span data-stu-id="97fe3-127">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="97fe3-128">有关详细信息，请单击[“数据集属性”对话框 ->“查询”（报表生成器）](../report-data/dataset-properties-dialog-box-query-report-builder.md)或[“数据集属性”对话框 ->“查询”](../dataset-properties-dialog-box-query.md)。</span><span class="sxs-lookup"><span data-stu-id="97fe3-128">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="97fe3-129">在 **“插入”** 选项卡上，单击 **“文本框”** 。</span><span class="sxs-lookup"><span data-stu-id="97fe3-129">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="97fe3-130">在列表中单击，然后拖动鼠标根据所需大小创建一个文本框。</span><span class="sxs-lookup"><span data-stu-id="97fe3-130">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="97fe3-131">在文本框中键入一个标签，如 My Field:  。</span><span class="sxs-lookup"><span data-stu-id="97fe3-131">Type a label in the text box - for example, **My Field**:.</span></span>  
  
4.  <span data-ttu-id="97fe3-132">将字段从数据集拖到文本框中。</span><span class="sxs-lookup"><span data-stu-id="97fe3-132">Drag a field from your dataset into the text box.</span></span> <span data-ttu-id="97fe3-133">此时将为您的字段创建一个占位符。</span><span class="sxs-lookup"><span data-stu-id="97fe3-133">A placeholder is created for your field.</span></span>  
  
5.  <span data-ttu-id="97fe3-134">对于基本格式设置，请选择占位符文本，然后在 **“开始”** 选项卡上的 **“字体”** 组中，单击其中一个格式设置选项。例如，单击“加粗”  按钮。</span><span class="sxs-lookup"><span data-stu-id="97fe3-134">For basic formatting, select the placeholder text and then click one of the formatting options in the **Font** group on the **Home** tab. For example, click the **Bold** button.</span></span>  
  
     <span data-ttu-id="97fe3-135">要获得更多格式设置选项，请右键单击占位符文本，然后单击“占位符属性”  。</span><span class="sxs-lookup"><span data-stu-id="97fe3-135">For more formatting options, right-click the placeholder text, and then click **Placeholder Properties**.</span></span>  
  
6.  <span data-ttu-id="97fe3-136">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="97fe3-136">Click **OK**.</span></span> <span data-ttu-id="97fe3-137">在报表设计视图中，文本框应包含“**My Field**: [*FieldName*]”，其中 *FieldName* 是你的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="97fe3-137">In report design view, the text box should contain "**My Field**: [*FieldName*]", where *FieldName* is the name of your field.</span></span>  
  
7.  <span data-ttu-id="97fe3-138">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="97fe3-138">Click **Run**.</span></span>  
  
 <span data-ttu-id="97fe3-139">列表会将字段中的每个值重复一次，每次重复时， *FieldName* 占位符都会由数据集中该字段的值替换。</span><span class="sxs-lookup"><span data-stu-id="97fe3-139">The list repeats one time for every value in the field, and the *FieldName* placeholder is replaced each time by the value of that field in the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fe3-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97fe3-140">See Also</span></span>  
 <span data-ttu-id="97fe3-141">[文本框（报表生成器和 SSRS）](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-141">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97fe3-142">[设置文本和占位符的格式（报表生成器和 SSRS）](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-142">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97fe3-143">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-143">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97fe3-144">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-144">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97fe3-145">[向报表添加 HTML（报表生成器和 SSRS）](add-html-into-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-145">[Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97fe3-146">[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-146">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97fe3-147">[设置数字和日期格式（报表生成器和 SSRS）](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97fe3-147">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="97fe3-148">“占位符属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97fe3-148">Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
