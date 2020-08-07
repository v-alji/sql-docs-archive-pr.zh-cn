---
title: CDC 拆分器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45dd16602625b28d2ca7e16f2fa6b0d62294fe81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587944"
---
# <a name="cdc-splitter"></a><span data-ttu-id="22e81-102">CDC 拆分器</span><span class="sxs-lookup"><span data-stu-id="22e81-102">CDC Splitter</span></span>
  <span data-ttu-id="22e81-103">CDC 拆分器将更改行的单个流从 CDC 源数据流拆分到多个不同的数据流中以便用于插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="22e81-103">The CDC splitter splits a single flow of change rows from a CDC source data flow into different data flows for Insert, Update and Delete operations.</span></span> <span data-ttu-id="22e81-104">基于必需的列 `__$operation` 及其在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 更改表中的标准值来拆分数据流。</span><span class="sxs-lookup"><span data-stu-id="22e81-104">The data flow is split based on the required column `__$operation` and its standard values in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables.</span></span>  
  
|<span data-ttu-id="22e81-105">操作的值</span><span class="sxs-lookup"><span data-stu-id="22e81-105">Value of Operation</span></span>|<span data-ttu-id="22e81-106">输出</span><span class="sxs-lookup"><span data-stu-id="22e81-106">Output</span></span>|<span data-ttu-id="22e81-107">说明</span><span class="sxs-lookup"><span data-stu-id="22e81-107">Description</span></span>|  
|------------------------|------------|-----------------|  
|<span data-ttu-id="22e81-108">1</span><span class="sxs-lookup"><span data-stu-id="22e81-108">1</span></span>|<span data-ttu-id="22e81-109">删除</span><span class="sxs-lookup"><span data-stu-id="22e81-109">Delete</span></span>|<span data-ttu-id="22e81-110">删除的行</span><span class="sxs-lookup"><span data-stu-id="22e81-110">Deleted Row</span></span>|  
|<span data-ttu-id="22e81-111">2</span><span class="sxs-lookup"><span data-stu-id="22e81-111">2</span></span>|<span data-ttu-id="22e81-112">插入</span><span class="sxs-lookup"><span data-stu-id="22e81-112">Insert</span></span>|<span data-ttu-id="22e81-113">插入的行（使用“净值且具有合并”  CDC 模式时不可用）</span><span class="sxs-lookup"><span data-stu-id="22e81-113">Inserted row (not available when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="22e81-114">3</span><span class="sxs-lookup"><span data-stu-id="22e81-114">3</span></span>|<span data-ttu-id="22e81-115">更新</span><span class="sxs-lookup"><span data-stu-id="22e81-115">Update</span></span>|<span data-ttu-id="22e81-116">更新前的行（仅在使用“全部且具有旧值”  CDC 模式时可用）</span><span class="sxs-lookup"><span data-stu-id="22e81-116">Before-update row (available only when using **All with Old Values** CDC mode)</span></span>|  
|<span data-ttu-id="22e81-117">4</span><span class="sxs-lookup"><span data-stu-id="22e81-117">4</span></span>|<span data-ttu-id="22e81-118">更新</span><span class="sxs-lookup"><span data-stu-id="22e81-118">Update</span></span>|<span data-ttu-id="22e81-119">更新后的行（与更新前相同）</span><span class="sxs-lookup"><span data-stu-id="22e81-119">After-update row (follows the Before-update)</span></span>|  
|<span data-ttu-id="22e81-120">5</span><span class="sxs-lookup"><span data-stu-id="22e81-120">5</span></span>|<span data-ttu-id="22e81-121">更新</span><span class="sxs-lookup"><span data-stu-id="22e81-121">Update</span></span>|<span data-ttu-id="22e81-122">合并行（仅在使用“净值且具有合并”  CDC 模式时可用）</span><span class="sxs-lookup"><span data-stu-id="22e81-122">Merge row (available only when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="22e81-123">其他</span><span class="sxs-lookup"><span data-stu-id="22e81-123">Other</span></span>|<span data-ttu-id="22e81-124">错误</span><span class="sxs-lookup"><span data-stu-id="22e81-124">Error</span></span>||  
  
 <span data-ttu-id="22e81-125">您可以使用拆分器连接到预定义的 INSERT、DELETE 和 UPDATE 输出以便进行进一步的处理。</span><span class="sxs-lookup"><span data-stu-id="22e81-125">You can use the splitter to connect to pre-defined INSERT, DELETE, and UPDATE outputs for further processing.</span></span>  
  
 <span data-ttu-id="22e81-126">此 CDC 拆分器转换有一个常规输入和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="22e81-126">The CDC Splitter transformation has one regular input and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="22e81-127">错误处理</span><span class="sxs-lookup"><span data-stu-id="22e81-127">Error Handling</span></span>  
 <span data-ttu-id="22e81-128">此 CDC 拆分器转换有一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="22e81-128">The CDC Splitter transformation has an error output.</span></span> <span data-ttu-id="22e81-129">具有 $operation 列的无效值的输入行被视为错误的，并且根据该输入的 **ErrorRowDisposition** 属性进行处理。</span><span class="sxs-lookup"><span data-stu-id="22e81-129">Input rows with an invalid value of the $operation column are considered erroneous and are handled according to the **ErrorRowDisposition** property of the input.</span></span>  
  
 <span data-ttu-id="22e81-130">组件的错误输出包括以下输出列：</span><span class="sxs-lookup"><span data-stu-id="22e81-130">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="22e81-131">**错误代码**：设置为 1。</span><span class="sxs-lookup"><span data-stu-id="22e81-131">**Error Code**: Set to 1.</span></span>  
  
-   <span data-ttu-id="22e81-132">**错误列**：导致错误（针对转换错误）的源列。</span><span class="sxs-lookup"><span data-stu-id="22e81-132">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="22e81-133">**错误行列**：导致了该错误的行的输入列。</span><span class="sxs-lookup"><span data-stu-id="22e81-133">**Error Row Columns**: The input columns of the row that caused the error.</span></span>  
  
## <a name="configuring-the-cdc-splitter"></a><span data-ttu-id="22e81-134">配置 CDC 拆分器</span><span class="sxs-lookup"><span data-stu-id="22e81-134">Configuring the CDC Splitter</span></span>  
 <span data-ttu-id="22e81-135">没有用于 CDC 拆分器的可配置属性。</span><span class="sxs-lookup"><span data-stu-id="22e81-135">There are no configurable properties for the CDC splitter.</span></span>  
  
 <span data-ttu-id="22e81-136">有关使用 CDC 拆分器的详细信息，请参阅 Microsoft SQL Server Integration Services 的 CDC 组件。</span><span class="sxs-lookup"><span data-stu-id="22e81-136">For more information about using the CDC splitter, see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
 <span data-ttu-id="22e81-137">**“高级编辑器”** 对话框包含可通过编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="22e81-137">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="22e81-138">打开 **“高级编辑器”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="22e81-138">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="22e81-139">在您的 **项目的** “数据流” [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 屏幕上，右键单击 CDC 拆分器，然后选择 **“显示高级编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="22e81-139">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e81-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22e81-140">See Also</span></span>  
 [<span data-ttu-id="22e81-141">根据更改的类型定向 CDC 流</span><span class="sxs-lookup"><span data-stu-id="22e81-141">Direct the CDC Stream According to the Type of Change</span></span>](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
