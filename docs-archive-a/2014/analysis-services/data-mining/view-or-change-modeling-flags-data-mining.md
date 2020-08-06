---
title: 查看或更改数据挖掘)  (建模标志 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf0edd827321685a2d6a9041759328a7ac6e7cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690236"
---
# <a name="view-or-change-modeling-flags-data-mining"></a><span data-ttu-id="36064-102">查看或更改建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="36064-102">View or Change Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="36064-103">建模标志是在挖掘结构列或挖掘模型列上设置的属性，用于控制分析期间算法处理数据的方式。</span><span class="sxs-lookup"><span data-stu-id="36064-103">Modeling flags are properties that you set on a mining structure column or mining model columns to control how the algorithm processes the data during analysis.</span></span>  
  
 <span data-ttu-id="36064-104">在数据挖掘设计器中，通过查看结构或模型的属性，可以查看和修改与挖掘结构或挖掘列关联的建模标志。</span><span class="sxs-lookup"><span data-stu-id="36064-104">In Data Mining Designer, you can view and modify the modeling flags associated with a mining structure or mining column by viewing the properties of the structure or model.</span></span> <span data-ttu-id="36064-105">还可以通过使用 DMX、AMO 或 XMLA 设置建模标志。</span><span class="sxs-lookup"><span data-stu-id="36064-105">You can also set modeling flags by using DMX, AMO, or XMLA.</span></span>  
  
 <span data-ttu-id="36064-106">此过程说明如何在设计器中更改建模标志。</span><span class="sxs-lookup"><span data-stu-id="36064-106">This procedure describes how to change the modeling flags in the designer.</span></span>  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a><span data-ttu-id="36064-107">查看或更改结构列或模型列的建模标志</span><span class="sxs-lookup"><span data-stu-id="36064-107">View or change the modeling flag for a structure column or model column</span></span>  
  
1.  <span data-ttu-id="36064-108">在 SQL Server Design Studio 中，打开解决方案资源管理器，然后双击挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="36064-108">In SQL Server Design Studio, open Solution Explorer, and then double-click the mining structure.</span></span>  
  
2.  <span data-ttu-id="36064-109">若要设置 NOT NULL 建模标志，请单击 "**挖掘结构**" 选项卡。若要设置回归量或 MODEL_EXISTENCE_ONLY 标志，请单击 "**挖掘模型**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="36064-109">To set the NOT NULL modeling flag, click the **Mining Structure** tab. To set the REGRESSOR or MODEL_EXISTENCE_ONLY flags, click the **Mining Model** tab.</span></span>  
  
3.  <span data-ttu-id="36064-110">右键单击要查看或更改的列，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="36064-110">Right-click the column you want to view or change, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="36064-111">若要添加新的建模标志，请单击 **“建模标志”** 属性旁边的文本框，然后选择要使用的建模标志的复选框。</span><span class="sxs-lookup"><span data-stu-id="36064-111">To add a new modeling flag, click the text box next to the **ModelingFlags** property, and select the check box or check boxes for the modeling flags you want to use.</span></span>  
  
     <span data-ttu-id="36064-112">建模标志只有在它们适合列数据类型时才显示。</span><span class="sxs-lookup"><span data-stu-id="36064-112">Modeling flags are displayed only if they are appropriate for the column data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36064-113">更改某个建模标志后，您必须重新处理该模型。</span><span class="sxs-lookup"><span data-stu-id="36064-113">After you change a modeling flag, you must reprocess the model.</span></span>  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a><span data-ttu-id="36064-114">获取模型中使用的建模标志</span><span class="sxs-lookup"><span data-stu-id="36064-114">Get the modeling flags used in the model</span></span>  
  
-   <span data-ttu-id="36064-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开 DMX 查询窗口，然后键入类似以下内容的查询：</span><span class="sxs-lookup"><span data-stu-id="36064-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window, and type a query like the following:</span></span>  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36064-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36064-116">See Also</span></span>  
 <span data-ttu-id="36064-117">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="36064-117">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="36064-118">建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="36064-118">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
  
