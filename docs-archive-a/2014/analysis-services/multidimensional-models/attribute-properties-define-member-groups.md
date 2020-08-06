---
title: 定义成员组 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95f9516c7a0077e97af348afa863fe15c8d4528b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693556"
---
# <a name="define-member-groups"></a><span data-ttu-id="78359-102">定义成员组</span><span class="sxs-lookup"><span data-stu-id="78359-102">Define Member Groups</span></span>
  <span data-ttu-id="78359-103">如果属性有很多成员，可以选择将这些成员分组到存储桶中，以减少用户在浏览某个层次结构中的数据时看到的成员数。</span><span class="sxs-lookup"><span data-stu-id="78359-103">If an attribute has a large number of members, you can choose to group those members into buckets, reducing the number of members that users see when they browse the data in a hierarchy.</span></span> <span data-ttu-id="78359-104">确定用于放置成员组的存储桶的数目，并为存储桶设置命名架构。</span><span class="sxs-lookup"><span data-stu-id="78359-104">You can also determine the number of buckets in which the members are groups and set a naming scheme for the buckets.</span></span> <span data-ttu-id="78359-105">有关详细信息，请参阅[对属性成员分组（离散化）](attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="78359-105">For more information, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
 <span data-ttu-id="78359-106">可以通过设置 **DiscretizationMethod** 属性来将成员分组，该属性可通过 **中的** “属性” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]窗口访问。</span><span class="sxs-lookup"><span data-stu-id="78359-106">You group members by setting the **DiscretizationMethod** property, which is accessed through the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="78359-107">创建成员组时，所做更改只有在处理了维度后才能供用户使用。</span><span class="sxs-lookup"><span data-stu-id="78359-107">When you create member groups, your changes are not available to users until you process the dimension.</span></span> <span data-ttu-id="78359-108">有关详细信息，请参阅[多维模型对象处理](processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="78359-108">For more information, see [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-create-member-groups"></a><span data-ttu-id="78359-109">创建成员组</span><span class="sxs-lookup"><span data-stu-id="78359-109">To create member groups</span></span>  
  
1.  <span data-ttu-id="78359-110">打开要使用的维度。</span><span class="sxs-lookup"><span data-stu-id="78359-110">Open the dimension that you want to work with.</span></span> <span data-ttu-id="78359-111">默认情况下，将打开 **“维度结构”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="78359-111">The **Dimension Structure** tab opens by default.</span></span>  
  
2.  <span data-ttu-id="78359-112">在“属性”\*\*\*\* 中，右键单击要对其成员进行分组的属性，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78359-112">In **Attributes**, right-click the attribute whose members you want to group, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="78359-113">从 **DiscretizationMethod**旁边的下拉列表中，选择对成员分组时所用的方法。</span><span class="sxs-lookup"><span data-stu-id="78359-113">From the drop-down list next to **DiscretizationMethod**, select a method by which to group the members.</span></span> <span data-ttu-id="78359-114">有关 **DiscretizationMethod** 设置的详细信息，请参阅[对属性成员分组（离散化）](attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="78359-114">For more information about **DiscretizationMethod** settings, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
  
