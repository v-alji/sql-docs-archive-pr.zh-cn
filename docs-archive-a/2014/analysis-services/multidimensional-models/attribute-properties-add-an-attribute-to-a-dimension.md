---
title: 将属性添加到维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
author: minewiskan
ms.author: owend
ms.openlocfilehash: 776591e94deedc679592cfe36d53fb1fea4093d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590954"
---
# <a name="add-an--attribute-to-a-dimension"></a><span data-ttu-id="30dbd-102">向维度中添加属性</span><span class="sxs-lookup"><span data-stu-id="30dbd-102">Add an  Attribute to a Dimension</span></span>
  <span data-ttu-id="30dbd-103">可以在中自动或手动将属性添加到维度中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="30dbd-103">You can add an attribute to a dimension either automatically or manually in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="30dbd-104">若要自动创建属性，请在 **的维度设计器的** “维度结构” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡中，选择要映射到属性的列，然后将该列从 **“数据源视图”** 窗格中拖到 **“属性”** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="30dbd-104">To create an attribute automatically, on the **Dimension Structure** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the column that you want to map to an attribute, and then drag that column from the **Data Source View** pane to the **Attributes** pane.</span></span> <span data-ttu-id="30dbd-105">这样便可创建映射到该列的属性，并为属性分配与该列名称相同的名称。</span><span class="sxs-lookup"><span data-stu-id="30dbd-105">This creates an attribute that is mapped to the column, and assigns the same name to the attribute as the name of the column.</span></span> <span data-ttu-id="30dbd-106">如果已经存在使用该名称的属性，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会在重复的名称之后添加一个序号后缀，针对第一个重复的名称添加“1”，以此类推。</span><span class="sxs-lookup"><span data-stu-id="30dbd-106">If an attribute that uses that name already exists, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adds an ordinal number suffix, starting with "1" for the first duplicate name.</span></span>  
  
 <span data-ttu-id="30dbd-107">若要手动创建属性，请将 **“属性”** 窗格设置为网格视图。</span><span class="sxs-lookup"><span data-stu-id="30dbd-107">To create an attribute manually, set the **Attributes** pane to grid view.</span></span> <span data-ttu-id="30dbd-108">在网格中最后一行的 "名称" 列中，单击该 **\<new attribute>** 项目。</span><span class="sxs-lookup"><span data-stu-id="30dbd-108">In the name column of the last row in the grid, click the **\<new attribute>** item.</span></span> <span data-ttu-id="30dbd-109">为新属性键入名称。</span><span class="sxs-lookup"><span data-stu-id="30dbd-109">Type a name for the new attribute.</span></span> <span data-ttu-id="30dbd-110">这样便可创建未映射到列的特性，并且该特性的所有属性都具有默认设置。</span><span class="sxs-lookup"><span data-stu-id="30dbd-110">This creates an attribute that is not mapped to a column and that has default settings for all its properties.</span></span> <span data-ttu-id="30dbd-111">在 **的** “属性” [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 窗口中，您可以通过配置新特性的 **KeyColumns** 属性来设置映射。</span><span class="sxs-lookup"><span data-stu-id="30dbd-111">You can set the mapping in the **Properties** window of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] by configuring the **KeyColumns** property for the new attribute.</span></span>  
  
 <span data-ttu-id="30dbd-112">有关详细信息，请参阅 [自动定义新属性](attribute-properties-define-a-new-attribute-automatically.md)、 [手动定义新属性](../define-a-new-attribute-manually.md)、 [将属性绑定到名称列](attribute-properties-bind-an-attribute-to-a-name-column.md)和 [修改某个特性的 KeyColumn 属性](attribute-properties-modify-the-keycolumn-property.md)。</span><span class="sxs-lookup"><span data-stu-id="30dbd-112">For more information, see [Define a New Attribute Automatically](attribute-properties-define-a-new-attribute-automatically.md), [Define a New Attribute Manually](../define-a-new-attribute-manually.md), [Bind an Attribute to a Name Column](attribute-properties-bind-an-attribute-to-a-name-column.md), and [Modify the KeyColumn Property of an Attribute](attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dbd-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30dbd-113">See Also</span></span>  
 [<span data-ttu-id="30dbd-114">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="30dbd-114">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
