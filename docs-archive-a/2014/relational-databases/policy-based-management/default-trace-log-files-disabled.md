---
title: 默认跟踪日志文件已禁用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fed8fb006427b4dda9d99c57cbabca8538efcad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580199"
---
# <a name="default-trace-log-files-disabled"></a><span data-ttu-id="573b2-102">默认跟踪日志文件已禁用</span><span class="sxs-lookup"><span data-stu-id="573b2-102">Default Trace Log Files Disabled</span></span>
  <span data-ttu-id="573b2-103">此规则检查 sp_configure 存储过程 default trace enabled 选项的值，以确定默认跟踪是设置成了 ON (1) 还是设置成了 OFF (0)。</span><span class="sxs-lookup"><span data-stu-id="573b2-103">This rule checks the value of the sp_configure stored procedure default trace enabled option to determine whether default trace is set ON (1) or OFF (0).</span></span> <span data-ttu-id="573b2-104">启用此选项后，默认跟踪提供有关对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]进行的配置和 DDL 更改的信息。</span><span class="sxs-lookup"><span data-stu-id="573b2-104">When this option is enabled, default tracing provides information about configuration and DDL changes to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="573b2-105">在某些情况下，当客户和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门解决 [!INCLUDE[ssDE](../../includes/ssde-md.md)]问题时，此信息对他们可能会有所帮助。</span><span class="sxs-lookup"><span data-stu-id="573b2-105">In some cases, this information can be helpful for customers and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support when they troubleshooting issues with the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="573b2-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="573b2-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="573b2-107">使用 sp_configure 存储过程通过将 default trace enabled 的值设置为 1 来启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="573b2-107">Use the sp_configure stored procedure to enable tracing by setting the value of default trace enabled to 1.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="573b2-108">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="573b2-108">For More Information</span></span>  
 [<span data-ttu-id="573b2-109">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="573b2-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="573b2-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="573b2-110">See Also</span></span>  
 [<span data-ttu-id="573b2-111">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="573b2-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
