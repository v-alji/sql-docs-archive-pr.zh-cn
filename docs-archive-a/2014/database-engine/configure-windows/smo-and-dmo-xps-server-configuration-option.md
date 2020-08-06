---
title: “SMO 和 DMO XP”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f18fc6fafcf033113c983f990700158a10aec92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693082"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a><span data-ttu-id="3c0d2-102">SMO 和 DMO XP 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="3c0d2-102">SMO and DMO XPs Server Configuration Option</span></span>
  <span data-ttu-id="3c0d2-103">使用 SMO 和 DMO XP 选项可以在此服务器上启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象 (SMO) 扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-103">Use the SMO and DMO XPs option to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) extended stored procedures on this server.</span></span>  
  
 <span data-ttu-id="3c0d2-104">请注意，从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，DMO 已从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中删除。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-104">Note than beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO has been removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3c0d2-105">下表中列出了该选项的可能值：</span><span class="sxs-lookup"><span data-stu-id="3c0d2-105">The possible values are described in the following table:</span></span>  
  
|<span data-ttu-id="3c0d2-106">值</span><span class="sxs-lookup"><span data-stu-id="3c0d2-106">Value</span></span>|<span data-ttu-id="3c0d2-107">含义</span><span class="sxs-lookup"><span data-stu-id="3c0d2-107">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="3c0d2-108">0</span><span class="sxs-lookup"><span data-stu-id="3c0d2-108">0</span></span>|<span data-ttu-id="3c0d2-109">SMO XP 不可用。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-109">SMO XPs are not available.</span></span>|  
|<span data-ttu-id="3c0d2-110">1</span><span class="sxs-lookup"><span data-stu-id="3c0d2-110">1</span></span>|<span data-ttu-id="3c0d2-111">SMO XP 可用。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-111">SMO XPs are available.</span></span> <span data-ttu-id="3c0d2-112">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-112">This is the default.</span></span>|  
  
 <span data-ttu-id="3c0d2-113">设置立即生效。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-113">The setting takes effect immediately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3c0d2-114">示例</span><span class="sxs-lookup"><span data-stu-id="3c0d2-114">Examples</span></span>  
 <span data-ttu-id="3c0d2-115">以下示例启用了 SMO 扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="3c0d2-115">The following example enables SMO extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c0d2-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c0d2-116">See Also</span></span>  
 [<span data-ttu-id="3c0d2-117">SQL Server 管理对象 (SMO) 编程指南</span><span class="sxs-lookup"><span data-stu-id="3c0d2-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
