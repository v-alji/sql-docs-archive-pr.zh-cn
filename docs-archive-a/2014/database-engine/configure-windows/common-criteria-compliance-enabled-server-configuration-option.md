---
title: common criteria compliance enabled 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6722d05351b8b9e80240abb4edef0633a97b6da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577846"
---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a><span data-ttu-id="3ac84-102">common criteria compliance enabled 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="3ac84-102">common criteria compliance enabled Server Configuration Option</span></span>
  <span data-ttu-id="3ac84-103">common criteria compliance enabled 选项用于启用通用准则所需的下列元素：</span><span class="sxs-lookup"><span data-stu-id="3ac84-103">The common criteria compliance enabled option enables the following elements that are required for the Common Criteria.</span></span>  
  
|<span data-ttu-id="3ac84-104">条件</span><span class="sxs-lookup"><span data-stu-id="3ac84-104">Criteria</span></span>|<span data-ttu-id="3ac84-105">说明</span><span class="sxs-lookup"><span data-stu-id="3ac84-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3ac84-106">残留信息保护 (RIP)</span><span class="sxs-lookup"><span data-stu-id="3ac84-106">Residual Information Protection (RIP)</span></span>|<span data-ttu-id="3ac84-107">RIP 要求将内存重新分配给新资源之前，用已知的位模式覆盖内存分配。</span><span class="sxs-lookup"><span data-stu-id="3ac84-107">RIP requires a memory allocation to be overwritten with a known pattern of bits before memory is reallocated to a new resource.</span></span> <span data-ttu-id="3ac84-108">满足 RIP 标准有助于提高安全性；然而，覆盖内存分配会使性能降低。</span><span class="sxs-lookup"><span data-stu-id="3ac84-108">Meeting the RIP standard can contribute to improved security; however, overwriting the memory allocation can slow performance.</span></span> <span data-ttu-id="3ac84-109">启用 common criteria compliance enabled 选项之后，将执行覆盖操作。</span><span class="sxs-lookup"><span data-stu-id="3ac84-109">After the common criteria compliance enabled option is enabled, the overwriting occurs.</span></span>|  
|<span data-ttu-id="3ac84-110">查看登录统计信息的能力</span><span class="sxs-lookup"><span data-stu-id="3ac84-110">The ability to view login statistics</span></span>|<span data-ttu-id="3ac84-111">启用 common criteria compliance enabled 选项之后，将启用登录审核。</span><span class="sxs-lookup"><span data-stu-id="3ac84-111">After the common criteria compliance enabled option is enabled, login auditing is enabled.</span></span> <span data-ttu-id="3ac84-112">用户每次成功登录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时，系统都会提供有关上一次成功登录的时间、上一次登录失败的时间以及上一次成功登录时间和当前登录时间之间尝试登录的次数的信息。</span><span class="sxs-lookup"><span data-stu-id="3ac84-112">Each time a user successfully logs in to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], information about the last successful login time, the last unsuccessful login time, and the number of attempts between the last successful and current login times is made available.</span></span> <span data-ttu-id="3ac84-113">可以通过查询 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 动态管理视图来查看这些登录统计信息。</span><span class="sxs-lookup"><span data-stu-id="3ac84-113">These login statistics can be viewed by querying the [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) dynamic management view.</span></span>|  
|<span data-ttu-id="3ac84-114">GRANT 列不应覆盖 DENY 表</span><span class="sxs-lookup"><span data-stu-id="3ac84-114">That column GRANT should not override table DENY</span></span>|<span data-ttu-id="3ac84-115">启用 common criteria compliance enabled 后，表级 DENY 将优先于列级 GRANT。</span><span class="sxs-lookup"><span data-stu-id="3ac84-115">After the common criteria compliance enabled option is enabled, a table-level DENY takes precedence over a column-level GRANT.</span></span> <span data-ttu-id="3ac84-116">未启用该选项时，列级 GRANT 则优先于表级 DENY。</span><span class="sxs-lookup"><span data-stu-id="3ac84-116">When the option is not enabled, a column-level GRANT takes precedence over a table-level DENY.</span></span>|  
  
 <span data-ttu-id="3ac84-117">common criteria compliance enabled 选项是高级选项。</span><span class="sxs-lookup"><span data-stu-id="3ac84-117">The common criteria compliance enabled option is an advanced option.</span></span> <span data-ttu-id="3ac84-118">通用准则仅针对 Enterprise Edition 和 Datacenter Edition 进行评估和认证。</span><span class="sxs-lookup"><span data-stu-id="3ac84-118">Common criteria is only evaluated and certified for the Enterprise edition and Datacenter edition.</span></span> <span data-ttu-id="3ac84-119">有关通用准则认证的最新状态，请参阅 [Microsoft SQL Server 通用准则](https://go.microsoft.com/fwlink/?LinkId=616319) 网站。</span><span class="sxs-lookup"><span data-stu-id="3ac84-119">For the latest status of common criteria certification, see the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ac84-120">除启用“common criteria compliance enabled”选项以外，还必须下载和运行一个版本，该版本可完成对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的配置以便符合通用准则评估保证级别 4 (EAL4+)。</span><span class="sxs-lookup"><span data-stu-id="3ac84-120">In addition to enabling the common criteria compliance enabled option, you also must download and run a script that finishes configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to comply with Common Criteria Evaluation Assurance Level 4+ (EAL4+).</span></span> <span data-ttu-id="3ac84-121">可以从 [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) （Microsoft SQL Server 通用准则）网站下载此脚本。</span><span class="sxs-lookup"><span data-stu-id="3ac84-121">You can download this script from the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
 <span data-ttu-id="3ac84-122">如果使用 sp_configure 系统存储过程来更改该设置，则只有在“show advanced options”设置为 1 时才能更改“common criteria compliance enabled”。</span><span class="sxs-lookup"><span data-stu-id="3ac84-122">If you are using the sp_configure system stored procedure to change the setting, you can change common criteria compliance enabled only when show advanced options is set to 1.</span></span> <span data-ttu-id="3ac84-123">该设置在服务器重新启动后生效。</span><span class="sxs-lookup"><span data-stu-id="3ac84-123">The setting takes effect after the server is restarted.</span></span> <span data-ttu-id="3ac84-124">可能的值为 0 和 1：</span><span class="sxs-lookup"><span data-stu-id="3ac84-124">The possible values are 0 and 1:</span></span>  
  
-   <span data-ttu-id="3ac84-125">0 表示未启用符合通用准则。</span><span class="sxs-lookup"><span data-stu-id="3ac84-125">0 indicates that common criteria compliance is not enabled.</span></span> <span data-ttu-id="3ac84-126">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="3ac84-126">This is the default.</span></span>  
  
-   <span data-ttu-id="3ac84-127">1 表示启用了符合通用准则。</span><span class="sxs-lookup"><span data-stu-id="3ac84-127">1 indicates that common criteria compliance is enabled.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3ac84-128">示例</span><span class="sxs-lookup"><span data-stu-id="3ac84-128">Examples</span></span>  
 <span data-ttu-id="3ac84-129">以下示例启用符合通用准则。</span><span class="sxs-lookup"><span data-stu-id="3ac84-129">The following example enables common criteria compliance.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ac84-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ac84-130">See Also</span></span>  
 [<span data-ttu-id="3ac84-131">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ac84-131">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
