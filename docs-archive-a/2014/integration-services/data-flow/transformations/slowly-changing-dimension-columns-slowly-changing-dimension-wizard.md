---
title: 渐变维度列（渐变维度向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6283887cbddb9844e0ac769281184f588dc2a94d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682964"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a><span data-ttu-id="ccd37-102">渐变维度列（渐变维度向导）</span><span class="sxs-lookup"><span data-stu-id="ccd37-102">Slowly Changing Dimension Columns (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="ccd37-103">可以使用 **“渐变维度列”** 对话框，为每个渐变维度列选择更改类型。</span><span class="sxs-lookup"><span data-stu-id="ccd37-103">Use the **Slowly Changing Dimensions Columns** dialog box to select a change type for each slowly changing dimension column.</span></span>  
  
 <span data-ttu-id="ccd37-104">若要了解有关此向导的详细信息，请参阅 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd37-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ccd37-105">选项</span><span class="sxs-lookup"><span data-stu-id="ccd37-105">Options</span></span>  
 <span data-ttu-id="ccd37-106">**维度列**</span><span class="sxs-lookup"><span data-stu-id="ccd37-106">**Dimension Columns**</span></span>  
 <span data-ttu-id="ccd37-107">从列表中选择维度列。</span><span class="sxs-lookup"><span data-stu-id="ccd37-107">Select a dimension column from the list.</span></span>  
  
 <span data-ttu-id="ccd37-108">**更改类型**</span><span class="sxs-lookup"><span data-stu-id="ccd37-108">**Change Type**</span></span>  
 <span data-ttu-id="ccd37-109">选择“固定的属性”，或从两种变化的属性类型中选择一种类型。 </span><span class="sxs-lookup"><span data-stu-id="ccd37-109">Select a **Fixed Attribute**, or select one of the two types of changing attributes.</span></span> <span data-ttu-id="ccd37-110">在不需要更改列中的值时，请使用 **“固定的属性”** ；设置后， [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 会将更改视为错误。</span><span class="sxs-lookup"><span data-stu-id="ccd37-110">Use **Fixed Attribute** when the value in a column should not change; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] then treats changes as errors.</span></span> <span data-ttu-id="ccd37-111">若要使用更改后的值覆盖现有的值，请使用 **“变化的属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ccd37-111">Use **Changing Attribute** to overwrite existing values with changed values.</span></span> <span data-ttu-id="ccd37-112">若要在新记录中保存更改后的值，并将以前的记录标记为已过时，请使用 **“历史属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ccd37-112">Use **Historical Attribute** to save changed values in new records, while marking previous records as outdated.</span></span>  
  
 <span data-ttu-id="ccd37-113">**删除**</span><span class="sxs-lookup"><span data-stu-id="ccd37-113">**Remove**</span></span>  
 <span data-ttu-id="ccd37-114">选择一个维度列，通过单击“删除”可以将其从映射列的列表中删除。 </span><span class="sxs-lookup"><span data-stu-id="ccd37-114">Select a dimension column, and remove it from the list of mapped columns by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd37-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ccd37-115">See Also</span></span>  
 [<span data-ttu-id="ccd37-116">使用渐变维度向导配置输出</span><span class="sxs-lookup"><span data-stu-id="ccd37-116">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
