---
title: 多维模型中的透视 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2d4be87ddbd691710b361d8b07d225bce37659fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579844"
---
# <a name="perspectives-in-multidimensional-models"></a><span data-ttu-id="6c693-102">多维模型中的透视</span><span class="sxs-lookup"><span data-stu-id="6c693-102">Perspectives in Multidimensional Models</span></span>
  <span data-ttu-id="6c693-103">透视是为特定应用程序或用户组创建的多维数据集的子集。</span><span class="sxs-lookup"><span data-stu-id="6c693-103">A perspective is a subset of a cube created for a particular application or group of users.</span></span> <span data-ttu-id="6c693-104">多维数据集本身是一个默认的透视。</span><span class="sxs-lookup"><span data-stu-id="6c693-104">The cube itself is the default perspective.</span></span> <span data-ttu-id="6c693-105">透视针对客户端显示为一个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6c693-105">A perspective is exposed to a client as a cube.</span></span> <span data-ttu-id="6c693-106">当用户查看透视时，该透视看上去像另一个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6c693-106">When a user views a perspective, it appears like another cube.</span></span> <span data-ttu-id="6c693-107">在透视中通过写回对多维数据集数据所做的任何更改也会作用于原始多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6c693-107">Any changes made to cube data through writeback in the perspective are to the original cube.</span></span> <span data-ttu-id="6c693-108">有关 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中视图的详细信息，请参阅 [透视图](../multidimensional-models-olap-logical-cube-objects/perspectives.md)。</span><span class="sxs-lookup"><span data-stu-id="6c693-108">For more information about the views in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Perspectives](../multidimensional-models-olap-logical-cube-objects/perspectives.md).</span></span>  
  
 <span data-ttu-id="6c693-109">使用多维数据集设计器的 **“透视”** 选项卡，可以创建或修改多维数据集中的透视。</span><span class="sxs-lookup"><span data-stu-id="6c693-109">Use the **Perspectives** tab in Cube Designer to create or modify perspectives in a cube.</span></span> <span data-ttu-id="6c693-110">**“透视”** 选项卡的第一列是 **“多维数据集对象”** 列，该列列出多维数据集中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="6c693-110">The first column of the **Perspectives** tab is the **Cube Objects** column, which lists all the objects in the cube.</span></span> <span data-ttu-id="6c693-111">这对应于多维数据集的默认透视，该透视是多维数据集本身。</span><span class="sxs-lookup"><span data-stu-id="6c693-111">This corresponds to the default perspective for the cube, which is the cube itself.</span></span>  
  
## <a name="creating-or-deleting-perspectives"></a><span data-ttu-id="6c693-112">创建或删除透视</span><span class="sxs-lookup"><span data-stu-id="6c693-112">Creating or Deleting Perspectives</span></span>  
 <span data-ttu-id="6c693-113">您可以通过在 **“多维数据集”** 菜单中单击 **“新建透视”** ，将某个透视添加到 **“透视”** 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="6c693-113">You can add a perspective to the **Perspectives** tab by clicking **New Perspective** on the **Cube** menu.</span></span> <span data-ttu-id="6c693-114">还可以单击工具栏上的“新建透视图”\*\*\*\* 按钮，或者右键单击窗格中的任意位置，再单击快捷菜单中的“新建透视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c693-114">You can also click the **New Perspective** button on the toolbar, or right-click anywhere in the pane and click **New Perspective** on the shortcut menu.</span></span> <span data-ttu-id="6c693-115">您可以向多维数据集中添加任意数量的透视。</span><span class="sxs-lookup"><span data-stu-id="6c693-115">You can add any number of perspectives to a cube.</span></span>  
  
 <span data-ttu-id="6c693-116">若要删除透视，请首先单击要删除的透视的列中的任意单元。</span><span class="sxs-lookup"><span data-stu-id="6c693-116">To remove a perspective, first click any cell in the column for the perspective that you want to delete.</span></span> <span data-ttu-id="6c693-117">然后在 **“多维数据集”** 菜单中，单击 **“删除透视”**。</span><span class="sxs-lookup"><span data-stu-id="6c693-117">Then, on the **Cube** menu, click **Delete Perspective**.</span></span> <span data-ttu-id="6c693-118">还可以单击工具栏上的“删除透视图”\*\*\*\* 按钮，或者右键单击要删除的透视图中的任意单元格，再单击快捷菜单中的“删除透视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c693-118">You can also click the **Delete Perspective** button on the toolbar, or right-click any cell in the perspective you want to delete, and then click **Delete Perspective** on the shortcut menu.</span></span>  
  
## <a name="renaming-perspectives"></a><span data-ttu-id="6c693-119">重命名透视</span><span class="sxs-lookup"><span data-stu-id="6c693-119">Renaming Perspectives</span></span>  
 <span data-ttu-id="6c693-120">每个透视的第一行都显示该透视的名称。</span><span class="sxs-lookup"><span data-stu-id="6c693-120">The first row of each perspective shows its name.</span></span> <span data-ttu-id="6c693-121">当您创建透视时，最初的名称便是“Perspective”（如果已经存在名为“Perspective”的透视，则在该名称后面紧跟以 1 开始的序号）。</span><span class="sxs-lookup"><span data-stu-id="6c693-121">When you create a perspective, the name is initially Perspective (followed by an ordinal number, starting with 1, if there is already a perspective called Perspective).</span></span> <span data-ttu-id="6c693-122">您可以单击名称对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="6c693-122">You can click the name to edit it.</span></span>  
  
## <a name="hiding-objects-from-a-perspective"></a><span data-ttu-id="6c693-123">对透视隐藏对象</span><span class="sxs-lookup"><span data-stu-id="6c693-123">Hiding Objects from a Perspective</span></span>  
 <span data-ttu-id="6c693-124">若要对透视隐藏对象，请清除与透视列中的对象对应的行中的复选框。</span><span class="sxs-lookup"><span data-stu-id="6c693-124">To hide an object from a perspective, clear the check box in the row that corresponds to the object in the column for the perspective.</span></span> <span data-ttu-id="6c693-125">可以对透视隐藏的多维数据集对象包括：</span><span class="sxs-lookup"><span data-stu-id="6c693-125">The cube objects that can be hidden from a perspective are:</span></span>  
  
-   <span data-ttu-id="6c693-126">度量值组</span><span class="sxs-lookup"><span data-stu-id="6c693-126">Measure groups</span></span>  
  
-   <span data-ttu-id="6c693-127">度量值</span><span class="sxs-lookup"><span data-stu-id="6c693-127">Measures</span></span>  
  
-   <span data-ttu-id="6c693-128">维度</span><span class="sxs-lookup"><span data-stu-id="6c693-128">Dimensions</span></span>  
  
-   <span data-ttu-id="6c693-129">层次结构</span><span class="sxs-lookup"><span data-stu-id="6c693-129">Hierarchies</span></span>  
  
-   <span data-ttu-id="6c693-130">命名集</span><span class="sxs-lookup"><span data-stu-id="6c693-130">Named sets</span></span>  
  
-   <span data-ttu-id="6c693-131">KPI</span><span class="sxs-lookup"><span data-stu-id="6c693-131">KPIs</span></span>  
  
-   <span data-ttu-id="6c693-132">操作</span><span class="sxs-lookup"><span data-stu-id="6c693-132">Actions</span></span>  
  
-   <span data-ttu-id="6c693-133">计算成员</span><span class="sxs-lookup"><span data-stu-id="6c693-133">Calculated members</span></span>  
  
 <span data-ttu-id="6c693-134">若要查看任意对象，请展开“多维数据集对象”\*\*\*\* 下任意对象类型的类别（“度量值组”\*\*\*\*、“维度”\*\*\*\*、“KPI”\*\*\*\*、“计算”\*\*\*\* 或“操作”\*\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="6c693-134">To view any object, expand the category (**Measure Groups**, **Dimensions**, **KPIs**, **Calculations**, or **Actions**) for any object type under **Cube Objects**.</span></span> <span data-ttu-id="6c693-135">若要查看维度中的层次结构或属性，请首先展开维度，然后展开 **“层次结构”** 或 **“属性”** 行。</span><span class="sxs-lookup"><span data-stu-id="6c693-135">To view hierarchies or attributes in a dimension, first expand a dimension, and then expand the **Hierarchies** or **Attributes** row.</span></span> <span data-ttu-id="6c693-136">若要查看度量值组中的度量值，请展开度量值组。</span><span class="sxs-lookup"><span data-stu-id="6c693-136">To view measures in a measure group, expand the measure group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c693-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c693-137">See Also</span></span>  
 [<span data-ttu-id="6c693-138">多维模型中的多维数据集</span><span class="sxs-lookup"><span data-stu-id="6c693-138">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
