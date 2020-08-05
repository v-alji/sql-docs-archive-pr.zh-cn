---
title: 多维模型中的操作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
author: minewiskan
ms.author: owend
ms.openlocfilehash: ce42907190363be085e8f4d8e9adfbab52a70590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580953"
---
# <a name="actions-in-multidimensional-models"></a><span data-ttu-id="a1676-102">多维模型中的操作</span><span class="sxs-lookup"><span data-stu-id="a1676-102">Actions in Multidimensional Models</span></span>
  <span data-ttu-id="a1676-103">操作是指最终用户针对所选多维数据集或其个部分启动的操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-103">An action is an end user-initiated operation upon a selected cube or portion of a cube.</span></span> <span data-ttu-id="a1676-104">操作可以通过将所选项目作为参数来启动应用程序，也可以检索有关所选项目的信息。</span><span class="sxs-lookup"><span data-stu-id="a1676-104">The operation can start an application with the selected item as a parameter, or it can retrieve information about the selected item.</span></span> <span data-ttu-id="a1676-105">有关操作的详细信息，请参阅[操作（Analysis Services - 多维数据）](actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a1676-105">For more information about actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="a1676-106">使用多维数据集设计器的 **“操作”** 选项卡可以为多维数据集生成操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-106">Use the **Actions** tab of Cube Designer to build actions for a cube.</span></span> <span data-ttu-id="a1676-107">指定下列各项：</span><span class="sxs-lookup"><span data-stu-id="a1676-107">Specify the following:</span></span>  
  
 <span data-ttu-id="a1676-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="a1676-108">**Name**</span></span>  
 <span data-ttu-id="a1676-109">选择用于标识操作的名称。</span><span class="sxs-lookup"><span data-stu-id="a1676-109">Select a name that identifies the action.</span></span>  
  
 <span data-ttu-id="a1676-110">**操作目标**</span><span class="sxs-lookup"><span data-stu-id="a1676-110">**Action Target**</span></span>  
 <span data-ttu-id="a1676-111">选择操作所附加到的对象。</span><span class="sxs-lookup"><span data-stu-id="a1676-111">Select the object to which the action is attached.</span></span> <span data-ttu-id="a1676-112">一般情况下，在客户端应用程序中，当最终用户选中了目标对象后就会显示该操作；但是，最终用户的何种行为会导致操作的显示，取决于客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="a1676-112">Generally, in client applications, the action is displayed when end users select the target object; however, the client application determines which end-user operation displays actions.</span></span> <span data-ttu-id="a1676-113">对于 **“目标类型”**，请从以下对象中选择：</span><span class="sxs-lookup"><span data-stu-id="a1676-113">For **Target type**, select from the following objects:</span></span>  
  
-   <span data-ttu-id="a1676-114">属性成员</span><span class="sxs-lookup"><span data-stu-id="a1676-114">Attribute members</span></span>  
  
-   <span data-ttu-id="a1676-115">单元</span><span class="sxs-lookup"><span data-stu-id="a1676-115">Cells</span></span>  
  
-   <span data-ttu-id="a1676-116">多维数据集</span><span class="sxs-lookup"><span data-stu-id="a1676-116">Cube</span></span>  
  
-   <span data-ttu-id="a1676-117">维度成员</span><span class="sxs-lookup"><span data-stu-id="a1676-117">Dimension members</span></span>  
  
-   <span data-ttu-id="a1676-118">层次结构</span><span class="sxs-lookup"><span data-stu-id="a1676-118">Hierarchy</span></span>  
  
-   <span data-ttu-id="a1676-119">层次结构成员</span><span class="sxs-lookup"><span data-stu-id="a1676-119">Hierarchy members</span></span>  
  
-   <span data-ttu-id="a1676-120">级别</span><span class="sxs-lookup"><span data-stu-id="a1676-120">Level</span></span>  
  
-   <span data-ttu-id="a1676-121">级别成员</span><span class="sxs-lookup"><span data-stu-id="a1676-121">Level members</span></span>  
  
 <span data-ttu-id="a1676-122">选择目标对象类型后，请在 **“目标对象”** 下面选择指定类型的多维数据集对象。</span><span class="sxs-lookup"><span data-stu-id="a1676-122">After you select the target object type, under **Target object**, select the cube object of the designated type.</span></span>  
  
 <span data-ttu-id="a1676-123">**条件(可选)**</span><span class="sxs-lookup"><span data-stu-id="a1676-123">**Condition (Optional)**</span></span>  
 <span data-ttu-id="a1676-124">指定其结果为布尔值的可选“多维表达式 (MDX)”表达式。</span><span class="sxs-lookup"><span data-stu-id="a1676-124">Specify an optional Multidimensional Expressions (MDX) expression that resolves to a Boolean value.</span></span> <span data-ttu-id="a1676-125">如果值是 `True`，则对指定目标执行操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-125">If the value is `True`, the action is performed on the specified target.</span></span> <span data-ttu-id="a1676-126">如果值是 `False`，则不执行操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-126">If the value is `False`, the action is not performed.</span></span>  
  
 <span data-ttu-id="a1676-127">**操作内容**</span><span class="sxs-lookup"><span data-stu-id="a1676-127">**Action Content**</span></span>  
 <span data-ttu-id="a1676-128">选择操作的类型。</span><span class="sxs-lookup"><span data-stu-id="a1676-128">Select the type of action.</span></span> <span data-ttu-id="a1676-129">下表总结了可用的类型。</span><span class="sxs-lookup"><span data-stu-id="a1676-129">The following table summarizes the available types.</span></span>  
  
|<span data-ttu-id="a1676-130">类型</span><span class="sxs-lookup"><span data-stu-id="a1676-130">Type</span></span>|<span data-ttu-id="a1676-131">说明</span><span class="sxs-lookup"><span data-stu-id="a1676-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a1676-132">数据集</span><span class="sxs-lookup"><span data-stu-id="a1676-132">Data Set</span></span>|<span data-ttu-id="a1676-133">检索数据集。</span><span class="sxs-lookup"><span data-stu-id="a1676-133">Retrieves a dataset.</span></span>|  
|<span data-ttu-id="a1676-134">专有</span><span class="sxs-lookup"><span data-stu-id="a1676-134">Proprietary</span></span>|<span data-ttu-id="a1676-135">使用除此表列出的这些类型以外的其他接口执行操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-135">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="a1676-136">行集</span><span class="sxs-lookup"><span data-stu-id="a1676-136">Row Set</span></span>|<span data-ttu-id="a1676-137">检索行集。</span><span class="sxs-lookup"><span data-stu-id="a1676-137">Retrieves a rowset.</span></span>|  
|<span data-ttu-id="a1676-138">Statement</span><span class="sxs-lookup"><span data-stu-id="a1676-138">Statement</span></span>|<span data-ttu-id="a1676-139">运行 OLE DB 命令。</span><span class="sxs-lookup"><span data-stu-id="a1676-139">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="a1676-140">URL</span><span class="sxs-lookup"><span data-stu-id="a1676-140">URL</span></span>|<span data-ttu-id="a1676-141">在 Internet 浏览器中显示可变页。</span><span class="sxs-lookup"><span data-stu-id="a1676-141">Displays a variable page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="a1676-142">对于 **“操作表达式”**，请指定运行操作时所传递的参数。</span><span class="sxs-lookup"><span data-stu-id="a1676-142">For **Action Expression**, specify the parameters that are passed when the action is run.</span></span> <span data-ttu-id="a1676-143">该语法的计算结果必须为字符串，并且必须包含以 MDX 编写的表达式。</span><span class="sxs-lookup"><span data-stu-id="a1676-143">The syntax must evaluate to a string, and you must include an expression written in MDX.</span></span> <span data-ttu-id="a1676-144">例如，MDX 表达式可以指示该语法所包含的多维数据集的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1676-144">For example, your MDX expression can indicate a part of the cube that is included in the syntax.</span></span> <span data-ttu-id="a1676-145">MDX 表达式在传递参数之前得到取值。</span><span class="sxs-lookup"><span data-stu-id="a1676-145">MDX expressions are evaluated before the parameters are passed.</span></span> <span data-ttu-id="a1676-146">MDX 生成器也可以帮助生成 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="a1676-146">Also, MDX Builder is available to help you build MDX expressions.</span></span>  
  
 <span data-ttu-id="a1676-147">**其他属性**</span><span class="sxs-lookup"><span data-stu-id="a1676-147">**Additional Properties**</span></span>  
 <span data-ttu-id="a1676-148">选择属性。</span><span class="sxs-lookup"><span data-stu-id="a1676-148">Select the property.</span></span> <span data-ttu-id="a1676-149">下表总结了可用的属性。</span><span class="sxs-lookup"><span data-stu-id="a1676-149">The following table summarizes the available properties.</span></span>  
  
|<span data-ttu-id="a1676-150">属性</span><span class="sxs-lookup"><span data-stu-id="a1676-150">Property</span></span>|<span data-ttu-id="a1676-151">说明</span><span class="sxs-lookup"><span data-stu-id="a1676-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a1676-152">**调用**</span><span class="sxs-lookup"><span data-stu-id="a1676-152">**Invocation**</span></span>|<span data-ttu-id="a1676-153">指定如何运行操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-153">Specifies how the action is run.</span></span> <span data-ttu-id="a1676-154">“交互”（默认）指定在用户访问对象时运行操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-154">Interactive, the default, specifies that the action is run when a user accesses an object.</span></span> <span data-ttu-id="a1676-155">可能的设置是：</span><span class="sxs-lookup"><span data-stu-id="a1676-155">The possible settings are:</span></span><br /><br /> <span data-ttu-id="a1676-156">Batch</span><span class="sxs-lookup"><span data-stu-id="a1676-156">Batch</span></span><br /><br /> <span data-ttu-id="a1676-157">交互</span><span class="sxs-lookup"><span data-stu-id="a1676-157">Interactive</span></span><br /><br /> <span data-ttu-id="a1676-158">处于打开状态</span><span class="sxs-lookup"><span data-stu-id="a1676-158">On Open</span></span>|  
|<span data-ttu-id="a1676-159">**应用程序**</span><span class="sxs-lookup"><span data-stu-id="a1676-159">**Application**</span></span>|<span data-ttu-id="a1676-160">说明操作的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a1676-160">Describes the application of the action.</span></span>|  
|<span data-ttu-id="a1676-161">**说明**</span><span class="sxs-lookup"><span data-stu-id="a1676-161">**Description**</span></span>|<span data-ttu-id="a1676-162">说明操作。</span><span class="sxs-lookup"><span data-stu-id="a1676-162">Describes the action.</span></span>|  
|<span data-ttu-id="a1676-163">**Caption**</span><span class="sxs-lookup"><span data-stu-id="a1676-163">**Caption**</span></span>|<span data-ttu-id="a1676-164">提供为操作显示的标题。</span><span class="sxs-lookup"><span data-stu-id="a1676-164">Provides a caption that is displayed for the action.</span></span> <span data-ttu-id="a1676-165">如果标题是 MDX，请 `True` 将 For **caption**指定为 mdx。</span><span class="sxs-lookup"><span data-stu-id="a1676-165">If the caption is MDX, specify `True` for **Caption is MDX**.</span></span>|  
|<span data-ttu-id="a1676-166">**标题是 MDX**</span><span class="sxs-lookup"><span data-stu-id="a1676-166">**Caption is MDX**</span></span>|<span data-ttu-id="a1676-167">如果标题是 MDX，请指定 `True`，如果不是，则指定 `False`。</span><span class="sxs-lookup"><span data-stu-id="a1676-167">Specify `True` if the caption is MDX or `False` if it is not.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a1676-168">必须使用 Analysis Services 脚本语言 (ASSL) 或分析管理对象 (AMO)，才能定义 HTML 和命令行操作类型。</span><span class="sxs-lookup"><span data-stu-id="a1676-168">You must use Analysis Services Scripting Language (ASSL) or Analysis Management Objects (AMO) to define HTML and Command Line action types.</span></span> <span data-ttu-id="a1676-169">有关详细信息，请参阅 [Action 元素 (ASSL)](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl)、[Type 元素 (Action) (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl) 和 [AMO OLAP 高级对象的编程](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects)。</span><span class="sxs-lookup"><span data-stu-id="a1676-169">For more information, see [Action Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl), [Type Element &#40;Action&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl), and [Programming AMO OLAP Advanced Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects).</span></span>  
  
## <a name="creating-a-reporting-action"></a><span data-ttu-id="a1676-170">创建报表操作</span><span class="sxs-lookup"><span data-stu-id="a1676-170">Creating a Reporting Action</span></span>  
 <span data-ttu-id="a1676-171">报表服务器会对基于 URL 的报表请求作出响应。</span><span class="sxs-lookup"><span data-stu-id="a1676-171">The report server responds to URL-based requests for reports.</span></span> <span data-ttu-id="a1676-172">若要创建报表操作，请在 **“多维数据集”** 菜单上单击 **“新建报表操作”**。</span><span class="sxs-lookup"><span data-stu-id="a1676-172">To create a reporting action, on the **Cube** menu, click **New Reporting Action**.</span></span> <span data-ttu-id="a1676-173">下面是特定于报表操作的选项。</span><span class="sxs-lookup"><span data-stu-id="a1676-173">The following options are specific to a reporting action.</span></span>  
  
 <span data-ttu-id="a1676-174">**报表服务器**</span><span class="sxs-lookup"><span data-stu-id="a1676-174">**Report Server**</span></span>  
 <span data-ttu-id="a1676-175">下表说明的属性是为报表服务器指定的。</span><span class="sxs-lookup"><span data-stu-id="a1676-175">The properties described in the following table are specified for the report server.</span></span>  
  
|<span data-ttu-id="a1676-176">属性</span><span class="sxs-lookup"><span data-stu-id="a1676-176">Property</span></span>|<span data-ttu-id="a1676-177">说明</span><span class="sxs-lookup"><span data-stu-id="a1676-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a1676-178">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="a1676-178">**Server name**</span></span>|<span data-ttu-id="a1676-179">运行报表服务器的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="a1676-179">The name of the computer running report server.</span></span>|  
|<span data-ttu-id="a1676-180">**服务器路径**</span><span class="sxs-lookup"><span data-stu-id="a1676-180">**Server path**</span></span>|<span data-ttu-id="a1676-181">报表服务器所显示的路径。</span><span class="sxs-lookup"><span data-stu-id="a1676-181">The path exposed by report server.</span></span>|  
|<span data-ttu-id="a1676-182">**报表格式**</span><span class="sxs-lookup"><span data-stu-id="a1676-182">**Report format**</span></span>|<span data-ttu-id="a1676-183">HTML5、HTML3、Excel 或 PDF。</span><span class="sxs-lookup"><span data-stu-id="a1676-183">HTML5, HTML3, Excel, or PDF.</span></span>|  
  
 <span data-ttu-id="a1676-184">**参数(可选)**</span><span class="sxs-lookup"><span data-stu-id="a1676-184">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="a1676-185">创建操作时，参数将作为 URL 字符串的一部分发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="a1676-185">The parameters are sent to the server as part of the URL string when the action is created.</span></span> <span data-ttu-id="a1676-186">它们包括 **“参数名称”** 和 **“参数值”**，后者是 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="a1676-186">They include **Parameter Name** and **Parameter Value**, which is an MDX expression.</span></span>  
  
 <span data-ttu-id="a1676-187">报表服务器 URL 的构造如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1676-187">The report server URL is constructed as follows:</span></span>  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 <span data-ttu-id="a1676-188">例如：</span><span class="sxs-lookup"><span data-stu-id="a1676-188">For example:</span></span>  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a><span data-ttu-id="a1676-189">创建钻取操作</span><span class="sxs-lookup"><span data-stu-id="a1676-189">Creating a Drillthrough Action</span></span>  
 <span data-ttu-id="a1676-190">钻取操作由行集操作定义，它将作为钻取语句返回到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="a1676-190">A drillthrough action is defined by a rowset action, which is returned to the client application as a drillthrough statement.</span></span> <span data-ttu-id="a1676-191">操作目标是度量值组的成员。</span><span class="sxs-lookup"><span data-stu-id="a1676-191">The action target is a member of a measure group.</span></span> <span data-ttu-id="a1676-192">若要创建新的钻取操作，请在 **“多维数据集”** 菜单上单击 **“新建钻取操作”**。</span><span class="sxs-lookup"><span data-stu-id="a1676-192">To create a new drillthrough action, on the **Cube** menu, click **New Drillthrough Action**.</span></span> <span data-ttu-id="a1676-193">下面是特定于钻取操作的选项：</span><span class="sxs-lookup"><span data-stu-id="a1676-193">The following options are specific to a drillthrough action:</span></span>  
  
 <span data-ttu-id="a1676-194">**钻取列**</span><span class="sxs-lookup"><span data-stu-id="a1676-194">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="a1676-195">选择一个或多个维度以及每个维度的、由该操作返回到客户端应用程序的钻取列。</span><span class="sxs-lookup"><span data-stu-id="a1676-195">Select one or more dimensions and, for each dimension, the drillthrough columns returned to the client application by the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1676-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1676-196">See Also</span></span>  
 [<span data-ttu-id="a1676-197">多维模型中的多维数据集</span><span class="sxs-lookup"><span data-stu-id="a1676-197">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
