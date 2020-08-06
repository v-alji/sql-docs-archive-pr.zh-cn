---
title: SMO 对象模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
ms.openlocfilehash: c973e381a6cc7de44a0072d012147271eaa609ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682800"
---
# <a name="smo-object-model"></a><span data-ttu-id="9178c-102">SMO 对象模型</span><span class="sxs-lookup"><span data-stu-id="9178c-102">SMO Object Model</span></span>
  <span data-ttu-id="9178c-103">SMO 对象模型由对象的层次结构构成。</span><span class="sxs-lookup"><span data-stu-id="9178c-103">The SMO object model is made up of a hierarchy of objects.</span></span> <span data-ttu-id="9178c-104"><xref:Microsoft.SqlServer.Management.Smo.Server> 对象是顶层对象，所有实例类对象都位于 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象之下。</span><span class="sxs-lookup"><span data-stu-id="9178c-104">The <xref:Microsoft.SqlServer.Management.Smo.Server> object is the top level object and all instance class objects reside under the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span>  
  
 <span data-ttu-id="9178c-105"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 类是具有单独的对象层次结构的顶级类。</span><span class="sxs-lookup"><span data-stu-id="9178c-105">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> class is a top level class with a separate object hierarchy.</span></span> <span data-ttu-id="9178c-106"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>对象表示 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可通过 WMI 提供程序使用的服务和网络设置。</span><span class="sxs-lookup"><span data-stu-id="9178c-106">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object represents [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings available through the WMI Provider.</span></span>  
  
 <span data-ttu-id="9178c-107">除了 <xref:Microsoft.SqlServer.Management.Smo.Server> 和 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 对象外，存在若干表示任务或操作的实用工具类，例如 <xref:Microsoft.SqlServer.Management.Smo.Transfer>、<xref:Microsoft.SqlServer.Management.Smo.Backup> 或 <xref:Microsoft.SqlServer.Management.Smo.Restore>。</span><span class="sxs-lookup"><span data-stu-id="9178c-107">Besides the <xref:Microsoft.SqlServer.Management.Smo.Server> and <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> objects, there are several utility classes that represent tasks or operations, such as <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup>, or <xref:Microsoft.SqlServer.Management.Smo.Restore></span></span>  
  
 <span data-ttu-id="9178c-108">SMO 对象模型由若干命名空间构成。</span><span class="sxs-lookup"><span data-stu-id="9178c-108">The SMO object model is made up of several namespaces.</span></span> <span data-ttu-id="9178c-109">有关详细信息，请参阅 [SMO 命名空间](smo-object-model-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="9178c-109">For more information, see [SMO Namespaces](smo-object-model-namespaces.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9178c-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9178c-110">See Also</span></span>  
 <span data-ttu-id="9178c-111">[SMO 对象模型关系图](smo-object-model-diagram.md) </span><span class="sxs-lookup"><span data-stu-id="9178c-111">[SMO Object Model Diagram](smo-object-model-diagram.md) </span></span>  
 <span data-ttu-id="9178c-112">[SMO 命名空间](smo-object-model-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="9178c-112">[SMO Namespaces](smo-object-model-namespaces.md) </span></span>  
 [<span data-ttu-id="9178c-113">用于配置管理的 WMI 提供程序的概念</span><span class="sxs-lookup"><span data-stu-id="9178c-113">WMI Provider for Configuration Management Concepts</span></span>](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
