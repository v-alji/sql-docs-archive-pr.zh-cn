---
title: 链接度量值组 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linked measure groups [Analysis Services]
- referencing measure groups
- Linked Measure Group Wizard
- measure groups [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: 7f838452-8669-4194-8e15-7afdc7f15251
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2a7d7443b8c25f5cbafa5af83364ef05d8053145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587066"
---
# <a name="linked-measure-groups"></a><span data-ttu-id="84ac9-102">链接度量值组</span><span class="sxs-lookup"><span data-stu-id="84ac9-102">Linked Measure Groups</span></span>
  <span data-ttu-id="84ac9-103">链接度量值组基于同一数据库内不同多维数据集中的另一度量值组，或基于一个不同的 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="84ac9-103">A linked measure group is based on another measure group in a different cube within the same database or a different Analysis Services database.</span></span> <span data-ttu-id="84ac9-104">如果要在多个多维数据集中重用一组度量值以及对应的数据值，可能使用链接度量值组。</span><span class="sxs-lookup"><span data-stu-id="84ac9-104">You might use a linked measure group if you want to reuse a set of measures, and the corresponding data values, in multiple cubes.</span></span>  
  
 <span data-ttu-id="84ac9-105">Microsoft 建议原始和链接度量值组驻留于在同一台服务器上运行的解决方案中。</span><span class="sxs-lookup"><span data-stu-id="84ac9-105">Microsoft recommends that the original and linked measure groups reside in solutions that run on the same server.</span></span> <span data-ttu-id="84ac9-106">在将来的版本中，将计划在远程服务器上链接到度量值组， (参阅[SQL Server 2014) 中的弃用 Analysis Services 功能](../deprecated-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="84ac9-106">Linking to a measure group on a remote server is scheduled for deprecation in a future release (see [Deprecated Analysis Services Features in SQL Server 2014](../deprecated-analysis-services-features-in-sql-server-2014.md)).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84ac9-107">链接度量值组为只读的。</span><span class="sxs-lookup"><span data-stu-id="84ac9-107">Linked measure groups are read-only.</span></span> <span data-ttu-id="84ac9-108">要获得最新更改，您必须基于已修改的源对象删除并重新创建所有链接度量值组。</span><span class="sxs-lookup"><span data-stu-id="84ac9-108">To pick up the latest changes, you must delete and recreate all linked measure groups based on the modified source object.</span></span> <span data-ttu-id="84ac9-109">因此，在以后需要修改度量值组时，应考虑是否可以采用在两个项目间复制和粘贴度量值组这个替代方法。</span><span class="sxs-lookup"><span data-stu-id="84ac9-109">For this reason, copy and pasting measure groups between projects is an alternative approach that you should consider in case future modifications to the measure group are required.</span></span>  
  
## <a name="usage-limitations"></a><span data-ttu-id="84ac9-110">使用限制</span><span class="sxs-lookup"><span data-stu-id="84ac9-110">Usage Limitations</span></span>  
 <span data-ttu-id="84ac9-111">如前所述，使用链接度量值的一个重要约束是无法直接自定义链接度量值。</span><span class="sxs-lookup"><span data-stu-id="84ac9-111">As noted previously, an important constraint to using linked measures is an inability to customize a linked measure directly.</span></span> <span data-ttu-id="84ac9-112">对数据类型、格式、数据绑定和可见性以及度量值组本身中项目的成员身份的修改都是必须在原始度量值组中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="84ac9-112">Modifications to the data type, format, data binding, and visibility, as well as membership of the items in the measure group itself, are all changes that must be made in the original measure group.</span></span>  
  
 <span data-ttu-id="84ac9-113">根据需要，在客户端应用程序对其进行访问时，链接度量值组与其他度量值组相同，并且其查询方式与其他度量值组的查询方式相同。</span><span class="sxs-lookup"><span data-stu-id="84ac9-113">Operationally, linked measure groups are identical to other measure groups when accessed by client applications, and are queried in the same manner as other measure groups.</span></span>  
  
 <span data-ttu-id="84ac9-114">查询包含链接度量值组的多维数据集时，会在目标多维数据集的第一次计算传递期间建立和解析链接。</span><span class="sxs-lookup"><span data-stu-id="84ac9-114">When you query a cube that contains a linked measure group, the link is established and resolved during the first calculation pass of the destination cube.</span></span> <span data-ttu-id="84ac9-115">受此行为影响，任何存储在链接度量值组中的计算都不会在计算查询之前进行解析；</span><span class="sxs-lookup"><span data-stu-id="84ac9-115">Because of this behavior, any calculations that are stored in the linked measure group cannot be resolved before the query is evaluated.</span></span> <span data-ttu-id="84ac9-116">换言之，必须在目标多维数据集中重新创建计算度量值和计算单元，而不是从源多维数据集中继承。</span><span class="sxs-lookup"><span data-stu-id="84ac9-116">In other words, calculated measures and calculated cells must be recreated in the destination cube rather than inherited from the source cube.</span></span>  
  
 <span data-ttu-id="84ac9-117">下面的列表汇总了使用限制。</span><span class="sxs-lookup"><span data-stu-id="84ac9-117">The following list summarizes usage limitations.</span></span>  
  
-   <span data-ttu-id="84ac9-118">不能通过另一个链接度量值组创建链接度量值组。</span><span class="sxs-lookup"><span data-stu-id="84ac9-118">You cannot create a linked measure group from another linked measure group.</span></span>  
  
-   <span data-ttu-id="84ac9-119">无法在链接度量值组中添加或删除度量值。</span><span class="sxs-lookup"><span data-stu-id="84ac9-119">You cannot add or remove measures in a linked measure group.</span></span> <span data-ttu-id="84ac9-120">成员身份仅在原始度量值组中定义。</span><span class="sxs-lookup"><span data-stu-id="84ac9-120">Membership is defined only in the original measure group.</span></span>  
  
-   <span data-ttu-id="84ac9-121">链接度量值组中不支持写回。</span><span class="sxs-lookup"><span data-stu-id="84ac9-121">Writeback is not supported in linked measure groups.</span></span>  
  
-   <span data-ttu-id="84ac9-122">链接度量值组无法在多个多对多关系中使用（尤其是在这些关系处于不同多维数据集中时）。</span><span class="sxs-lookup"><span data-stu-id="84ac9-122">Linked measure groups cannot be used in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="84ac9-123">这样做可能导致不明确的聚合。</span><span class="sxs-lookup"><span data-stu-id="84ac9-123">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="84ac9-124">有关详细信息，请参阅 [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)（包含多对多关系的多维数据集中链接度量值的不正确数量）。</span><span class="sxs-lookup"><span data-stu-id="84ac9-124">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
 <span data-ttu-id="84ac9-125">链接度量值组中包含的度量值只能直接与从同一 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中检索到的链接维度一起组织。</span><span class="sxs-lookup"><span data-stu-id="84ac9-125">The measures contained in a linked measure group can be directly organized only along linked dimensions retrieved from the same [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="84ac9-126">但是，您可以使用计算成员将来自链接度量值组的信息与多维数据集中的其他非链接维度进行关联。</span><span class="sxs-lookup"><span data-stu-id="84ac9-126">However, you can use calculated members to relate information from linked measure groups to the other, non-linked dimensions in your cube.</span></span> <span data-ttu-id="84ac9-127">您还可以使用间接关系（例如，引用关系或多对多关系）将非链接维度与链接度量值组进行关联。</span><span class="sxs-lookup"><span data-stu-id="84ac9-127">You can also use an indirect relationship, such as a reference or many-to-many relationship, to relate non-linked dimensions to a linked measure group.</span></span>  
  
## <a name="create-or-modify-a-linked-measure"></a><span data-ttu-id="84ac9-128">创建或修改链接度量值</span><span class="sxs-lookup"><span data-stu-id="84ac9-128">Create or modify a linked measure</span></span>  
 <span data-ttu-id="84ac9-129">使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 可创建链接度量值组。</span><span class="sxs-lookup"><span data-stu-id="84ac9-129">Use [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to create a linked measure group.</span></span>  
  
1.  <span data-ttu-id="84ac9-130">在源多维数据集中立即完成对原始度量值组的所有修改，这样不必在后续多维数据集中重新创建链接度量值组。</span><span class="sxs-lookup"><span data-stu-id="84ac9-130">Finalize any modifications to the original measure group now, in the source cube, so that you don't have to recreate the linked measure groups later in subsequent cubes.</span></span> <span data-ttu-id="84ac9-131">可以重命名链接对象，但是无法更改任何其他属性。</span><span class="sxs-lookup"><span data-stu-id="84ac9-131">You can rename a linked object, but you cannot change any other properties.</span></span>  
  
2.  <span data-ttu-id="84ac9-132">在解决方案资源管理器中，双击要向其添加链接度量值组的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="84ac9-132">In Solution Explorer, double-click the cube to which you are adding the linked measure group.</span></span> <span data-ttu-id="84ac9-133">此步骤在多维数据集设计器中打开多维数据集。</span><span class="sxs-lookup"><span data-stu-id="84ac9-133">This step opens the cube in Cube Designer.</span></span>  
  
3.  <span data-ttu-id="84ac9-134">在多维数据集设计器中的“度量值”窗格或“维度”窗格上，右键单击任一窗格中的任何位置，然后选择“新建链接对象”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="84ac9-134">In Cube Designer, in either the Measures pane or Dimensions pane, right-click anywhere in either pane, then select **New Linked Object**.</span></span> <span data-ttu-id="84ac9-135">这会启动链接对象向导。</span><span class="sxs-lookup"><span data-stu-id="84ac9-135">This starts the Linked Object Wizard.</span></span>  
  
4.  <span data-ttu-id="84ac9-136">在第一页上，指定数据源。</span><span class="sxs-lookup"><span data-stu-id="84ac9-136">On the first page, specify the data source.</span></span> <span data-ttu-id="84ac9-137">此步骤建立原始度量值组的位置。</span><span class="sxs-lookup"><span data-stu-id="84ac9-137">This step establishes the location of the original measure group.</span></span> <span data-ttu-id="84ac9-138">默认值是当前数据库中的当前多维数据集，不过也可以选择其他 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="84ac9-138">The default is the current cube in the current database, but you can also choose a different Analysis Services database.</span></span>  
  
5.  <span data-ttu-id="84ac9-139">在下一页中，选择要链接的度量值组或维度。</span><span class="sxs-lookup"><span data-stu-id="84ac9-139">On the next page, choose the measure group or dimension you want to link.</span></span> <span data-ttu-id="84ac9-140">维度和多维数据集对象（如度量值组）会分别列出。</span><span class="sxs-lookup"><span data-stu-id="84ac9-140">Dimensions and Cube objects, such as measure groups, are listed separately.</span></span> <span data-ttu-id="84ac9-141">只有当前多维数据集中尚不存在的对象才可用。</span><span class="sxs-lookup"><span data-stu-id="84ac9-141">Only those objects not already present in the current cube are available.</span></span>  
  
6.  <span data-ttu-id="84ac9-142">单击 **“完成”** 创建链接对象。</span><span class="sxs-lookup"><span data-stu-id="84ac9-142">Click **Finish** to create the linked object.</span></span> <span data-ttu-id="84ac9-143">链接对象出现在“度量值”和“维度”窗格中（通过链接图标指示）。</span><span class="sxs-lookup"><span data-stu-id="84ac9-143">Linked objects appear in the Measures and Dimensions pane, indicated by the link icon.</span></span>  
  
## <a name="secure-a-linked-measure"></a><span data-ttu-id="84ac9-144">保护链接度量值</span><span class="sxs-lookup"><span data-stu-id="84ac9-144">Secure a linked measure</span></span>  
 <span data-ttu-id="84ac9-145">定义了链接之后，在管理对链接度量值组中度量值的访问时，将采用与管理对其他度量值组的访问相同的方式。</span><span class="sxs-lookup"><span data-stu-id="84ac9-145">After the link has been defined, access to the measures in a linked measure group, is managed in the same manner as access to other measure groups.</span></span> <span data-ttu-id="84ac9-146">链接对象与其非链接对等对象一起出现在角色设计器中。</span><span class="sxs-lookup"><span data-stu-id="84ac9-146">A linked object appears alongside its non-linked counterparts in Role Designer.</span></span> <span data-ttu-id="84ac9-147">有关管理度量值组安全性的详细信息，请参阅[授予多维数据集或模型权限 (Analysis Services)](grant-cube-or-model-permissions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="84ac9-147">For more information on managing security for a measure group, see [Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="84ac9-148">为了定义或使用链接度量值组，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的 Windows 服务帐户必须属于在源 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上对源多维数据集和度量值组具有 `ReadDefinition` 和 `Read` 访问权的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库角色，或必须属于源 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Administrators 角色。</span><span class="sxs-lookup"><span data-stu-id="84ac9-148">In order to define or use a linked measure group, the Windows service account for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance must belong to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has `ReadDefinition` and `Read` access rights on the source [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to the source cube and measure group, or must belong to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Administrators role for the source [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ac9-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84ac9-149">See Also</span></span>  
 [<span data-ttu-id="84ac9-150">定义链接维度</span><span class="sxs-lookup"><span data-stu-id="84ac9-150">Define Linked Dimensions</span></span>](define-linked-dimensions.md)  
  
  
