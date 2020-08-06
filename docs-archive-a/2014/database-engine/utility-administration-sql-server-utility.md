---
title: 实用工具管理 (SQL Server 实用工具) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 3e5a00c3-8905-40f0-9ddc-d924df9c2f0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fca4ea655ffdcf8471d1340016d16f2c5b9c352a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689569"
---
# <a name="utility-administration-sql-server-utility"></a><span data-ttu-id="072c5-102">实用工具管理（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="072c5-102">Utility Administration (SQL Server Utility)</span></span>
  <span data-ttu-id="072c5-103">使用“实用工具管理”选项卡可以管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具的策略、安全性和数据仓库设置。</span><span class="sxs-lookup"><span data-stu-id="072c5-103">Use the Utility Administration tabs to manage policy, security, and data warehouse settings for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="072c5-104">有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具概念的详细信息，请参阅 [SQL Server 实用工具功能和任务](../relational-databases/manage/sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="072c5-104">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility concepts, see [SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="072c5-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="072c5-105">UI element list</span></span>  
 <span data-ttu-id="072c5-106">“策略”选项卡 - 使用“策略”选项卡可查看或指定全局监视策略。</span><span class="sxs-lookup"><span data-stu-id="072c5-106">Policy tab - Use the policy tab to view or specify global monitoring policies.</span></span>  
  
 <span data-ttu-id="072c5-107">设置全局数据层应用程序监视策略。</span><span class="sxs-lookup"><span data-stu-id="072c5-107">Set global data-tier application monitoring policies.</span></span> <span data-ttu-id="072c5-108">若要展开此选项的值列表，请单击策略名称旁的箭头，或者单击策略标题。</span><span class="sxs-lookup"><span data-stu-id="072c5-108">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="072c5-109">何时应用程序会用尽处理器容量？</span><span class="sxs-lookup"><span data-stu-id="072c5-109">When is an application running out of processor capacity?</span></span> <span data-ttu-id="072c5-110">若要更改此策略，请使用策略说明右侧的控件，然后单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="072c5-110">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="072c5-111">您还可以使用显示底部的按钮还原默认值或放弃更改。</span><span class="sxs-lookup"><span data-stu-id="072c5-111">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="072c5-112">处理器使用率的默认最大值是 70%。</span><span class="sxs-lookup"><span data-stu-id="072c5-112">The default maximum value for processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="072c5-113">处理器使用率的默认最小值是 0%。</span><span class="sxs-lookup"><span data-stu-id="072c5-113">The default minimum value for processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="072c5-114">何时应用程序会用尽文件空间？</span><span class="sxs-lookup"><span data-stu-id="072c5-114">When is an application running out of file space?</span></span> <span data-ttu-id="072c5-115">若要更改数据文件或日志文件空间使用率的策略，请使用策略说明右侧的控件，然后单击“应用” 。</span><span class="sxs-lookup"><span data-stu-id="072c5-115">To change the policy for data file or log file space utilization, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="072c5-116">您还可以使用显示底部的按钮还原默认值或放弃更改。</span><span class="sxs-lookup"><span data-stu-id="072c5-116">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="072c5-117">文件空间使用率的默认最大值是 70%。</span><span class="sxs-lookup"><span data-stu-id="072c5-117">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="072c5-118">文件空间使用率的默认最小值是 0%。</span><span class="sxs-lookup"><span data-stu-id="072c5-118">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="072c5-119">设置全局 SQL Server 托管实例应用程序监视策略。</span><span class="sxs-lookup"><span data-stu-id="072c5-119">Set global SQL Server managed instance application monitoring policies.</span></span> <span data-ttu-id="072c5-120">若要展开此选项的值列表，请单击策略名称旁的箭头，或者单击策略标题。</span><span class="sxs-lookup"><span data-stu-id="072c5-120">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="072c5-121">何时 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例会用尽处理器容量？</span><span class="sxs-lookup"><span data-stu-id="072c5-121">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of processor capacity?</span></span> <span data-ttu-id="072c5-122">若要更改此策略，请使用策略说明右侧的控件，然后单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="072c5-122">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="072c5-123">您还可以使用显示底部的按钮还原默认值或放弃更改。</span><span class="sxs-lookup"><span data-stu-id="072c5-123">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="072c5-124">实例处理器使用率的默认最大值是 70%。</span><span class="sxs-lookup"><span data-stu-id="072c5-124">The default maximum value for instance processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="072c5-125">实例处理器使用率的默认最小值是 0%。</span><span class="sxs-lookup"><span data-stu-id="072c5-125">The default minimum value for instance processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="072c5-126">何时 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 计算机的托管实例会用尽处理器容量？</span><span class="sxs-lookup"><span data-stu-id="072c5-126">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of processor capacity?</span></span> <span data-ttu-id="072c5-127">若要更改此策略，请使用策略说明右侧的控件，然后单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="072c5-127">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="072c5-128">您还可以使用显示底部的按钮还原默认值或放弃更改。</span><span class="sxs-lookup"><span data-stu-id="072c5-128">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="072c5-129">计算机处理器使用率的默认最大值是 70%。</span><span class="sxs-lookup"><span data-stu-id="072c5-129">The default maximum value for computer processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="072c5-130">计算机处理器使用率的默认最小值是 0%。</span><span class="sxs-lookup"><span data-stu-id="072c5-130">The default minimum value for computer processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="072c5-131">何时 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例会用尽文件空间？</span><span class="sxs-lookup"><span data-stu-id="072c5-131">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of file space?</span></span> <span data-ttu-id="072c5-132">若要更改数据文件或日志文件空间使用率的策略，请使用策略说明右侧的控件，然后单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="072c5-132">To change the policy for data file or log file space utilization , use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="072c5-133">您还可以使用显示底部的按钮还原默认值或放弃更改。</span><span class="sxs-lookup"><span data-stu-id="072c5-133">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="072c5-134">文件空间使用率的默认最大值是 70%。</span><span class="sxs-lookup"><span data-stu-id="072c5-134">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="072c5-135">文件空间使用率的默认最小值是 0%。</span><span class="sxs-lookup"><span data-stu-id="072c5-135">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="072c5-136">何时 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 计算机的托管实例会用尽存储卷空间？</span><span class="sxs-lookup"><span data-stu-id="072c5-136">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of storage volume space?</span></span> <span data-ttu-id="072c5-137">若要更改此策略，请使用策略说明右侧的控件，然后单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="072c5-137">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="072c5-138">您还可以使用显示底部的按钮还原默认值或放弃更改。</span><span class="sxs-lookup"><span data-stu-id="072c5-138">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="072c5-139">计算机卷空间使用率的默认最大值是 70%。</span><span class="sxs-lookup"><span data-stu-id="072c5-139">The default maximum value for computer volume space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="072c5-140">计算机卷空间使用率的默认最小值是 0%。</span><span class="sxs-lookup"><span data-stu-id="072c5-140">The default minimum value for computer volume space utilization is 0%.</span></span>  
  
 <span data-ttu-id="072c5-141">减少高度易失性资源中的策略违反干扰。</span><span class="sxs-lookup"><span data-stu-id="072c5-141">Reducing policy violation noise from highly volatile resources.</span></span> <span data-ttu-id="072c5-142">若要展开此功能的控件，请单击显示右侧的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="072c5-142">To expand the controls for this feature, click on the down-arrow on the right side of the display.</span></span>  
 <span data-ttu-id="072c5-143">有关详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)</span><span class="sxs-lookup"><span data-stu-id="072c5-143">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="072c5-144">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="072c5-144">UI element list</span></span>  
 <span data-ttu-id="072c5-145">“安全性”选项卡 - 显示有权管理 UCP 或从 UCP 进行读取的登录名。</span><span class="sxs-lookup"><span data-stu-id="072c5-145">Security tab - Displays login names with permissions to administer or read from the UCP.</span></span>  
  
 <span data-ttu-id="072c5-146">从将添加到实用工具读取者角色的 UCP 选择登录名。</span><span class="sxs-lookup"><span data-stu-id="072c5-146">Select the logins from the UCP that will be added to the Utility Reader role.</span></span>  
 <span data-ttu-id="072c5-147">实用工具读取者权限允许用户帐户：</span><span class="sxs-lookup"><span data-stu-id="072c5-147">The Utility Reader privilege allows the user account to:</span></span>  
  
-   <span data-ttu-id="072c5-148">连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具。</span><span class="sxs-lookup"><span data-stu-id="072c5-148">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="072c5-149">在 SSMS 的实用工具资源管理器中查看所有视点。</span><span class="sxs-lookup"><span data-stu-id="072c5-149">See all viewpoints in the Utility Explorer in SSMS.</span></span>  
  
-   <span data-ttu-id="072c5-150">在 SSMS 的实用工具资源管理器中查看“实用工具管理”节点的设置。</span><span class="sxs-lookup"><span data-stu-id="072c5-150">See settings on the Utility Administration node in Utility Explorer in SSMS.</span></span>  
  
 <span data-ttu-id="072c5-151">实用工具管理员可以将 SQL Server 的实例注册到 SQL Server 实用工具中和从 SQL Server 实用工具中删除 SQL Server 的实例，以及修改托管实例上的策略和修改 UCP 上的管理设置。</span><span class="sxs-lookup"><span data-stu-id="072c5-151">Utility administrators can enroll instances of SQL Server into and remove instances of SQL Server from a SQL Server Utility, as well as modify policies on managed instances and modify administration settings on the UCP.</span></span>  
  
 <span data-ttu-id="072c5-152">要作为实用工具管理员，您必须对 SQL Server 的实例具有 sysadmin 权限。</span><span class="sxs-lookup"><span data-stu-id="072c5-152">To be a Utility administrator, you must have sysadmin privileges on the instance of SQL Server.</span></span> <span data-ttu-id="072c5-153">若要添加或更改 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP 的用户帐户，请使用 SSMS 中的对象资源管理器将该用户添加到 SQL Server 的 UCP 实例的服务器登录名中。</span><span class="sxs-lookup"><span data-stu-id="072c5-153">To add or change user accounts for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, use Object Explorer in SSMS to add the user to the server logins of the UCP instance of SQL Server.</span></span> <span data-ttu-id="072c5-154">有关详细信息，请参阅 [sp_addlogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="072c5-154">For more information, see [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="072c5-155">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="072c5-155">UI element list</span></span>  
 <span data-ttu-id="072c5-156">“数据仓库”选项卡 - 为实用工具管理数据仓库显示配置详细信息。</span><span class="sxs-lookup"><span data-stu-id="072c5-156">Data Warehouse tab - Displays configuration details for the utility management data warehouse.</span></span>  
  
 <span data-ttu-id="072c5-157">数据保留</span><span class="sxs-lookup"><span data-stu-id="072c5-157">Data Retention</span></span>  
 <span data-ttu-id="072c5-158">针对为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例收集的使用率信息，指定数据保持期。</span><span class="sxs-lookup"><span data-stu-id="072c5-158">Specify the data retention period for utilization information collected for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="072c5-159">默认保持期为 1 年。</span><span class="sxs-lookup"><span data-stu-id="072c5-159">The default time period is 1 year.</span></span> <span data-ttu-id="072c5-160">最小值为 1 个月。</span><span class="sxs-lookup"><span data-stu-id="072c5-160">The minimum value is 1 month.</span></span> <span data-ttu-id="072c5-161">支持的最长的值是 2 年。</span><span class="sxs-lookup"><span data-stu-id="072c5-161">The longest supported value is 2 years.</span></span>  
  
 <span data-ttu-id="072c5-162">实用工具数据仓库配置信息</span><span class="sxs-lookup"><span data-stu-id="072c5-162">Utility Data Warehouse Configuration Information</span></span>  
 <span data-ttu-id="072c5-163">以下配置设置在此版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中不可配置：</span><span class="sxs-lookup"><span data-stu-id="072c5-163">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="072c5-164">UMDW 名称：Sysutility_mdw_\<GUID>_DATA。</span><span class="sxs-lookup"><span data-stu-id="072c5-164">UMDW name: Sysutility_mdw_\<GUID>_DATA.</span></span>  
  
-   <span data-ttu-id="072c5-165">收集组上载频率：每隔 15 分钟。</span><span class="sxs-lookup"><span data-stu-id="072c5-165">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="072c5-166">UMDW 目录是可配置的：\<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中，\<System drive> 通常为 C:\ 驱动器。</span><span class="sxs-lookup"><span data-stu-id="072c5-166">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="072c5-167">日志文件 UMDW_\<GUID>_LOG 位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="072c5-167">The log file, UMDW_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="072c5-168">可以使用 detach/attach 或 ALTER DATABASE 更改该 UMDW (sysutility_mdw) 文件位置。</span><span class="sxs-lookup"><span data-stu-id="072c5-168">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="072c5-169">我们建议使用 ALTER DATABASE。</span><span class="sxs-lookup"><span data-stu-id="072c5-169">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="072c5-170">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="072c5-170">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="072c5-171">返回到出厂默认值</span><span class="sxs-lookup"><span data-stu-id="072c5-171">Go back to out-of-the-box defaults</span></span>  
 <span data-ttu-id="072c5-172">若要将此选项卡上的设置重置为默认值，请单击“还原默认设置”按钮，然后单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="072c5-172">To reset settings on this tab to default values, click the **Restore Defaults** button, then click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072c5-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="072c5-173">See Also</span></span>  
 <span data-ttu-id="072c5-174">[实用工具仪表板 &#40;SQL Server 实用工具&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="072c5-174">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="072c5-175">[已部署的数据层应用程序详细信息（SQL Server 实用工具）](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="072c5-175">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="072c5-176">[托管实例详细信息（SQL Server 实用工具）](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="072c5-176">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="072c5-177">在 SQL Server 实用工具中监视 SQL Server 的实例</span><span class="sxs-lookup"><span data-stu-id="072c5-177">Monitor Instances of SQL Server in the SQL Server Utility</span></span>](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)  
  
  
