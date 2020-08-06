---
title: 审核转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8e302f6dd1dc5666ae65af2eb9705a4922915c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682966"
---
# <a name="audit-transformation"></a><span data-ttu-id="f94a6-102">审核转换</span><span class="sxs-lookup"><span data-stu-id="f94a6-102">Audit Transformation</span></span>
  <span data-ttu-id="f94a6-103">通过进行审核转换，包中的数据流可以包含有关运行包的环境的数据。</span><span class="sxs-lookup"><span data-stu-id="f94a6-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="f94a6-104">例如，包、计算机和操作员的名称可添加到数据流中。</span><span class="sxs-lookup"><span data-stu-id="f94a6-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="f94a6-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中包含了提供这些信息的系统变量。</span><span class="sxs-lookup"><span data-stu-id="f94a6-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] includes system variables that provide this information.</span></span>  
  
## <a name="system-variables"></a><span data-ttu-id="f94a6-106">系统变量</span><span class="sxs-lookup"><span data-stu-id="f94a6-106">System Variables</span></span>  
 <span data-ttu-id="f94a6-107">下表介绍了审核转换可以使用的系统变量。</span><span class="sxs-lookup"><span data-stu-id="f94a6-107">The following table describes the system variables that the Audit transformation can use.</span></span>  
  
|<span data-ttu-id="f94a6-108">系统变量</span><span class="sxs-lookup"><span data-stu-id="f94a6-108">System variable</span></span>|<span data-ttu-id="f94a6-109">索引</span><span class="sxs-lookup"><span data-stu-id="f94a6-109">Index</span></span>|<span data-ttu-id="f94a6-110">说明</span><span class="sxs-lookup"><span data-stu-id="f94a6-110">Description</span></span>|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|<span data-ttu-id="f94a6-111">0</span><span class="sxs-lookup"><span data-stu-id="f94a6-111">0</span></span>|<span data-ttu-id="f94a6-112">标识包的执行实例的 GUID。</span><span class="sxs-lookup"><span data-stu-id="f94a6-112">The GUID that identifies the execution instance of the package.</span></span>|  
|`PackageID`|<span data-ttu-id="f94a6-113">1</span><span class="sxs-lookup"><span data-stu-id="f94a6-113">1</span></span>|<span data-ttu-id="f94a6-114">包的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="f94a6-114">The unique identifier of the package.</span></span>|  
|`PackageName`|<span data-ttu-id="f94a6-115">2</span><span class="sxs-lookup"><span data-stu-id="f94a6-115">2</span></span>|<span data-ttu-id="f94a6-116">包名称。</span><span class="sxs-lookup"><span data-stu-id="f94a6-116">The package name.</span></span>|  
|`VersionID`|<span data-ttu-id="f94a6-117">3</span><span class="sxs-lookup"><span data-stu-id="f94a6-117">3</span></span>|<span data-ttu-id="f94a6-118">包的版本。</span><span class="sxs-lookup"><span data-stu-id="f94a6-118">The version of the package.</span></span>|  
|`ExecutionStartTime`|<span data-ttu-id="f94a6-119">4</span><span class="sxs-lookup"><span data-stu-id="f94a6-119">4</span></span>|<span data-ttu-id="f94a6-120">包开始运行的时间。</span><span class="sxs-lookup"><span data-stu-id="f94a6-120">The time the package started to run.</span></span>|  
|`MachineName`|<span data-ttu-id="f94a6-121">5</span><span class="sxs-lookup"><span data-stu-id="f94a6-121">5</span></span>|<span data-ttu-id="f94a6-122">计算机名称。</span><span class="sxs-lookup"><span data-stu-id="f94a6-122">The computer name.</span></span>|  
|`UserName`|<span data-ttu-id="f94a6-123">6</span><span class="sxs-lookup"><span data-stu-id="f94a6-123">6</span></span>|<span data-ttu-id="f94a6-124">启动包的人员的登录名。</span><span class="sxs-lookup"><span data-stu-id="f94a6-124">The login name of the person who started the package.</span></span>|  
|`TaskName`|<span data-ttu-id="f94a6-125">7</span><span class="sxs-lookup"><span data-stu-id="f94a6-125">7</span></span>|<span data-ttu-id="f94a6-126">与审核转换相关联的数据流任务的名称。</span><span class="sxs-lookup"><span data-stu-id="f94a6-126">The name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="f94a6-127">**TaskId**</span><span class="sxs-lookup"><span data-stu-id="f94a6-127">**TaskId**</span></span>|<span data-ttu-id="f94a6-128">8</span><span class="sxs-lookup"><span data-stu-id="f94a6-128">8</span></span>|<span data-ttu-id="f94a6-129">数据流任务的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="f94a6-129">The unique identifier of the Data Flow task.</span></span>|  
  
## <a name="configuration-of-the-audit-transformation"></a><span data-ttu-id="f94a6-130">审核转换的配置</span><span class="sxs-lookup"><span data-stu-id="f94a6-130">Configuration of the Audit Transformation</span></span>  
 <span data-ttu-id="f94a6-131">您可以通过提供要添加到转换输出的新输出列的名称，然后将系统变量映射到该输出列，来配置审核转换。</span><span class="sxs-lookup"><span data-stu-id="f94a6-131">You configure the Audit transformation by providing the name of a new output column to add to the transformation output, and then mapping the system variable to the output column.</span></span> <span data-ttu-id="f94a6-132">可以将单个系统变量映射到多个列。</span><span class="sxs-lookup"><span data-stu-id="f94a6-132">You can map a single system variable to multiple columns.</span></span>  
  
 <span data-ttu-id="f94a6-133">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="f94a6-133">This transformation has one input and one output.</span></span> <span data-ttu-id="f94a6-134">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="f94a6-134">It does not support an error output.</span></span>  
  
 <span data-ttu-id="f94a6-135">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="f94a6-135">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f94a6-136">有关可在 **“审核转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Audit Transformation Editor](../../audit-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="f94a6-136">For more information about the properties that you can set in the **Audit Transformation Editor** dialog box, see [Audit Transformation Editor](../../audit-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="f94a6-137">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="f94a6-137">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="f94a6-138">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="f94a6-138">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f94a6-139">Common Properties</span><span class="sxs-lookup"><span data-stu-id="f94a6-139">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="f94a6-140">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="f94a6-140">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="f94a6-141">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f94a6-141">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
