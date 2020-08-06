---
title: 对 SQL Server Reporting Services Standard 和 Enterprise 的 CPU 和内存限制的更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bd889344f5b0bc72320ff8467ebd6ecc654872f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579972"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a><span data-ttu-id="4e7bf-102">对 SQL Server Reporting Services Standard 和 Enterprise 的 CPU 和内存限制的更改</span><span class="sxs-lookup"><span data-stu-id="4e7bf-102">Changes to CPU and memory limits for SQL Server Reporting Services Standard and Enterprise</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="4e7bf-103">Reporting Services Standard 和 Enterprise 支持最多 64 GB 的系统内存。</span><span class="sxs-lookup"><span data-stu-id="4e7bf-103">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4e7bf-104">组件</span><span class="sxs-lookup"><span data-stu-id="4e7bf-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a><span data-ttu-id="4e7bf-105">说明</span><span class="sxs-lookup"><span data-stu-id="4e7bf-105">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4e7bf-106">Reporting Services Standard 和 Enterprise 支持最多 64 GB 的系统内存。</span><span class="sxs-lookup"><span data-stu-id="4e7bf-106">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span> <span data-ttu-id="4e7bf-107">您可能需要重新配置您的当前系统设置，以便顺应新的限制。</span><span class="sxs-lookup"><span data-stu-id="4e7bf-107">You may need to reconfigure your current system settings to align with the new limits.</span></span>  
  
 <span data-ttu-id="4e7bf-108">有关的其他版本的 CPU 和内存限制的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[按版本的 SQL Server 计算容量限制](../compute-capacity-limits-by-edition-of-sql-server.md)和[SQL Server 版本支持的内存](https://go.microsoft.com/fwlink/?LinkId=212633)。</span><span class="sxs-lookup"><span data-stu-id="4e7bf-108">For more information about CPU and memory limits for other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), and [Memory Supported by the Editions of SQL Server](https://go.microsoft.com/fwlink/?LinkId=212633).</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="4e7bf-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="4e7bf-109">Corrective Action</span></span>  
 <span data-ttu-id="4e7bf-110">您可能需要重新配置您的当前系统设置，以便顺应新的 CPU 和内存限制。</span><span class="sxs-lookup"><span data-stu-id="4e7bf-110">You may need to reconfigure your current system settings to align with the new CPU and memory limits.</span></span> <span data-ttu-id="4e7bf-111">有关详细信息，请参阅[ALTER SERVER configuration &#40;transact-sql&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)和[服务器内存服务器配置选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4e7bf-111">For more information, see [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), and [Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7bf-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e7bf-112">See Also</span></span>  
 <span data-ttu-id="4e7bf-113">[SQL Server 2014 的各个版本支持的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="4e7bf-113">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 [<span data-ttu-id="4e7bf-114">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="4e7bf-114">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
