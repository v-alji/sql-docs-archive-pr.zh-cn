---
title: 保留锁配置选项默认值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a1d1dcf82d9cd0ef8ef2c15cb68ef78b53a8a54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578163"
---
# <a name="keep-the-locks-configuration-option-default-value"></a><span data-ttu-id="70ee4-102">保留锁配置选项默认值</span><span class="sxs-lookup"><span data-stu-id="70ee4-102">Keep the Locks Configuration Option Default Value</span></span>
  <span data-ttu-id="70ee4-103">此规则检查锁配置选项的值。</span><span class="sxs-lookup"><span data-stu-id="70ee4-103">This rule checks the value of the locks configuration option.</span></span> <span data-ttu-id="70ee4-104">此选项确定可用锁的最大数量。</span><span class="sxs-lookup"><span data-stu-id="70ee4-104">This option determines the maximum number of available locks.</span></span> <span data-ttu-id="70ee4-105">这将限制 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 用于锁的内存量。</span><span class="sxs-lookup"><span data-stu-id="70ee4-105">This limits how much memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for locks.</span></span> <span data-ttu-id="70ee4-106">默认设置 0 使 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 可以根据不断变化的系统要求动态地分配和解除分配锁结构。</span><span class="sxs-lookup"><span data-stu-id="70ee4-106">The default setting of 0 enables the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically based on changing system requirements.</span></span>  
  
 <span data-ttu-id="70ee4-107">如果锁为非零值，则批处理作业将停止，如果该值超出指定值，将生成“超出锁值”错误消息。</span><span class="sxs-lookup"><span data-stu-id="70ee4-107">If locks is nonzero, batch jobs will stop, and an "out of locks" error message will be generated, if the value specified is exceeded.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="70ee4-108">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="70ee4-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="70ee4-109">在下面的语句中使用 sp_configure 系统存储过程将锁值更改为默认设置：</span><span class="sxs-lookup"><span data-stu-id="70ee4-109">Use the sp_configure system stored procedure to change the value of locks to its default setting by using the following statement:</span></span>  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="70ee4-110">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="70ee4-110">For More Information</span></span>  
 [<span data-ttu-id="70ee4-111">配置 locks 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="70ee4-111">Configure the locks Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [<span data-ttu-id="70ee4-112">sys.dm_tran_locks (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70ee4-112">sys.dm_tran_locks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [<span data-ttu-id="70ee4-113">sys.dm_os_wait_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70ee4-113">sys.dm_os_wait_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [<span data-ttu-id="70ee4-114">Microsoft 知识库文章 271509</span><span class="sxs-lookup"><span data-stu-id="70ee4-114">Microsoft Knowledge Base article 271509</span></span>](https://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a><span data-ttu-id="70ee4-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70ee4-115">See Also</span></span>  
 [<span data-ttu-id="70ee4-116">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="70ee4-116">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
