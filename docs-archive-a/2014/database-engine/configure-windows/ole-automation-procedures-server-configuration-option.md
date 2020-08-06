---
title: Ole Automation Procedures 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d34615ce1f808c1015c9c3d312a38a67dba291b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683051"
---
# <a name="ole-automation-procedures-server-configuration-option"></a><span data-ttu-id="885bd-102">Ole Automation Procedures 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="885bd-102">Ole Automation Procedures Server Configuration Option</span></span>
  <span data-ttu-id="885bd-103">使用 `Ole Automation Procedures` 选项可指定是否可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理中实例化 OLE Automation 对象。</span><span class="sxs-lookup"><span data-stu-id="885bd-103">Use the `Ole Automation Procedures` option to specify whether OLE Automation objects can be instantiated within [!INCLUDE[tsql](../../includes/tsql-md.md)] batches.</span></span> <span data-ttu-id="885bd-104">还可以使用基于策略的管理或者 **sp_configure** 存储过程来配置这一选项。</span><span class="sxs-lookup"><span data-stu-id="885bd-104">This option can also be configured using the Policy-Based Management or the **sp_configure** stored procedure.</span></span> <span data-ttu-id="885bd-105">有关详细信息，请参阅 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="885bd-105">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
 <span data-ttu-id="885bd-106">可以将 `Ole Automation Procedures` 选项设置为以下值。</span><span class="sxs-lookup"><span data-stu-id="885bd-106">The `Ole Automation Procedures` option can be set to the following values.</span></span>  
  
 <span data-ttu-id="885bd-107">0</span><span class="sxs-lookup"><span data-stu-id="885bd-107">0</span></span>  
 <span data-ttu-id="885bd-108">禁用 OLE Automation Procedures。</span><span class="sxs-lookup"><span data-stu-id="885bd-108">OLE Automation Procedures are disabled.</span></span> <span data-ttu-id="885bd-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新实例的默认值。</span><span class="sxs-lookup"><span data-stu-id="885bd-109">Default for new instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="885bd-110">1</span><span class="sxs-lookup"><span data-stu-id="885bd-110">1</span></span>  
 <span data-ttu-id="885bd-111">启用 OLE Automation Procedures。</span><span class="sxs-lookup"><span data-stu-id="885bd-111">OLE Automation Procedures are enabled.</span></span>  
  
 <span data-ttu-id="885bd-112">当启用 OLE Automation Procedures 时，对 **sp_OACreate** 的调用将会启动 OLE 共享执行环境。</span><span class="sxs-lookup"><span data-stu-id="885bd-112">When OLE Automation Procedures are enabled, a call to **sp_OACreate** will start the OLE shared execution environment.</span></span>  
  
 <span data-ttu-id="885bd-113">`Ole Automation Procedures`可以使用**sp_configure**系统存储过程来查看和更改选项的当前值。</span><span class="sxs-lookup"><span data-stu-id="885bd-113">The current value of the `Ole Automation Procedures` option can be viewed and changed by using the **sp_configure** system stored procedure.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="885bd-114">示例</span><span class="sxs-lookup"><span data-stu-id="885bd-114">Examples</span></span>  
 <span data-ttu-id="885bd-115">以下示例显示了如何查看 OLE Automation Procedures 的当前设置。</span><span class="sxs-lookup"><span data-stu-id="885bd-115">The following example shows how to view the current setting of OLE Automation procedures.</span></span>  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 <span data-ttu-id="885bd-116">以下示例显示了如何启用 OLE Automation Procedures。</span><span class="sxs-lookup"><span data-stu-id="885bd-116">The following example shows how to enable OLE Automation procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="885bd-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="885bd-117">See Also</span></span>  
 <span data-ttu-id="885bd-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="885bd-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="885bd-119">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="885bd-119">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="885bd-120">[外围应用配置器](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="885bd-120">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 [<span data-ttu-id="885bd-121">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="885bd-121">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
