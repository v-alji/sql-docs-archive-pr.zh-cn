---
title: " (ssbdiagnose) 发出元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: stevestein
ms.author: sstein
ms.openlocfilehash: a178c1323c1c20f84e67d4d7699fc313090a4c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682475"
---
# <a name="issue-element-ssbdiagnose"></a><span data-ttu-id="e1f72-102">Issue 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="e1f72-102">Issue Element (ssbdiagnose)</span></span>
  <span data-ttu-id="e1f72-103">报告 **ssbdiagnose** 实用工具发现的问题。</span><span class="sxs-lookup"><span data-stu-id="e1f72-103">Reports an issue that was found by the **ssbdiagnose** utility.</span></span> <span data-ttu-id="e1f72-104">在 **ssbdiagnose** XML 输出文件中，所报告的每个问题都有一个 Issue 元素。</span><span class="sxs-lookup"><span data-stu-id="e1f72-104">The **ssbdiagnose** XML output file has one Issue element per issue reported.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f72-105">语法</span><span class="sxs-lookup"><span data-stu-id="e1f72-105">Syntax</span></span>  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="e1f72-106">元素属性</span><span class="sxs-lookup"><span data-stu-id="e1f72-106">Element Attributes</span></span>  
  
|<span data-ttu-id="e1f72-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="e1f72-107">Attribute</span></span>|<span data-ttu-id="e1f72-108">说明</span><span class="sxs-lookup"><span data-stu-id="e1f72-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e1f72-109">标识 Issue 元素报告的问题类别：</span><span class="sxs-lookup"><span data-stu-id="e1f72-109">Identifies which category of problem the Issue element is reporting:</span></span><br /><br /> <span data-ttu-id="e1f72-110">**“诊断”** 报告在分析 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 配置时发现的配置问题。</span><span class="sxs-lookup"><span data-stu-id="e1f72-110">**"Diagnosis"** Reports a configuration issue found when you analyze a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span><br /><br /> <span data-ttu-id="e1f72-111">“问题” 报告阻止 **ssbdiagnose** 完成其分析的问题。</span><span class="sxs-lookup"><span data-stu-id="e1f72-111">**"Problem"** Reports an issue that has prevented **ssbdiagnose** from completing its analysis.</span></span> <span data-ttu-id="e1f72-112">更正问题并重新运行 **ssbdiagnose**。</span><span class="sxs-lookup"><span data-stu-id="e1f72-112">Correct the problem and rerun **ssbdiagnose**.</span></span><br /><br /> <span data-ttu-id="e1f72-113">**“事件”** 报告在运行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -RUNTIME **检查时发现的** 事件。</span><span class="sxs-lookup"><span data-stu-id="e1f72-113">**"Event"** Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event found when you run a **-RUNTIME** check.</span></span> <span data-ttu-id="e1f72-114">仅当指定了 **-SHOWEVENTS** 时才报告事件。</span><span class="sxs-lookup"><span data-stu-id="e1f72-114">Events are only reported if **-SHOWEVENTS** is specified.</span></span>|  
|`code`|<span data-ttu-id="e1f72-115">标识消息的错误号。</span><span class="sxs-lookup"><span data-stu-id="e1f72-115">Identifies the error number for the message.</span></span>|  
|`server`|<span data-ttu-id="e1f72-116">标识在其中发现了问题的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="e1f72-116">Identifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the problem was found.</span></span> <span data-ttu-id="e1f72-117">如果问题在默认实例中，则服务器属性只具有计算机名称。</span><span class="sxs-lookup"><span data-stu-id="e1f72-117">If the problem was in a default instance, the server attribute only has the computer name.</span></span> <span data-ttu-id="e1f72-118">如果问题在命名实例中，则服务器属性的格式为 ComputerName\InstanceName。</span><span class="sxs-lookup"><span data-stu-id="e1f72-118">If the problem was in a named instance, the server attribute is in the form ComputerName\InstanceName.</span></span>|  
|`database`|<span data-ttu-id="e1f72-119">标识在其中发现了问题的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e1f72-119">Identifies the name of the database in which the problem was found.</span></span>|  
|`object`|<span data-ttu-id="e1f72-120">标识在其中发现了问题的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="e1f72-120">Identifies the name of the object in which the problem was found.</span></span> <span data-ttu-id="e1f72-121">如果问题为实例或数据库级别的问题，则对象属性将重复该实例或数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e1f72-121">If the problem was an instance or database level issue, the object attribute repeats the instance or database name.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="e1f72-122">元素特征</span><span class="sxs-lookup"><span data-stu-id="e1f72-122">Element Characteristics</span></span>  
  
|<span data-ttu-id="e1f72-123">特征</span><span class="sxs-lookup"><span data-stu-id="e1f72-123">Characteristic</span></span>|<span data-ttu-id="e1f72-124">说明</span><span class="sxs-lookup"><span data-stu-id="e1f72-124">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e1f72-125">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="e1f72-125">**Data type and length**</span></span>|<span data-ttu-id="e1f72-126">，无限长。</span><span class="sxs-lookup"><span data-stu-id="e1f72-126">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="e1f72-127">**值**</span><span class="sxs-lookup"><span data-stu-id="e1f72-127">**Value**</span></span>|<span data-ttu-id="e1f72-128">返回错误消息的文本。</span><span class="sxs-lookup"><span data-stu-id="e1f72-128">Returns the text of the error message.</span></span>|  
|<span data-ttu-id="e1f72-129">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="e1f72-129">**Occurrence**</span></span>|<span data-ttu-id="e1f72-130">每个报告错误一次。</span><span class="sxs-lookup"><span data-stu-id="e1f72-130">Once per reported error.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e1f72-131">元素关系</span><span class="sxs-lookup"><span data-stu-id="e1f72-131">Element Relationships</span></span>  
  
|<span data-ttu-id="e1f72-132">关系</span><span class="sxs-lookup"><span data-stu-id="e1f72-132">Relationship</span></span>|<span data-ttu-id="e1f72-133">元素</span><span class="sxs-lookup"><span data-stu-id="e1f72-133">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e1f72-134">**父元素**</span><span class="sxs-lookup"><span data-stu-id="e1f72-134">**Parent element**</span></span>|[<span data-ttu-id="e1f72-135">DiagnosticInformation 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="e1f72-135">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="e1f72-136">**子元素**</span><span class="sxs-lookup"><span data-stu-id="e1f72-136">**Child elements**</span></span>|<span data-ttu-id="e1f72-137">无</span><span class="sxs-lookup"><span data-stu-id="e1f72-137">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1f72-138">示例</span><span class="sxs-lookup"><span data-stu-id="e1f72-138">Example</span></span>  
 <span data-ttu-id="e1f72-139">此元素报告没有主密钥的数据库的 1102 错误，分析 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 配置时在该数据库中发现了错误。</span><span class="sxs-lookup"><span data-stu-id="e1f72-139">This element reports an 1102 error for a database that does not have a master key, where the error was found when you analyzed a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span>  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1f72-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1f72-140">See Also</span></span>  
 [<span data-ttu-id="e1f72-141">ssbdiagnose 实用工具 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="e1f72-141">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
