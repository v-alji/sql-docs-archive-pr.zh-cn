---
title: 启用和配置 FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], enabling
ms.assetid: 78737e19-c65b-48d9-8fa9-aa6f1e1bce73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f6c0e505bd32636d045519b36e439bc21c7079d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576841"
---
# <a name="enable-and-configure-filestream"></a><span data-ttu-id="2cfbf-102">启用和配置 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="2cfbf-102">Enable and Configure FILESTREAM</span></span>
  <span data-ttu-id="2cfbf-103">在开始使用 FILESTREAM 之前，必须在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例中启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-103">Before you can start to use FILESTREAM, you must enable FILESTREAM on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="2cfbf-104">本主题说明了如何使用 SQL Server 配置管理器来启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-104">This topic describes how to enable FILESTREAM by using SQL Server Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cfbf-105">不能在 64 位操作系统上运行的 32 位版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-105">You cannot enable FILESTREAM on a 32-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a 64-bit operating system.</span></span>  
  
##  <a name="enabling-filestream"></a><a name="enabling"></a> <span data-ttu-id="2cfbf-106">启用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="2cfbf-106">Enabling FILESTREAM</span></span>  
  
#### <a name="to-enable-and-change-filestream-settings"></a><span data-ttu-id="2cfbf-107">启用和更改 FILESTREAM 设置</span><span class="sxs-lookup"><span data-stu-id="2cfbf-107">To enable and change FILESTREAM settings</span></span>  
  
1.  <span data-ttu-id="2cfbf-108">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="2cfbf-109">在服务列表中，右键单击“SQL Server 服务”  ，然后单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-109">In the list of services, right-click **SQL Server Services**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="2cfbf-110">在“SQL Server 配置管理器”  管理单元中，找到要在其中启用 FILESTREAM 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-110">In the **SQL Server Configuration Manager** snap-in, locate the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to enable FILESTREAM.</span></span>  
  
4.  <span data-ttu-id="2cfbf-111">右键单击该实例，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-111">Right-click the instance, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="2cfbf-112">在 **“SQL Server 属性”** 对话框中，单击 **“FILESTREAM”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-112">In the **SQL Server Properties** dialog box, click the **FILESTREAM** tab.</span></span>  
  
6.  <span data-ttu-id="2cfbf-113">选中“针对 Transact-SQL 访问启用 FILESTREAM”  复选框。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-113">Select the **Enable FILESTREAM for Transact-SQL access** check box.</span></span>  
  
7.  <span data-ttu-id="2cfbf-114">如果要在 Windows 中读取和写入 FILESTREAM 数据，请单击“针对文件 I/O 流访问启用 FILESTREAM”  。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-114">If you want to read and write FILESTREAM data from Windows, click **Enable FILESTREAM for file I/O streaming access**.</span></span> <span data-ttu-id="2cfbf-115">在 **“Windows 共享名”** 框中输入 Windows 共享的名称。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-115">Enter the name of the Windows share in the **Windows Share Name** box.</span></span>  
  
8.  <span data-ttu-id="2cfbf-116">如果远程客户端必须访问存储在此共享中的 FILESTREAM 数据，请选择 **“允许远程客户端针对 FILESTREAM 数据启用流访问”** 。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-116">If remote clients must access the FILESTREAM data that is stored on this share, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span>  
  
9. <span data-ttu-id="2cfbf-117">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-117">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="2cfbf-118">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，单击 **“新建查询”** 以显示查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
11. <span data-ttu-id="2cfbf-119">在查询编辑器中，输入以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码：</span><span class="sxs-lookup"><span data-stu-id="2cfbf-119">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
    ```sql  
    EXEC sp_configure filestream_access_level, 2  
    RECONFIGURE  
    ```  
  
12. <span data-ttu-id="2cfbf-120">单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-120">Click **Execute**.</span></span>  
  
13. <span data-ttu-id="2cfbf-121">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-121">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  

  
##  <a name="best-practices"></a><a name="best"></a> <span data-ttu-id="2cfbf-122">最佳实践</span><span class="sxs-lookup"><span data-stu-id="2cfbf-122">Best Practices</span></span>  
  
###  <a name="physical-configuration-and-maintenance"></a><a name="config"></a><span data-ttu-id="2cfbf-123">物理配置和维护</span><span class="sxs-lookup"><span data-stu-id="2cfbf-123">Physical Configuration and Maintenance</span></span>  
 <span data-ttu-id="2cfbf-124">设置 FILESTREAM 存储卷时，请考虑下列准则：</span><span class="sxs-lookup"><span data-stu-id="2cfbf-124">When you set up FILESTREAM storage volumes, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="2cfbf-125">禁用 FILESTREAM 计算机系统中的短文件名。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-125">Turn off short file names on FILESTREAM computer systems.</span></span> <span data-ttu-id="2cfbf-126">创建短文件名需要花费相当长的时间。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-126">Short file names take significantly longer to create.</span></span> <span data-ttu-id="2cfbf-127">若要禁用短文件名，请使用 Windows **fsutil** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-127">To disable short file names, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="2cfbf-128">定期对 FILESTREAM 计算机系统进行碎片整理。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-128">Regularly defragment FILESTREAM computer systems.</span></span>  
  
-   <span data-ttu-id="2cfbf-129">使用 64-KB NTFS 簇。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-129">Use 64-KB NTFS clusters.</span></span> <span data-ttu-id="2cfbf-130">压缩卷必须设置为 4-KB NTFS 簇。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-130">Compressed volumes must be set to 4-KB NTFS clusters.</span></span>  
  
-   <span data-ttu-id="2cfbf-131">对 FILESTREAM 卷禁用索引并设置 **disablelastaccess** 若要设置 **disablelastaccess**，请使用 Windows **fsutil** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-131">Disable indexing on FILESTREAM volumes and set **disablelastaccess** To set **disablelastaccess**, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="2cfbf-132">除非必要，否则请禁止对 FILESTREAM 卷进行防病毒扫描。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-132">Disable antivirus scanning of FILESTREAM volumes when it is not unnecessary.</span></span> <span data-ttu-id="2cfbf-133">如果需要进行防病毒扫描，请避免设置将自动删除有问题文件的策略。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-133">If antivirus scanning is necessary, avoid setting policies that will automatically delete offending files.</span></span>  
  
-   <span data-ttu-id="2cfbf-134">设置并调整 RAID 级别，以达到应用程序所需的容错能力和性能。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-134">Set up and tune the RAID level for fault tolerance and the performance that is required by an application.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="2cfbf-135">RAID 级别</span><span class="sxs-lookup"><span data-stu-id="2cfbf-135">RAID level</span></span>|<span data-ttu-id="2cfbf-136">写性能</span><span class="sxs-lookup"><span data-stu-id="2cfbf-136">Write performance</span></span>|<span data-ttu-id="2cfbf-137">读性能</span><span class="sxs-lookup"><span data-stu-id="2cfbf-137">Read performance</span></span>|<span data-ttu-id="2cfbf-138">容错</span><span class="sxs-lookup"><span data-stu-id="2cfbf-138">Fault tolerance</span></span>|<span data-ttu-id="2cfbf-139">备注</span><span class="sxs-lookup"><span data-stu-id="2cfbf-139">Remarks</span></span>|  
|<span data-ttu-id="2cfbf-140">RAID 5</span><span class="sxs-lookup"><span data-stu-id="2cfbf-140">RAID 5</span></span>|<span data-ttu-id="2cfbf-141">一般</span><span class="sxs-lookup"><span data-stu-id="2cfbf-141">Normal</span></span>|<span data-ttu-id="2cfbf-142">一般</span><span class="sxs-lookup"><span data-stu-id="2cfbf-142">Normal</span></span>|<span data-ttu-id="2cfbf-143">很好</span><span class="sxs-lookup"><span data-stu-id="2cfbf-143">Excellent</span></span>|<span data-ttu-id="2cfbf-144">性能比一个磁盘或 JBOD 更好；比 RAID 0 或条带化 RAID 5 差。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-144">Performance is better than one disk or JBOD; and less than RAID 0 or RAID 5 with striping.</span></span>|  
|<span data-ttu-id="2cfbf-145">RAID 0</span><span class="sxs-lookup"><span data-stu-id="2cfbf-145">RAID 0</span></span>|<span data-ttu-id="2cfbf-146">很好</span><span class="sxs-lookup"><span data-stu-id="2cfbf-146">Excellent</span></span>|<span data-ttu-id="2cfbf-147">很好</span><span class="sxs-lookup"><span data-stu-id="2cfbf-147">Excellent</span></span>|<span data-ttu-id="2cfbf-148">无</span><span class="sxs-lookup"><span data-stu-id="2cfbf-148">None</span></span>||  
|<span data-ttu-id="2cfbf-149">RAID 5 ＋ 条带化</span><span class="sxs-lookup"><span data-stu-id="2cfbf-149">RAID 5 + stripping</span></span>|<span data-ttu-id="2cfbf-150">很好</span><span class="sxs-lookup"><span data-stu-id="2cfbf-150">Excellent</span></span>|<span data-ttu-id="2cfbf-151">很好</span><span class="sxs-lookup"><span data-stu-id="2cfbf-151">Excellent</span></span>|<span data-ttu-id="2cfbf-152">很好</span><span class="sxs-lookup"><span data-stu-id="2cfbf-152">Excellent</span></span>|<span data-ttu-id="2cfbf-153">成本最高的选项。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-153">Most expensive option.</span></span>|  
  

  
###  <a name="physical-database-design"></a><a name="database"></a><span data-ttu-id="2cfbf-154">物理数据库设计</span><span class="sxs-lookup"><span data-stu-id="2cfbf-154">Physical Database Design</span></span>  
 <span data-ttu-id="2cfbf-155">设计 FILESTREAM 数据库时，应考虑下列准则：</span><span class="sxs-lookup"><span data-stu-id="2cfbf-155">When you design a FILESTREAM database, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="2cfbf-156">FILESTREAM 列必须附带相应的 `uniqueidentifier` ROWGUID 列。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-156">FILESTREAM columns must be accompanied by a corresponding `uniqueidentifier`ROWGUID column.</span></span> <span data-ttu-id="2cfbf-157">这些类型的表还必须附带唯一索引。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-157">These kinds of tables must also be accompanied by a unique index.</span></span> <span data-ttu-id="2cfbf-158">此索引通常不是聚集索引。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-158">Typically this index is not a clustered index.</span></span> <span data-ttu-id="2cfbf-159">如果数据库业务逻辑需要聚集索引，则必须确保该索引中存储的值不是随机的。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-159">If the databases business logic requires a clustered index, you have to make sure that the values stored in the index are not random.</span></span> <span data-ttu-id="2cfbf-160">随机值将导致每次向表中添加行或从表中删除行时，索引都会重新排序。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-160">Random values will cause the index to be reordered every time that a row is added or removed from the table.</span></span>  
  
-   <span data-ttu-id="2cfbf-161">出于性能方面的考虑，FILESTREAM 文件组和容器应驻留在操作系统、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志、tempdb 或分页文件以外的卷上。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-161">For performance reasons, FILESTREAM filegroups and containers should reside on volumes other than the operating system, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log, tempdb, or paging file.</span></span>  
  
-   <span data-ttu-id="2cfbf-162">FILESTREAM 不直接支持空间管理和策略。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-162">Space management and policies are not directly supported by FILESTREAM.</span></span> <span data-ttu-id="2cfbf-163">但是，您可以通过将每个 FILESTREAM 文件组分配到独立的卷并使用该卷的管理功能来间接地管理空间和应用策略。</span><span class="sxs-lookup"><span data-stu-id="2cfbf-163">However, you can manage space and apply policies indirectly by assigning each FILESTREAM filegroup to a separate volume and using the volume's management features.</span></span>  
  
  
