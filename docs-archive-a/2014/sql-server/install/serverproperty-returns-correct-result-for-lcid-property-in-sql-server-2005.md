---
title: SERVERPROPERTY 返回 SQL Server 2005 | 中 LCID 属性的正确结果Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebb125a86e6e30f2c3638004593da7657f02f1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689719"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a><span data-ttu-id="3aa75-102">在 SQL Server 2005 中，SERVERPROPERTY 返回 LCID 属性的正确结果</span><span class="sxs-lookup"><span data-stu-id="3aa75-102">SERVERPROPERTY returns correct result for LCID property in SQL Server 2005</span></span>
  <span data-ttu-id="3aa75-103">当在使用二进制排序规则的服务器上运行 SERVERPROPERTY('LCID') 时，该函数返回与服务器的排序规则相对应的 Windows 区域设置标识符 (LCID)。</span><span class="sxs-lookup"><span data-stu-id="3aa75-103">When SERVERPROPERTY('LCID') is run on binary collation servers, the function returns the Windows locale identifier (LCID) that corresponds to the collation of the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aa75-104">对于包含对 SERVERPROPERTY ('LCID') 的引用并且在其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上运行的批处理文件和跟踪文件，只有其他实例的排序规则与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当前实例的排序规则相同时，升级顾问才会检测此行为更改。</span><span class="sxs-lookup"><span data-stu-id="3aa75-104">For batch and trace files that contain references to SERVERPROPERTY ('LCID') and are run on other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Upgrade Advisor will detect this behavior change only if the other instances have the same collation as the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3aa75-105">纠正措施</span><span class="sxs-lookup"><span data-stu-id="3aa75-105">Corrective Action</span></span>  
 <span data-ttu-id="3aa75-106">修改应用程序，使 SERVERPROPERTY('LCID') 返回与服务器排序规则对应的 Windows LCID。</span><span class="sxs-lookup"><span data-stu-id="3aa75-106">Modify applications to expect SERVERPROPERTY('LCID') to return the Windows LCID that corresponds to the collation of the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa75-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3aa75-107">See Also</span></span>  
 <span data-ttu-id="3aa75-108">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="3aa75-108">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="3aa75-109">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="3aa75-109">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
