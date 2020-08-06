---
title: 排除使用代理的多服务器作业的故障 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19de975ef5e1f22c93cec72a5014a01da5b03dd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689227"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a><span data-ttu-id="ef5c0-102">排除使用代理的多服务器作业的故障</span><span class="sxs-lookup"><span data-stu-id="ef5c0-102">Troubleshoot Multiserver Jobs That Use Proxies</span></span>
  <span data-ttu-id="ef5c0-103">如果分布式作业的步骤与某个代理关联，则该作业将在目标服务器上该代理帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="ef5c0-103">Distributed jobs whose steps are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="ef5c0-104">如果从主服务器下载使用代理帐户的作业步骤时失败，则请检查 **msdb** 数据库中 **sysdownloadlist** 表的 **error_message** 列是否存在下列错误消息：</span><span class="sxs-lookup"><span data-stu-id="ef5c0-104">If job steps that use proxy accounts fail when downloaded from the master server, check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="ef5c0-105">“该作业步骤需要代理帐户，但是目标服务器上禁用了代理匹配功能。”</span><span class="sxs-lookup"><span data-stu-id="ef5c0-105">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="ef5c0-106">若要解决此错误，请设置**\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\MSSQL.**_ \<n_> **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName**注册表子项\*\*设置为 1 () 为 true \*\*。</span><span class="sxs-lookup"><span data-stu-id="ef5c0-106">To resolve this error, set the **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.**_\<n_>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** registry subkey to **1 (true)**.</span></span> <span data-ttu-id="ef5c0-107">默认情况下，此子项设置为**0** (`false`) 。</span><span class="sxs-lookup"><span data-stu-id="ef5c0-107">By default, this subkey is set to **0** (`false`).</span></span> <span data-ttu-id="ef5c0-108">MSSQL 的值 **。**\<*n*></span><span class="sxs-lookup"><span data-stu-id="ef5c0-108">The value of **MSSQL.**\<*n*></span></span> <span data-ttu-id="ef5c0-109">是实例名称;例如， **mssql. 1**或**mssql. 3**。</span><span class="sxs-lookup"><span data-stu-id="ef5c0-109">is the instance name; for example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
-   <span data-ttu-id="ef5c0-110">“找不到代理。”</span><span class="sxs-lookup"><span data-stu-id="ef5c0-110">"Proxy not found."</span></span>  
  
     <span data-ttu-id="ef5c0-111">若要解决此错误，请确保目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="ef5c0-111">To resolve this error, make sure a proxy account exists on the target server with the same name as the master server proxy account under which the job step runs.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef5c0-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef5c0-112">See Also</span></span>  
 [<span data-ttu-id="ef5c0-113">创建多服务器环境</span><span class="sxs-lookup"><span data-stu-id="ef5c0-113">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
  
  
