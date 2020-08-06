---
title: 将列映射到复合域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a665b2096579c9da35a1b69be46c4ba6103610f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589792"
---
# <a name="map-columns-to-composite-domains"></a><span data-ttu-id="c8a9f-102">将列映射到复合域</span><span class="sxs-lookup"><span data-stu-id="c8a9f-102">Map Columns to Composite Domains</span></span>
  <span data-ttu-id="c8a9f-103">一个复合域包含两个或多个单一域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-103">A composite domain consists of two or more single domains.</span></span> <span data-ttu-id="c8a9f-104">您可以将多个列映射到域，也可以将具有分隔值的单个列映射到域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-104">You can map multiple columns to the domain, or you can map a single column with delimited values to the domain.</span></span>  
  
 <span data-ttu-id="c8a9f-105">当您具有多个列时，必须将一个列映射到复合域中的每个单一域，以便应用复合域规则来执行数据清理。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-105">When you have multiple columns, you must map a column to each single domain in the composite domain to apply the composite domain rules to data cleansing.</span></span> <span data-ttu-id="c8a9f-106">在数据质量客户端中选择复合域中包含的单一域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-106">You select the single domains contained in the composite domain, in the Data Quality Client.</span></span> <span data-ttu-id="c8a9f-107">有关详细信息，请参阅 [创建复合域](../../../data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-107">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="c8a9f-108">在您具有含分隔值的单个列时，必须将该单个列映射到复合域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-108">When you have a single column with delimited values, you must map the single column to the composite domain.</span></span> <span data-ttu-id="c8a9f-109">这些值的出现顺序必须与单一域在复合域中的出现顺序相同。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-109">The values must appear in the same order as the single domains appear in the composite domain.</span></span> <span data-ttu-id="c8a9f-110">数据源中的分隔符必须匹配用于解析复合域值的分隔符。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-110">The delimiter in the data source must match the delimiter that is used to parse the composite domain values.</span></span> <span data-ttu-id="c8a9f-111">在数据质量客户端中为复合域选择分隔符，以及设置其他属性。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-111">You select the delimiter for the composite domain, as well as set other properties, in the Data Quality Client.</span></span> <span data-ttu-id="c8a9f-112">有关详细信息，请参阅 [创建复合域](../../../data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-112">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
### <a name="to-map-multiple-columns-to-a-composite-domain"></a><span data-ttu-id="c8a9f-113">将多个列映射到一个复合域</span><span class="sxs-lookup"><span data-stu-id="c8a9f-113">To map multiple columns to a composite domain</span></span>  
  
1.  <span data-ttu-id="c8a9f-114">右键单击 DQS 清理转换，然后单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-114">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="c8a9f-115">在 **“连接管理器”** 选项卡上，确认复合域显示在可用域列表中。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-115">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="c8a9f-116">在 **“映射”** 选项卡上，在 **“可用输入列”** 区域中选择列。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-116">On the **Mapping** tab, select the columns in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="c8a9f-117">对于 **“输入列”** 字段中列出的每个列，在 **“域”** 字段中选择一个单一域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-117">For each column listed in the **Input Column** field, select a single domain in the **Domain** field.</span></span> <span data-ttu-id="c8a9f-118">仅选择处于复合域中的单一域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-118">Select only single domains that are in the composite domain.</span></span>  
  
5.  <span data-ttu-id="c8a9f-119">根据需要，修改在 **“源别名”** 、 **“输出别名”** 和 **“状态别名”** 字段中出现的名称。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-119">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="c8a9f-120">根据需要，在 **“高级”** 选项卡上设置属性。有关属性的详细信息，请参阅 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-120">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a><span data-ttu-id="c8a9f-121">将具有分隔值的列映射到复合域</span><span class="sxs-lookup"><span data-stu-id="c8a9f-121">To map a column with delimited values to a composite domain</span></span>  
  
1.  <span data-ttu-id="c8a9f-122">右键单击 DQS 清理转换，然后单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-122">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="c8a9f-123">在 **“连接管理器”** 选项卡上，确认复合域显示在可用域列表中。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-123">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="c8a9f-124">在 **“映射”** 选项卡上，在 **“可用输入列”** 区域中选择列。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-124">On the **Mapping** tab, select the column in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="c8a9f-125">对于 **“输入列”** 字段中列出的列，在 **“域”** 字段中选择复合域。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-125">For the column listed in the **Input Column** field, select the composite domain in the **Domain** field.</span></span>  
  
5.  <span data-ttu-id="c8a9f-126">根据需要，修改在 **“源别名”** 、 **“输出别名”** 和 **“状态别名”** 字段中出现的名称。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-126">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="c8a9f-127">根据需要，在 **“高级”** 选项卡上设置属性。有关属性的详细信息，请参阅 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="c8a9f-127">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a9f-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8a9f-128">See Also</span></span>  
 [<span data-ttu-id="c8a9f-129">DQS 清理转换</span><span class="sxs-lookup"><span data-stu-id="c8a9f-129">DQS Cleansing Transformation</span></span>](dqs-cleansing-transformation.md)  
  
  
