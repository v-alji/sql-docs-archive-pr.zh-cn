---
title: c2 audit mode 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3407a2a94a43adb2d3d3b52994093d6ed0c2e684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693091"
---
# <a name="c2-audit-mode-server-configuration-option"></a><span data-ttu-id="2d108-102">c2 审核模式服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="2d108-102">c2 audit mode Server Configuration Option</span></span>
  <span data-ttu-id="2d108-103">可以通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或使用 **sp_configure** 中的“c2 审核模式”选项来配置 C2 审核模式。</span><span class="sxs-lookup"><span data-stu-id="2d108-103">C2 audit mode can be configured through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or with the **c2 audit mode** option in **sp_configure**.</span></span> <span data-ttu-id="2d108-104">选择此选项将配置服务器，以记录对语句和对象的失败和成功的访问尝试。</span><span class="sxs-lookup"><span data-stu-id="2d108-104">Selecting this option will configure the server to record both failed and successful attempts to access statements and objects.</span></span> <span data-ttu-id="2d108-105">这些信息可以帮助您了解系统活动并跟踪可能的安全策略冲突。</span><span class="sxs-lookup"><span data-stu-id="2d108-105">This information can help you profile system activity and track possible security policy violations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="2d108-106">C2 安全标准已经由通用准则认证所取代。</span><span class="sxs-lookup"><span data-stu-id="2d108-106">The C2 security standard has been superseded by Common Criteria Certification.</span></span> <span data-ttu-id="2d108-107">请参阅 [启用了通用准则合规性的服务器配置选项](common-criteria-compliance-enabled-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="2d108-107">See the [common criteria compliance enabled Server Configuration Option](common-criteria-compliance-enabled-server-configuration-option.md).</span></span>  
  
## <a name="audit-log-file"></a><span data-ttu-id="2d108-108">审核日志文件</span><span class="sxs-lookup"><span data-stu-id="2d108-108">Audit Log File</span></span>  
 <span data-ttu-id="2d108-109">C2 审核模式数据保存在实例的默认数据目录中的某个文件内。</span><span class="sxs-lookup"><span data-stu-id="2d108-109">C2 audit mode data is saved in a file in the default data directory of the instance.</span></span> <span data-ttu-id="2d108-110">如果审核日志文件达到了 200 MB 的大小限制， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将创建新文件、关闭旧文件并将所有新的审核记录写入新文件。</span><span class="sxs-lookup"><span data-stu-id="2d108-110">If the audit log file reaches its size limit of 200 megabytes (MB), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will create a new file, close the old file, and write all new audit records to the new file.</span></span> <span data-ttu-id="2d108-111">此过程将继续下去，直到审核数据目录已满或审核被关闭。</span><span class="sxs-lookup"><span data-stu-id="2d108-111">This process will continue until the audit data directory fills up or auditing is turned off.</span></span> <span data-ttu-id="2d108-112">若要确定 C2 跟踪的状态，请查询 sys.traces 目录视图。</span><span class="sxs-lookup"><span data-stu-id="2d108-112">To determine the status of a C2 trace, query the sys.traces catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2d108-113">C2 审核模式将大量事件信息保存在日志文件中，可能会导致日志文件迅速增大。</span><span class="sxs-lookup"><span data-stu-id="2d108-113">C2 audit mode saves a large amount of event information to the log file, which can grow quickly.</span></span> <span data-ttu-id="2d108-114">如果保存日志的数据目录空间不足， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将自行关闭。</span><span class="sxs-lookup"><span data-stu-id="2d108-114">If the data directory in which logs are being saved runs out of space, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will shut itself down.</span></span> <span data-ttu-id="2d108-115">如果将审核设置为自动启动，则必须使用 **-f** 标志（跳过审核）重新启动该实例或为审核日志释放更多磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="2d108-115">If auditing is set to start automatically, you must either restart the instance with the **-f** flag (which bypasses auditing), or free up additional disk space for the audit log.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="2d108-116">权限</span><span class="sxs-lookup"><span data-stu-id="2d108-116">Permissions</span></span>  
 <span data-ttu-id="2d108-117">要求具有 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="2d108-117">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d108-118">示例</span><span class="sxs-lookup"><span data-stu-id="2d108-118">Example</span></span>  
 <span data-ttu-id="2d108-119">下面的示例将启用 C2 审核模式。</span><span class="sxs-lookup"><span data-stu-id="2d108-119">The following example turns on C2 audit mode.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d108-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d108-120">See Also</span></span>  
 <span data-ttu-id="2d108-121">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2d108-121">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2d108-122">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2d108-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="2d108-123">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2d108-123">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
