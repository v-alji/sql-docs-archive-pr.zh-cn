---
title: 属性表达式中的枚举常量 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cb4ae32bf564e98d8cfc843e9497b15222fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690005"
---
# <a name="enumerated-constants-in-property-expressions"></a><span data-ttu-id="0a5a3-102">属性表达式中的枚举常量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-102">Enumerated Constants in Property Expressions</span></span>
  <span data-ttu-id="0a5a3-103">如果属性表达式包括枚举器成员列表中的值，则该表达式必须使用枚举器成员的数值，而不是成员的友好名称。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-103">If property expressions include values from an enumerator member list, the expression must use the numeric value of the enumerator member instead of the friendly name of the member.</span></span> <span data-ttu-id="0a5a3-104">例如，如果表达式设置 `LoggingMode` 属性，则必须使用数值 2 而不是友好名称“Disabled”。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-104">For example, if an expression sets the `LoggingMode` property then you must use the numeric value 2 instead of the friendly name Disabled.</span></span>  
  
 <span data-ttu-id="0a5a3-105">此主题只列出通常会在属性表达式中使用其成员的枚举器的友好名称的等价数值。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-105">This topic lists only the numeric values equivalent to friendly names of enumerators whose members are commonly used in property expressions.</span></span> <span data-ttu-id="0a5a3-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象模型包括很多其他枚举器，在编写对象模型以便以编程方式生成包时，或为任务和数据流组件等自定义包元素编写代码时，需要使用这些枚举器。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-106">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model includes many additional enumerators that you use when you program the object model to build packages programmatically or code custom package elements such as tasks and data flow components.</span></span>  
  
 <span data-ttu-id="0a5a3-107">除了包和包对象的自定义属性外， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的“属性”窗口还包括一组可用于包、任务以及 Foreach 循环、For 循环和序列容器的属性。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-107">In addition to the custom properties for packages and package objects, the Properties window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] includes a set of properties that are available to packages, tasks, and the Foreach Loop, For Loop, and Sequence containers.</span></span> <span data-ttu-id="0a5a3-108">由枚举器中的值设置的通用属性： `ForceExecutionResult` 、 `LoggingMode` 、 `IsolationLevel` 和 `Transaction Option` -在 "通用属性" 部分中列出。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-108">The common properties that are set by values from enumerators-`ForceExecutionResult`, `LoggingMode`, `IsolationLevel`, and `Transaction Option`-are listed in Common Properties section.</span></span>  
  
 <span data-ttu-id="0a5a3-109">以下部分提供了有关枚举常量的信息：</span><span class="sxs-lookup"><span data-stu-id="0a5a3-109">The following sections provide information about enumerated constants:</span></span>  
  
 [<span data-ttu-id="0a5a3-110">包</span><span class="sxs-lookup"><span data-stu-id="0a5a3-110">Package</span></span>](#Package)  
  
 [<span data-ttu-id="0a5a3-111">Foreach 循环枚举器</span><span class="sxs-lookup"><span data-stu-id="0a5a3-111">Foreach Loop Enumerators</span></span>](#Foreach)  
  
 [<span data-ttu-id="0a5a3-112">任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-112">Tasks</span></span>](#Tasks)  
  
 [<span data-ttu-id="0a5a3-113">维护计划任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-113">Maintenance Plan Tasks</span></span>](#MaintenancePlanTasks)  
  
 [<span data-ttu-id="0a5a3-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="0a5a3-114">Common Properties</span></span>](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> <span data-ttu-id="0a5a3-115">“包”</span><span class="sxs-lookup"><span data-stu-id="0a5a3-115">Package</span></span>  
 <span data-ttu-id="0a5a3-116">下表列出了通过使用枚举器中的值所设置的包的属性的友好名称和等价数值。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-116">The following tables lists the friendly names and the numeric value equivalents for properties of packages that you set by using values from an enumerator.</span></span>  
  
 <span data-ttu-id="0a5a3-117">`PackageType`属性-通过使用枚举中的值设置 `DTSPackageType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-117">`PackageType` property-Set by using values from the `DTSPackageType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-118">DTSPackageType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-118">Friendly name in DTSPackageType</span></span>|<span data-ttu-id="0a5a3-119">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-119">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-120">默认</span><span class="sxs-lookup"><span data-stu-id="0a5a3-120">Default</span></span>|<span data-ttu-id="0a5a3-121">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-121">0</span></span>|  
|<span data-ttu-id="0a5a3-122">DTSWizard</span><span class="sxs-lookup"><span data-stu-id="0a5a3-122">DTSWizard</span></span>|<span data-ttu-id="0a5a3-123">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-123">1</span></span>|  
|<span data-ttu-id="0a5a3-124">DTSDesigner</span><span class="sxs-lookup"><span data-stu-id="0a5a3-124">DTSDesigner</span></span>|<span data-ttu-id="0a5a3-125">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-125">2</span></span>|  
|<span data-ttu-id="0a5a3-126">SQLReplication</span><span class="sxs-lookup"><span data-stu-id="0a5a3-126">SQLReplication</span></span>|<span data-ttu-id="0a5a3-127">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-127">3</span></span>|  
|<span data-ttu-id="0a5a3-128">DTSDesigner100</span><span class="sxs-lookup"><span data-stu-id="0a5a3-128">DTSDesigner100</span></span>|<span data-ttu-id="0a5a3-129">5</span><span class="sxs-lookup"><span data-stu-id="0a5a3-129">5</span></span>|  
|<span data-ttu-id="0a5a3-130">SQLDBMaint</span><span class="sxs-lookup"><span data-stu-id="0a5a3-130">SQLDBMaint</span></span>|<span data-ttu-id="0a5a3-131">6</span><span class="sxs-lookup"><span data-stu-id="0a5a3-131">6</span></span>|  
  
 <span data-ttu-id="0a5a3-132">`CheckpointUsage`属性-通过使用枚举中的值设置 `DTSCheckpointUsage` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-132">`CheckpointUsage` property-Set by using values from the `DTSCheckpointUsage` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-133">DTSCheckpointUsage 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-133">Friendly name in DTSCheckpointUsage</span></span>|<span data-ttu-id="0a5a3-134">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-134">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-135">从不</span><span class="sxs-lookup"><span data-stu-id="0a5a3-135">Never</span></span>|<span data-ttu-id="0a5a3-136">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-136">0</span></span>|  
|<span data-ttu-id="0a5a3-137">IfExists</span><span class="sxs-lookup"><span data-stu-id="0a5a3-137">IfExists</span></span>|<span data-ttu-id="0a5a3-138">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-138">1</span></span>|  
|<span data-ttu-id="0a5a3-139">始终</span><span class="sxs-lookup"><span data-stu-id="0a5a3-139">Always</span></span>|<span data-ttu-id="0a5a3-140">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-140">2</span></span>|  
  
 <span data-ttu-id="0a5a3-141">`PackagePriorityClass`属性-通过使用枚举中的值设置 `DTSPriorityClass` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-141">`PackagePriorityClass` property-Set by using values from the `DTSPriorityClass` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-142">DTSPriorityClass 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-142">Friendly name in DTSPriorityClass</span></span>|<span data-ttu-id="0a5a3-143">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-143">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-144">默认</span><span class="sxs-lookup"><span data-stu-id="0a5a3-144">Default</span></span>|<span data-ttu-id="0a5a3-145">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-145">0</span></span>|  
|<span data-ttu-id="0a5a3-146">AboveNormal</span><span class="sxs-lookup"><span data-stu-id="0a5a3-146">AboveNormal</span></span>|<span data-ttu-id="0a5a3-147">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-147">1</span></span>|  
|<span data-ttu-id="0a5a3-148">一般</span><span class="sxs-lookup"><span data-stu-id="0a5a3-148">Normal</span></span>|<span data-ttu-id="0a5a3-149">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-149">2</span></span>|  
|<span data-ttu-id="0a5a3-150">BelowNormal</span><span class="sxs-lookup"><span data-stu-id="0a5a3-150">BelowNormal</span></span>|<span data-ttu-id="0a5a3-151">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-151">3</span></span>|  
|<span data-ttu-id="0a5a3-152">空闲</span><span class="sxs-lookup"><span data-stu-id="0a5a3-152">Idle</span></span>|<span data-ttu-id="0a5a3-153">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-153">4</span></span>|  
  
 <span data-ttu-id="0a5a3-154">`ProtectionLevel`属性-通过使用枚举中的值设置 `DTSProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-154">`ProtectionLevel` property-Set by using values from the `DTSProtectionLevel` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-155">DTSProtectionLevel 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-155">Friendly name in DTSProtectionLevel</span></span>|<span data-ttu-id="0a5a3-156">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-156">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-157">DontSaveSensitive</span><span class="sxs-lookup"><span data-stu-id="0a5a3-157">DontSaveSensitive</span></span>|<span data-ttu-id="0a5a3-158">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-158">0</span></span>|  
|<span data-ttu-id="0a5a3-159">EncryptSensitiveWithUserKey</span><span class="sxs-lookup"><span data-stu-id="0a5a3-159">EncryptSensitiveWithUserKey</span></span>|<span data-ttu-id="0a5a3-160">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-160">1</span></span>|  
|<span data-ttu-id="0a5a3-161">EncryptSensitiveWithPassword</span><span class="sxs-lookup"><span data-stu-id="0a5a3-161">EncryptSensitiveWithPassword</span></span>|<span data-ttu-id="0a5a3-162">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-162">2</span></span>|  
|<span data-ttu-id="0a5a3-163">EncryptAllWithPassword</span><span class="sxs-lookup"><span data-stu-id="0a5a3-163">EncryptAllWithPassword</span></span>|<span data-ttu-id="0a5a3-164">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-164">3</span></span>|  
|<span data-ttu-id="0a5a3-165">EncryptAllWithUserKey</span><span class="sxs-lookup"><span data-stu-id="0a5a3-165">EncryptAllWithUserKey</span></span>|<span data-ttu-id="0a5a3-166">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-166">4</span></span>|  
|<span data-ttu-id="0a5a3-167">ServerStorage</span><span class="sxs-lookup"><span data-stu-id="0a5a3-167">ServerStorage</span></span>|<span data-ttu-id="0a5a3-168">5</span><span class="sxs-lookup"><span data-stu-id="0a5a3-168">5</span></span>|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> <span data-ttu-id="0a5a3-169">优先约束</span><span class="sxs-lookup"><span data-stu-id="0a5a3-169">Precedence Constraints</span></span>  
 <span data-ttu-id="0a5a3-170">`EvalOp`属性-通过使用枚举中的值设置 `DTSPrecedenceEvalOp` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-170">`EvalOp` property-Set by using values from the `DTSPrecedenceEvalOp` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-171">DTSPrecedenceEvalOp 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-171">Friendly name in DTSPrecedenceEvalOp</span></span>|<span data-ttu-id="0a5a3-172">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-172">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-173">表达式</span><span class="sxs-lookup"><span data-stu-id="0a5a3-173">Expression</span></span>|<span data-ttu-id="0a5a3-174">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-174">1</span></span>|  
|<span data-ttu-id="0a5a3-175">约束</span><span class="sxs-lookup"><span data-stu-id="0a5a3-175">Constraint</span></span>|<span data-ttu-id="0a5a3-176">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-176">2</span></span>|  
|<span data-ttu-id="0a5a3-177">ExpressionAndConstraint</span><span class="sxs-lookup"><span data-stu-id="0a5a3-177">ExpressionAndConstraint</span></span>|<span data-ttu-id="0a5a3-178">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-178">3</span></span>|  
|<span data-ttu-id="0a5a3-179">ExpressionOrConstraint</span><span class="sxs-lookup"><span data-stu-id="0a5a3-179">ExpressionOrConstraint</span></span>|<span data-ttu-id="0a5a3-180">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-180">4</span></span>|  
  
 <span data-ttu-id="0a5a3-181">`Value`属性-通过使用枚举中的值设置 `DTSExecResult` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-181">`Value` property-Set by using values from the `DTSExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-182">友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-182">Friendly Name</span></span>|<span data-ttu-id="0a5a3-183">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-183">Numeric Value</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="0a5a3-184">Success</span><span class="sxs-lookup"><span data-stu-id="0a5a3-184">Success</span></span>|<span data-ttu-id="0a5a3-185">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-185">0</span></span>|  
|<span data-ttu-id="0a5a3-186">失败</span><span class="sxs-lookup"><span data-stu-id="0a5a3-186">Failure</span></span>|<span data-ttu-id="0a5a3-187">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-187">1</span></span>|  
|<span data-ttu-id="0a5a3-188">Completion</span><span class="sxs-lookup"><span data-stu-id="0a5a3-188">Completion</span></span>|<span data-ttu-id="0a5a3-189">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-189">2</span></span>|  
|<span data-ttu-id="0a5a3-190">已取消</span><span class="sxs-lookup"><span data-stu-id="0a5a3-190">Canceled</span></span>|<span data-ttu-id="0a5a3-191">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-191">3</span></span>|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> <span data-ttu-id="0a5a3-192">Foreach 循环枚举器</span><span class="sxs-lookup"><span data-stu-id="0a5a3-192">Foreach Loop Enumerators</span></span>  
 <span data-ttu-id="0a5a3-193">Foreach 循环包括一组其属性可以由属性表达式设置的枚举器。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-193">The Foreach Loop includes a set of enumerators with properties that can be set by property expressions.</span></span>  
  
### <a name="foreach-ado-enumerator"></a><span data-ttu-id="0a5a3-194">Foreach ADO 枚举器</span><span class="sxs-lookup"><span data-stu-id="0a5a3-194">Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="0a5a3-195">`Type`属性-通过使用枚举中的值设置 `ADOEnumerationType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-195">`Type` property-Set by using values from the `ADOEnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-196">ADOEnumerationType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-196">Friendly name in ADOEnumerationType</span></span>|<span data-ttu-id="0a5a3-197">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-197">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-198">EnumerateTables</span><span class="sxs-lookup"><span data-stu-id="0a5a3-198">EnumerateTables</span></span>|<span data-ttu-id="0a5a3-199">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-199">0</span></span>|  
|<span data-ttu-id="0a5a3-200">EnumerateAllRows</span><span class="sxs-lookup"><span data-stu-id="0a5a3-200">EnumerateAllRows</span></span>|<span data-ttu-id="0a5a3-201">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-201">1</span></span>|  
|<span data-ttu-id="0a5a3-202">EnumerateRowsInFirstTable</span><span class="sxs-lookup"><span data-stu-id="0a5a3-202">EnumerateRowsInFirstTable</span></span>|<span data-ttu-id="0a5a3-203">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-203">2</span></span>|  
  
### <a name="foreach-nodelist-enumerator"></a><span data-ttu-id="0a5a3-204">Foreach Nodelist 枚举器</span><span class="sxs-lookup"><span data-stu-id="0a5a3-204">Foreach Nodelist Enumerator</span></span>  
 <span data-ttu-id="0a5a3-205">`SourceDocumentType`、 `InnerXPathStringSourceType` 和**将 outerxpathstringsourcetype**属性-通过使用枚举中的值设置 `SourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-205">`SourceDocumentType`, `InnerXPathStringSourceType`, and **OuterXPathStringSourceType** properties-Set by using values from the `SourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-206">SourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-206">Friendly name in SourceType</span></span>|<span data-ttu-id="0a5a3-207">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-207">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-208">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-208">FileConnection</span></span>|<span data-ttu-id="0a5a3-209">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-209">0</span></span>|  
|<span data-ttu-id="0a5a3-210">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-210">Variable</span></span>|<span data-ttu-id="0a5a3-211">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-211">1</span></span>|  
|<span data-ttu-id="0a5a3-212">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-212">DirectInput</span></span>|<span data-ttu-id="0a5a3-213">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-213">2</span></span>|  
  
 <span data-ttu-id="0a5a3-214">`EnumerationType`属性-通过使用枚举中的值设置 `EnumerationType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-214">`EnumerationType` property-Set by using values from the `EnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-215">EnumerationType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-215">Friendly name in EnumerationType</span></span>|<span data-ttu-id="0a5a3-216">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-216">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-217">导航器</span><span class="sxs-lookup"><span data-stu-id="0a5a3-217">Navigator</span></span>|<span data-ttu-id="0a5a3-218">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-218">0</span></span>|  
|<span data-ttu-id="0a5a3-219">节点</span><span class="sxs-lookup"><span data-stu-id="0a5a3-219">Node</span></span>|<span data-ttu-id="0a5a3-220">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-220">1</span></span>|  
|<span data-ttu-id="0a5a3-221">NodeText</span><span class="sxs-lookup"><span data-stu-id="0a5a3-221">NodeText</span></span>|<span data-ttu-id="0a5a3-222">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-222">2</span></span>|  
|<span data-ttu-id="0a5a3-223">ElementCollection</span><span class="sxs-lookup"><span data-stu-id="0a5a3-223">ElementCollection</span></span>|<span data-ttu-id="0a5a3-224">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-224">3</span></span>|  
  
 <span data-ttu-id="0a5a3-225">`InnerElementType`属性-通过使用枚举中的值设置 `InnerElementType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-225">`InnerElementType` property-Set by using values from the `InnerElementType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-226">InnerElementType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-226">Friendly name in InnerElementType</span></span>|<span data-ttu-id="0a5a3-227">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-227">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-228">导航器</span><span class="sxs-lookup"><span data-stu-id="0a5a3-228">Navigator</span></span>|<span data-ttu-id="0a5a3-229">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-229">0</span></span>|  
|<span data-ttu-id="0a5a3-230">节点</span><span class="sxs-lookup"><span data-stu-id="0a5a3-230">Node</span></span>|<span data-ttu-id="0a5a3-231">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-231">1</span></span>|  
|<span data-ttu-id="0a5a3-232">NodeText</span><span class="sxs-lookup"><span data-stu-id="0a5a3-232">NodeText</span></span>|<span data-ttu-id="0a5a3-233">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-233">2</span></span>|  
  
##  <a name="tasks"></a><a name="Tasks"></a> <span data-ttu-id="0a5a3-234">“任务”</span><span class="sxs-lookup"><span data-stu-id="0a5a3-234">Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="0a5a3-235">包括许多其属性可以由属性表达式设置的任务。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-235">includes numerous tasks with properties that can be set by property expressions.</span></span>  
  
### <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="0a5a3-236">Analysis Services 执行 DDL 任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-236">Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="0a5a3-237">`SourceType`属性-通过使用枚举中的值设置 `DDLSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-237">`SourceType` property-Set by using values from the `DDLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-238">DDLSourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-238">Friendly name in DDLSourceType</span></span>|<span data-ttu-id="0a5a3-239">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-239">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-240">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-240">DirectInput</span></span>|<span data-ttu-id="0a5a3-241">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-241">0</span></span>|  
|<span data-ttu-id="0a5a3-242">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-242">FileConnection</span></span>|<span data-ttu-id="0a5a3-243">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-243">1</span></span>|  
|<span data-ttu-id="0a5a3-244">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-244">Variable</span></span>|<span data-ttu-id="0a5a3-245">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-245">2</span></span>|  
  
### <a name="bulk-insert-task"></a><span data-ttu-id="0a5a3-246">大容量插入任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-246">Bulk Insert Task</span></span>  
 <span data-ttu-id="0a5a3-247">`DataFileType`属性-通过使用枚举中的值设置 `DTSBulkInsert_DataFileType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-247">`DataFileType` property-Set by using values from the `DTSBulkInsert_DataFileType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-248">DTSBulkInsert_DataFileType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-248">Friendly name in DTSBulkInsert_DataFileType</span></span>|<span data-ttu-id="0a5a3-249">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-249">Numeric value</span></span>|  
|--------------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-250">DTSBulkInsert_DataFileType_Char</span><span class="sxs-lookup"><span data-stu-id="0a5a3-250">DTSBulkInsert_DataFileType_Char</span></span>|<span data-ttu-id="0a5a3-251">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-251">0</span></span>|  
|<span data-ttu-id="0a5a3-252">DTSBulkInsert_DataFileType_Native</span><span class="sxs-lookup"><span data-stu-id="0a5a3-252">DTSBulkInsert_DataFileType_Native</span></span>|<span data-ttu-id="0a5a3-253">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-253">1</span></span>|  
|<span data-ttu-id="0a5a3-254">DTSBulkInsert_DataFileType_WideChar</span><span class="sxs-lookup"><span data-stu-id="0a5a3-254">DTSBulkInsert_DataFileType_WideChar</span></span>|<span data-ttu-id="0a5a3-255">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-255">2</span></span>|  
|<span data-ttu-id="0a5a3-256">DTSBulkInsert_DataFileType_WideNative</span><span class="sxs-lookup"><span data-stu-id="0a5a3-256">DTSBulkInsert_DataFileType_WideNative</span></span>|<span data-ttu-id="0a5a3-257">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-257">3</span></span>|  
  
### <a name="execute-sql-task"></a><span data-ttu-id="0a5a3-258">执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-258">Execute SQL Task</span></span>  
 <span data-ttu-id="0a5a3-259">`ResultSetType`属性-通过使用枚举中的值设置 `ResultSetType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-259">`ResultSetType` property-Set by using values from the `ResultSetType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-260">ResultSetType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-260">Friendly name in ResultSetType</span></span>|<span data-ttu-id="0a5a3-261">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-261">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-262">ResultSetType_None</span><span class="sxs-lookup"><span data-stu-id="0a5a3-262">ResultSetType_None</span></span>|<span data-ttu-id="0a5a3-263">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-263">1</span></span>|  
|<span data-ttu-id="0a5a3-264">ResultSetType_SingleRow</span><span class="sxs-lookup"><span data-stu-id="0a5a3-264">ResultSetType_SingleRow</span></span>|<span data-ttu-id="0a5a3-265">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-265">2</span></span>|  
|<span data-ttu-id="0a5a3-266">ResultSetType_Rowset</span><span class="sxs-lookup"><span data-stu-id="0a5a3-266">ResultSetType_Rowset</span></span>|<span data-ttu-id="0a5a3-267">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-267">3</span></span>|  
|<span data-ttu-id="0a5a3-268">ResultSetType_XML</span><span class="sxs-lookup"><span data-stu-id="0a5a3-268">ResultSetType_XML</span></span>|<span data-ttu-id="0a5a3-269">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-269">4</span></span>|  
  
 <span data-ttu-id="0a5a3-270">`SqlStatementSourceType`属性-通过使用枚举中的值设置 `SqlStatementSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-270">`SqlStatementSourceType` property-Set by using values from the `SqlStatementSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-271">SqlStatementSourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-271">Friendly name in SqlStatementSourceType</span></span>|<span data-ttu-id="0a5a3-272">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-272">Numeric Value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-273">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-273">DirectInput</span></span>|<span data-ttu-id="0a5a3-274">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-274">1</span></span>|  
|<span data-ttu-id="0a5a3-275">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-275">FileConnection</span></span>|<span data-ttu-id="0a5a3-276">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-276">2</span></span>|  
|<span data-ttu-id="0a5a3-277">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-277">Variable</span></span>|<span data-ttu-id="0a5a3-278">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-278">3</span></span>|  
  
### <a name="file-system-task"></a><span data-ttu-id="0a5a3-279">文件系统任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-279">File System Task</span></span>  
 <span data-ttu-id="0a5a3-280">`Operation`属性-通过使用枚举中的值设置 `DTSFileSystemOperation` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-280">`Operation` property-Set by using values from the `DTSFileSystemOperation` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-281">DTSFileSystemOperation 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-281">Friendly name in DTSFileSystemOperation</span></span>|<span data-ttu-id="0a5a3-282">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-282">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-283">CopyFile</span><span class="sxs-lookup"><span data-stu-id="0a5a3-283">CopyFile</span></span>|<span data-ttu-id="0a5a3-284">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-284">0</span></span>|  
|<span data-ttu-id="0a5a3-285">MoveFile</span><span class="sxs-lookup"><span data-stu-id="0a5a3-285">MoveFile</span></span>|<span data-ttu-id="0a5a3-286">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-286">1</span></span>|  
|<span data-ttu-id="0a5a3-287">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="0a5a3-287">DeleteFile</span></span>|<span data-ttu-id="0a5a3-288">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-288">2</span></span>|  
|<span data-ttu-id="0a5a3-289">RenameFile</span><span class="sxs-lookup"><span data-stu-id="0a5a3-289">RenameFile</span></span>|<span data-ttu-id="0a5a3-290">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-290">3</span></span>|  
|<span data-ttu-id="0a5a3-291">SetAttributes</span><span class="sxs-lookup"><span data-stu-id="0a5a3-291">SetAttributes</span></span>|<span data-ttu-id="0a5a3-292">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-292">4</span></span>|  
|<span data-ttu-id="0a5a3-293">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="0a5a3-293">CreateDirectory</span></span>|<span data-ttu-id="0a5a3-294">5</span><span class="sxs-lookup"><span data-stu-id="0a5a3-294">5</span></span>|  
|<span data-ttu-id="0a5a3-295">CopyDirectory</span><span class="sxs-lookup"><span data-stu-id="0a5a3-295">CopyDirectory</span></span>|<span data-ttu-id="0a5a3-296">6</span><span class="sxs-lookup"><span data-stu-id="0a5a3-296">6</span></span>|  
|<span data-ttu-id="0a5a3-297">MoveDirectory</span><span class="sxs-lookup"><span data-stu-id="0a5a3-297">MoveDirectory</span></span>|<span data-ttu-id="0a5a3-298">7</span><span class="sxs-lookup"><span data-stu-id="0a5a3-298">7</span></span>|  
|<span data-ttu-id="0a5a3-299">DeleteDirectory</span><span class="sxs-lookup"><span data-stu-id="0a5a3-299">DeleteDirectory</span></span>|<span data-ttu-id="0a5a3-300">8</span><span class="sxs-lookup"><span data-stu-id="0a5a3-300">8</span></span>|  
|<span data-ttu-id="0a5a3-301">DeleteDirectoryContent</span><span class="sxs-lookup"><span data-stu-id="0a5a3-301">DeleteDirectoryContent</span></span>|<span data-ttu-id="0a5a3-302">9</span><span class="sxs-lookup"><span data-stu-id="0a5a3-302">9</span></span>|  
  
 <span data-ttu-id="0a5a3-303">`Attributes`属性-通过使用枚举中的值设置 `DTSFileSystemAttributes` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-303">`Attributes` property-Set by using values from the `DTSFileSystemAttributes` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-304">DTSFileSystemAttributes 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-304">Friendly name in DTSFileSystemAttributes</span></span>|<span data-ttu-id="0a5a3-305">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-305">Numeric value</span></span>|  
|----------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-306">一般</span><span class="sxs-lookup"><span data-stu-id="0a5a3-306">Normal</span></span>|<span data-ttu-id="0a5a3-307">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-307">0</span></span>|  
|<span data-ttu-id="0a5a3-308">存档</span><span class="sxs-lookup"><span data-stu-id="0a5a3-308">Archive</span></span>|<span data-ttu-id="0a5a3-309">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-309">1</span></span>|  
|<span data-ttu-id="0a5a3-310">Hidden</span><span class="sxs-lookup"><span data-stu-id="0a5a3-310">Hidden</span></span>|<span data-ttu-id="0a5a3-311">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-311">2</span></span>|  
|<span data-ttu-id="0a5a3-312">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="0a5a3-312">ReadOnly</span></span>|<span data-ttu-id="0a5a3-313">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-313">4</span></span>|  
|<span data-ttu-id="0a5a3-314">系统</span><span class="sxs-lookup"><span data-stu-id="0a5a3-314">System</span></span>|<span data-ttu-id="0a5a3-315">8</span><span class="sxs-lookup"><span data-stu-id="0a5a3-315">8</span></span>|  
  
### <a name="ftp-task"></a><span data-ttu-id="0a5a3-316">FTP 任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-316">FTP Task</span></span>  
 <span data-ttu-id="0a5a3-317">`Operation`属性-通过使用枚举中的值设置 `DTSFTPOp` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-317">`Operation` property-Set by using values from the `DTSFTPOp` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-318">DTSFTPOp 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-318">Friendly name in DTSFTPOp</span></span>|<span data-ttu-id="0a5a3-319">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-319">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-320">Send</span><span class="sxs-lookup"><span data-stu-id="0a5a3-320">Send</span></span>|<span data-ttu-id="0a5a3-321">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-321">0</span></span>|  
|<span data-ttu-id="0a5a3-322">接收</span><span class="sxs-lookup"><span data-stu-id="0a5a3-322">Receive</span></span>|<span data-ttu-id="0a5a3-323">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-323">1</span></span>|  
|<span data-ttu-id="0a5a3-324">DeleteLocal</span><span class="sxs-lookup"><span data-stu-id="0a5a3-324">DeleteLocal</span></span>|<span data-ttu-id="0a5a3-325">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-325">2</span></span>|  
|<span data-ttu-id="0a5a3-326">DeleteRemote</span><span class="sxs-lookup"><span data-stu-id="0a5a3-326">DeleteRemote</span></span>|<span data-ttu-id="0a5a3-327">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-327">3</span></span>|  
|<span data-ttu-id="0a5a3-328">MakeDirLocal</span><span class="sxs-lookup"><span data-stu-id="0a5a3-328">MakeDirLocal</span></span>|<span data-ttu-id="0a5a3-329">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-329">4</span></span>|  
|<span data-ttu-id="0a5a3-330">MakeDirRemote</span><span class="sxs-lookup"><span data-stu-id="0a5a3-330">MakeDirRemote</span></span>|<span data-ttu-id="0a5a3-331">5</span><span class="sxs-lookup"><span data-stu-id="0a5a3-331">5</span></span>|  
|<span data-ttu-id="0a5a3-332">RemoveDirLocal</span><span class="sxs-lookup"><span data-stu-id="0a5a3-332">RemoveDirLocal</span></span>|<span data-ttu-id="0a5a3-333">6</span><span class="sxs-lookup"><span data-stu-id="0a5a3-333">6</span></span>|  
|<span data-ttu-id="0a5a3-334">RemoveDirRemote</span><span class="sxs-lookup"><span data-stu-id="0a5a3-334">RemoveDirRemote</span></span>|<span data-ttu-id="0a5a3-335">7</span><span class="sxs-lookup"><span data-stu-id="0a5a3-335">7</span></span>|  
  
### <a name="message-queue-task"></a><span data-ttu-id="0a5a3-336">Message Queue Task</span><span class="sxs-lookup"><span data-stu-id="0a5a3-336">Message Queue Task</span></span>  
 <span data-ttu-id="0a5a3-337">`MessageType`属性-通过使用枚举中的值设置 `MQMessageType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-337">`MessageType` property-Set by using values from the `MQMessageType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-338">MQMessageType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-338">Friendly name in MQMessageType</span></span>|<span data-ttu-id="0a5a3-339">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-339">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-340">DTSMQMessageType_String</span><span class="sxs-lookup"><span data-stu-id="0a5a3-340">DTSMQMessageType_String</span></span>|<span data-ttu-id="0a5a3-341">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-341">0</span></span>|  
|<span data-ttu-id="0a5a3-342">DTSMQMessageType_DataFile</span><span class="sxs-lookup"><span data-stu-id="0a5a3-342">DTSMQMessageType_DataFile</span></span>|<span data-ttu-id="0a5a3-343">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-343">1</span></span>|  
|<span data-ttu-id="0a5a3-344">DTSMQMessageType_Variables</span><span class="sxs-lookup"><span data-stu-id="0a5a3-344">DTSMQMessageType_Variables</span></span>|<span data-ttu-id="0a5a3-345">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-345">2</span></span>|  
|<span data-ttu-id="0a5a3-346">DTSMQMessagType_StringMessageToVariable</span><span class="sxs-lookup"><span data-stu-id="0a5a3-346">DTSMQMessagType_StringMessageToVariable</span></span>|<span data-ttu-id="0a5a3-347">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-347">3</span></span>|  
  
 <span data-ttu-id="0a5a3-348">`StringCompareType`属性-通过使用枚举中的值设置 `MQStringMessageCompare` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-348">`StringCompareType` property-Set by using values from the `MQStringMessageCompare` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-349">MQStringMessageCompare 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-349">Friendly name in MQStringMessageCompare</span></span>|<span data-ttu-id="0a5a3-350">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-350">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-351">DTSMQStringMessageCompare_None</span><span class="sxs-lookup"><span data-stu-id="0a5a3-351">DTSMQStringMessageCompare_None</span></span>|<span data-ttu-id="0a5a3-352">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-352">0</span></span>|  
|<span data-ttu-id="0a5a3-353">DTSMQStringMessageCompare_Exact</span><span class="sxs-lookup"><span data-stu-id="0a5a3-353">DTSMQStringMessageCompare_Exact</span></span>|<span data-ttu-id="0a5a3-354">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-354">1</span></span>|  
|<span data-ttu-id="0a5a3-355">DTSMQStringMessageCompare_IgnoreCase</span><span class="sxs-lookup"><span data-stu-id="0a5a3-355">DTSMQStringMessageCompare_IgnoreCase</span></span>|<span data-ttu-id="0a5a3-356">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-356">2</span></span>|  
|<span data-ttu-id="0a5a3-357">DTSMQStringMessageCompare_Contains</span><span class="sxs-lookup"><span data-stu-id="0a5a3-357">DTSMQStringMessageCompare_Contains</span></span>|<span data-ttu-id="0a5a3-358">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-358">3</span></span>|  
  
 <span data-ttu-id="0a5a3-359">`TaskType`属性-通过使用枚举中的值设置 `MQType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-359">`TaskType` property-Set by using values from the `MQType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-360">MQType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-360">Friendly name in MQType</span></span>|<span data-ttu-id="0a5a3-361">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-361">Numeric value</span></span>|  
|-----------------------------|-------------------|  
|<span data-ttu-id="0a5a3-362">DTSMQType_Sender</span><span class="sxs-lookup"><span data-stu-id="0a5a3-362">DTSMQType_Sender</span></span>|<span data-ttu-id="0a5a3-363">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-363">0</span></span>|  
|<span data-ttu-id="0a5a3-364">DTSMQType_Receiver</span><span class="sxs-lookup"><span data-stu-id="0a5a3-364">DTSMQType_Receiver</span></span>|<span data-ttu-id="0a5a3-365">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-365">1</span></span>|  
  
### <a name="send-mail-task"></a><span data-ttu-id="0a5a3-366">发送邮件任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-366">Send Mail Task</span></span>  
 <span data-ttu-id="0a5a3-367">`MessageSourceType`属性-通过使用枚举中的值设置 `SendMailMessageSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-367">`MessageSourceType` property-Set by using values from the `SendMailMessageSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-368">SendMailMessageSourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-368">Friendly Name in SendMailMessageSourceType</span></span>|<span data-ttu-id="0a5a3-369">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-369">Numeric Value</span></span>|  
|------------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-370">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-370">DirectInput</span></span>|<span data-ttu-id="0a5a3-371">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-371">0</span></span>|  
|<span data-ttu-id="0a5a3-372">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-372">FileConnection</span></span>|<span data-ttu-id="0a5a3-373">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-373">1</span></span>|  
|<span data-ttu-id="0a5a3-374">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-374">Variable</span></span>|<span data-ttu-id="0a5a3-375">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-375">2</span></span>|  
  
 <span data-ttu-id="0a5a3-376">`Priority`属性-通过使用枚举中的值设置 `MailPriority` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-376">`Priority` property-Set by using values from the `MailPriority` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-377">MailPriority 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-377">Friendly Name in MailPriority</span></span>|<span data-ttu-id="0a5a3-378">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-378">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-379">高</span><span class="sxs-lookup"><span data-stu-id="0a5a3-379">High</span></span>|<span data-ttu-id="0a5a3-380">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-380">1</span></span>|  
|<span data-ttu-id="0a5a3-381">一般</span><span class="sxs-lookup"><span data-stu-id="0a5a3-381">Normal</span></span>|<span data-ttu-id="0a5a3-382">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-382">3</span></span>|  
|<span data-ttu-id="0a5a3-383">低</span><span class="sxs-lookup"><span data-stu-id="0a5a3-383">Low</span></span>|<span data-ttu-id="0a5a3-384">5</span><span class="sxs-lookup"><span data-stu-id="0a5a3-384">5</span></span>|  
  
### <a name="transfer-database-task"></a><span data-ttu-id="0a5a3-385">传输数据库任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-385">Transfer Database Task</span></span>  
 <span data-ttu-id="0a5a3-386">`Action`属性-通过使用枚举中的值设置 `TransferAction` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-386">`Action` property-Set by using values from the `TransferAction` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-387">TransferAction 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-387">Friendly name in TransferAction</span></span>|<span data-ttu-id="0a5a3-388">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-388">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-389">复制</span><span class="sxs-lookup"><span data-stu-id="0a5a3-389">Copy</span></span>|<span data-ttu-id="0a5a3-390">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-390">0</span></span>|  
|<span data-ttu-id="0a5a3-391">移动</span><span class="sxs-lookup"><span data-stu-id="0a5a3-391">Move</span></span>|<span data-ttu-id="0a5a3-392">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-392">1</span></span>|  
  
 <span data-ttu-id="0a5a3-393">`Method`属性-通过使用枚举中的值设置 `TransferMethod` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-393">`Method` property-Set by using values from the `TransferMethod` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-394">TransferMethod 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-394">Friendly name in TransferMethod</span></span>|<span data-ttu-id="0a5a3-395">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-395">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-396">DatabaseOffline</span><span class="sxs-lookup"><span data-stu-id="0a5a3-396">DatabaseOffline</span></span>|<span data-ttu-id="0a5a3-397">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-397">0</span></span>|  
|<span data-ttu-id="0a5a3-398">DatabaseOnline</span><span class="sxs-lookup"><span data-stu-id="0a5a3-398">DatabaseOnline</span></span>|<span data-ttu-id="0a5a3-399">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-399">1</span></span>|  
  
### <a name="transfer-error-messages-task"></a><span data-ttu-id="0a5a3-400">传输错误消息任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-400">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="0a5a3-401">`IfObjectExists`属性-通过使用枚举中的值设置 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-401">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-402">IfObjectExists 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-402">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="0a5a3-403">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-403">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-404">FailTask</span><span class="sxs-lookup"><span data-stu-id="0a5a3-404">FailTask</span></span>|<span data-ttu-id="0a5a3-405">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-405">0</span></span>|  
|<span data-ttu-id="0a5a3-406">Overwrite</span><span class="sxs-lookup"><span data-stu-id="0a5a3-406">Overwrite</span></span>|<span data-ttu-id="0a5a3-407">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-407">1</span></span>|  
|<span data-ttu-id="0a5a3-408">跳过</span><span class="sxs-lookup"><span data-stu-id="0a5a3-408">Skip</span></span>|<span data-ttu-id="0a5a3-409">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-409">2</span></span>|  
  
### <a name="transfer-jobs-task"></a><span data-ttu-id="0a5a3-410">传输作业任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-410">Transfer Jobs Task</span></span>  
 <span data-ttu-id="0a5a3-411">`IfObjectExists`属性-通过使用枚举中的值设置 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-411">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-412">IfObjectExists 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-412">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="0a5a3-413">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-413">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-414">FailTask</span><span class="sxs-lookup"><span data-stu-id="0a5a3-414">FailTask</span></span>|<span data-ttu-id="0a5a3-415">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-415">0</span></span>|  
|<span data-ttu-id="0a5a3-416">Overwrite</span><span class="sxs-lookup"><span data-stu-id="0a5a3-416">Overwrite</span></span>|<span data-ttu-id="0a5a3-417">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-417">1</span></span>|  
|<span data-ttu-id="0a5a3-418">跳过</span><span class="sxs-lookup"><span data-stu-id="0a5a3-418">Skip</span></span>|<span data-ttu-id="0a5a3-419">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-419">2</span></span>|  
  
### <a name="transfer-logins-task"></a><span data-ttu-id="0a5a3-420">传输登录名任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-420">Transfer Logins Task</span></span>  
 <span data-ttu-id="0a5a3-421">`IfObjectExists`属性-通过使用枚举中的值设置 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-421">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-422">IfObjectExists 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-422">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="0a5a3-423">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-423">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-424">FailTask</span><span class="sxs-lookup"><span data-stu-id="0a5a3-424">FailTask</span></span>|<span data-ttu-id="0a5a3-425">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-425">0</span></span>|  
|<span data-ttu-id="0a5a3-426">Overwrite</span><span class="sxs-lookup"><span data-stu-id="0a5a3-426">Overwrite</span></span>|<span data-ttu-id="0a5a3-427">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-427">1</span></span>|  
|<span data-ttu-id="0a5a3-428">跳过</span><span class="sxs-lookup"><span data-stu-id="0a5a3-428">Skip</span></span>|<span data-ttu-id="0a5a3-429">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-429">2</span></span>|  
  
 <span data-ttu-id="0a5a3-430">`LoginsToTransfer`属性-通过使用枚举中的值设置 `LoginsToTransfer` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-430">`LoginsToTransfer` property-Set by using values from the `LoginsToTransfer` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-431">LoginsToTransfer 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-431">Friendly name in LoginsToTransfer</span></span>|<span data-ttu-id="0a5a3-432">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-432">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-433">AllLogins</span><span class="sxs-lookup"><span data-stu-id="0a5a3-433">AllLogins</span></span>|<span data-ttu-id="0a5a3-434">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-434">0</span></span>|  
|<span data-ttu-id="0a5a3-435">SelectedLogins</span><span class="sxs-lookup"><span data-stu-id="0a5a3-435">SelectedLogins</span></span>|<span data-ttu-id="0a5a3-436">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-436">1</span></span>|  
|<span data-ttu-id="0a5a3-437">AllLoginsFromSelectedDatabases</span><span class="sxs-lookup"><span data-stu-id="0a5a3-437">AllLoginsFromSelectedDatabases</span></span>|<span data-ttu-id="0a5a3-438">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-438">2</span></span>|  
  
### <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="0a5a3-439">传输主存储过程任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-439">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="0a5a3-440">`IfObjectExists`属性-通过使用枚举中的值设置 `IfObjectExists` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-440">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-441">IfObjectExists 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-441">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="0a5a3-442">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-442">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-443">FailTask</span><span class="sxs-lookup"><span data-stu-id="0a5a3-443">FailTask</span></span>|<span data-ttu-id="0a5a3-444">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-444">0</span></span>|  
|<span data-ttu-id="0a5a3-445">Overwrite</span><span class="sxs-lookup"><span data-stu-id="0a5a3-445">Overwrite</span></span>|<span data-ttu-id="0a5a3-446">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-446">1</span></span>|  
|<span data-ttu-id="0a5a3-447">跳过</span><span class="sxs-lookup"><span data-stu-id="0a5a3-447">Skip</span></span>|<span data-ttu-id="0a5a3-448">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-448">2</span></span>|  
  
### <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="0a5a3-449">传输 SQL Server 对象任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-449">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="0a5a3-450">`ExistingData`属性-通过使用枚举中的值设置 `ExistingData` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-450">`ExistingData` property-Set by using values from the `ExistingData` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-451">ExistingData 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-451">Friendly name in ExistingData</span></span>|<span data-ttu-id="0a5a3-452">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-452">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-453">将</span><span class="sxs-lookup"><span data-stu-id="0a5a3-453">Replace</span></span>|<span data-ttu-id="0a5a3-454">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-454">0</span></span>|  
|<span data-ttu-id="0a5a3-455">附加</span><span class="sxs-lookup"><span data-stu-id="0a5a3-455">Append</span></span>|<span data-ttu-id="0a5a3-456">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-456">1</span></span>|  
  
### <a name="web-service-task"></a><span data-ttu-id="0a5a3-457">Web 服务任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-457">Web Service Task</span></span>  
 <span data-ttu-id="0a5a3-458">`OutputType`属性-通过使用枚举中的值设置 `DTSOutputType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-458">`OutputType` property-Set by using values from the `DTSOutputType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-459">DTSOutputType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-459">Friendly name in DTSOutputType</span></span>|<span data-ttu-id="0a5a3-460">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-460">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-461">文件</span><span class="sxs-lookup"><span data-stu-id="0a5a3-461">File</span></span>|<span data-ttu-id="0a5a3-462">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-462">0</span></span>|  
|<span data-ttu-id="0a5a3-463">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-463">Variable</span></span>|<span data-ttu-id="0a5a3-464">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-464">1</span></span>|  
  
### <a name="wmi-data-reader-task"></a><span data-ttu-id="0a5a3-465">WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-465">WMI Data Reader Task</span></span>  
 <span data-ttu-id="0a5a3-466">`OverwriteDestination`属性-通过使用枚举中的值设置 `OverwriteDestination` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-466">`OverwriteDestination` property-Set by using values from the `OverwriteDestination` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-467">OverwriteDestination 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-467">Friendly name in OverwriteDestination</span></span>|<span data-ttu-id="0a5a3-468">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-468">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-469">OverwriteDestination</span><span class="sxs-lookup"><span data-stu-id="0a5a3-469">OverwriteDestination</span></span>|<span data-ttu-id="0a5a3-470">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-470">0</span></span>|  
|<span data-ttu-id="0a5a3-471">AppendToDestination</span><span class="sxs-lookup"><span data-stu-id="0a5a3-471">AppendToDestination</span></span>|<span data-ttu-id="0a5a3-472">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-472">1</span></span>|  
|<span data-ttu-id="0a5a3-473">KeepOriginal</span><span class="sxs-lookup"><span data-stu-id="0a5a3-473">KeepOriginal</span></span>|<span data-ttu-id="0a5a3-474">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-474">2</span></span>|  
  
 <span data-ttu-id="0a5a3-475">`OutputType`属性-通过使用枚举中的值设置 `OutputType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-475">`OutputType` property-Set by using values from the `OutputType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-476">OutputType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-476">Friendly name in OutputType</span></span>|<span data-ttu-id="0a5a3-477">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-477">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-478">DataTable</span><span class="sxs-lookup"><span data-stu-id="0a5a3-478">DataTable</span></span>|<span data-ttu-id="0a5a3-479">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-479">0</span></span>|  
|<span data-ttu-id="0a5a3-480">PropertyValue</span><span class="sxs-lookup"><span data-stu-id="0a5a3-480">PropertyValue</span></span>|<span data-ttu-id="0a5a3-481">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-481">1</span></span>|  
|<span data-ttu-id="0a5a3-482">PropertyNameAndValue</span><span class="sxs-lookup"><span data-stu-id="0a5a3-482">PropertyNameAndValue</span></span>|<span data-ttu-id="0a5a3-483">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-483">2</span></span>|  
  
 <span data-ttu-id="0a5a3-484">`DestinationType`属性-通过使用枚举中的值设置 `DestinationType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-484">`DestinationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-485">DestinationType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-485">Friendly name in DestinationType</span></span>|<span data-ttu-id="0a5a3-486">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-486">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-487">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-487">FileConnection</span></span>|<span data-ttu-id="0a5a3-488">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-488">0</span></span>|  
|<span data-ttu-id="0a5a3-489">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-489">Variable</span></span>|<span data-ttu-id="0a5a3-490">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-490">1</span></span>|  
  
 <span data-ttu-id="0a5a3-491">`WqlQuerySourceType`属性-通过使用枚举中的值设置 `QuerySourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-491">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-492">QuerySourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-492">Friendly Name in QuerySourceType</span></span>|<span data-ttu-id="0a5a3-493">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-493">Numeric Value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-494">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-494">FileConnection</span></span>|<span data-ttu-id="0a5a3-495">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-495">0</span></span>|  
|<span data-ttu-id="0a5a3-496">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-496">DirectInput</span></span>|<span data-ttu-id="0a5a3-497">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-497">1</span></span>|  
|<span data-ttu-id="0a5a3-498">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-498">Variable</span></span>|<span data-ttu-id="0a5a3-499">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-499">2</span></span>|  
  
 <span data-ttu-id="0a5a3-500">WMI 事件观察器 `ActionAtEvent` 属性-通过使用枚举中的值设置 `ActionAtEvent` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-500">WMI Event Watcher `ActionAtEvent` property-Set by using values from the `ActionAtEvent` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-501">ActionAtEvent 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-501">Friendly Name in ActionAtEvent</span></span>|<span data-ttu-id="0a5a3-502">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-502">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-503">LogTheEventAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="0a5a3-503">LogTheEventAndFireDTSEvent</span></span>|<span data-ttu-id="0a5a3-504">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-504">0</span></span>|  
|<span data-ttu-id="0a5a3-505">LogTheEvent</span><span class="sxs-lookup"><span data-stu-id="0a5a3-505">LogTheEvent</span></span>|<span data-ttu-id="0a5a3-506">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-506">1</span></span>|  
  
 <span data-ttu-id="0a5a3-507">`ActionAtTimeout`属性-通过使用枚举中的值设置 `ActionAtTimeout` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-507">`ActionAtTimeout` property-Set by using values from the `ActionAtTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-508">ActionAtTimeout 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-508">Friendly name in ActionAtTimeout</span></span>|<span data-ttu-id="0a5a3-509">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-509">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-510">LogTimeoutAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="0a5a3-510">LogTimeoutAndFireDTSEvent</span></span>|<span data-ttu-id="0a5a3-511">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-511">0</span></span>|  
|<span data-ttu-id="0a5a3-512">LogTimeout</span><span class="sxs-lookup"><span data-stu-id="0a5a3-512">LogTimeout</span></span>|<span data-ttu-id="0a5a3-513">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-513">1</span></span>|  
  
 <span data-ttu-id="0a5a3-514">`AfterEvent`属性-通过使用枚举中的值设置 `AfterEvent` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-514">`AfterEvent` property-Set by using values from the `AfterEvent` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-515">AfterEvent 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-515">Friendly name in AfterEvent</span></span>|<span data-ttu-id="0a5a3-516">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-516">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-517">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="0a5a3-517">ReturnWithSuccess</span></span>|<span data-ttu-id="0a5a3-518">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-518">0</span></span>|  
|<span data-ttu-id="0a5a3-519">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="0a5a3-519">ReturnWithFailure</span></span>|<span data-ttu-id="0a5a3-520">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-520">1</span></span>|  
|<span data-ttu-id="0a5a3-521">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="0a5a3-521">WatchfortheEventAgain</span></span>|<span data-ttu-id="0a5a3-522">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-522">2</span></span>|  
  
 <span data-ttu-id="0a5a3-523">`AfterTimeout`属性-通过使用枚举中的值设置 `AfterTimeout` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-523">`AfterTimeout` property-Set by using values from the `AfterTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-524">AfterTimeout 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-524">Friendly name in AfterTimeout</span></span>|<span data-ttu-id="0a5a3-525">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-525">Numeric value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-526">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="0a5a3-526">ReturnWithSuccess</span></span>|<span data-ttu-id="0a5a3-527">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-527">0</span></span>|  
|<span data-ttu-id="0a5a3-528">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="0a5a3-528">ReturnWithFailure</span></span>|<span data-ttu-id="0a5a3-529">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-529">1</span></span>|  
|<span data-ttu-id="0a5a3-530">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="0a5a3-530">WatchfortheEventAgain</span></span>|<span data-ttu-id="0a5a3-531">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-531">2</span></span>|  
  
 <span data-ttu-id="0a5a3-532">`WqlQuerySourceType`属性-通过使用枚举中的值设置 `QuerySourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-532">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-533">QuerySourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-533">Friendly name in QuerySourceType</span></span>|<span data-ttu-id="0a5a3-534">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-534">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-535">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-535">FileConnection</span></span>|<span data-ttu-id="0a5a3-536">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-536">0</span></span>|  
|<span data-ttu-id="0a5a3-537">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-537">DirectInput</span></span>|<span data-ttu-id="0a5a3-538">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-538">1</span></span>|  
|<span data-ttu-id="0a5a3-539">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-539">Variable</span></span>|<span data-ttu-id="0a5a3-540">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-540">2</span></span>|  
  
### <a name="xml-task"></a><span data-ttu-id="0a5a3-541">XML 任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-541">XML Task</span></span>  
 <span data-ttu-id="0a5a3-542">`OperationType`属性-通过使用枚举中的值设置 `DTSXMLOperation` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-542">`OperationType` property-Set by using values from the `DTSXMLOperation` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-543">DTSXMLOperation 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-543">Friendly name in DTSXMLOperation</span></span>|<span data-ttu-id="0a5a3-544">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-544">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-545">验证</span><span class="sxs-lookup"><span data-stu-id="0a5a3-545">Validate</span></span>|<span data-ttu-id="0a5a3-546">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-546">0</span></span>|  
|<span data-ttu-id="0a5a3-547">XSLT</span><span class="sxs-lookup"><span data-stu-id="0a5a3-547">XSLT</span></span>|<span data-ttu-id="0a5a3-548">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-548">1</span></span>|  
|<span data-ttu-id="0a5a3-549">XPATH</span><span class="sxs-lookup"><span data-stu-id="0a5a3-549">XPATH</span></span>|<span data-ttu-id="0a5a3-550">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-550">2</span></span>|  
|<span data-ttu-id="0a5a3-551">合并</span><span class="sxs-lookup"><span data-stu-id="0a5a3-551">Merge</span></span>|<span data-ttu-id="0a5a3-552">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-552">3</span></span>|  
|<span data-ttu-id="0a5a3-553">差异</span><span class="sxs-lookup"><span data-stu-id="0a5a3-553">Diff</span></span>|<span data-ttu-id="0a5a3-554">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-554">4</span></span>|  
|<span data-ttu-id="0a5a3-555">修补程序</span><span class="sxs-lookup"><span data-stu-id="0a5a3-555">Patch</span></span>|<span data-ttu-id="0a5a3-556">5</span><span class="sxs-lookup"><span data-stu-id="0a5a3-556">5</span></span>|  
  
 <span data-ttu-id="0a5a3-557">`SourceType`、 `SecondOperandType` 和 `XPathSourceType` 属性-通过使用枚举中的值设置 `DTSXMLSourceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-557">`SourceType`, `SecondOperandType`, and `XPathSourceType` properties-Set by using values from the `DTSXMLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-558">DTSXMLSourceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-558">Friendly name in DTSXMLSourceType</span></span>|<span data-ttu-id="0a5a3-559">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-559">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-560">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-560">FileConnection</span></span>|<span data-ttu-id="0a5a3-561">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-561">0</span></span>|  
|<span data-ttu-id="0a5a3-562">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-562">Variable</span></span>|<span data-ttu-id="0a5a3-563">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-563">1</span></span>|  
|<span data-ttu-id="0a5a3-564">DirectInput</span><span class="sxs-lookup"><span data-stu-id="0a5a3-564">DirectInput</span></span>|<span data-ttu-id="0a5a3-565">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-565">2</span></span>|  
  
 <span data-ttu-id="0a5a3-566">`DestinationType`和**DiffGramDestinationType**属性-通过使用枚举中的值设置 `DTSXMLSaveResultTo` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-566">`DestinationType` and **DiffGramDestinationType** properties-Set by using values from the `DTSXMLSaveResultTo` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-567">DTSXMLSaveResultTo 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-567">Friendly name in DTSXMLSaveResultTo</span></span>|<span data-ttu-id="0a5a3-568">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-568">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-569">文件连接</span><span class="sxs-lookup"><span data-stu-id="0a5a3-569">FileConnection</span></span>|<span data-ttu-id="0a5a3-570">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-570">0</span></span>|  
|<span data-ttu-id="0a5a3-571">变量</span><span class="sxs-lookup"><span data-stu-id="0a5a3-571">Variable</span></span>|<span data-ttu-id="0a5a3-572">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-572">1</span></span>|  
  
 <span data-ttu-id="0a5a3-573">`ValidationType`属性-通过使用枚举中的值设置 `DTSXMLValidationType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-573">`ValidationType` property-Set by using values from the `DTSXMLValidationType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-574">DTSXMLValidationType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-574">Friendly name in DTSXMLValidationType</span></span>|<span data-ttu-id="0a5a3-575">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-575">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-576">DTD</span><span class="sxs-lookup"><span data-stu-id="0a5a3-576">DTD</span></span>|<span data-ttu-id="0a5a3-577">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-577">0</span></span>|  
|<span data-ttu-id="0a5a3-578">XSD</span><span class="sxs-lookup"><span data-stu-id="0a5a3-578">XSD</span></span>|<span data-ttu-id="0a5a3-579">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-579">1</span></span>|  
  
 <span data-ttu-id="0a5a3-580">`XPathOperation`属性-通过使用枚举中的值设置 `DTSXMLXPathOperation` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-580">`XPathOperation` property-Set by using values from the `DTSXMLXPathOperation` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-581">DTSXMLXPathOperation 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-581">Friendly name in DTSXMLXPathOperation</span></span>|<span data-ttu-id="0a5a3-582">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-582">Numeric Value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-583">计算</span><span class="sxs-lookup"><span data-stu-id="0a5a3-583">Evaluation</span></span>|<span data-ttu-id="0a5a3-584">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-584">0</span></span>|  
|<span data-ttu-id="0a5a3-585">值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-585">Values</span></span>|<span data-ttu-id="0a5a3-586">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-586">1</span></span>|  
|<span data-ttu-id="0a5a3-587">NodeList</span><span class="sxs-lookup"><span data-stu-id="0a5a3-587">NodeList</span></span>|<span data-ttu-id="0a5a3-588">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-588">2</span></span>|  
  
 <span data-ttu-id="0a5a3-589">`DiffOptions`属性-通过使用枚举中的值设置 `DTSXMLDiffOptions` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-589">`DiffOptions` property-Set by using values from the `DTSXMLDiffOptions` enumeration.</span></span> <span data-ttu-id="0a5a3-590">此枚举器中的选项不相互排斥。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-590">The options in this enumerator are not mutually exclusive.</span></span> <span data-ttu-id="0a5a3-591">若要使用多个选项，请将要应用的选项作为逗号分隔的列表提供。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-591">To use multiple options, provide a comma-separated list of the options to apply.</span></span>  
  
|<span data-ttu-id="0a5a3-592">DTSXMLDiffOptions 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-592">Friendly name in DTSXMLDiffOptions</span></span>|<span data-ttu-id="0a5a3-593">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-593">Numeric Value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-594">无</span><span class="sxs-lookup"><span data-stu-id="0a5a3-594">None</span></span>|<span data-ttu-id="0a5a3-595">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-595">0</span></span>|  
|<span data-ttu-id="0a5a3-596">IgnoreChildOrder</span><span class="sxs-lookup"><span data-stu-id="0a5a3-596">IgnoreChildOrder</span></span>|<span data-ttu-id="0a5a3-597">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-597">1</span></span>|  
|<span data-ttu-id="0a5a3-598">IgnoreComments</span><span class="sxs-lookup"><span data-stu-id="0a5a3-598">IgnoreComments</span></span>|<span data-ttu-id="0a5a3-599">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-599">2</span></span>|  
|<span data-ttu-id="0a5a3-600">IgnorePI</span><span class="sxs-lookup"><span data-stu-id="0a5a3-600">IgnorePI</span></span>|<span data-ttu-id="0a5a3-601">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-601">4</span></span>|  
|<span data-ttu-id="0a5a3-602">IgnoreWhitespace</span><span class="sxs-lookup"><span data-stu-id="0a5a3-602">IgnoreWhitespace</span></span>|<span data-ttu-id="0a5a3-603">8</span><span class="sxs-lookup"><span data-stu-id="0a5a3-603">8</span></span>|  
|<span data-ttu-id="0a5a3-604">IgnoreNamespaces</span><span class="sxs-lookup"><span data-stu-id="0a5a3-604">IgnoreNamespaces</span></span>|<span data-ttu-id="0a5a3-605">16</span><span class="sxs-lookup"><span data-stu-id="0a5a3-605">16</span></span>|  
|<span data-ttu-id="0a5a3-606">IgnorePrefixes</span><span class="sxs-lookup"><span data-stu-id="0a5a3-606">IgnorePrefixes</span></span>|<span data-ttu-id="0a5a3-607">32</span><span class="sxs-lookup"><span data-stu-id="0a5a3-607">32</span></span>|  
|<span data-ttu-id="0a5a3-608">IgnoreXmlDecl</span><span class="sxs-lookup"><span data-stu-id="0a5a3-608">IgnoreXmlDecl</span></span>|<span data-ttu-id="0a5a3-609">64</span><span class="sxs-lookup"><span data-stu-id="0a5a3-609">64</span></span>|  
|<span data-ttu-id="0a5a3-610">IgnoreDtd</span><span class="sxs-lookup"><span data-stu-id="0a5a3-610">IgnoreDtd</span></span>|<span data-ttu-id="0a5a3-611">128</span><span class="sxs-lookup"><span data-stu-id="0a5a3-611">128</span></span>|  
  
 <span data-ttu-id="0a5a3-612">`DiffAlgorithm`属性-通过使用枚举中的值设置 `DTSXMLDiffAlgorithm` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-612">`DiffAlgorithm` property-Set by using values from the `DTSXMLDiffAlgorithm` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-613">DTSXMLDiffAlgorithm 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-613">Friendly name in DTSXMLDiffAlgorithm</span></span>|<span data-ttu-id="0a5a3-614">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-614">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-615">Auto</span><span class="sxs-lookup"><span data-stu-id="0a5a3-615">Auto</span></span>|<span data-ttu-id="0a5a3-616">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-616">0</span></span>|  
|<span data-ttu-id="0a5a3-617">Fast</span><span class="sxs-lookup"><span data-stu-id="0a5a3-617">Fast</span></span>|<span data-ttu-id="0a5a3-618">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-618">1</span></span>|  
|<span data-ttu-id="0a5a3-619">Precise</span><span class="sxs-lookup"><span data-stu-id="0a5a3-619">Precise</span></span>|<span data-ttu-id="0a5a3-620">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-620">2</span></span>|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> <span data-ttu-id="0a5a3-621">维护计划任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-621">Maintenance Plan Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="0a5a3-622">包括的一组任务将执行在维护计划和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中使用的 SQL Server 任务。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-622">includes a set of tasks that perform SQL Server tasks for use in maintenance plans and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0a5a3-623">不支持通过编程来使用这些任务，而且编程参考文档不包括这些任务及其枚举器的 API 文档。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-623">does not support working with these tasks programmatically and programming reference documentation does not include API documentation of these tasks and their enumerators.</span></span>  
  
### <a name="all-maintenance-tasks"></a><span data-ttu-id="0a5a3-624">所有维护任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-624">All Maintenance Tasks</span></span>  
 <span data-ttu-id="0a5a3-625">所有维护任务均使用以下枚举来设置指定的属性。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-625">All maintenance tasks use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="0a5a3-626">`DatabaseSelectionType`属性-通过使用枚举中的值设置 `DatabaseSelection` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-626">`DatabaseSelectionType` property-Set by using values from the `DatabaseSelection` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-627">DatabaseSelection 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-627">Friendly name in DatabaseSelection</span></span>|<span data-ttu-id="0a5a3-628">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-628">Numeric value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-629">无</span><span class="sxs-lookup"><span data-stu-id="0a5a3-629">None</span></span>|<span data-ttu-id="0a5a3-630">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-630">0</span></span>|  
|<span data-ttu-id="0a5a3-631">All</span><span class="sxs-lookup"><span data-stu-id="0a5a3-631">All</span></span>|<span data-ttu-id="0a5a3-632">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-632">1</span></span>|  
|<span data-ttu-id="0a5a3-633">系统</span><span class="sxs-lookup"><span data-stu-id="0a5a3-633">System</span></span>|<span data-ttu-id="0a5a3-634">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-634">2</span></span>|  
|<span data-ttu-id="0a5a3-635">用户</span><span class="sxs-lookup"><span data-stu-id="0a5a3-635">User</span></span>|<span data-ttu-id="0a5a3-636">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-636">3</span></span>|  
|<span data-ttu-id="0a5a3-637">特定</span><span class="sxs-lookup"><span data-stu-id="0a5a3-637">Specific</span></span>|<span data-ttu-id="0a5a3-638">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-638">4</span></span>|  
  
 <span data-ttu-id="0a5a3-639">`TableSelectionType`属性-通过使用枚举中的值设置 `TableSelection` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-639">`TableSelectionType` property-Set by using values from the `TableSelection` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-640">TableSelection 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-640">Friendly name in TableSelection</span></span>|<span data-ttu-id="0a5a3-641">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-641">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-642">无</span><span class="sxs-lookup"><span data-stu-id="0a5a3-642">None</span></span>|<span data-ttu-id="0a5a3-643">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-643">0</span></span>|  
|<span data-ttu-id="0a5a3-644">All</span><span class="sxs-lookup"><span data-stu-id="0a5a3-644">All</span></span>|<span data-ttu-id="0a5a3-645">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-645">1</span></span>|  
|<span data-ttu-id="0a5a3-646">特定</span><span class="sxs-lookup"><span data-stu-id="0a5a3-646">Specific</span></span>|<span data-ttu-id="0a5a3-647">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-647">2</span></span>|  
  
 <span data-ttu-id="0a5a3-648">`ObjectTypeSelection`属性-通过使用枚举中的值设置 `ObjectType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-648">`ObjectTypeSelection` property-Set by using values from the `ObjectType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-649">ObjectType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-649">Friendly name in ObjectType</span></span>|<span data-ttu-id="0a5a3-650">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-650">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-651">表</span><span class="sxs-lookup"><span data-stu-id="0a5a3-651">Table</span></span>|<span data-ttu-id="0a5a3-652">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-652">0</span></span>|  
|<span data-ttu-id="0a5a3-653">查看</span><span class="sxs-lookup"><span data-stu-id="0a5a3-653">View</span></span>|<span data-ttu-id="0a5a3-654">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-654">1</span></span>|  
|<span data-ttu-id="0a5a3-655">TableView</span><span class="sxs-lookup"><span data-stu-id="0a5a3-655">TableView</span></span>|<span data-ttu-id="0a5a3-656">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-656">2</span></span>|  
  
### <a name="back-up-database-task"></a><span data-ttu-id="0a5a3-657">“备份数据库”任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-657">Back Up Database Task</span></span>  
 <span data-ttu-id="0a5a3-658">`DestinationCreationType`属性-通过使用枚举中的值设置 `DestinationType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-658">`DestinationCreationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-659">DestinationType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-659">Friendly name in DestinationType</span></span>|<span data-ttu-id="0a5a3-660">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-660">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-661">Auto</span><span class="sxs-lookup"><span data-stu-id="0a5a3-661">Auto</span></span>|<span data-ttu-id="0a5a3-662">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-662">0</span></span>|  
|<span data-ttu-id="0a5a3-663">手动</span><span class="sxs-lookup"><span data-stu-id="0a5a3-663">Manual</span></span>|<span data-ttu-id="0a5a3-664">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-664">1</span></span>|  
  
 <span data-ttu-id="0a5a3-665">`ExistingBackupsAction`属性-通过使用枚举中的值设置 `ActionForExistingBackups` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-665">`ExistingBackupsAction` property-Set by using values from the `ActionForExistingBackups` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-666">ActionForExistingBackups 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-666">Friendly name in ActionForExistingBackups</span></span>|<span data-ttu-id="0a5a3-667">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-667">Numeric value</span></span>|  
|-----------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-668">附加</span><span class="sxs-lookup"><span data-stu-id="0a5a3-668">Append</span></span>|<span data-ttu-id="0a5a3-669">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-669">0</span></span>|  
|<span data-ttu-id="0a5a3-670">Overwrite</span><span class="sxs-lookup"><span data-stu-id="0a5a3-670">Overwrite</span></span>|<span data-ttu-id="0a5a3-671">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-671">1</span></span>|  
  
 <span data-ttu-id="0a5a3-672">`BackupAction`属性-通过使用枚举中的值设置 `BackupTaskType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-672">`BackupAction` property-Set by using values from the `BackupTaskType` enumeration.</span></span> <span data-ttu-id="0a5a3-673">此属性与 `BackupIsIncremental` 属性一起使用以定义该任务所执行的备份的类型。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-673">This property works with the `BackupIsIncremental` property to define the type of backup that the task performs.</span></span>  
  
|<span data-ttu-id="0a5a3-674">BackupTaskType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-674">Friendly name in BackupTaskType</span></span>|<span data-ttu-id="0a5a3-675">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-675">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-676">数据库</span><span class="sxs-lookup"><span data-stu-id="0a5a3-676">Database</span></span>|<span data-ttu-id="0a5a3-677">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-677">0</span></span>|  
|<span data-ttu-id="0a5a3-678">文件</span><span class="sxs-lookup"><span data-stu-id="0a5a3-678">Files</span></span>|<span data-ttu-id="0a5a3-679">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-679">1</span></span>|  
|<span data-ttu-id="0a5a3-680">日志</span><span class="sxs-lookup"><span data-stu-id="0a5a3-680">Log</span></span>|<span data-ttu-id="0a5a3-681">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-681">2</span></span>|  
  
 <span data-ttu-id="0a5a3-682">`BackupDevice`通过使用管理对象中的值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) 枚举来设置属性 `DeviceType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-682">`BackupDevice` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `DeviceType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-683">DeviceType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-683">Friendly name in DeviceType</span></span>|<span data-ttu-id="0a5a3-684">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-684">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-685">LogicalDevice</span><span class="sxs-lookup"><span data-stu-id="0a5a3-685">LogicalDevice</span></span>|<span data-ttu-id="0a5a3-686">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-686">0</span></span>|  
|<span data-ttu-id="0a5a3-687">磁带</span><span class="sxs-lookup"><span data-stu-id="0a5a3-687">Tape</span></span>|<span data-ttu-id="0a5a3-688">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-688">1</span></span>|  
|<span data-ttu-id="0a5a3-689">文件</span><span class="sxs-lookup"><span data-stu-id="0a5a3-689">File</span></span>|<span data-ttu-id="0a5a3-690">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-690">2</span></span>|  
|<span data-ttu-id="0a5a3-691">Pipe</span><span class="sxs-lookup"><span data-stu-id="0a5a3-691">Pipe</span></span>|<span data-ttu-id="0a5a3-692">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-692">3</span></span>|  
|<span data-ttu-id="0a5a3-693">VirtualDevice</span><span class="sxs-lookup"><span data-stu-id="0a5a3-693">VirtualDevice</span></span>|<span data-ttu-id="0a5a3-694">4</span><span class="sxs-lookup"><span data-stu-id="0a5a3-694">4</span></span>|  
  
### <a name="maintenance-cleanup-task"></a><span data-ttu-id="0a5a3-695">“清除维护”任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-695">Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="0a5a3-696">`FileTypeSelected`属性-通过使用枚举中的值设置 `FileType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-696">`FileTypeSelected` property-Set by using values from the `FileType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-697">FileType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-697">Friendly name in FileType</span></span>|<span data-ttu-id="0a5a3-698">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-698">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-699">FileBackup</span><span class="sxs-lookup"><span data-stu-id="0a5a3-699">FileBackup</span></span>|<span data-ttu-id="0a5a3-700">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-700">0</span></span>|  
|<span data-ttu-id="0a5a3-701">FileReport</span><span class="sxs-lookup"><span data-stu-id="0a5a3-701">FileReport</span></span>|<span data-ttu-id="0a5a3-702">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-702">1</span></span>|  
  
 <span data-ttu-id="0a5a3-703">`OlderThanTimeUnitType`属性-通过使用枚举中的值设置 `TimeUnitType` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-703">`OlderThanTimeUnitType` property-Set by using values from the `TimeUnitType` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-704">TimeUnitType 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-704">Friendly Name in TimeUnitType</span></span>|<span data-ttu-id="0a5a3-705">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-705">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-706">日期</span><span class="sxs-lookup"><span data-stu-id="0a5a3-706">Day</span></span>|<span data-ttu-id="0a5a3-707">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-707">0</span></span>|  
|<span data-ttu-id="0a5a3-708">Week</span><span class="sxs-lookup"><span data-stu-id="0a5a3-708">Week</span></span>|<span data-ttu-id="0a5a3-709">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-709">1</span></span>|  
|<span data-ttu-id="0a5a3-710">月份</span><span class="sxs-lookup"><span data-stu-id="0a5a3-710">Month</span></span>|<span data-ttu-id="0a5a3-711">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-711">2</span></span>|  
|<span data-ttu-id="0a5a3-712">年龄</span><span class="sxs-lookup"><span data-stu-id="0a5a3-712">Year</span></span>|<span data-ttu-id="0a5a3-713">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-713">3</span></span>|  
  
### <a name="update-statistics-task"></a><span data-ttu-id="0a5a3-714">“更新统计信息”任务</span><span class="sxs-lookup"><span data-stu-id="0a5a3-714">Update Statistics Task</span></span>  
 <span data-ttu-id="0a5a3-715">`UpdateType`通过使用管理对象中的值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) 枚举来设置属性 `StatisticsTarget` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-715">`UpdateType` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `StatisticsTarget` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-716">StatisticsTarget 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-716">Friendly name in StatisticsTarget</span></span>|<span data-ttu-id="0a5a3-717">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-717">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-718">列</span><span class="sxs-lookup"><span data-stu-id="0a5a3-718">Column</span></span>|<span data-ttu-id="0a5a3-719">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-719">1</span></span>|  
|<span data-ttu-id="0a5a3-720">索引</span><span class="sxs-lookup"><span data-stu-id="0a5a3-720">Index</span></span>|<span data-ttu-id="0a5a3-721">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-721">2</span></span>|  
|<span data-ttu-id="0a5a3-722">All</span><span class="sxs-lookup"><span data-stu-id="0a5a3-722">All</span></span>|<span data-ttu-id="0a5a3-723">3</span><span class="sxs-lookup"><span data-stu-id="0a5a3-723">3</span></span>|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> <span data-ttu-id="0a5a3-724">通用属性</span><span class="sxs-lookup"><span data-stu-id="0a5a3-724">Common Properties</span></span>  
 <span data-ttu-id="0a5a3-725">包、任务和 Foreach 循环、For 循环和序列容器可以使用以下枚举来设置指定的属性。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-725">Packages, tasks, and the Foreach Loop, For Loop, and Sequence containers can use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="0a5a3-726">`ForceExecutionResult`属性-通过使用枚举中的值设置 `DTSForcedExecResult` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-726">`ForceExecutionResult` property-Set by using values from the `DTSForcedExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-727">DTSForcedExecResult 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-727">Friendly name in DTSForcedExecResult</span></span>|<span data-ttu-id="0a5a3-728">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-728">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-729">无</span><span class="sxs-lookup"><span data-stu-id="0a5a3-729">None</span></span>|<span data-ttu-id="0a5a3-730">-1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-730">-1</span></span>|  
|<span data-ttu-id="0a5a3-731">Success</span><span class="sxs-lookup"><span data-stu-id="0a5a3-731">Success</span></span>|<span data-ttu-id="0a5a3-732">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-732">0</span></span>|  
|<span data-ttu-id="0a5a3-733">失败</span><span class="sxs-lookup"><span data-stu-id="0a5a3-733">Failure</span></span>|<span data-ttu-id="0a5a3-734">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-734">1</span></span>|  
|<span data-ttu-id="0a5a3-735">Completion</span><span class="sxs-lookup"><span data-stu-id="0a5a3-735">Completion</span></span>|<span data-ttu-id="0a5a3-736">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-736">2</span></span>|  
  
 <span data-ttu-id="0a5a3-737">`IsolationLevel`属性-由 .NET Framework 枚举设置 `IsolationLevel` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-737">`IsolationLevel` property-Set by the .NET Framework `IsolationLevel` enumeration.</span></span> <span data-ttu-id="0a5a3-738">详细信息，请参阅位于 [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313)中的 .NET Framework 类库。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-738">For more information, see the .NET Framework Class Library in the [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).</span></span>  
  
 <span data-ttu-id="0a5a3-739">`LoggingMode`属性-通过使用枚举中的值设置 `DTSLoggingMode` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-739">`LoggingMode` property-Set by using values from the `DTSLoggingMode` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-740">DTSLoggingMode 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-740">Friendly name in DTSLoggingMode</span></span>|<span data-ttu-id="0a5a3-741">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-741">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-742">UseParentSetting</span><span class="sxs-lookup"><span data-stu-id="0a5a3-742">UseParentSetting</span></span>|<span data-ttu-id="0a5a3-743">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-743">0</span></span>|  
|<span data-ttu-id="0a5a3-744">已启用</span><span class="sxs-lookup"><span data-stu-id="0a5a3-744">Enabled</span></span>|<span data-ttu-id="0a5a3-745">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-745">1</span></span>|  
|<span data-ttu-id="0a5a3-746">已禁用</span><span class="sxs-lookup"><span data-stu-id="0a5a3-746">Disabled</span></span>|<span data-ttu-id="0a5a3-747">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-747">2</span></span>|  
  
 <span data-ttu-id="0a5a3-748">`TransactionOption`属性-通过使用枚举中的值设置 `DTSTransactionOption` 。</span><span class="sxs-lookup"><span data-stu-id="0a5a3-748">`TransactionOption` property-Set by using values from the `DTSTransactionOption` enumeration.</span></span>  
  
|<span data-ttu-id="0a5a3-749">DTSTransactionOption 中的友好名称</span><span class="sxs-lookup"><span data-stu-id="0a5a3-749">Friendly name in DTSTransactionOption</span></span>|<span data-ttu-id="0a5a3-750">数值</span><span class="sxs-lookup"><span data-stu-id="0a5a3-750">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="0a5a3-751">NotSupported</span><span class="sxs-lookup"><span data-stu-id="0a5a3-751">NotSupported</span></span>|<span data-ttu-id="0a5a3-752">0</span><span class="sxs-lookup"><span data-stu-id="0a5a3-752">0</span></span>|  
|<span data-ttu-id="0a5a3-753">支持</span><span class="sxs-lookup"><span data-stu-id="0a5a3-753">Supported</span></span>|<span data-ttu-id="0a5a3-754">1</span><span class="sxs-lookup"><span data-stu-id="0a5a3-754">1</span></span>|  
|<span data-ttu-id="0a5a3-755">必选</span><span class="sxs-lookup"><span data-stu-id="0a5a3-755">Required</span></span>|<span data-ttu-id="0a5a3-756">2</span><span class="sxs-lookup"><span data-stu-id="0a5a3-756">2</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="0a5a3-757">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0a5a3-757">Related Tasks</span></span>  
 [<span data-ttu-id="0a5a3-758">添加或更改属性表达式</span><span class="sxs-lookup"><span data-stu-id="0a5a3-758">Add or Change a Property Expression</span></span>](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a><span data-ttu-id="0a5a3-759">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a5a3-759">See Also</span></span>  
 <span data-ttu-id="0a5a3-760">[在包中使用属性表达式](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="0a5a3-760">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="0a5a3-761">[Integration Services (SSIS) 包](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="0a5a3-761">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="0a5a3-762">[Integration Services 容器](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="0a5a3-762">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="0a5a3-763">[Integration Services 任务](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="0a5a3-763">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="0a5a3-764">优先约束</span><span class="sxs-lookup"><span data-stu-id="0a5a3-764">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
  
