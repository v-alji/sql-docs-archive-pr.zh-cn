---
title: 打开日志文件查看器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269ff10275f7463a8a85249a2a0f06fe9bde364a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580727"
---
# <a name="open-log-file-viewer"></a><span data-ttu-id="acaec-102">打开日志文件查看器</span><span class="sxs-lookup"><span data-stu-id="acaec-102">Open Log File Viewer</span></span>
  <span data-ttu-id="acaec-103">可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的日志文件查看器来访问有关在以下日志中捕获的错误和事件的信息：</span><span class="sxs-lookup"><span data-stu-id="acaec-103">You can use Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to access information about errors and events that are captured in the following logs:</span></span>  
  
-   <span data-ttu-id="acaec-104">审核集合</span><span class="sxs-lookup"><span data-stu-id="acaec-104">Audit Collection</span></span>  
  
-   <span data-ttu-id="acaec-105">数据收集</span><span class="sxs-lookup"><span data-stu-id="acaec-105">Data Collection</span></span>  
  
-   <span data-ttu-id="acaec-106">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="acaec-106">Database Mail</span></span>  
  
-   <span data-ttu-id="acaec-107">作业历史记录</span><span class="sxs-lookup"><span data-stu-id="acaec-107">Job History</span></span>  
  
-   <span data-ttu-id="acaec-108">SQL Server</span><span class="sxs-lookup"><span data-stu-id="acaec-108">SQL Server</span></span>  
  
-   <span data-ttu-id="acaec-109">SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="acaec-109">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="acaec-110">Windows 事件（这些 Windows 事件还可以从事件查看器进行访问。）</span><span class="sxs-lookup"><span data-stu-id="acaec-110">Windows events (These Windows events can also be accessed from Event Viewer.)</span></span>  
  
 <span data-ttu-id="acaec-111">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，您可以使用已注册的服务器从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地或远程实例查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日志文件。</span><span class="sxs-lookup"><span data-stu-id="acaec-111">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can use Registered Servers to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from local or remote instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="acaec-112">通过使用已注册的服务器，无论实例处于联机还是脱机状态，您都可以查看日志文件。</span><span class="sxs-lookup"><span data-stu-id="acaec-112">By using Registered Servers, you can view the log files when the instances are either online or offline.</span></span> <span data-ttu-id="acaec-113">有关联机访问的详细信息，请参阅本主题后面的“从已注册的服务器查看联机日志文件”过程。</span><span class="sxs-lookup"><span data-stu-id="acaec-113">For more information about online access, see the procedure "To view online log files from Registered Servers" later in this topic.</span></span> <span data-ttu-id="acaec-114">有关如何访问脱机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件的详细信息，请参阅 [查看脱机日志文件](view-offline-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="acaec-114">For more information about how to access offline [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files, see [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
 <span data-ttu-id="acaec-115">可以通过多种方法打开日志文件查看器，具体情况取决于您要查看的信息。</span><span class="sxs-lookup"><span data-stu-id="acaec-115">You can open Log File Viewer in several ways, depending on the information that you want to view.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="acaec-116">权限</span><span class="sxs-lookup"><span data-stu-id="acaec-116">Permissions</span></span>  
 <span data-ttu-id="acaec-117">若要访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机实例的日志文件，你需要有 securityadmin 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="acaec-117">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="acaec-118">若要访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脱机实例的日志文件，不仅必须具有 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空间的读取权限，还必须具有存储日志文件的文件夹的读取权限。</span><span class="sxs-lookup"><span data-stu-id="acaec-118">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="acaec-119">有关详细信息，请参阅 [查看脱机日志文件](view-offline-log-files.md)主题的“安全性”部分。</span><span class="sxs-lookup"><span data-stu-id="acaec-119">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
### <a name="security"></a><span data-ttu-id="acaec-120">安全性</span><span class="sxs-lookup"><span data-stu-id="acaec-120">Security</span></span>  
 <span data-ttu-id="acaec-121">要求具有 securityadmin 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="acaec-121">Requires membership in the securityadmin fixed server role.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="acaec-122">查看日志文件</span><span class="sxs-lookup"><span data-stu-id="acaec-122">View Log Files</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a><span data-ttu-id="acaec-123">查看与常规 SQL Server 活动相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-123">To view logs that are related to general SQL Server activity</span></span>  
  
1.  <span data-ttu-id="acaec-124">在对象资源管理器中，展开 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-124">In Object Explorer, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="acaec-125">执行下列任一操作：</span><span class="sxs-lookup"><span data-stu-id="acaec-125">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="acaec-126">右键单击“SQL Server 日志”，指向“查看”，然后单击“SQL Server 日志”或“SQL Server 和 Windows 日志”。</span><span class="sxs-lookup"><span data-stu-id="acaec-126">Right-click **SQL Server Logs**, point to **View**, and then click either **SQL Server Log** or **SQL Server and Windows Log**.</span></span>  
  
    -   <span data-ttu-id="acaec-127">展开“SQL Server 日志”，右键单击任何日志文件，然后单击“查看 SQL Server 日志”。</span><span class="sxs-lookup"><span data-stu-id="acaec-127">Expand **SQL Server Logs**, right-click any log file, and then click **View SQL Server Log**.</span></span> <span data-ttu-id="acaec-128">还可以双击任何日志文件。</span><span class="sxs-lookup"><span data-stu-id="acaec-128">You can also double-click any log file.</span></span>  
  
     <span data-ttu-id="acaec-129">这些日志包括 **“数据库邮件”** 、 **“SQL Server”** 、 **“SQL Server 代理”** 和 **“Windows NT”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-129">The logs include **Database Mail**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a><span data-ttu-id="acaec-130">查看与作业相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-130">To view logs that are related to jobs</span></span>  
  
-   <span data-ttu-id="acaec-131">在对象资源管理器中，展开“SQL Server 代理”，右键单击“作业”，然后单击“查看历史记录”。</span><span class="sxs-lookup"><span data-stu-id="acaec-131">In Object Explorer, expand **SQL Server Agent**, right-click **Jobs**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="acaec-132">这些日志包括 **“数据库邮件”** 、 **“作业历史记录”** 和 **“SQL Server 代理”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-132">The logs include **Database Mail**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a><span data-ttu-id="acaec-133">查看与维护计划相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-133">To view logs that are related to maintenance plans</span></span>  
  
-   <span data-ttu-id="acaec-134">在对象资源管理器中，展开“管理”，右键单击“维护计划”，然后单击“查看历史记录”。</span><span class="sxs-lookup"><span data-stu-id="acaec-134">In Object Explorer, expand **Management**, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="acaec-135">这些日志包括 **“数据库邮件”** 、 **“作业历史记录”** 、 **“维护计划”** 、 **“远程维护计划”** 和 **“SQL Server 代理”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-135">The logs include **Database Mail**, **Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a><span data-ttu-id="acaec-136">查看与数据收集相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-136">To view logs that are related to Data Collection</span></span>  
  
-   <span data-ttu-id="acaec-137">在对象资源管理器中，展开“管理”，右键单击“数据收集”，然后单击“查看日志”。</span><span class="sxs-lookup"><span data-stu-id="acaec-137">In Object Explorer, expand **Management**, right-click **Data Collection**, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="acaec-138">这些日志包括 **“数据收集”** 、 **“作业历史记录”** 和 **“SQL Server 代理”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-138">The logs include **Data Collection**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a><span data-ttu-id="acaec-139">查看与数据库邮件相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-139">To view logs that are related to Database Mail</span></span>  
  
-   <span data-ttu-id="acaec-140">在对象资源管理器中，展开“管理”，右键单击“数据库邮件”，然后单击“查看数据库邮件日志”。</span><span class="sxs-lookup"><span data-stu-id="acaec-140">In Object Explorer, expand **Management**, right-click **Database Mail**, and then click **View Database Mail Log**.</span></span>  
  
     <span data-ttu-id="acaec-141">这些日志包括 **“数据库邮件”** 、“作业历史记录”、 **“维护计划”** 、 **“远程维护计划”** 、 **“SQL Server”** 、 **“SQL Server 代理”** 和 **“Windows NT”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-141">The logs include **Database Mail, Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="acaec-142">查看与审核集合相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-142">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="acaec-143">在对象资源管理器中，依次展开“安全性”和“审核”，右键单击一个审核，然后单击“查看审核日志”。</span><span class="sxs-lookup"><span data-stu-id="acaec-143">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="acaec-144">这些日志包括 **“审核集合”** 和 **“Windows NT”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-144">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="acaec-145">查看与审核集合相关的日志</span><span class="sxs-lookup"><span data-stu-id="acaec-145">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="acaec-146">在对象资源管理器中，依次展开“安全性”和“审核”，右键单击一个审核，然后单击“查看审核日志”。</span><span class="sxs-lookup"><span data-stu-id="acaec-146">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="acaec-147">这些日志包括 **“审核集合”** 和 **“Windows NT”** 。</span><span class="sxs-lookup"><span data-stu-id="acaec-147">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acaec-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acaec-148">See Also</span></span>  
 <span data-ttu-id="acaec-149">[日志文件查看器](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="acaec-149">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="acaec-150">[SQL Server Audit（数据库引擎）](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="acaec-150">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="acaec-151">查看脱机日志文件</span><span class="sxs-lookup"><span data-stu-id="acaec-151">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
