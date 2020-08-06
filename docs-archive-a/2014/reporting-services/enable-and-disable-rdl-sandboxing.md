---
title: 启用和禁用 RDL 沙盒 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d5619e9f-ec5b-4376-9b34-1f74de6fade7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7af1477751093862c99d00978278315e600511e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691101"
---
# <a name="enable-and-disable-rdl-sandboxing"></a><span data-ttu-id="76672-102">启用和禁用 RDL 沙盒</span><span class="sxs-lookup"><span data-stu-id="76672-102">Enable and Disable RDL Sandboxing</span></span>
  <span data-ttu-id="76672-103">通过 RDL（报表定义语言）沙盒处理功能，您可以在多个用户使用报表服务器的单个 Web 场的情况下检测到和限制单个用户使用的特定类型的资源。</span><span class="sxs-lookup"><span data-stu-id="76672-103">The RDL (Report Definition Language) Sandboxing feature lets you detect and restrict the usage of specific types of resources, by individual tenants, in an environment of multiple tenants that use a single web farm of report servers.</span></span> <span data-ttu-id="76672-104">相关的示例是宿主服务方案，在此方案中，您可能维护多个用户（并且可能是不同的公司）使用的报表服务器的单个 Web 场。</span><span class="sxs-lookup"><span data-stu-id="76672-104">An example of this is a hosting services scenario where you might maintain a single web farm of report servers that are used by multiple tenants, and perhaps different companies.</span></span> <span data-ttu-id="76672-105">作为报表服务器管理员，您可以启用此功能以帮助实现以下目标：</span><span class="sxs-lookup"><span data-stu-id="76672-105">As a report server administrator, you can enable this feature to help achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="76672-106">限制外部资源的大小。</span><span class="sxs-lookup"><span data-stu-id="76672-106">Restrict external resource sizes.</span></span> <span data-ttu-id="76672-107">外部资源包括图像、.xslt 文件和地图数据。</span><span class="sxs-lookup"><span data-stu-id="76672-107">External resources include images, .xslt files, and map data.</span></span>  
  
-   <span data-ttu-id="76672-108">在报表发布时，限制在表达式文本中使用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="76672-108">At report publish time, limit types and members that are used in expression text.</span></span>  
  
-   <span data-ttu-id="76672-109">在报表处理时，限制文本长度和表达式返回值的大小。</span><span class="sxs-lookup"><span data-stu-id="76672-109">At report processing time, limit the length of the text and the size of the return value for expressions.</span></span>  
  
 <span data-ttu-id="76672-110">在启用 RDL 沙盒处理时，禁用以下功能：</span><span class="sxs-lookup"><span data-stu-id="76672-110">When RDL Sandboxing is enabled, the following features are disabled:</span></span>  
  
-   <span data-ttu-id="76672-111">报表定义的元素中的自定义代码 **\<Code>** 。</span><span class="sxs-lookup"><span data-stu-id="76672-111">Custom code in the **\<Code>** element of a report definition.</span></span>  
  
-   <span data-ttu-id="76672-112">用于 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] 自定义报表项的 RDL 向后兼容模式。</span><span class="sxs-lookup"><span data-stu-id="76672-112">RDL backward compatibility mode for [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] custom report items.</span></span>  
  
-   <span data-ttu-id="76672-113">表达式中的命名参数。</span><span class="sxs-lookup"><span data-stu-id="76672-113">Named parameters in expressions.</span></span>  
  
 <span data-ttu-id="76672-114">本主题介绍 `RDLSandboxing` RSReportServer.Config 文件中 <> 元素中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="76672-114">This topic describes each element in the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span> <span data-ttu-id="76672-115">有关如何修改此文件的详细信息，请参阅[修改 Reporting Services 配置文件 (RSreportserver.config)](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="76672-115">For more information about how to modify this file, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="76672-116">服务器跟踪日志记录与 RDL 沙盒处理功能相关的活动。</span><span class="sxs-lookup"><span data-stu-id="76672-116">A server trace log records activity related to the RDL Sandboxing feature.</span></span> <span data-ttu-id="76672-117">有关跟踪日志的详细信息，请参阅 [报表服务器服务跟踪日志](report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="76672-117">For more information about trace logs, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="76672-118">示例配置</span><span class="sxs-lookup"><span data-stu-id="76672-118">Example Configuration</span></span>  
 <span data-ttu-id="76672-119">下面的示例演示 `RDLSandboxing` RSReportServer.Config 文件中 <> 元素的设置和示例值。</span><span class="sxs-lookup"><span data-stu-id="76672-119">The following example shows the settings and example values for the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span>  
  
```  
<RDLSandboxing>  
   <MaxExpressionLength>5000</MaxExpressionLength>  
   <MaxResourceSize>5000</MaxResourceSize>  
   <MaxStringResultLength>3000</MaxStringResultLength>  
   <MaxArrayResultLength>250</MaxArrayResultLength>  
   <Types>  
      <Allow Namespace="System.Drawing" AllowNew="True">Bitmap</Allow>  
      <Allow Namespace="TypeConverters.Custom" AllowNew="True">*</Allow>  
   </Types>  
   <Members>  
      <Deny>Format</Deny>  
      <Deny>StrDup</Deny>  
   </Members>  
</RDLSandboxing>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="76672-120">配置设置</span><span class="sxs-lookup"><span data-stu-id="76672-120">Configuration Settings</span></span>  
 <span data-ttu-id="76672-121">下表提供了有关配置设置的信息。</span><span class="sxs-lookup"><span data-stu-id="76672-121">The following table provides information about configuration settings.</span></span> <span data-ttu-id="76672-122">将按设置在配置文件中的显示顺序依次列出：</span><span class="sxs-lookup"><span data-stu-id="76672-122">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="76672-123">设置</span><span class="sxs-lookup"><span data-stu-id="76672-123">Setting</span></span>|<span data-ttu-id="76672-124">说明</span><span class="sxs-lookup"><span data-stu-id="76672-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76672-125">**MaxExpressionLength**</span><span class="sxs-lookup"><span data-stu-id="76672-125">**MaxExpressionLength**</span></span>|<span data-ttu-id="76672-126">RDL 表达式中允许的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="76672-126">Maximum number of characters allowed in RDL expressions.</span></span><br /><br /> <span data-ttu-id="76672-127">默认值：1000</span><span class="sxs-lookup"><span data-stu-id="76672-127">Default: 1000</span></span>|  
|<span data-ttu-id="76672-128">**MaxResourceSize**</span><span class="sxs-lookup"><span data-stu-id="76672-128">**MaxResourceSize**</span></span>|<span data-ttu-id="76672-129">外部资源允许的最大 KB 数。</span><span class="sxs-lookup"><span data-stu-id="76672-129">Maximum number of KB allowed for an external resource.</span></span><br /><br /> <span data-ttu-id="76672-130">默认值：100</span><span class="sxs-lookup"><span data-stu-id="76672-130">Default: 100</span></span>|  
|<span data-ttu-id="76672-131">**MaxStringResultLength**</span><span class="sxs-lookup"><span data-stu-id="76672-131">**MaxStringResultLength**</span></span>|<span data-ttu-id="76672-132">RDL 表达式的返回值中允许的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="76672-132">Maximum number of characters allowed in a return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="76672-133">默认值：1000</span><span class="sxs-lookup"><span data-stu-id="76672-133">Default: 1000</span></span>|  
|<span data-ttu-id="76672-134">**MaxArrayResultLength**</span><span class="sxs-lookup"><span data-stu-id="76672-134">**MaxArrayResultLength**</span></span>|<span data-ttu-id="76672-135">RDL 表达式的数组返回值中允许的最大项数。</span><span class="sxs-lookup"><span data-stu-id="76672-135">Maximum number of items allowed in an array return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="76672-136">默认值：100</span><span class="sxs-lookup"><span data-stu-id="76672-136">Default: 100</span></span>|  
|<span data-ttu-id="76672-137">**类型**</span><span class="sxs-lookup"><span data-stu-id="76672-137">**Types**</span></span>|<span data-ttu-id="76672-138">在 RDL 表达式内允许的成员的列表。</span><span class="sxs-lookup"><span data-stu-id="76672-138">The list of members to allow within RDL expressions.</span></span>|  
|<span data-ttu-id="76672-139">**允许**</span><span class="sxs-lookup"><span data-stu-id="76672-139">**Allow**</span></span>|<span data-ttu-id="76672-140">RDL 表达式中允许的一个类型或一组类型。</span><span class="sxs-lookup"><span data-stu-id="76672-140">A type or set of types to allow in RDL expressions.</span></span>|  
|<span data-ttu-id="76672-141">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="76672-141">**Namespace**</span></span>|<span data-ttu-id="76672-142">**Allow** 的属性，它是包含应用于 Value 的一个或多个类型的命名空间。</span><span class="sxs-lookup"><span data-stu-id="76672-142">Attribute for **Allow** that is the namespace that contains one or more types that apply to Value.</span></span> <span data-ttu-id="76672-143">此属性不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="76672-143">This property is case-insensitive.</span></span>|  
|`AllowNew`|<span data-ttu-id="76672-144">**Allow**的布尔属性，控制是否允许在 rdl 表达式或 rdl 元素中创建类型的新实例 **\<Class>** 。</span><span class="sxs-lookup"><span data-stu-id="76672-144">Boolean attribute for **Allow** that controls whether new instances of the type are allowed to be created in RDL expressions or in an RDL **\<Class>** element.</span></span><br /><br /> <span data-ttu-id="76672-145">注意：启用后，无论的设置如何，都 `RDLSandboxing` 不能在 RDL 表达式中创建新数组 `AllowNew` 。</span><span class="sxs-lookup"><span data-stu-id="76672-145">Note: When `RDLSandboxing` is enabled, new arrays cannot be created in RDL expressions, regardless of the setting of `AllowNew`.</span></span>|  
|<span data-ttu-id="76672-146">**值**</span><span class="sxs-lookup"><span data-stu-id="76672-146">**Value**</span></span>|<span data-ttu-id="76672-147">**Allow** 的值，作为在 RDL 表达式中要允许的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="76672-147">Value for **Allow** that is the name of the type to allow in RDL expressions.</span></span> <span data-ttu-id="76672-148">值 **\*** 指示命名空间中的所有类型都是允许的。</span><span class="sxs-lookup"><span data-stu-id="76672-148">The value **\*** indicates that all types in the namespace are allowed.</span></span> <span data-ttu-id="76672-149">此属性不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="76672-149">This property is case-insensitive.</span></span>|  
|<span data-ttu-id="76672-150">**成员**</span><span class="sxs-lookup"><span data-stu-id="76672-150">**Members**</span></span>|<span data-ttu-id="76672-151">对于包含在元素中的类型的列表，为在 **\<Types>** RDL 表达式中不允许的成员名称的列表。</span><span class="sxs-lookup"><span data-stu-id="76672-151">For the list of types that are include in the **\<Types>** element, the list of member names that are not allowed in RDL expressions.</span></span>|  
|<span data-ttu-id="76672-152">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="76672-152">**Deny**</span></span>|<span data-ttu-id="76672-153">在 RDL 表达式中不允许的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="76672-153">The name of a member that is not allowed in RDL expressions.</span></span> <span data-ttu-id="76672-154">此属性不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="76672-154">This property is case-insensitive.</span></span><br /><br /> <span data-ttu-id="76672-155">注意：在为某一成员指定了 **Deny** 后，不允许所有类型的具有此名称的所有成员。</span><span class="sxs-lookup"><span data-stu-id="76672-155">Note: When **Deny** is specified for a member, all members with this name for all types are not allowed.</span></span>|  
  
## <a name="working-with-expressions-when-rdl-sandboxing-is-enabled"></a><span data-ttu-id="76672-156">当启用 RDL 沙盒处理时使用表达式</span><span class="sxs-lookup"><span data-stu-id="76672-156">Working with Expressions when RDL Sandboxing is Enabled</span></span>  
 <span data-ttu-id="76672-157">您可以修改 RDL 沙盒处理功能，以便通过以下方式管理表达式使用的资源：</span><span class="sxs-lookup"><span data-stu-id="76672-157">You can modify the RDL Sandboxing feature to help manage the resources that are used by an expression in the following ways:</span></span>  
  
-   <span data-ttu-id="76672-158">限制用于表达式的字符数。</span><span class="sxs-lookup"><span data-stu-id="76672-158">Restrict the number of characters that are used for an expression.</span></span>  
  
-   <span data-ttu-id="76672-159">限制表达式所返回的结果的大小。</span><span class="sxs-lookup"><span data-stu-id="76672-159">Restrict the size of the result returned by an expression.</span></span>  
  
-   <span data-ttu-id="76672-160">允许可以在表达式中使用的类型的特定列表。</span><span class="sxs-lookup"><span data-stu-id="76672-160">Allow a specific list of types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="76672-161">对于可在表达式中使用的允许类型的列表，按名称限制成员的列表。</span><span class="sxs-lookup"><span data-stu-id="76672-161">Restrict the list of members by name for the list of allowed types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="76672-162">通过 RDL 沙盒处理功能，您可以创建已批准类型的列表和拒绝的成员的列表。</span><span class="sxs-lookup"><span data-stu-id="76672-162">The RDL Sandboxing feature enables you to create a list of approved types and a list of denied members.</span></span> <span data-ttu-id="76672-163">已批准类型的列表称为允许列表。</span><span class="sxs-lookup"><span data-stu-id="76672-163">The list of approved types is called an allow list.</span></span> <span data-ttu-id="76672-164">拒绝的成员的列表称为阻止列表。</span><span class="sxs-lookup"><span data-stu-id="76672-164">The list of denied members is called a block list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76672-165">在报表定义中，计算机无法知道表达式引用的每个实例的类型。</span><span class="sxs-lookup"><span data-stu-id="76672-165">In the report definition, a computer cannot know the type of each instances of an expression reference.</span></span> <span data-ttu-id="76672-166">在您将一个成员添加到该阻止列表时，即拒绝允许列表中所有类型的该名称的所有成员。</span><span class="sxs-lookup"><span data-stu-id="76672-166">When you add a member to the block list, you are denying all members of that name across all types in the allow list.</span></span>  
  
 <span data-ttu-id="76672-167">在运行时验证 RDL 表达式结果。</span><span class="sxs-lookup"><span data-stu-id="76672-167">RDL expression results are verified at run time.</span></span> <span data-ttu-id="76672-168">在发布报表时在报表定义中验证 RDL 表达式。</span><span class="sxs-lookup"><span data-stu-id="76672-168">RDL expressions are verified in the report definition when the report is published.</span></span> <span data-ttu-id="76672-169">监控报表服务器跟踪日志以发现冲突。</span><span class="sxs-lookup"><span data-stu-id="76672-169">Monitor the report server trace log for violations.</span></span> <span data-ttu-id="76672-170">有关详细信息，请参阅 [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="76672-170">For more information, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
### <a name="working-with-types"></a><span data-ttu-id="76672-171">使用类型</span><span class="sxs-lookup"><span data-stu-id="76672-171">Working with Types</span></span>  
 <span data-ttu-id="76672-172">在您将某一类型添加到允许列表中时，即控制用于访问 RDL 表达式的以下入口点：</span><span class="sxs-lookup"><span data-stu-id="76672-172">When you add a type to the allow list, you are controlling the following entry points to access RDL expressions:</span></span>  
  
-   <span data-ttu-id="76672-173">某一类型的静态成员。</span><span class="sxs-lookup"><span data-stu-id="76672-173">Static members of a type.</span></span>  
  
-   <span data-ttu-id="76672-174">[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` 方法。</span><span class="sxs-lookup"><span data-stu-id="76672-174">The [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` method.</span></span>  
  
-   <span data-ttu-id="76672-175">**\<Classes>** 报表定义中的元素。</span><span class="sxs-lookup"><span data-stu-id="76672-175">The **\<Classes>** element in the report definition.</span></span>  
  
-   <span data-ttu-id="76672-176">已为允许列表中的某一类型添加到阻止列表中的成员。</span><span class="sxs-lookup"><span data-stu-id="76672-176">Members that you have added to the block list for a type in the allow list.</span></span>  
  
 <span data-ttu-id="76672-177">允许列表不控制以下入口点：</span><span class="sxs-lookup"><span data-stu-id="76672-177">The allow list does not control the following entry points:</span></span>  
  
-   <span data-ttu-id="76672-178">报表数据集。</span><span class="sxs-lookup"><span data-stu-id="76672-178">Report datasets.</span></span> <span data-ttu-id="76672-179">从查询返回的报表数据集中的字段可以包含任何有效的 RDL 类型。</span><span class="sxs-lookup"><span data-stu-id="76672-179">Fields in report datasets that are returned from queries might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="76672-180">报表参数。</span><span class="sxs-lookup"><span data-stu-id="76672-180">Report parameters.</span></span> <span data-ttu-id="76672-181">用户提供的参数值可以包含任何有效的 RDL 类型。</span><span class="sxs-lookup"><span data-stu-id="76672-181">User-supplied parameter values might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="76672-182">未处于阻止列表中的已启用类型的成员。</span><span class="sxs-lookup"><span data-stu-id="76672-182">Members of an enabled type that are not in the block list.</span></span> <span data-ttu-id="76672-183">默认情况下，启用允许列表中所有类型的所有成员。</span><span class="sxs-lookup"><span data-stu-id="76672-183">By default, all members of all types in the allow list are enabled.</span></span> <span data-ttu-id="76672-184">在您将一个成员名称添加到该阻止列表时，即拒绝允许列表中所有类型的具有该名称的所有成员。</span><span class="sxs-lookup"><span data-stu-id="76672-184">When you add a member name to the block list, you are denying all members with that name across all types that are in the allow list.</span></span>  
  
 <span data-ttu-id="76672-185">若要启用一种类型的成员，但拒绝其他类型的具有相同名称的成员，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="76672-185">To enable a member of one type but deny a member with the same name for a different type, you must do the following:</span></span>  
  
-   <span data-ttu-id="76672-186">**\<Deny>** 为成员名称添加元素。</span><span class="sxs-lookup"><span data-stu-id="76672-186">Add a **\<Deny>** element for the member name.</span></span>  
  
-   <span data-ttu-id="76672-187">对于您想要启用的成员，为其创建一个代理成员，该成员在自定义程序集中的类上具有不同的名称。</span><span class="sxs-lookup"><span data-stu-id="76672-187">Create a proxy member with a different name on a class in a custom assembly for the member that you want to enable.</span></span>  
  
-   <span data-ttu-id="76672-188">将该新类添加到允许列表中。</span><span class="sxs-lookup"><span data-stu-id="76672-188">Add that new class to the allow list.</span></span>  
  
 <span data-ttu-id="76672-189">若要将 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 函数添加到允许列表，请将来自 Microsoft.VisualBasic 命名空间的相应类型添加到该允许列表。</span><span class="sxs-lookup"><span data-stu-id="76672-189">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework functions to the allow list, add the corresponding types from the Microsoft.VisualBasic namespace to the allow list.</span></span>  
  
 <span data-ttu-id="76672-190">若要将 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 类型关键字添加到允许列表，请将相应的 CLR 类型添加到该允许列表。</span><span class="sxs-lookup"><span data-stu-id="76672-190">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework type keywords to the allow list, add the corresponding CLR type to the allow list.</span></span> <span data-ttu-id="76672-191">例如，若要使用 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 关键字 `Integer` ，请将以下 XML 片段添加到 **\<RDLSandboxing>** 元素：</span><span class="sxs-lookup"><span data-stu-id="76672-191">For example, to use the [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework keyword `Integer`, add the following XML fragment to the **\<RDLSandboxing>** element:</span></span>  
  
```  
<Allow Namespace="System">Int32</Allow>  
```  
  
 <span data-ttu-id="76672-192">若要将泛型或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 可以为 Null 类型添加到允许列表，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="76672-192">To add a generic or a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type to the allow list, you must do the following:</span></span>  
  
-   <span data-ttu-id="76672-193">为泛型或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 可以为 Null 类型创建代理类型。</span><span class="sxs-lookup"><span data-stu-id="76672-193">Create a proxy type for the generic or [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type.</span></span>  
  
-   <span data-ttu-id="76672-194">向允许列表中添加该代理类型。</span><span class="sxs-lookup"><span data-stu-id="76672-194">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="76672-195">将一个类型从某一自定义程序集添加到允许列表并不隐式授予对该程序集的执行权限。</span><span class="sxs-lookup"><span data-stu-id="76672-195">Adding a type from a custom assembly to the allow list does not implicitly grant execute permission on the assembly.</span></span> <span data-ttu-id="76672-196">您必须专门修改代码访问安全文件，并对您的程序集提供执行权限。</span><span class="sxs-lookup"><span data-stu-id="76672-196">You must specifically modify the code access security file and provide execute permission to your assembly.</span></span> <span data-ttu-id="76672-197">有关详细信息，请参阅 [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="76672-197">For more information, see [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
#### <a name="maintaining-the-deny-list-of-members"></a><span data-ttu-id="76672-198">维护 \<Deny> 成员列表</span><span class="sxs-lookup"><span data-stu-id="76672-198">Maintaining the \<Deny> List of Members</span></span>  
 <span data-ttu-id="76672-199">在您将某一新类型添加到允许列表时，使用以下列表可以确定何时可能必须更新成员的阻止列表：</span><span class="sxs-lookup"><span data-stu-id="76672-199">When you add a new type to the allow list, use the following list to determine when you might have to update the block list of members:</span></span>  
  
-   <span data-ttu-id="76672-200">在您使用引入新类型的版本更新自定义程序集时。</span><span class="sxs-lookup"><span data-stu-id="76672-200">When you update a custom assembly with a version that introduces new types.</span></span>  
  
-   <span data-ttu-id="76672-201">在您向允许列表中的类型添加成员时。</span><span class="sxs-lookup"><span data-stu-id="76672-201">When you add members to the types in the allow list.</span></span>  
  
-   <span data-ttu-id="76672-202">在您更新报表服务器上的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 时。</span><span class="sxs-lookup"><span data-stu-id="76672-202">When you update the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] on the report server.</span></span>  
  
-   <span data-ttu-id="76672-203">在您将报表服务器升级到 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]的更高版本时。</span><span class="sxs-lookup"><span data-stu-id="76672-203">When you upgrade the report server to a later version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="76672-204">在您更新报表服务器以处理更高版本的 RDL 架构时，因为新成员可能已添加到 RDL 类型中。</span><span class="sxs-lookup"><span data-stu-id="76672-204">When you update a report server to handle a later RDL schema, because new members might have been added to RDL types.</span></span>  
  
### <a name="working-with-operators-and-new"></a><span data-ttu-id="76672-205">使用运算符和 New</span><span class="sxs-lookup"><span data-stu-id="76672-205">Working with Operators and New</span></span>  
 <span data-ttu-id="76672-206">默认情况下，`New` 以外的所有 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 语言运算符都始终是允许的。</span><span class="sxs-lookup"><span data-stu-id="76672-206">By default, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework language operators, except for `New`, are always allowed.</span></span> <span data-ttu-id="76672-207">`New`运算符由 `AllowNew` 元素上的属性控制 **\<Allow>** 。</span><span class="sxs-lookup"><span data-stu-id="76672-207">The `New` operator is controlled by the `AllowNew` attribute on the **\<Allow>** element.</span></span> <span data-ttu-id="76672-208">始终允许使用其他语言运算符（如默认集合访问器运算符 `!` 和 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 强制转换宏，如 `CInt` ）。</span><span class="sxs-lookup"><span data-stu-id="76672-208">Other language operators, such as the default collection accessor operator `!` and [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework cast macros such as `CInt`, are always allowed.</span></span>  
  
 <span data-ttu-id="76672-209">不支持将运算符添加到阻止列表（包括自定义运算符）。</span><span class="sxs-lookup"><span data-stu-id="76672-209">Adding operators to a block list, including custom operators, is not supported.</span></span> <span data-ttu-id="76672-210">要排除某一类型的运算符，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="76672-210">To exclude operators for a type, you must do the following:</span></span>  
  
-   <span data-ttu-id="76672-211">创建一个代理类型，它不实现您想要排除的运算符。</span><span class="sxs-lookup"><span data-stu-id="76672-211">Create a proxy type that does not implement the operators that you want to exclude.</span></span>  
  
-   <span data-ttu-id="76672-212">向允许列表中添加该代理类型。</span><span class="sxs-lookup"><span data-stu-id="76672-212">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="76672-213">若要在 RDL 表达式中创建一个新数组，请在方法中对您定义的类创建该数组，并且将该类添加到允许列表。</span><span class="sxs-lookup"><span data-stu-id="76672-213">To create a new array in an RDL expression, create the array in a method on a class that you define, and add that class to the allow list.</span></span>  
  
 <span data-ttu-id="76672-214">若要在 RDL 表达式中创建一个新数组，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="76672-214">To create a new array in an RDL expression, you must do the following:</span></span>  
  
-   <span data-ttu-id="76672-215">定义一个新类，并在方法中对该类创建数组。</span><span class="sxs-lookup"><span data-stu-id="76672-215">Define a new class and create the array in a method on that class.</span></span>  
  
-   <span data-ttu-id="76672-216">将该类添加到允许列表中。</span><span class="sxs-lookup"><span data-stu-id="76672-216">Add the class to the allow list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76672-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76672-217">See Also</span></span>  
 <span data-ttu-id="76672-218">[Rsreportserver.config 配置文件](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="76672-218">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 [<span data-ttu-id="76672-219">报表服务器服务跟踪日志</span><span class="sxs-lookup"><span data-stu-id="76672-219">Report Server Service Trace Log</span></span>](report-server/report-server-service-trace-log.md)  
  
  
