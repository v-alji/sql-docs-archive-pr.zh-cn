---
title: 自定义报表项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86b819cb4d305e537a52a2e7f25cdfa3aefa5f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693655"
---
# <a name="custom-report-items"></a><span data-ttu-id="ff9fa-102">自定义报表项</span><span class="sxs-lookup"><span data-stu-id="ff9fa-102">Custom Report Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ff9fa-103">提供大量工具，用于生成和发布企业报表，管理安全性和订阅，以及通过全面的 API 扩展报表功能。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-103">provides a rich set of tools for building and publishing enterprise reports, managing security and subscriptions, and extending the reporting functionality through a comprehensive API.</span></span> <span data-ttu-id="ff9fa-104">报表使用称作报表定义语言 (RDL) 的基于 XML 的语言定义。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-104">Reports are defined using an XML-based language called Report Definition Language (RDL).</span></span> <span data-ttu-id="ff9fa-105">RDL 提供一组指令，用于描述报表的布局、查询信息和项类型。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-105">RDL provides a set of instructions that describe layout, query information, and item types for a report.</span></span> <span data-ttu-id="ff9fa-106">可以通过编写自定义报表项来扩展 RDL。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-106">It is possible to extend RDL by writing a custom report item.</span></span> <span data-ttu-id="ff9fa-107">自定义报表项由运行时组件（由报表处理器在运行时调用）和设计时组件（允许在报表设计器中使用该自定义报表项）构成。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-107">The custom report item consists of a run-time component, which is called by the report processor at run time, and a design-time component, which allows the custom report item to be available in Report Designer.</span></span>  
  
 <span data-ttu-id="ff9fa-108">有关完全实现的自定义报表项的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-108">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-scenarios"></a><span data-ttu-id="ff9fa-109">自定义报表项应用场景</span><span class="sxs-lookup"><span data-stu-id="ff9fa-109">Custom Report Item Scenarios</span></span>  
 <span data-ttu-id="ff9fa-110">需要将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到其应用程序中的开发人员可能要求在 RDL 中不固有支持的功能。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-110">Developers who need to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into their applications may require functionality that is not natively supported in RDL.</span></span> <span data-ttu-id="ff9fa-111">这可能包括如下项：映射控件、水平列表、垂直列表和透视表矩阵。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-111">This may include items such as: map controls, horizontal lists, columnar lists, and repivotable matrixes.</span></span> <span data-ttu-id="ff9fa-112">可以开发运行时自定义报表项组件并向应用程序分发，以便满足此需求。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-112">A run-time custom report item component can be developed and distributed with an application to fill this need.</span></span>  
  
 <span data-ttu-id="ff9fa-113">除了提供不固有支持的功能外，某些开发人员可能要通过随 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 一起提供的控件的替代版本扩展现有功能。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-113">In addition to providing functionality that isn't natively supported, some developers may want to extend existing functionality with alternative versions of controls that are already included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ff9fa-114">在此应用场景中，开发人员可以提供三个组件：运行时组件、设计时组件和在需要时将现有报表项转换为自定义报表项的设计时报表项转换组件。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-114">In this scenario, a developer could provide three components: a run-time component, a design-time component, and a design-time report item conversion component that converts an existing report item into a custom report item on demand.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff9fa-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="ff9fa-115">In This Section</span></span>  
 [<span data-ttu-id="ff9fa-116">自定义报表项体系结构</span><span class="sxs-lookup"><span data-stu-id="ff9fa-116">Custom Report Item Architecture</span></span>](custom-report-item-architecture.md)  
 <span data-ttu-id="ff9fa-117">描述组成自定义报表项的组件。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-117">Describes the components that make up a custom report item.</span></span>  
  
 [<span data-ttu-id="ff9fa-118">自定义报表项实现要求</span><span class="sxs-lookup"><span data-stu-id="ff9fa-118">Custom Report Item Implementation Requirements</span></span>](custom-report-item-implementation-requirements.md)  
 <span data-ttu-id="ff9fa-119">描述用于创建自定义报表项的先决条件。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-119">Describes prerequisites for creating a custom report item.</span></span>  
  
 [<span data-ttu-id="ff9fa-120">创建自定义报表项运行时组件</span><span class="sxs-lookup"><span data-stu-id="ff9fa-120">Creating a Custom Report Item Run-Time Component</span></span>](creating-a-custom-report-item-run-time-component.md)  
 <span data-ttu-id="ff9fa-121">描述如何创建自定义报表项运行时组件。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-121">Describes how to create a custom report item run-time component.</span></span>  
  
 [<span data-ttu-id="ff9fa-122">创建自定义报表项设计时组件</span><span class="sxs-lookup"><span data-stu-id="ff9fa-122">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
 <span data-ttu-id="ff9fa-123">描述如何创建自定义报表项设计时组件。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-123">Describes how to create a custom report item design-time component.</span></span>  
  
 [<span data-ttu-id="ff9fa-124">如何：部署自定义报表项</span><span class="sxs-lookup"><span data-stu-id="ff9fa-124">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
 <span data-ttu-id="ff9fa-125">描述如何部署自定义报表项。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-125">Describes how to deploy a custom report item.</span></span>  
  
 [<span data-ttu-id="ff9fa-126">自定义报表项类库</span><span class="sxs-lookup"><span data-stu-id="ff9fa-126">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
 <span data-ttu-id="ff9fa-127">描述 `Microsoft.ReportDesigner` 命名空间中的自定义报表项基础结构类和托管包装类。</span><span class="sxs-lookup"><span data-stu-id="ff9fa-127">Describes the custom report item infrastructure classes and managed wrapper classes in the `Microsoft.ReportDesigner` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9fa-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff9fa-128">See Also</span></span>  
 [<span data-ttu-id="ff9fa-129">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="ff9fa-129">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
