---
title: 在脚本组件中引发事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78eb44239f4e58e43bdd65c41d5fdeb58d053a6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587904"
---
# <a name="raising-events-in-the-script-component"></a><span data-ttu-id="82cfa-102">在脚本组件中引发事件</span><span class="sxs-lookup"><span data-stu-id="82cfa-102">Raising Events in the Script Component</span></span>
  <span data-ttu-id="82cfa-103">事件提供向包含包报告错误、警告和其他信息（如任务进度或状态）的方式。</span><span class="sxs-lookup"><span data-stu-id="82cfa-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="82cfa-104">包为管理事件通知提供事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="82cfa-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="82cfa-105">脚本组件可以通过对 `ScriptMain` 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 属性调用方法来引发事件。</span><span class="sxs-lookup"><span data-stu-id="82cfa-105">The Script component can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class.</span></span> <span data-ttu-id="82cfa-106">有关 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包如何处理事件的详细信息，请参阅 [Integration Services (SSIS) 事件处理程序](../../integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="82cfa-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="82cfa-107">事件可以记录到包中已启用的任何日志提供程序中。</span><span class="sxs-lookup"><span data-stu-id="82cfa-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="82cfa-108">日志提供程序在数据存储区中存储有关事件的信息。</span><span class="sxs-lookup"><span data-stu-id="82cfa-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="82cfa-109">脚本组件还可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法将信息记录到日志提供程序中而不引发事件。</span><span class="sxs-lookup"><span data-stu-id="82cfa-109">The Script component can also use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="82cfa-110">有关如何使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法的详细信息，请参阅以下内容。</span><span class="sxs-lookup"><span data-stu-id="82cfa-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method, see the following section.</span></span>  
  
 <span data-ttu-id="82cfa-111">为了引发事件，脚本任务将调用由 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 属性公开的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 接口的以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="82cfa-111">To raise an event, the Script task calls one of the following methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface exposed by the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property:</span></span>  
  
|<span data-ttu-id="82cfa-112">事件</span><span class="sxs-lookup"><span data-stu-id="82cfa-112">Event</span></span>|<span data-ttu-id="82cfa-113">说明</span><span class="sxs-lookup"><span data-stu-id="82cfa-113">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|<span data-ttu-id="82cfa-114">引发包中用户定义的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="82cfa-114">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|<span data-ttu-id="82cfa-115">将错误情况通知包。</span><span class="sxs-lookup"><span data-stu-id="82cfa-115">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|<span data-ttu-id="82cfa-116">为用户提供信息。</span><span class="sxs-lookup"><span data-stu-id="82cfa-116">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|<span data-ttu-id="82cfa-117">将组件的进度通知包。</span><span class="sxs-lookup"><span data-stu-id="82cfa-117">Informs the package of the progress of the component.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|<span data-ttu-id="82cfa-118">向包发出通知：组件处于有必要发出用户通知，但不是错误条件的状态。</span><span class="sxs-lookup"><span data-stu-id="82cfa-118">Informs the package that the component is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
 <span data-ttu-id="82cfa-119">下面是一个简单的引发错误事件的示例：</span><span class="sxs-lookup"><span data-stu-id="82cfa-119">Here is a simple example of raising an Error event:</span></span>  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
<span data-ttu-id="82cfa-120">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="82cfa-120">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="82cfa-121">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="82cfa-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="82cfa-122">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="82cfa-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="82cfa-123">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="82cfa-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82cfa-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82cfa-124">See Also</span></span>  
 <span data-ttu-id="82cfa-125">[Integration Services (SSIS) 事件处理程序](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="82cfa-125">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="82cfa-126">在包中添加事件处理程序</span><span class="sxs-lookup"><span data-stu-id="82cfa-126">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
