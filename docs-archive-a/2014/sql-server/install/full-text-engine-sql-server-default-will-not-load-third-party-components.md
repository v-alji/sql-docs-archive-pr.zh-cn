---
title: 默认情况下，用于 SQL Server 的 Microsoft 全文引擎将不会加载未签名的第三方组件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591744"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a><span data-ttu-id="02e15-102">Microsoft SQL Server 全文引擎在默认情况下不加载未签名的第三方组件</span><span class="sxs-lookup"><span data-stu-id="02e15-102">The Microsoft Full-Text Engine for SQL Server will not load unsigned third-party components by default</span></span>
  <span data-ttu-id="02e15-103">默认情况下，[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文引擎将不加载未经 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 签名的组件。</span><span class="sxs-lookup"><span data-stu-id="02e15-103">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not load components that are not signed by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="02e15-104">组件</span><span class="sxs-lookup"><span data-stu-id="02e15-104">Component</span></span>  
 <span data-ttu-id="02e15-105">全文搜索</span><span class="sxs-lookup"><span data-stu-id="02e15-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="02e15-106">说明</span><span class="sxs-lookup"><span data-stu-id="02e15-106">Description</span></span>  
 <span data-ttu-id="02e15-107">默认情况下，在升级后 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文引擎将不加载服务器上当前已安装的第三方筛选器，如 PDF 筛选器。</span><span class="sxs-lookup"><span data-stu-id="02e15-107">A third-party filter, such as a PDF filter, that is currently installed on the server will not be loaded by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by default after upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="02e15-108">纠正措施</span><span class="sxs-lookup"><span data-stu-id="02e15-108">Corrective Action</span></span>  
 <span data-ttu-id="02e15-109">若要加载第三方筛选器，必须在该实例上设置*load_os_resource*并关闭*verify_signature* 。</span><span class="sxs-lookup"><span data-stu-id="02e15-109">To load a third party filter, you must set *load_os_resource* and turn off *verify_signature* on that instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e15-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02e15-110">See Also</span></span>  
 [<span data-ttu-id="02e15-111">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="02e15-111">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
