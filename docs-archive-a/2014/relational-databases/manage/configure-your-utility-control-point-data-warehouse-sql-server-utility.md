---
title: 配置实用工具控制点数据仓库（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60b9623b468f2763cf619c325412373e3603f3a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578884"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a><span data-ttu-id="6c091-102">配置您的实用工具控制点数据仓库（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="6c091-102">Configure Your Utility Control Point Data Warehouse (SQL Server Utility)</span></span>
  <span data-ttu-id="6c091-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例收集的数据存储在实用工具管理数据仓库 (UMDW) 中；UMDW 文件名为 sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="6c091-103">Data collected by managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are stored in the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="6c091-104">您可以配置 UMDW 数据保持期。</span><span class="sxs-lookup"><span data-stu-id="6c091-104">You can configure the UMDW data retention period.</span></span> <span data-ttu-id="6c091-105">有关详细信息，请参阅[实用工具管理（SQL Server 实用工具）](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="6c091-105">For more information, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="6c091-106">以下配置设置在此版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中不可配置：</span><span class="sxs-lookup"><span data-stu-id="6c091-106">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="6c091-107">UMDW 名称：Sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="6c091-107">UMDW name: Sysutility_mdw.</span></span>  
  
-   <span data-ttu-id="6c091-108">收集组上载频率：每隔 15 分钟。</span><span class="sxs-lookup"><span data-stu-id="6c091-108">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="6c091-109">UMDW 目录是可配置的：\<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中，\<System drive> 通常为 C:\ 驱动器。</span><span class="sxs-lookup"><span data-stu-id="6c091-109">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="6c091-110">日志文件 Sysutility_mdw_\<GUID>_LOG 位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="6c091-110">The log file, Sysutility_mdw_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c091-111">可以使用 detach/attach 或 ALTER DATABASE 更改该 UMDW (sysutility_mdw) 文件位置。</span><span class="sxs-lookup"><span data-stu-id="6c091-111">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="6c091-112">我们建议使用 ALTER DATABASE。</span><span class="sxs-lookup"><span data-stu-id="6c091-112">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="6c091-113">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6c091-113">For more information see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c091-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c091-114">See Also</span></span>  
 [<span data-ttu-id="6c091-115">SQL Server 实用工具功能和任务</span><span class="sxs-lookup"><span data-stu-id="6c091-115">SQL Server Utility Features and Tasks</span></span>](sql-server-utility-features-and-tasks.md)  
  
  
