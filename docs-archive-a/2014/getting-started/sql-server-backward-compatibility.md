---
title: SQL Server 向后兼容性 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac47cb74-5578-417d-bcef-f970d9527705
author: rothja
ms.author: jroth
ms.openlocfilehash: a4d38041ce4daa12911dc706d382460324931c90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688997"
---
# <a name="sql-server-backward-compatibility"></a><span data-ttu-id="d3dd4-102">SQL Server 的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="d3dd4-102">SQL Server Backward Compatibility</span></span>
  <span data-ttu-id="d3dd4-103">向后兼容性部分中的主题介绍 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 了各版本之间的行为变化 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-103">Topics in the backward compatibility section describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d3dd4-104">本主题范围中包含的功能包括数据可编程性、外围应用配置器工具、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装程序、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务，以及其他多种功能更改。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-104">Features included in this topic area include data programmability, surface area configuration tools, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>  
  
|<span data-ttu-id="d3dd4-105">主题</span><span class="sxs-lookup"><span data-stu-id="d3dd4-105">Topic</span></span>|<span data-ttu-id="d3dd4-106">说明</span><span class="sxs-lookup"><span data-stu-id="d3dd4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d3dd4-107">SQL Server 2014 中不推荐使用的 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="d3dd4-107">Deprecated SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/deprecated-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="d3dd4-108">此版本中不推荐使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-108">Deprecated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="d3dd4-109">本主题介绍了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置和安装功能。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-109">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="d3dd4-110">SQL Server 2014 中不再推荐使用的 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="d3dd4-110">Discontinued SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="d3dd4-111">此版本中不再推荐使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-111">Discontinued [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality in this release.</span></span> <span data-ttu-id="d3dd4-112">本主题介绍了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置和安装功能。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-112">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="d3dd4-113">SQL Server 2014 中 SQL Server 功能的重大更改</span><span class="sxs-lookup"><span data-stu-id="d3dd4-113">Breaking Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/breaking-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="d3dd4-114">可能需要更改应用程序的更改。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-114">Changes that might require changes to applications.</span></span> <span data-ttu-id="d3dd4-115">本主题介绍了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置和安装功能。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-115">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="d3dd4-116">SQL Server 2014 中 SQL Server 功能的行为更改</span><span class="sxs-lookup"><span data-stu-id="d3dd4-116">Behavior Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/behavior-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="d3dd4-117">此版本中对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能的行为更改。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-117">Behavioral  changes to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="d3dd4-118">本主题介绍了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置和安装功能。</span><span class="sxs-lookup"><span data-stu-id="d3dd4-118">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3dd4-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3dd4-119">See Also</span></span>  
 [<span data-ttu-id="d3dd4-120">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="d3dd4-120">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
