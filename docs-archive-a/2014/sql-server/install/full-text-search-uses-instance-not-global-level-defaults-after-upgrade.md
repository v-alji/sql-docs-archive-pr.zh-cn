---
title: 升级将导致全文搜索在默认情况下使用实例级（而非全局）断字符和筛选器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b6cea7ab63351fad25f0205a614e364328171a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591739"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a><span data-ttu-id="f7bfa-102">升级将导致全文搜索在默认情况下使用实例级(而非全局)的断字符和筛选器</span><span class="sxs-lookup"><span data-stu-id="f7bfa-102">Upgrading will cause Full-Text Search to use instance-level, not global, word breakers and filters by default</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f7bfa-103">提供了一种方法，允许在实例级别注册新的断字符和筛选器。</span><span class="sxs-lookup"><span data-stu-id="f7bfa-103">provides a way to allow instance-level registration of new word breakers and filters.</span></span>  
  
## <a name="component"></a><span data-ttu-id="f7bfa-104">组件</span><span class="sxs-lookup"><span data-stu-id="f7bfa-104">Component</span></span>  
 <span data-ttu-id="f7bfa-105">全文搜索</span><span class="sxs-lookup"><span data-stu-id="f7bfa-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="f7bfa-106">说明</span><span class="sxs-lookup"><span data-stu-id="f7bfa-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f7bfa-107">允许注册实例级的新的断字符和筛选器。</span><span class="sxs-lookup"><span data-stu-id="f7bfa-107">allows the instance-level registration of new word breakers and filters.</span></span> <span data-ttu-id="f7bfa-108">这种实例级注册提供了实例间的功能隔离和安全隔离。</span><span class="sxs-lookup"><span data-stu-id="f7bfa-108">This instance-level registration provides functional and security isolation between instances.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f7bfa-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="f7bfa-109">Corrective Action</span></span>  
 <span data-ttu-id="f7bfa-110">升级后，使用 `sp_fulltext_service` 设置服务属性和 `load_os_resources`，以便允许加载组件。</span><span class="sxs-lookup"><span data-stu-id="f7bfa-110">After upgrading, use the `sp_fulltext_service` to set the service property and `load_os_resources`, which allows the components to be loaded.</span></span> <span data-ttu-id="f7bfa-111">必须运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="f7bfa-111">You must run the following:</span></span>  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a><span data-ttu-id="f7bfa-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7bfa-112">See Also</span></span>  
 [<span data-ttu-id="f7bfa-113">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="f7bfa-113">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
