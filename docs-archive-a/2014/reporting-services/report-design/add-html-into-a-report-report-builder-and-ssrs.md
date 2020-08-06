---
title: 向报表添加 HTML（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 605c84843d62fb664a8a665a3fc3b024f8f87186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692265"
---
# <a name="add-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="907aa-102">向报表添加 HTML（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="907aa-102">Add HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="907aa-103">可以使用占位符从数据集中的字段导入 HTML 以在报表中使用。</span><span class="sxs-lookup"><span data-stu-id="907aa-103">Using a placeholder, you can import HTML from a field in your dataset for use in the report.</span></span> <span data-ttu-id="907aa-104">默认情况下，占位符表示纯文本，因此需要将占位符的标记类型改为 HTML。</span><span class="sxs-lookup"><span data-stu-id="907aa-104">By default, a placeholder represents plain text, so you will need to change the placeholder mark-up type to HTML.</span></span> <span data-ttu-id="907aa-105">有关详细信息，请参阅[将 HTML 导入报表（报表生成器和 SSRS）](importing-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="907aa-105">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-html-from-a-field-in-your-dataset-into-a-text-box"></a><span data-ttu-id="907aa-106">将 HTML 从数据集中的字段添加到文本框中</span><span class="sxs-lookup"><span data-stu-id="907aa-106">To add HTML from a field in your dataset into a text box</span></span>  
  
1.  <span data-ttu-id="907aa-107">在 **“插入”** 选项卡上，单击 **“列表”** 。</span><span class="sxs-lookup"><span data-stu-id="907aa-107">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="907aa-108">单击设计图面，然后拖动鼠标根据所需大小创建一个文本框。</span><span class="sxs-lookup"><span data-stu-id="907aa-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
     <span data-ttu-id="907aa-109">此时将打开 **“数据集属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="907aa-109">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="907aa-110">可以使用共享数据集或嵌入在报表中的数据集。</span><span class="sxs-lookup"><span data-stu-id="907aa-110">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="907aa-111">有关详细信息，请单击[“数据集属性”对话框 ->“查询”（报表生成器）](../report-data/dataset-properties-dialog-box-query-report-builder.md)或[“数据集属性”对话框 ->“查询”](../dataset-properties-dialog-box-query.md)。</span><span class="sxs-lookup"><span data-stu-id="907aa-111">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="907aa-112">在 **“插入”** 选项卡上，单击 **“文本框”** 。</span><span class="sxs-lookup"><span data-stu-id="907aa-112">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="907aa-113">在列表中单击，然后拖动鼠标根据所需大小创建一个文本框。</span><span class="sxs-lookup"><span data-stu-id="907aa-113">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="907aa-114">将数据集中的 HTML 字段拖到文本框中。</span><span class="sxs-lookup"><span data-stu-id="907aa-114">Drag an HTML field from your dataset into the text box.</span></span> <span data-ttu-id="907aa-115">此时将为您的字段创建一个占位符。</span><span class="sxs-lookup"><span data-stu-id="907aa-115">A placeholder is created for your field.</span></span>  
  
4.  <span data-ttu-id="907aa-116">右键单击该占位符，然后单击“占位符属性”  。</span><span class="sxs-lookup"><span data-stu-id="907aa-116">Right-click the placeholder, and then click **Placeholder Properties**.</span></span>  
  
5.  <span data-ttu-id="907aa-117">在 **“常规”** 选项卡中，确保 **“值”** 框中包含要对您在步骤 3 中所放置字段进行比较的表达式。</span><span class="sxs-lookup"><span data-stu-id="907aa-117">On the **General** tab, verify that the **Value** box contains an expression that evaluates to the field you dropped in step 3.</span></span>  
  
6.  <span data-ttu-id="907aa-118">单击“HTML - 将 HTML 标记解释为样式”  。</span><span class="sxs-lookup"><span data-stu-id="907aa-118">Click **HTML - Interpret HTML tags as styles**.</span></span> <span data-ttu-id="907aa-119">这会使字段被视为 HTML。</span><span class="sxs-lookup"><span data-stu-id="907aa-119">This causes the field to be evaluated as HTML.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="907aa-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="907aa-120">See Also</span></span>  
 <span data-ttu-id="907aa-121">[设置数字和日期格式（报表生成器和 SSRS）](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="907aa-121">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="907aa-122">[设置线条、颜色和图像的格式（报表生成器和 SSRS）](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="907aa-122">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="907aa-123">“占位符属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="907aa-123">Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
