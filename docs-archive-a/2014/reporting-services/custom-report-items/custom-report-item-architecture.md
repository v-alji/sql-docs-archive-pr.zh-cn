---
title: 自定义报表项体系结构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a053eb55547da9030eebe9036667cca2e14606f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577399"
---
# <a name="custom-report-item-architecture"></a><span data-ttu-id="7f126-102">自定义报表项体系结构</span><span class="sxs-lookup"><span data-stu-id="7f126-102">Custom Report Item Architecture</span></span>
  <span data-ttu-id="7f126-103">自定义报表项是对报表定义语言 (RDL) 的扩展，允许开发人员添加在 RDL 中并不固有支持的功能或扩展现有控件的功能。</span><span class="sxs-lookup"><span data-stu-id="7f126-103">A custom report item is an extension to the Report Definition Language (RDL) that allows developers to add functionality that's not natively supported in RDL or extend the functionality of existing controls.</span></span> <span data-ttu-id="7f126-104">有两个用于自定义报表项的主要组件：运行时组件和设计时组件。</span><span class="sxs-lookup"><span data-stu-id="7f126-104">There are two main components to a custom report item: the run-time component and the design-time component.</span></span> <span data-ttu-id="7f126-105">这些组件作为 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 程序集实现，并且可用任何符合 CLS 的语言编写。</span><span class="sxs-lookup"><span data-stu-id="7f126-105">These components are implemented as [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assemblies, and can be written in any CLS-compliant language.</span></span>  
  
## <a name="the-run-time-component"></a><span data-ttu-id="7f126-106">运行时组件</span><span class="sxs-lookup"><span data-stu-id="7f126-106">The Run-Time Component</span></span>  
 <span data-ttu-id="7f126-107">自定义报表项的运行时组件由报表处理器在运行时调用。</span><span class="sxs-lookup"><span data-stu-id="7f126-107">The run-time component for a custom report item is called by the report processor at run time.</span></span> <span data-ttu-id="7f126-108">该运行时组件接受报表处理器在运行时传递的数据、处理这些数据并返回包含呈现的自定义报表项的图像。</span><span class="sxs-lookup"><span data-stu-id="7f126-108">The run-time component accepts data passed by the report processor at run time, processes this data, and returns an image containing the rendered custom report item.</span></span>  
  
 <span data-ttu-id="7f126-109">![自定义报表项运行时组件](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "自定义报表项运行时组件")</span><span class="sxs-lookup"><span data-stu-id="7f126-109">![Custom report item run-time component](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Custom report item run-time component")</span></span>  
  
## <a name="the-design-time-component"></a><span data-ttu-id="7f126-110">设计时组件</span><span class="sxs-lookup"><span data-stu-id="7f126-110">The Design-Time Component</span></span>  
 <span data-ttu-id="7f126-111">设计时组件允许在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的报表设计器界面中定义和操作自定义报表项。</span><span class="sxs-lookup"><span data-stu-id="7f126-111">The design-time component allows the custom report item to be defined and manipulated in the Report Designer interface in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="7f126-112">设计时组件由若干子控件构成，这些子控件控制设计环境中自定义报表项的外观和属性。</span><span class="sxs-lookup"><span data-stu-id="7f126-112">The design-time component consists of several sub-controls that control the appearance and properties of the custom report item in the design environment.</span></span>  
  
 <span data-ttu-id="7f126-113">![自定义报表项设计时组件](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "自定义报表项设计时组件")</span><span class="sxs-lookup"><span data-stu-id="7f126-113">![Custom report item design-time component](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Custom report item design-time component")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f126-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f126-114">See Also</span></span>  
 <span data-ttu-id="7f126-115">[创建自定义报表项运行时组件](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="7f126-115">[Creating a Custom Report Item Run-Time Component](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="7f126-116">[创建自定义报表项设计时组件](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="7f126-116">[Creating a Custom Report Item Design-Time Component](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span></span>  
 [<span data-ttu-id="7f126-117">如何：部署自定义报表项</span><span class="sxs-lookup"><span data-stu-id="7f126-117">How to: Deploy a Custom Report Item</span></span>](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
