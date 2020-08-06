---
title: 用于服务器事件的 WMI 提供程序的概念 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- server events [WMI]
- SQL Server WMI Provider
- WMI Provider for Server Events
- monitoring events [WMI]
- events [WMI]
ms.assetid: 80767fe0-32ac-406a-81a0-8212cd6ce7e4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 922ae033b30894d62d5e356b0ee3d395cf552180
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586536"
---
# <a name="wmi-provider-for-server-events-concepts"></a><span data-ttu-id="0ddcb-102">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="0ddcb-102">WMI Provider for Server Events Concepts</span></span>
  <span data-ttu-id="0ddcb-103">利用 WMI Provider for Server Events，可以使用 Windows Management Instrumentation (WMI) 监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的事件。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-103">The WMI Provider for Server Events lets you use Windows Management Instrumentation (WMI) to monitor events in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ddcb-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="0ddcb-104">In This Section</span></span>  
 [<span data-ttu-id="0ddcb-105">了解服务器事件 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="0ddcb-105">Understanding the WMI Provider for Server Events</span></span>](understanding-the-wmi-provider-for-server-events.md)  
 <span data-ttu-id="0ddcb-106">概述了提供程序的体系结构，以及如何对 SQL Server 代理进行编程以使用它。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-106">Provides an overview of the provider architecture and how SQL Server Agent can be programmed to work with it.</span></span>  
  
 [<span data-ttu-id="0ddcb-107">使用服务器事件 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="0ddcb-107">Working with the WMI Provider for Server Events</span></span>](working-with-the-wmi-provider-for-server-events.md)  
 <span data-ttu-id="0ddcb-108">说明在使用提供程序进行编程之前需要考虑的因素。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-108">Explains the factors that you need to consider before programming with the provider.</span></span>  
  
 [<span data-ttu-id="0ddcb-109">将 WQL 与 WMI Provider for Server Events 结合使用</span><span class="sxs-lookup"><span data-stu-id="0ddcb-109">Using WQL with the WMI Provider for Server Events</span></span>](using-wql-with-the-wmi-provider-for-server-events.md)  
 <span data-ttu-id="0ddcb-110">解释 WMI 查询语言 (WQL) 的语法以及如何使用它对提供程序进行编程。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-110">Explains the WMI Query Language (WQL) syntax and how to use it when you program against the provider.</span></span>  
  
 [<span data-ttu-id="0ddcb-111">示例：使用服务器事件 WMI 提供程序创建 SQL Server 代理警报</span><span class="sxs-lookup"><span data-stu-id="0ddcb-111">Sample: Creating a SQL Server Agent Alert by Using the WMI Provider for Server Events</span></span>](sample-creating-a-sql-server-agent-alert-with-the-wmi-provider.md)  
 <span data-ttu-id="0ddcb-112">提供一个示例，该示例使用 WMI 提供程序返回要对其创建 SQL Server 代理警报的跟踪事件信息。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-112">Provides an example of using the WMI Provider to return trace event information on which to create a SQL Server Agent alert.</span></span>  
  
 [<span data-ttu-id="0ddcb-113">示例：将 WMI 事件提供程序与 .NET Framework 结合使用</span><span class="sxs-lookup"><span data-stu-id="0ddcb-113">Sample: Use the WMI Event Provider with the .NET Framework</span></span>](sample-using-the-wmi-event-provider-with-the-net-framework.md)  
 <span data-ttu-id="0ddcb-114">提供一个示例，该示例使用 WMI 提供程序在一个 C# 应用程序中返回事件数据。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-114">Provides an example of using the WMI Provider to return event data in a C# application.</span></span>  
  
 [<span data-ttu-id="0ddcb-115">服务器事件 WMI 提供程序类和属性</span><span class="sxs-lookup"><span data-stu-id="0ddcb-115">WMI Provider for Server Events Classes and Properties</span></span>](wmi-provider-for-server-events-classes-and-properties.md)  
 <span data-ttu-id="0ddcb-116">介绍构成提供程序的编程模式的事件类和属性。</span><span class="sxs-lookup"><span data-stu-id="0ddcb-116">Introduces the event classes and properties that make up the programming mode of the provider.</span></span>  
  
  
