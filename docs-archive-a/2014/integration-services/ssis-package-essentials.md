---
title: SSIS 包基础知识 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c58ddc13b5c149b84fa550f312782b02786d062
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690732"
---
# <a name="ssis-package-essentials"></a><span data-ttu-id="8245e-102">SSIS 包基本要素</span><span class="sxs-lookup"><span data-stu-id="8245e-102">SSIS Package Essentials</span></span>
  <span data-ttu-id="8245e-103">包是用于实现 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 功能以提取、转换和加载数据的对象。</span><span class="sxs-lookup"><span data-stu-id="8245e-103">A package is the object that implements [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] functionality to extract, transform, and load data.</span></span> <span data-ttu-id="8245e-104">可以通过使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 中的 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]设计器来创建包。</span><span class="sxs-lookup"><span data-stu-id="8245e-104">You create a package by using the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="8245e-105">也可以通过运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导入和导出向导或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 连接项目向导来创建包。</span><span class="sxs-lookup"><span data-stu-id="8245e-105">You can also create a package by running the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard or the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Connections Project Wizard.</span></span> <span data-ttu-id="8245e-106">有关详细信息，请在 SSIS 设计器和[导入项目向导](../../2014/integration-services/import-project-wizard.md) [SQL Server Data Tools 中创建包](create-packages-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="8245e-106">For more information, [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) in SSIS Designer and [Import Project Wizard](../../2014/integration-services/import-project-wizard.md).</span></span>  
  
 <span data-ttu-id="8245e-107">基本包中包括以下元素：</span><span class="sxs-lookup"><span data-stu-id="8245e-107">A basic package includes the following elements:</span></span>  
  
 <span data-ttu-id="8245e-108">**控制流元素**</span><span class="sxs-lookup"><span data-stu-id="8245e-108">**Control flow elements**</span></span>  
 <span data-ttu-id="8245e-109">此类必需的元素执行各种功能，提供结构以及控制元素运行的顺序。</span><span class="sxs-lookup"><span data-stu-id="8245e-109">These required elements perform various functions, provide structure, and control the order in which elements run.</span></span> <span data-ttu-id="8245e-110">主控制流元素是指任务、容器和优先约束。</span><span class="sxs-lookup"><span data-stu-id="8245e-110">The main control flow elements are tasks, containers, and precedence constraints.</span></span> <span data-ttu-id="8245e-111">包中必须至少有一个控制流元素。</span><span class="sxs-lookup"><span data-stu-id="8245e-111">There must be at least one control flow element in a package.</span></span>  
  
 <span data-ttu-id="8245e-112">有关详细信息，请参阅 [Control Flow](control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="8245e-112">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="8245e-113">**数据流元素**</span><span class="sxs-lookup"><span data-stu-id="8245e-113">**Data flow elements**</span></span>  
 <span data-ttu-id="8245e-114">此类可选的元素可提取数据，修改数据以及将数据加载到数据源。</span><span class="sxs-lookup"><span data-stu-id="8245e-114">These optional elements extract data, modify data, and load data into data sources.</span></span> <span data-ttu-id="8245e-115">主数据流元素是指源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="8245e-115">The main data flow elements are sources, transformations, and destinations.</span></span> <span data-ttu-id="8245e-116">包中不一定要包含数据流元素。</span><span class="sxs-lookup"><span data-stu-id="8245e-116">There does not have to be any data flow elements in package.</span></span>  
  
 <span data-ttu-id="8245e-117">有关详细信息，请参阅 [Data Flow](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="8245e-117">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="8245e-118">有关如何创建基本包的示例，请参阅[第1课：创建项目和基本包](lesson-1-create-a-project-and-basic-package-with-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="8245e-118">For an example of how to create a basic package, see [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8245e-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8245e-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8245e-120">在 SQL Server Data Tools 中创建包</span><span class="sxs-lookup"><span data-stu-id="8245e-120">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)  
  
-   [<span data-ttu-id="8245e-121">在控制流中添加或删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="8245e-121">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [<span data-ttu-id="8245e-122">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="8245e-122">Set the Properties of a Task or Container</span></span>](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [<span data-ttu-id="8245e-123">在数据流中添加或删除组件</span><span class="sxs-lookup"><span data-stu-id="8245e-123">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a><span data-ttu-id="8245e-124">相关内容</span><span class="sxs-lookup"><span data-stu-id="8245e-124">Related Content</span></span>  
  
1.  <span data-ttu-id="8245e-125">MSDN.Microsoft.com 上的视频 [创建基本包（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=131023)</span><span class="sxs-lookup"><span data-stu-id="8245e-125">Video, [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023), on MSDN.Microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8245e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8245e-126">See Also</span></span>  
 <span data-ttu-id="8245e-127">[Integration Services &#40;SSIS&#41; 包](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="8245e-127">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="8245e-128">优先约束</span><span class="sxs-lookup"><span data-stu-id="8245e-128">Precedence Constraints</span></span>](control-flow/precedence-constraints.md)  
  
  
