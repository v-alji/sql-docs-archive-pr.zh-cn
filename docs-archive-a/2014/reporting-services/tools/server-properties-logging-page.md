---
title: 服务器属性（“日志记录”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587711"
---
# <a name="server-properties-logging-page"></a><span data-ttu-id="b15f0-102">服务器属性（“日志记录”页）</span><span class="sxs-lookup"><span data-stu-id="b15f0-102">Server Properties (Logging Page)</span></span>
  <span data-ttu-id="b15f0-103">使用此页可以对报表服务器收集的报表执行数据设置限制。</span><span class="sxs-lookup"><span data-stu-id="b15f0-103">Use this page to set limits on the report execution data that is collected by a report server.</span></span> <span data-ttu-id="b15f0-104">执行数据存储在报表服务器数据库内部。</span><span class="sxs-lookup"><span data-stu-id="b15f0-104">Execution data is stored internally in the report server database.</span></span> <span data-ttu-id="b15f0-105">可以跟踪在本机模式或 SharePoint 集成模式下运行的报表服务器的报表活动。</span><span class="sxs-lookup"><span data-stu-id="b15f0-105">You can track report activity for report server that runs in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="b15f0-106">如果报表服务器是扩展部署的一部分，则报表执行日志会将有关整个部署内所有报表活动的记录保存到一个日志文件中。</span><span class="sxs-lookup"><span data-stu-id="b15f0-106">If the report server is part of a scale-out deployment, the report execution log maintains a record of all report activity for the entire deployment in a single log file.</span></span>  
  
 <span data-ttu-id="b15f0-107">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到 Report Server，右键单击 Report Server 名称，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="b15f0-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="b15f0-108">单击 **“日志记录”** 将此页打开。</span><span class="sxs-lookup"><span data-stu-id="b15f0-108">Click **Logging** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b15f0-109">选项</span><span class="sxs-lookup"><span data-stu-id="b15f0-109">Options</span></span>  
 <span data-ttu-id="b15f0-110">**启用报表执行日志记录**</span><span class="sxs-lookup"><span data-stu-id="b15f0-110">**Enable report execution logging**</span></span>  
 <span data-ttu-id="b15f0-111">单击此选项可创建和存储有关服务器上报表活动的信息。</span><span class="sxs-lookup"><span data-stu-id="b15f0-111">Click to create and store information about report activity on the server.</span></span> <span data-ttu-id="b15f0-112">如果启用此选项，则报表服务器将跟踪已使用的报表、报表的处理频率、已执行的报表操作的类型、输出格式和运行报表的人员。</span><span class="sxs-lookup"><span data-stu-id="b15f0-112">If this option is enabled, the report server will track which reports are used, the frequency of report processing, the type of report operation that was performed, the output format, and who ran the report.</span></span> <span data-ttu-id="b15f0-113">有关日志中捕获的其他数据点的详细信息，请参阅[报表服务器执行日志和 ExecutionLog3 视图](../report-server/report-server-executionlog-and-the-executionlog3-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b15f0-113">For more information about additional data points that are captured in the log, see [Report Server Execution Log and the ExecutionLog3 View](../report-server/report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
 <span data-ttu-id="b15f0-114">**删除保留时间超过以下天数的日志条目**</span><span class="sxs-lookup"><span data-stu-id="b15f0-114">**Remove log entries older than this number of days**</span></span>  
 <span data-ttu-id="b15f0-115">指定天数，报表执行日志中超过此天数的日志条目将被切除。</span><span class="sxs-lookup"><span data-stu-id="b15f0-115">Specify the number of days after which log entries will be trimmed from the report execution log.</span></span> <span data-ttu-id="b15f0-116">默认值为 60 天。</span><span class="sxs-lookup"><span data-stu-id="b15f0-116">The default value is 60 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15f0-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b15f0-117">See Also</span></span>  
 <span data-ttu-id="b15f0-118">[设置报表服务器属性 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b15f0-118">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="b15f0-119">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b15f0-119">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="b15f0-120">[Reporting Services 日志文件和来源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="b15f0-120">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="b15f0-121">[Management Studio F1 帮助中的报表服务器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b15f0-121">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="b15f0-122">报告服务器执行日志和 ExecutionLog3 视图</span><span class="sxs-lookup"><span data-stu-id="b15f0-122">Report Server Execution Log and the ExecutionLog3 View</span></span>](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
