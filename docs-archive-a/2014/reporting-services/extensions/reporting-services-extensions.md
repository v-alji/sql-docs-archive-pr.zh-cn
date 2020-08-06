---
title: Reporting Services 扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ac942147c75424dae46d9a8e35dc57fba50755f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587222"
---
# <a name="reporting-services-extensions"></a><span data-ttu-id="c02fb-102">Reporting Services 扩展插件</span><span class="sxs-lookup"><span data-stu-id="c02fb-102">Reporting Services Extensions</span></span>
  <span data-ttu-id="c02fb-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的模块化体系结构旨在实现可扩展性。</span><span class="sxs-lookup"><span data-stu-id="c02fb-103">The modular architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="c02fb-104">提供了一个托管代码 API，以便您能够轻松地开发、安装和管理由许多 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件使用的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c02fb-104">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="c02fb-105">可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 创建专用或共享的程序集，并添加新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能以满足不断发展的业务需要。</span><span class="sxs-lookup"><span data-stu-id="c02fb-105">You can create private or shared assemblies using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality to meet your evolving business needs.</span></span>  
  
 <span data-ttu-id="c02fb-106">通过 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的独树一帜的可扩展体系结构，开发人员可以扩展产品及其组件的特定功能。</span><span class="sxs-lookup"><span data-stu-id="c02fb-106">The unique extensibility architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables developers to extend specific features of the product and its components.</span></span> <span data-ttu-id="c02fb-107">目前，全面支持扩展 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的数据处理功能。</span><span class="sxs-lookup"><span data-stu-id="c02fb-107">Currently, broad support exists for extending the data processing capabilities of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="c02fb-108">数据处理 API 包括大家所熟悉的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口构造和约定，使开发人员能够将附加的数据处理功能内置于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="c02fb-108">The data processing API includes familiar, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider constructs and conventions that enable developers to build additional data processing into [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="c02fb-109">这些数据处理扩展插件向报表服务器和报表设计器中添加功能，从而可以将自定义数据无缝集成到报表中。</span><span class="sxs-lookup"><span data-stu-id="c02fb-109">These data processing extensions add functionality to both the Report Server and Report Designer, enabling seamless integration of custom data into reports.</span></span>  
  
 <span data-ttu-id="c02fb-110">另一个支持的扩展插件是传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c02fb-110">Another supported extension is the delivery extension.</span></span> <span data-ttu-id="c02fb-111">传递 API 与 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 体系结构完全集成，从而在将报表通知发送到用户时能够使用多种传递机制。</span><span class="sxs-lookup"><span data-stu-id="c02fb-111">The delivery API is fully integrated with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] architecture, enabling a wide variety of delivery mechanisms to be used when sending report notifications to users.</span></span> <span data-ttu-id="c02fb-112">您可以扩展报表服务器以向用户提供自定义传递，并且可以扩展报表管理器的订阅管理页以便实现使用自定义传递扩展插件的订阅。</span><span class="sxs-lookup"><span data-stu-id="c02fb-112">You can extend the Report Server to provide custom delivery to users and you can extend the subscription management pages of Report Manager to enable subscriptions that use custom delivery extensions.</span></span>  
  
 <span data-ttu-id="c02fb-113">另一个报表服务器扩展插件报表定义自定义扩展插件 (RDCE) 可以在将某一报表定义传递到处理引擎前动态自定义该报表定义。</span><span class="sxs-lookup"><span data-stu-id="c02fb-113">Another report server extension, Report Definition Customization Extension (RDCE), can dynamically customize a report definition before it is passed to the processing engine.</span></span> <span data-ttu-id="c02fb-114">您可以基于用户或语言之类的因素自定义报表。</span><span class="sxs-lookup"><span data-stu-id="c02fb-114">You might customize reports based on factors such as users or languages.</span></span> <span data-ttu-id="c02fb-115">例如，您可能要为不同用户（例如经理或部门成员）实现不同的视图，或者可能要自定义某一报表以便在以法语或阿拉伯语呈现时具有不同的布局。</span><span class="sxs-lookup"><span data-stu-id="c02fb-115">For example, you might want to implement different views for various users such as managers or members of a department, or you might want to customize a report to have a different layout when it is rendered in French or Arabic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c02fb-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="c02fb-116">In This Section</span></span>  
 [<span data-ttu-id="c02fb-117">扩展插件的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="c02fb-117">Security Considerations for Extensions</span></span>](security-considerations-for-extensions.md)  
 <span data-ttu-id="c02fb-118">介绍与开发和部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 扩展插件相关的安全问题。</span><span class="sxs-lookup"><span data-stu-id="c02fb-118">Describes security issues related to developing and deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 [<span data-ttu-id="c02fb-119">实现数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="c02fb-119">Implementing a Data Processing Extension</span></span>](data-processing/implementing-a-data-processing-extension.md)  
 <span data-ttu-id="c02fb-120">介绍用于实现 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据处理扩展插件的要求和步骤。</span><span class="sxs-lookup"><span data-stu-id="c02fb-120">Describes the requirements and steps for implementing a data processing extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="c02fb-121">实现传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="c02fb-121">Implementing a Delivery Extension</span></span>](delivery-extension/implementing-a-delivery-extension.md)  
 <span data-ttu-id="c02fb-122">介绍用于实现 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 传递扩展插件的要求和步骤。</span><span class="sxs-lookup"><span data-stu-id="c02fb-122">Describes the requirements and steps for implementing a delivery extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="c02fb-123">实现呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="c02fb-123">Implementing a Rendering Extension</span></span>](rendering-extension/implementing-a-rendering-extension.md)  
 <span data-ttu-id="c02fb-124">介绍如何开发呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c02fb-124">Contains an introduction to developing rendering extensions.</span></span>  
  
 [<span data-ttu-id="c02fb-125">实现安全扩展插件</span><span class="sxs-lookup"><span data-stu-id="c02fb-125">Implementing a Security Extension</span></span>](security-extension/implementing-a-security-extension.md)  
 <span data-ttu-id="c02fb-126">介绍用于实现 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安全扩展插件的要求和步骤。</span><span class="sxs-lookup"><span data-stu-id="c02fb-126">Describes the requirements and steps for implementing a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] security extension.</span></span>  
  
 [<span data-ttu-id="c02fb-127">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="c02fb-127">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
 <span data-ttu-id="c02fb-128">包含用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 扩展功能的扩展插件 API 库的编程参考。</span><span class="sxs-lookup"><span data-stu-id="c02fb-128">Contains the programming reference for the extension API library for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensibility features.</span></span>  
  
  
