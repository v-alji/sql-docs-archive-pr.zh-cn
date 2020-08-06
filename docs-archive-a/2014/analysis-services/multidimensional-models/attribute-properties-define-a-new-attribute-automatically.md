---
title: 自动定义新属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40f9ae1f00dd0a6520c6d1b06111864fba02e8f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693562"
---
# <a name="define-a-new-attribute-automatically"></a><span data-ttu-id="76347-102">自动定义新属性</span><span class="sxs-lookup"><span data-stu-id="76347-102">Define a New Attribute Automatically</span></span>
  <span data-ttu-id="76347-103">可以在维度设计器中使用拖放编辑功能，在某个维度中创建新属性。</span><span class="sxs-lookup"><span data-stu-id="76347-103">You can create a new attribute in a dimension by using drag-and-drop editing in the Dimension Designer.</span></span>  
  
### <a name="to-create-a-new-attribute-automatically"></a><span data-ttu-id="76347-104">自动创建新的属性</span><span class="sxs-lookup"><span data-stu-id="76347-104">To create a new attribute automatically</span></span>  
  
1.  <span data-ttu-id="76347-105">在维度设计器中，打开要在其中创建属性的维度。</span><span class="sxs-lookup"><span data-stu-id="76347-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="76347-106">在 **“维度结构”** 选项卡上，从 **“数据源视图”** 窗格内要将属性绑定到的表中，选择相应的列，然后将该列拖至 **“属性”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="76347-106">On the **Dimension Structure** tab, in the **Data Source View** pane, in the table to which you want to bind the attribute, select the column, and then drag the column to the **Attributes** pane.</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="76347-107">将创建新属性，其名称与其绑定到的列的名称相同。</span><span class="sxs-lookup"><span data-stu-id="76347-107">creates the new attribute that has the same name as the column to which it is bound.</span></span> <span data-ttu-id="76347-108">如果多个属性使用相同的列，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在属性名称后面加一个数字。</span><span class="sxs-lookup"><span data-stu-id="76347-108">If there are multiple attributes that use the same column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] appends a number to the attribute name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76347-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76347-109">See Also</span></span>  
 <span data-ttu-id="76347-110">[多维模型中的维度](dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="76347-110">[Dimensions in Multidimensional Models](dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="76347-111">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="76347-111">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
