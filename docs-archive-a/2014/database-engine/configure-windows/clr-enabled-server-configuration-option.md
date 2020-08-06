---
title: clr enabled 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577844"
---
# <a name="clr-enabled-server-configuration-option"></a><span data-ttu-id="d1ac2-102">clr enabled 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="d1ac2-102">clr enabled Server Configuration Option</span></span>
  <span data-ttu-id="d1ac2-103">可以使用 clr enabled 选项指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]是否可以运行用户程序集。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-103">Use the clr enabled option to specify whether user assemblies can be run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d1ac2-104">clr enabled 选项提供下列值。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-104">The clr enabled option provides the following values.</span></span>  
  
|<span data-ttu-id="d1ac2-105">值</span><span class="sxs-lookup"><span data-stu-id="d1ac2-105">Value</span></span>|<span data-ttu-id="d1ac2-106">说明</span><span class="sxs-lookup"><span data-stu-id="d1ac2-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d1ac2-107">0</span><span class="sxs-lookup"><span data-stu-id="d1ac2-107">0</span></span>|<span data-ttu-id="d1ac2-108">不允许在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上执行程序集。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-108">Assembly execution not allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="d1ac2-109">1</span><span class="sxs-lookup"><span data-stu-id="d1ac2-109">1</span></span>|<span data-ttu-id="d1ac2-110">允许在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上执行程序集。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-110">Assembly execution allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
 <span data-ttu-id="d1ac2-111">在对此设置所做的更改生效前，必须重新启动 WOW64 服务器。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-111">WOW64 servers must be restarted before the changes to this setting will take effect.</span></span> <span data-ttu-id="d1ac2-112">其他服务器类型不需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-112">Restart is not required for other server types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1ac2-113">运行 RECONFIGURE 时，clr enabled 选项的运行值将从 1 更改为 0，所有包含用户程序集的应用程序域将立即被卸载。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-113">When RECONFIGURE is run and the run value of the clr enabled option is changed from 1 to 0, all application domains containing user assemblies are immediately unloaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1ac2-114">轻型池不支持执行公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-114">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="d1ac2-115">禁用以下两个选项中的一个：“clr enabled”或“lightweight pooling”。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-115">Disable one of two options: "clr enabled" or "lightweight pooling.</span></span> <span data-ttu-id="d1ac2-116">依赖于 CLR 并且在纤程模式下无法正常工作的功能包括：`hierarchy` 数据类型、复制和基于策略的管理。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-116">Features that rely upon CLR and that do not work properly in fiber mode include the `hierarchy` data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1ac2-117">示例</span><span class="sxs-lookup"><span data-stu-id="d1ac2-117">Example</span></span>  
 <span data-ttu-id="d1ac2-118">下面的示例首先显示 clr enabled 选项的当前设置，然后通过将选项值设置为 1 启用该选项。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-118">The following example first displays the current setting of the clr enabled option and then enables the option by setting the option value to 1.</span></span> <span data-ttu-id="d1ac2-119">若要禁用该选项，请将此值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="d1ac2-119">To disable the option, set the value to 0.</span></span>  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1ac2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1ac2-120">See Also</span></span>  
 <span data-ttu-id="d1ac2-121">[lightweight pooling 服务器配置选项](lightweight-pooling-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="d1ac2-121">[lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md) </span></span>  
 <span data-ttu-id="d1ac2-122">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1ac2-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="d1ac2-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1ac2-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="d1ac2-124">lightweight pooling 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="d1ac2-124">lightweight pooling Server Configuration Option</span></span>](lightweight-pooling-server-configuration-option.md)  
  
  
