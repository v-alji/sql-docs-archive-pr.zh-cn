---
title: 将 UCP 从 SQL Server 的一个实例移到另一个实例（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2cf17a79c9a1bb1bd7e86e1ecb36ef671414fb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586662"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a><span data-ttu-id="d966d-102">将 UCP 从 SQL Server 的一个实例移到另一个实例（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="d966d-102">Move a UCP from One Instance of SQL Server to Another (SQL Server Utility)</span></span>
  <span data-ttu-id="d966d-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中将实用工具控制点 (UCP) 从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的一个实例移到另一个实例。</span><span class="sxs-lookup"><span data-stu-id="d966d-103">This topic describes how to move a utility control point (UCP) from one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d966d-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d966d-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a><span data-ttu-id="d966d-105">将 UCP 从 SQL Server 的一个实例移到另一个实例。</span><span class="sxs-lookup"><span data-stu-id="d966d-105">Move a UCP from one instance of SQL Server to another.</span></span>  
  
1.  <span data-ttu-id="d966d-106">在将成为新 UCP 的新宿主实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上创建该新的 UCP。</span><span class="sxs-lookup"><span data-stu-id="d966d-106">Create a new UCP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that will be the new host instance of the UCP.</span></span> <span data-ttu-id="d966d-107">有关详细信息，请参阅[创建 SQL Server 实用工具控制点（SQL Server 实用工具）](create-a-sql-server-utility-control-point-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d966d-107">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="d966d-108">如果已经在您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何实例设置了非默认的策略设置，则记录策略阈值，以便您可以在新的 UCP 上重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="d966d-108">If non-default policy settings have been set for any instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make note of the policy thresholds so that you can re-establish them on the new UCP.</span></span> <span data-ttu-id="d966d-109">在将实例添加到新的 UCP 时应用默认策略。</span><span class="sxs-lookup"><span data-stu-id="d966d-109">Default policies are applied when instances are added to the new UCP.</span></span> <span data-ttu-id="d966d-110">如果默认策略在起作用，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具列表视图将在 **“策略类型”** 列中显示 **“全局”** 。</span><span class="sxs-lookup"><span data-stu-id="d966d-110">If default policies are in effect, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility list view displays **Global** in the **Policy Type** column.</span></span>  
  
3.  <span data-ttu-id="d966d-111">从旧的 UCP 中删除所有托管实例。</span><span class="sxs-lookup"><span data-stu-id="d966d-111">Remove all managed instances from the old UCP.</span></span> <span data-ttu-id="d966d-112">有关详细信息，请参阅 [从 SQL Server 实用工具中删除 SQL Server 的实例](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d966d-112">For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
4.  <span data-ttu-id="d966d-113">从旧的 UCP 备份实用工具管理数据仓库 (UMDW)。</span><span class="sxs-lookup"><span data-stu-id="d966d-113">Back up the utility management data warehouse (UMDW) from the old UCP.</span></span> <span data-ttu-id="d966d-114">文件名是 Sysutility_mdw_\<GUID>_DATA，数据库默认位置是 \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中，\<System drive> 通常为 C:\ 驱动器。</span><span class="sxs-lookup"><span data-stu-id="d966d-114">The filename is Sysutility_mdw_\<GUID>_DATA, and the database default location is \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="d966d-115">有关详细信息，请参阅 [通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="d966d-115">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
5.  <span data-ttu-id="d966d-116">将 UMDW 的备份还原到新 UCP。</span><span class="sxs-lookup"><span data-stu-id="d966d-116">Restore the backup of the UMDW to the new UCP.</span></span> <span data-ttu-id="d966d-117">有关详细信息，请参阅 [通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="d966d-117">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
6.  <span data-ttu-id="d966d-118">将实例注册到新的 UCP 中，使它们由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具管理。</span><span class="sxs-lookup"><span data-stu-id="d966d-118">Enroll instances into the new UCP to make them managed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="d966d-119">有关详细信息，请参阅[注册 SQL Server 的实例（SQL Server 实用工具）](enroll-an-instance-of-sql-server-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d966d-119">For more information, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
7.  <span data-ttu-id="d966d-120">根据需要，为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的托管实例实现自定义策略定义。</span><span class="sxs-lookup"><span data-stu-id="d966d-120">Implement custom policy definitions for the managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as necessary.</span></span>  
  
8.  <span data-ttu-id="d966d-121">等待大约 1 小时，以便数据收集和聚合操作完成。</span><span class="sxs-lookup"><span data-stu-id="d966d-121">Wait approximately 1 hour for data collection and aggregation operations to complete.</span></span>  
  
9. <span data-ttu-id="d966d-122">若要刷新数据，请在“实用工具资源管理器”中右键单击“托管实例”节点，然后选择“刷新”。</span><span class="sxs-lookup"><span data-stu-id="d966d-122">To refresh data, right-click the **Managed Instances** node in **Utility Explorer**, then select **Refresh**.</span></span> <span data-ttu-id="d966d-123">列表视图数据将显示在 **“实用工具资源管理器”** 内容窗格中。</span><span class="sxs-lookup"><span data-stu-id="d966d-123">List view data are displayed in the **Utility Explorer** content pane.</span></span> <span data-ttu-id="d966d-124">有关详细信息，请参阅[查看资源运行状况策略结果（SQL Server 实用工具）](view-resource-health-policy-results-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d966d-124">For more information, see [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d966d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d966d-125">See Also</span></span>  
 <span data-ttu-id="d966d-126">[SQL Server 实用工具的功能和任务](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d966d-126">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="d966d-127">注册 SQL Server 实例（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="d966d-127">Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;</span></span>](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
