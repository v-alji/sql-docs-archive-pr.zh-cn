---
title: 在 SQL Server 的同一实例中运行实用工具和非实用工具收集组的注意事项Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67df2d65cc9da4026377e77c152c0d78f3749932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587810"
---
# <a name="considerations-for-running-utility-and-non-utility-collection-sets-on-the-same-instance-of-sql-server"></a><span data-ttu-id="c4d0b-102">在 SQL Server 的同一实例中运行实用工具和非实用工具收集组的注意事项</span><span class="sxs-lookup"><span data-stu-id="c4d0b-102">Considerations for Running Utility and non-Utility Collection Sets on the Same Instance of SQL Server</span></span>
  <span data-ttu-id="c4d0b-103">支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组与非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组并行。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection set is supported side-by-side with non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets.</span></span> <span data-ttu-id="c4d0b-104">也就是说，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某一托管实例是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具的成员时，该托管实例可由其他收集组监视。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-104">That is, a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be monitored by other collection sets while it is a member of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="c4d0b-105">但是，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例正在注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具时，您必须禁用非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组功能。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-105">However, you must disable non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection functionality while the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being enrolled into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="c4d0b-106">在向 UCP 注册了该实例后，您可以重新启动非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-106">After the instance is enrolled with the UCP, you can restart non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets.</span></span> <span data-ttu-id="c4d0b-107">但要注意的是，该托管实例上的所有收集组会将其数据上载到实用工具管理数据仓库 (UMDW) 中；UMDW 文件名为 sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-107">Note, however, that all collection sets on the managed instance will upload their data to the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="c4d0b-108">若要将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组与非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组并行运行，请考虑以下要点：</span><span class="sxs-lookup"><span data-stu-id="c4d0b-108">To run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets side-by-side with non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets, consider the following points:</span></span>  
  
-   <span data-ttu-id="c4d0b-109">支持并行收集组。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-109">Side-by-side collection sets are supported.</span></span>  
  
-   <span data-ttu-id="c4d0b-110">在将实例注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具时您必须禁用现有的数据收集器。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-110">You must disable existing data collectors while enrolling instances into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="c4d0b-111">为了满足验证要求，您必须在创建 UCP 前在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例上运行以下存储过程，并且在将其注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中之前在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例上运行以下存储过程：</span><span class="sxs-lookup"><span data-stu-id="c4d0b-111">To pass validation requirements, you must run the following stored procedures on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you create a UCP, and on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you enroll it into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility:</span></span>  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     <span data-ttu-id="c4d0b-112">如果您在启动“创建 UCP 向导”或“添加托管实例向导”之前未运行这些存储过程，操作将失败：</span><span class="sxs-lookup"><span data-stu-id="c4d0b-112">If you do not run these stored procedures before you launch the Create UCP Wizard or Add Managed Instance Wizard, the operation will fail.</span></span>  
  
-   <span data-ttu-id="c4d0b-113">您必须为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例上的所有收集组使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实用工具 UMDW (sysutility_mdw)。</span><span class="sxs-lookup"><span data-stu-id="c4d0b-113">You must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility UMDW (sysutility_mdw) for all collection sets on a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d0b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4d0b-114">See Also</span></span>  
 <span data-ttu-id="c4d0b-115">[SQL Server 实用工具的功能和任务](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="c4d0b-115">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="c4d0b-116">配置实用工具控制点数据仓库（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="c4d0b-116">Configure Your Utility Control Point Data Warehouse &#40;SQL Server Utility&#41;</span></span>](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
