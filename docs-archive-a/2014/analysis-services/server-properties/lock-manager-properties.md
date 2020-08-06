---
title: 锁管理器属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- lock manager properties [Analysis Services]
- LockWaitGranularityMS property
- DefaultLockTimeoutMS property
- DeadlockDetectionGranularityMS property
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d10927f1c549f00625b8affb801ec7b0831827c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694583"
---
# <a name="lock-manager-properties"></a><span data-ttu-id="d74a8-102">锁管理器属性</span><span class="sxs-lookup"><span data-stu-id="d74a8-102">Lock Manager Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d74a8-103">支持下表中列出的锁管理器服务器属性。</span><span class="sxs-lookup"><span data-stu-id="d74a8-103">supports the lock manager server properties listed in the following table.</span></span> <span data-ttu-id="d74a8-104">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d74a8-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="d74a8-105">**适用于：** 多维和表格服务器模式</span><span class="sxs-lookup"><span data-stu-id="d74a8-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d74a8-106">属性</span><span class="sxs-lookup"><span data-stu-id="d74a8-106">Properties</span></span>  
 `DefaultLockTimeoutMS`  
 <span data-ttu-id="d74a8-107">有符号 32 位整数属性，用于定义内部锁请求的默认锁超时值（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="d74a8-107">A signed 32-bit integer property that defines default lock timeout in milliseconds for internal lock requests.</span></span>  
  
 <span data-ttu-id="d74a8-108">该属性的默认值为 -1，指示没有为内部锁请求指定超时值。</span><span class="sxs-lookup"><span data-stu-id="d74a8-108">The default value for this property is -1, which indicates there is no timeout for internal lock requests.</span></span>  
  
 `LockWaitGranularityMS`  
 <span data-ttu-id="d74a8-109">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="d74a8-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DeadlockDetectionGranularityMS`  
 <span data-ttu-id="d74a8-110">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="d74a8-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74a8-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d74a8-111">See Also</span></span>  
 <span data-ttu-id="d74a8-112">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d74a8-112">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="d74a8-113">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="d74a8-113">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
