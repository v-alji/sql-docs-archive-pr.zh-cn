---
title: 使用数据库邮件而不是 SQL Mail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6a957b65975645bdeb9f55faee4e650b53718b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580180"
---
# <a name="use-database-mail-instead-of-sql-mail"></a><span data-ttu-id="f8dba-102">使用数据库邮件而不是 SQL Mail</span><span class="sxs-lookup"><span data-stu-id="f8dba-102">Use Database Mail Instead of SQL Mail</span></span>
  <span data-ttu-id="f8dba-103">此规则检查 sys.configurations 目录视图以确定 SQL Mail XPs 服务器范围配置选项是否已设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="f8dba-103">This rule checks the sys.configurations catalog view to determine whether the SQL Mail XPs server-wide configuration option is set to ON.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="f8dba-104">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="f8dba-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="f8dba-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的将来版本中将删除 SQL Mail。</span><span class="sxs-lookup"><span data-stu-id="f8dba-105">SQL Mail will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f8dba-106">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f8dba-106">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="f8dba-107">要发送邮件，请使用“数据库邮件”。</span><span class="sxs-lookup"><span data-stu-id="f8dba-107">To send mail, use Database Mail.</span></span>  
  
 <span data-ttu-id="f8dba-108">SQL Mail 在进程内运行到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f8dba-108">SQL Mail runs in-process to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="f8dba-109">如果 SQL Mail 关闭，服务器也会关闭。</span><span class="sxs-lookup"><span data-stu-id="f8dba-109">If SQL Mail goes down, so does the server.</span></span> <span data-ttu-id="f8dba-110">数据库邮件在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外的单独进程内运行，它是可伸缩的，并且不需要在生产服务器上安装扩展 MAPI 客户端组件。</span><span class="sxs-lookup"><span data-stu-id="f8dba-110">Database Mail runs outside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a separate process, is scalable, and does not require Extended MAPI client components to be installed on the production server.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="f8dba-111">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="f8dba-111">For More Information</span></span>  
 [<span data-ttu-id="f8dba-112">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="f8dba-112">Database Mail</span></span>](../database-mail/database-mail.md)  
  
## <a name="see-also"></a><span data-ttu-id="f8dba-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8dba-113">See Also</span></span>  
 [<span data-ttu-id="f8dba-114">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="f8dba-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
