---
title: ad hoc distributed queries 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d07b3c038597916cdaf026e24e90aab9d6b61616
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576977"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a><span data-ttu-id="e99e1-102">即席分布式查询服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="e99e1-102">ad hoc distributed queries Server Configuration Option</span></span>
  <span data-ttu-id="e99e1-103">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许使用 OPENROWSET 和 OPENDATASOURCE 进行即席分布式查询。</span><span class="sxs-lookup"><span data-stu-id="e99e1-103">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc distributed queries using OPENROWSET and OPENDATASOURCE.</span></span> <span data-ttu-id="e99e1-104">此选项设置为 1 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许进行即席访问。</span><span class="sxs-lookup"><span data-stu-id="e99e1-104">When this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows ad hoc access.</span></span> <span data-ttu-id="e99e1-105">如果此选项未设置或设置为 0，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许进行即席访问。</span><span class="sxs-lookup"><span data-stu-id="e99e1-105">When this option is not set or is set to 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc access.</span></span>  
  
 <span data-ttu-id="e99e1-106">即席分布式查询使用 OPENROWSET 和 OPENDATASOURCE 函数连接到使用 OLE DB 的远程数据源。</span><span class="sxs-lookup"><span data-stu-id="e99e1-106">Ad hoc distributed queries use the OPENROWSET and OPENDATASOURCE functions to connect to remote data sources that use OLE DB.</span></span> <span data-ttu-id="e99e1-107">OPENROWSET 和 OPENDATASOURCE 只应在引用不常访问的 OLE DB 数据源时使用。</span><span class="sxs-lookup"><span data-stu-id="e99e1-107">OPENROWSET and OPENDATASOURCE should be used only to reference OLE DB data sources that are accessed infrequently.</span></span> <span data-ttu-id="e99e1-108">对于将要经常访问的数据源，应定义链接服务器。</span><span class="sxs-lookup"><span data-stu-id="e99e1-108">For any data sources that will be accessed more than several times, define a linked server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e99e1-109">允许使用临时名称意味着到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何经过身份验证的登录名均可访问该访问接口。</span><span class="sxs-lookup"><span data-stu-id="e99e1-109">Enabling the use of ad hoc names means that any authenticated login to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can access the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e99e1-110">管理员应对任何本地登录名都能安全访问的访问接口启用此功能。</span><span class="sxs-lookup"><span data-stu-id="e99e1-110">administrators should enable this feature for providers that are safe to be accessed by any local login.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e99e1-111">备注</span><span class="sxs-lookup"><span data-stu-id="e99e1-111">Remarks</span></span>  
 <span data-ttu-id="e99e1-112">尝试进行即席连接但未启用“即席分布式查询”会导致错误：消息 7415，级别 16，状态 1，行 1</span><span class="sxs-lookup"><span data-stu-id="e99e1-112">Attempting to make an ad hoc connection with **Ad Hoc Distributed Queries** not enabled results in error: Msg 7415, Level 16, State 1, Line 1</span></span>  
  
 <span data-ttu-id="e99e1-113">已拒绝对 OLE DB 访问接口“Microsoft.ACE.OLEDB.12.0”的即席访问。</span><span class="sxs-lookup"><span data-stu-id="e99e1-113">Ad hoc access to OLE DB provider 'Microsoft.ACE.OLEDB.12.0' has been denied.</span></span> <span data-ttu-id="e99e1-114">必须通过链接服务器来访问此访问接口。</span><span class="sxs-lookup"><span data-stu-id="e99e1-114">You must access this provider through a linked server.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e99e1-115">示例</span><span class="sxs-lookup"><span data-stu-id="e99e1-115">Examples</span></span>  
 <span data-ttu-id="e99e1-116">下面的示例启用即席分布式查询，然后使用 `Seattle1` 函数查询名为 `OPENROWSET` 的服务器。</span><span class="sxs-lookup"><span data-stu-id="e99e1-116">The following example enables ad hoc distributed queries and then queries a server named `Seattle1` using the `OPENROWSET` function.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e99e1-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e99e1-117">See Also</span></span>  
 <span data-ttu-id="e99e1-118">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e99e1-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="e99e1-119">[链接服务器（数据库引擎）](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="e99e1-119">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="e99e1-120">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e99e1-120">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="e99e1-121">[OPENDATASOURCE (Transact-SQL)](/sql/t-sql/functions/opendatasource-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e99e1-121">[OPENDATASOURCE &#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span></span>  
 [<span data-ttu-id="e99e1-122">sp_addlinkedserver (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e99e1-122">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  
