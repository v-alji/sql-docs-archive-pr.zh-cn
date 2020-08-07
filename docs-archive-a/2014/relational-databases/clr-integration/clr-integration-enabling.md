---
title: 启用 CLR 集成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7187906f1376deb81ca7ff4770af7b12b63c022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691232"
---
# <a name="enabling-clr-integration"></a><span data-ttu-id="98f47-102">启用 CLR 集成</span><span class="sxs-lookup"><span data-stu-id="98f47-102">Enabling CLR Integration</span></span>
  <span data-ttu-id="98f47-103">默认情况下关闭公共语言运行时 (CLR) 集成功能，必须启用该功能才能使用借助 CLR 集成实现的对象。</span><span class="sxs-lookup"><span data-stu-id="98f47-103">The common language runtime (CLR) integration feature is off by default, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="98f47-104">若要启用 CLR 集成，请使用**sp_configure**存储过程的 " **clr 已启用**" 选项：</span><span class="sxs-lookup"><span data-stu-id="98f47-104">To enable CLR integration, use the **clr enabled** option of the **sp_configure** stored procedure:</span></span>  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="98f47-105">可以通过将 " **clr 已启用**" 选项设置为0来禁用 clr 集成。</span><span class="sxs-lookup"><span data-stu-id="98f47-105">You can disable CLR integration by setting the **clr enabled** option to 0.</span></span> <span data-ttu-id="98f47-106">禁用 CLR 集成后，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 停止执行所有 CLR 例程并卸载所有应用程序域。</span><span class="sxs-lookup"><span data-stu-id="98f47-106">When you disable CLR integration, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stops executing all CLR routines and unloads all application domains.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98f47-107">若要启用 CLR 集成，必须具有 ALTER SETTINGS 服务器级别权限，该权限由**sysadmin**和**serveradmin**固定服务器角色的成员隐式持有。</span><span class="sxs-lookup"><span data-stu-id="98f47-107">To enable CLR integration, you must have ALTER SETTINGS server level permission, which is implicitly held by members of the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98f47-108">配置使用大量内存空间和大量处理器的计算机可能在启动 SQL Server 时无法加载其中的 CLR 集成功能。</span><span class="sxs-lookup"><span data-stu-id="98f47-108">Computers configured with large amounts of memory and a large number of processors may fail to load the CLR integration feature of SQL Server when starting the server.</span></span> <span data-ttu-id="98f47-109">若要解决此问题，请使用 **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务启动选项启动服务器，并指定足够大的内存值。</span><span class="sxs-lookup"><span data-stu-id="98f47-109">To address this issue, start the server by using the **-gmemory_to_reserve**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service startup option, and specify a memory value large enough.</span></span> <span data-ttu-id="98f47-110">有关详细信息，请参阅 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="98f47-110">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98f47-111">轻型池不支持执行公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="98f47-111">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="98f47-112">启用 CLR 集成之前，必须禁用轻型池。</span><span class="sxs-lookup"><span data-stu-id="98f47-112">Before enabling CLR integration, you must disable lightweight pooling.</span></span> <span data-ttu-id="98f47-113">有关详细信息，请参阅 [lightweight pooling 服务器配置选项](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="98f47-113">For more information, see [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f47-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98f47-114">See Also</span></span>  
 <span data-ttu-id="98f47-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98f47-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="98f47-116">[clr enabled 服务器配置选项](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="98f47-116">[clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="98f47-117">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98f47-117">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="98f47-118">[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98f47-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="98f47-119">服务器级角色</span><span class="sxs-lookup"><span data-stu-id="98f47-119">Server-Level Roles</span></span>](../security/authentication-access/server-level-roles.md)  
  
  
