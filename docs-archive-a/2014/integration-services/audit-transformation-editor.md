---
title: 审核转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af6490643a0bef60cca961dc9a0564c5f6b46484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693026"
---
# <a name="audit-transformation-editor"></a><span data-ttu-id="1b777-102">审核转换编辑器</span><span class="sxs-lookup"><span data-stu-id="1b777-102">Audit Transformation Editor</span></span>
  <span data-ttu-id="1b777-103">通过进行审核转换，包中的数据流可以包含有关运行包的环境的数据。</span><span class="sxs-lookup"><span data-stu-id="1b777-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="1b777-104">例如，包、计算机和操作员的名称可添加到数据流中。</span><span class="sxs-lookup"><span data-stu-id="1b777-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="1b777-105">中包含了提供这些信息的系统变量。</span><span class="sxs-lookup"><span data-stu-id="1b777-105">includes system variables that provide this information.</span></span>  
  
 <span data-ttu-id="1b777-106">若要了解有关审核转换的详细信息，请参阅 [Audit Transformation](data-flow/transformations/audit-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="1b777-106">To learn more about the Audit transformation, see [Audit Transformation](data-flow/transformations/audit-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b777-107">选项</span><span class="sxs-lookup"><span data-stu-id="1b777-107">Options</span></span>  
 <span data-ttu-id="1b777-108">**输出列名称**</span><span class="sxs-lookup"><span data-stu-id="1b777-108">**Output column name**</span></span>  
 <span data-ttu-id="1b777-109">为包含审核信息的新输出列提供名称。</span><span class="sxs-lookup"><span data-stu-id="1b777-109">Provide the name for a new output column that will contain the audit information.</span></span>  
  
 <span data-ttu-id="1b777-110">**审核类型**</span><span class="sxs-lookup"><span data-stu-id="1b777-110">**Audit type**</span></span>  
 <span data-ttu-id="1b777-111">选择用于提供审核信息的可用系统变量。</span><span class="sxs-lookup"><span data-stu-id="1b777-111">Select an available system variable to supply the audit information.</span></span>  
  
|<span data-ttu-id="1b777-112">值</span><span class="sxs-lookup"><span data-stu-id="1b777-112">Value</span></span>|<span data-ttu-id="1b777-113">说明</span><span class="sxs-lookup"><span data-stu-id="1b777-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b777-114">**执行实例 GUID**</span><span class="sxs-lookup"><span data-stu-id="1b777-114">**Execution instance GUID**</span></span>|<span data-ttu-id="1b777-115">插入唯一标识包的执行实例的 GUID。</span><span class="sxs-lookup"><span data-stu-id="1b777-115">Insert the GUID that uniquely identifies the execution instance of the package.</span></span>|  
|<span data-ttu-id="1b777-116">**包 ID**</span><span class="sxs-lookup"><span data-stu-id="1b777-116">**Package ID**</span></span>|<span data-ttu-id="1b777-117">插入唯一标识包的 GUID。</span><span class="sxs-lookup"><span data-stu-id="1b777-117">Insert the GUID that uniquely identifies the package.</span></span>|  
|<span data-ttu-id="1b777-118">**包名称**</span><span class="sxs-lookup"><span data-stu-id="1b777-118">**Package name**</span></span>|<span data-ttu-id="1b777-119">插入包名称。</span><span class="sxs-lookup"><span data-stu-id="1b777-119">Insert the package name.</span></span>|  
|<span data-ttu-id="1b777-120">**版本 ID**</span><span class="sxs-lookup"><span data-stu-id="1b777-120">**Version ID**</span></span>|<span data-ttu-id="1b777-121">插入唯一标识包版本的 GUID。</span><span class="sxs-lookup"><span data-stu-id="1b777-121">Insert the GUID that uniquely identifies the version of the package.</span></span>|  
|<span data-ttu-id="1b777-122">**执行开始时间**</span><span class="sxs-lookup"><span data-stu-id="1b777-122">**Execution start time**</span></span>|<span data-ttu-id="1b777-123">插入包执行的开始时间。</span><span class="sxs-lookup"><span data-stu-id="1b777-123">Insert the time at which package execution started.</span></span>|  
|<span data-ttu-id="1b777-124">**计算机名称**</span><span class="sxs-lookup"><span data-stu-id="1b777-124">**Machine name**</span></span>|<span data-ttu-id="1b777-125">插入启动包的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="1b777-125">Insert the name of the computer on which the package was launched.</span></span>|  
|<span data-ttu-id="1b777-126">**用户名**</span><span class="sxs-lookup"><span data-stu-id="1b777-126">**User name**</span></span>|<span data-ttu-id="1b777-127">插入启动包的用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="1b777-127">Insert the login name of the user who launched the package.</span></span>|  
|<span data-ttu-id="1b777-128">**任务名称**</span><span class="sxs-lookup"><span data-stu-id="1b777-128">**Task name**</span></span>|<span data-ttu-id="1b777-129">插入与审核转换相关联的数据流任务的名称。</span><span class="sxs-lookup"><span data-stu-id="1b777-129">Insert the name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="1b777-130">**任务 ID**</span><span class="sxs-lookup"><span data-stu-id="1b777-130">**Task ID**</span></span>|<span data-ttu-id="1b777-131">插入唯一标识与审核转换相关联的数据流任务的 GUID。</span><span class="sxs-lookup"><span data-stu-id="1b777-131">Insert the GUID that uniquely identifies the Data Flow task with which the Audit transformation is associated.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b777-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b777-132">See Also</span></span>  
 [<span data-ttu-id="1b777-133">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="1b777-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
