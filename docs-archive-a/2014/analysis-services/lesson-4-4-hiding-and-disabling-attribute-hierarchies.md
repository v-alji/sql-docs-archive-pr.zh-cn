---
title: 隐藏和禁用属性层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095039c2-7104-414c-a9a6-327b03ce79df
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc043c68d2a83424a14707799fd90bf893abc12d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694154"
---
# <a name="hiding-and-disabling-attribute-hierarchies"></a><span data-ttu-id="8100a-102">隐藏和禁用属性层次结构</span><span class="sxs-lookup"><span data-stu-id="8100a-102">Hiding and Disabling Attribute Hierarchies</span></span>
  <span data-ttu-id="8100a-103">默认情况下，将为维度中的每个属性创建一个属性层次结构，并且每个层次结构均可用于确定事实数据的维度。</span><span class="sxs-lookup"><span data-stu-id="8100a-103">By default, an attribute hierarchy is created for every attribute in a dimension, and each hierarchy is available for dimensioning fact data.</span></span> <span data-ttu-id="8100a-104">此层次结构由“全部”级别和包含该层次结构中所有成员的详细级别组成。</span><span class="sxs-lookup"><span data-stu-id="8100a-104">This hierarchy consists of an "All" level and a detail level containing all members of the hierarchy.</span></span> <span data-ttu-id="8100a-105">正如您已经了解到的，可以将属性组织到用户定义层次结构中，以提供在多维数据集中的导航路径。</span><span class="sxs-lookup"><span data-stu-id="8100a-105">As you have already learned, you can organize attributes into user-defined hierarchies to provide navigation paths in a cube.</span></span> <span data-ttu-id="8100a-106">在某些环境下，可能需要禁用或隐藏某些属性以及它们的层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-106">Under certain circumstances, you may want to disable or hide some attributes and their hierarchies.</span></span> <span data-ttu-id="8100a-107">例如，某些属性（如，社会保障号码或身份证号、付费率、出生日期和登录信息）不是用户将要用来维度化多维数据集信息的属性。</span><span class="sxs-lookup"><span data-stu-id="8100a-107">For example, certain attributes such as social security numbers or national identification numbers, pay rates, birth dates, and login information are not attributes by which users will dimension cube information.</span></span> <span data-ttu-id="8100a-108">而这些信息通常只是作为特定属性成员的详细信息而显示。</span><span class="sxs-lookup"><span data-stu-id="8100a-108">Instead, this information is generally only viewed as details of a particular attribute member.</span></span> <span data-ttu-id="8100a-109">您可能需要隐藏这些属性层次结构，使这些属性只在作为特定属性的成员属性时可见。</span><span class="sxs-lookup"><span data-stu-id="8100a-109">You may want to hide these attribute hierarchies, leaving the attributes visible only as member properties of a specific attribute.</span></span> <span data-ttu-id="8100a-110">可能还需要使其他属性的成员（例如，客户名称或邮政编码）只在通过用户层次结构而不是单独通过属性层次结构进行查看时才可见。</span><span class="sxs-lookup"><span data-stu-id="8100a-110">You may also want to make members of other attributes, such as customer names or postal codes, visible only when they are viewed through a user hierarchy instead of independently through an attribute hierarchy.</span></span> <span data-ttu-id="8100a-111">这样做的一个理由可能是属性层次结构中不同成员的个数差异太大。</span><span class="sxs-lookup"><span data-stu-id="8100a-111">One reason to do so may be the sheer number of distinct members in the attribute hierarchy.</span></span> <span data-ttu-id="8100a-112">最后，为了改善处理性能，应该禁用用户不用于浏览的属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-112">Finally, to improve processing performance, you should disable attribute hierarchies that users will not use for browsing.</span></span>

 <span data-ttu-id="8100a-113">“AttributeHierarchyEnabled”\*\*\*\* 属性的值确定是否创建特性层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-113">The value of the **AttributeHierarchyEnabled** property determines whether an attribute hierarchy is created.</span></span> <span data-ttu-id="8100a-114">如果此属性设置为“False”\*\*\*\*，则不会创建特性层次结构，并且无法将特性用作用户层次结构中的一个级别；特性层次结构只作为成员属性存在。</span><span class="sxs-lookup"><span data-stu-id="8100a-114">If this property is set to **False**, the attribute hierarchy is not created and the attribute cannot be used as a level in a user hierarchy; the attribute hierarchy exists as a member property only.</span></span> <span data-ttu-id="8100a-115">但是，禁用的属性层次结构仍然可以用来对另一个属性的成员进行排序。</span><span class="sxs-lookup"><span data-stu-id="8100a-115">However, a disabled attribute hierarchy can still be used to order the members of another attribute.</span></span> <span data-ttu-id="8100a-116">如果“AttributeHierarchyEnabled”\*\*\*\* 属性的值设置为“True”\*\*\*\*，则“AttributeHierarchyVisible”\*\*\*\* 属性的值确定特性层次结构是否可见（与在用户定义层次结构中的用法无关）。</span><span class="sxs-lookup"><span data-stu-id="8100a-116">If the value of the **AttributeHierarchyEnabled** property is set to **True**, the value of the **AttributeHierarchyVisible** property determines whether the attribute hierarchy is visible independent of its use in a user-defined hierarchy.</span></span>

 <span data-ttu-id="8100a-117">启用属性层次结构时，可能需要指定以下其他三个属性的值：</span><span class="sxs-lookup"><span data-stu-id="8100a-117">When an attribute hierarchy is enabled, you may want to specify values for the following three additional properties:</span></span>

-   <span data-ttu-id="8100a-118">**IsAggregatable**</span><span class="sxs-lookup"><span data-stu-id="8100a-118">**IsAggregatable**</span></span>

     <span data-ttu-id="8100a-119">默认情况下，为所有属性层次结构定义了一个“(全部)”级别。</span><span class="sxs-lookup"><span data-stu-id="8100a-119">By default, an (All) level is defined for all attribute hierarchies.</span></span> <span data-ttu-id="8100a-120">若要禁用已启用的特性层次结构的“(全部)”级别，请将此属性的值设置为“False”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8100a-120">To disable the (All) level for an enabled attribute hierarchy, set the value for this property to **False**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="8100a-121">“IsAggregatable”\*\*\*\* 属性设置为 False 的特性只能用作用户定义层次结构的根，且必须指定默认成员（否则，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 引擎将为你选择一个默认成员）。</span><span class="sxs-lookup"><span data-stu-id="8100a-121">An attribute that has its **IsAggregatable** property set to false can only be used as the root of a user-defined hierarchy and must have a default member specified (otherwise, one will be chosen for you by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] engine).</span></span>

-   <span data-ttu-id="8100a-122">**AttributeHierarchyOrdered**</span><span class="sxs-lookup"><span data-stu-id="8100a-122">**AttributeHierarchyOrdered**</span></span>

     <span data-ttu-id="8100a-123">默认情况下，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会在处理期间对已启用的特性层次结构的成员进行排序，然后按“OrderBy”\*\*\*\* 属性的值（例如，按名称或按键）存储成员。</span><span class="sxs-lookup"><span data-stu-id="8100a-123">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] orders the members of enabled attribute hierarchies during processing, and then stores the members by the value of the **OrderBy** property, such as by Name or Key.</span></span> <span data-ttu-id="8100a-124">如果不关心排序，则可以通过将此属性的值设置为“False”\*\*\*\* 来提高处理性能。</span><span class="sxs-lookup"><span data-stu-id="8100a-124">If you do not care about ordering, you can increase processing performance by setting the value of this property to **False**.</span></span>

-   <span data-ttu-id="8100a-125">**AttributeHierarchyOptimizedState**</span><span class="sxs-lookup"><span data-stu-id="8100a-125">**AttributeHierarchyOptimizedState**</span></span>

     <span data-ttu-id="8100a-126">默认情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将在处理期间为每个已启用的属性层次结构创建索引，以提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="8100a-126">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates an index for each enabled attribute hierarchy during processing, to improve query performance.</span></span> <span data-ttu-id="8100a-127">如果不打算使用特性层次结构进行浏览，则可以通过将此属性的值设置为“NotOptimized”\*\*\*\* 来提高处理性能。</span><span class="sxs-lookup"><span data-stu-id="8100a-127">If you do not plan to use an attribute hierarchy for browsing, you can increase processing performance by setting the value of this property to **NotOptimized**.</span></span> <span data-ttu-id="8100a-128">但是，如果使用隐藏的层次结构作为维度的键属性，则通过创建属性成员的索引仍然能提高性能。</span><span class="sxs-lookup"><span data-stu-id="8100a-128">However, if you use a hidden hierarchy as the key attribute for the dimension, creating an index of the attribute members will still improve performance.</span></span>

 <span data-ttu-id="8100a-129">如果禁用了属性层次结构，则不应用这些属性。</span><span class="sxs-lookup"><span data-stu-id="8100a-129">These properties do not apply if an attribute hierarchy is disabled.</span></span>

 <span data-ttu-id="8100a-130">在该主题内的任务中，将禁用不会用于浏览的“雇员”维度中的社会保障号码和其他属性。</span><span class="sxs-lookup"><span data-stu-id="8100a-130">In the tasks in this topic, you will disable social security numbers and other attributes in the Employee dimension that will not be used for browsing.</span></span> <span data-ttu-id="8100a-131">然后，将隐藏“客户”维度中的客户名称和邮政编码属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-131">You will then hide the customer name and postal code attribute hierarchies in the Customer dimension.</span></span> <span data-ttu-id="8100a-132">层次结构中的大量属性成员将使对这些层次结构的浏览速度变得非常缓慢，这与用户层次结构无关。</span><span class="sxs-lookup"><span data-stu-id="8100a-132">The large number of attribute members in these hierarchies will make browsing these hierarchies very slow independent of a user hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-employee-dimension"></a><span data-ttu-id="8100a-133">设置“雇员”维度中的属性层次结构属性</span><span class="sxs-lookup"><span data-stu-id="8100a-133">Setting Attribute Hierarchy Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="8100a-134">切换到“雇员”维度的维度设计器，然后单击“浏览器”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8100a-134">Switch to Dimension Designer for the Employee dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="8100a-135">确认“层次结构”\*\*\*\* 列表中显示以下属性层次结构：</span><span class="sxs-lookup"><span data-stu-id="8100a-135">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="8100a-136">**基本报酬**</span><span class="sxs-lookup"><span data-stu-id="8100a-136">**Base Rate**</span></span>

    -   <span data-ttu-id="8100a-137">**Birth Date**</span><span class="sxs-lookup"><span data-stu-id="8100a-137">**Birth Date**</span></span>

    -   <span data-ttu-id="8100a-138">**登录 ID**</span><span class="sxs-lookup"><span data-stu-id="8100a-138">**Login ID**</span></span>

    -   <span data-ttu-id="8100a-139">**经理 SSN**</span><span class="sxs-lookup"><span data-stu-id="8100a-139">**Manager SSN**</span></span>

    -   <span data-ttu-id="8100a-140">**SSN**</span><span class="sxs-lookup"><span data-stu-id="8100a-140">**SSN**</span></span>

3.  <span data-ttu-id="8100a-141">切换到“维度结构”\*\*\*\* 选项卡，然后在“属性”\*\*\*\* 窗格中选择以下属性。</span><span class="sxs-lookup"><span data-stu-id="8100a-141">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane.</span></span> <span data-ttu-id="8100a-142">可以通过在按住 Ctrl 键的同时单击各个度量值的方式来选择多个度量值：</span><span class="sxs-lookup"><span data-stu-id="8100a-142">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>

    -   <span data-ttu-id="8100a-143">**基本报酬**</span><span class="sxs-lookup"><span data-stu-id="8100a-143">**Base Rate**</span></span>

    -   <span data-ttu-id="8100a-144">**Birth Date**</span><span class="sxs-lookup"><span data-stu-id="8100a-144">**Birth Date**</span></span>

    -   <span data-ttu-id="8100a-145">**登录 ID**</span><span class="sxs-lookup"><span data-stu-id="8100a-145">**Login ID**</span></span>

    -   <span data-ttu-id="8100a-146">**经理 SSN**</span><span class="sxs-lookup"><span data-stu-id="8100a-146">**Manager SSN**</span></span>

    -   <span data-ttu-id="8100a-147">**SSN**</span><span class="sxs-lookup"><span data-stu-id="8100a-147">**SSN**</span></span>

4.  <span data-ttu-id="8100a-148">在“属性”窗口中，将所选特性的“AttributeHierarchyEnabled”\*\*\*\* 属性的值设置为“False”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8100a-148">In the Properties window, set the value of the **AttributeHierarchyEnabled** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="8100a-149">请注意，“属性”\*\*\*\* 窗格中每个属性的图标都会发生更改，以指示该属性未启用。</span><span class="sxs-lookup"><span data-stu-id="8100a-149">Notice in the **Attributes** pane that the icon for each attribute has changed to indicate that the attribute is not enabled.</span></span>

     <span data-ttu-id="8100a-150">下图显示将所选特性的“AttributeHierarchyEnabled”\*\*\*\* 属性设置为 False。</span><span class="sxs-lookup"><span data-stu-id="8100a-150">The following image shows the **AttributeHierarchyEnabled** property set to False for the selected attributes.</span></span>

     <span data-ttu-id="8100a-151">![AttributeHierarchyEnabled 属性设置为 False](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled 属性设置为 False")</span><span class="sxs-lookup"><span data-stu-id="8100a-151">![AttributeHierarchyEnabled property set to False](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled property set to False")</span></span>

5.  <span data-ttu-id="8100a-152">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8100a-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

6.  <span data-ttu-id="8100a-153">处理成功完成后，请切换到“浏览器”\*\*\*\* 选项卡，单击“重新连接”\*\*\*\*，然后尝试浏览修改后的属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-153">When processing has successfully completed, switch to the **Browser** tab, click **Reconnect**, and then try to browse the modified attribute hierarchies.</span></span>

     <span data-ttu-id="8100a-154">请注意，修改后的属性的成员不可作为“层次结构”\*\*\*\* 列表中的属性层次结构进行浏览。</span><span class="sxs-lookup"><span data-stu-id="8100a-154">Notice that the members of the modified attributes are not available for browsing as attribute hierarchies in the **Hierarchy** list.</span></span> <span data-ttu-id="8100a-155">如果尝试添加一个禁用的属性层次结构作为用户层次结构的一个级别，那么您将收到错误消息，通知您必须启用该属性层次结构才能参与用户定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-155">If you try to add one of the disabled attribute hierarchies as a level in a user hierarchy, you will receive an error notifying you that the attribute hierarchy must be enabled to participate in a user-defined hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-customer-dimension"></a><span data-ttu-id="8100a-156">设置“客户”维度中的属性层次结构属性</span><span class="sxs-lookup"><span data-stu-id="8100a-156">Setting Attribute Hierarchy Properties in the Customer Dimension</span></span>

1.  <span data-ttu-id="8100a-157">切换到“客户”维度的维度设计器，然后单击“浏览器”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8100a-157">Switch to Dimension Designer for the Customer dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="8100a-158">确认“层次结构”\*\*\*\* 列表中显示以下属性层次结构：</span><span class="sxs-lookup"><span data-stu-id="8100a-158">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="8100a-159">**全名**</span><span class="sxs-lookup"><span data-stu-id="8100a-159">**Full Name**</span></span>

    -   <span data-ttu-id="8100a-160">**邮政编码**</span><span class="sxs-lookup"><span data-stu-id="8100a-160">**Postal Code**</span></span>

3.  <span data-ttu-id="8100a-161">切换到“维度结构”\*\*\*\* 选项卡，然后通过使用 Ctrl 键同时选择多个属性，在“属性”\*\*\*\* 窗格中选择以下属性：</span><span class="sxs-lookup"><span data-stu-id="8100a-161">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane by using the CTRL key to select multiple attributes at the same time:</span></span>

    -   <span data-ttu-id="8100a-162">**全名**</span><span class="sxs-lookup"><span data-stu-id="8100a-162">**Full Name**</span></span>

    -   <span data-ttu-id="8100a-163">**邮政编码**</span><span class="sxs-lookup"><span data-stu-id="8100a-163">**Postal Code**</span></span>

4.  <span data-ttu-id="8100a-164">在“属性”窗口中，将所选特性的“AttributeHierarchyVisible”\*\*\*\* 属性的值设置为“False”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8100a-164">In the Properties window, set the value of the **AttributeHierarchyVisible** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="8100a-165">由于这些属性层次结构的成员将用于确定事实数据的维度，因此，对这些属性层次结构的成员进行排序和优化将提高性能。</span><span class="sxs-lookup"><span data-stu-id="8100a-165">Because the members of these attribute hierarchies will be used for dimensioning fact data, ordering and optimizing the members of these attribute hierarchies will improve performance.</span></span> <span data-ttu-id="8100a-166">因此，不应当更改这些特性的属性。</span><span class="sxs-lookup"><span data-stu-id="8100a-166">Therefore, the properties of these attributes should not be changed.</span></span>

     <span data-ttu-id="8100a-167">下图显示将“AttributeHierarchyVisible”\*\*\*\* 属性设置为 False。</span><span class="sxs-lookup"><span data-stu-id="8100a-167">The following image shows the **AttributeHierarchyVisible** property set to False.</span></span>

     <span data-ttu-id="8100a-168">![AttributeHierarchyVisible 属性设置为 False](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible 属性设置为 False")</span><span class="sxs-lookup"><span data-stu-id="8100a-168">![AttributeHierarchyVisible property set to False](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible property set to False")</span></span>

5.  <span data-ttu-id="8100a-169">将“邮政编码”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖到“层次结构和级别”\*\*\*\* 窗格中的“客户所在地域”\*\*\*\* 用户层次结构中（直接放在“市/县”\*\*\*\* 级别下）。</span><span class="sxs-lookup"><span data-stu-id="8100a-169">Drag the **Postal Code** attribute from the **Attributes** pane into the **Customer Geography** user hierarchy in the **Hierarchies and Levels** pane, immediately under the **City** level.</span></span>

     <span data-ttu-id="8100a-170">注意，隐藏的属性仍然可以成为用户层次结构中的级别。</span><span class="sxs-lookup"><span data-stu-id="8100a-170">Notice that a hidden attribute can still become a level in a user hierarchy.</span></span>

6.  <span data-ttu-id="8100a-171">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8100a-171">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

7.  <span data-ttu-id="8100a-172">成功完成部署后，请切换到“客户”维度的“浏览器”\*\*\*\* 选项卡，然后单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8100a-172">When deployment has successfully completed, switch to the **Browser** tab for the Customer dimension, and then click **Reconnect**.</span></span>

8.  <span data-ttu-id="8100a-173">尝试从“层次结构”\*\*\*\* 列表中选择任何一个修改后的属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="8100a-173">Try to select either of the modified attribute hierarchies from the **Hierarchy** list.</span></span>

     <span data-ttu-id="8100a-174">请注意，任何修改后的属性层次结构都不会出现在“层次结构”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="8100a-174">Notice that neither of the modified attribute hierarchies appears in the **Hierarchy** list.</span></span>

9. <span data-ttu-id="8100a-175">在“层次结构”\*\*\*\* 列表中，选择“客户所在地域”\*\*\*\*，然后在浏览器窗格中浏览每个级别。</span><span class="sxs-lookup"><span data-stu-id="8100a-175">In the **Hierarchy** list, select **Customer Geography**, and then browse each level in the browser pane.</span></span>

     <span data-ttu-id="8100a-176">请注意，隐藏的级别“邮政编码”\*\*\*\* 和“全名”\*\*\*\* 在该用户定义层次结构中可见。</span><span class="sxs-lookup"><span data-stu-id="8100a-176">Notice that the hidden levels, **Postal Code** and **Full Name**, are visible in the user-defined hierarchy.</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="8100a-177">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="8100a-177">Next Task in Lesson</span></span>
 [<span data-ttu-id="8100a-178">根据辅助属性对属性成员进行排序</span><span class="sxs-lookup"><span data-stu-id="8100a-178">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)


