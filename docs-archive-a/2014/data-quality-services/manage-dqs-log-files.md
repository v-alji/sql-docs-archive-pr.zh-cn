---
title: 管理 DQS 日志文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ca85772b8cc8aca41b75ad05d028bc444f280378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590381"
---
# <a name="manage-dqs-log-files"></a><span data-ttu-id="c231d-102">管理 DQS 日志文件</span><span class="sxs-lookup"><span data-stu-id="c231d-102">Manage DQS Log Files</span></span>
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] <span data-ttu-id="c231d-103">(DQS) 日志文件可帮助您诊断和解决与 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]和 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]有关的问题。</span><span class="sxs-lookup"><span data-stu-id="c231d-103">(DQS) log files help you in diagnosing and troubleshooting issue with [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="c231d-104">为 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]和 [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]生成单独的日志文件。</span><span class="sxs-lookup"><span data-stu-id="c231d-104">Separate log files are generated for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
 <span data-ttu-id="c231d-105">您可以使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 为 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 功能和模块配置日志严重性设置。</span><span class="sxs-lookup"><span data-stu-id="c231d-105">You can use [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] to configure the log severity setting for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] features and modules.</span></span> <span data-ttu-id="c231d-106">或者，您还可以通过在 DQS_MAIN 数据库中手动更改 DQS 日志配置设置以及在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 计算机上更改 XML 文件，为 DQS 日志文件配置其他一些（高级）设置。</span><span class="sxs-lookup"><span data-stu-id="c231d-106">Additionally, you can also configure some other (advanced) settings for the DQS log files by manually changing the DQS log configuration settings in the DQS_MAIN database and an XML file on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer.</span></span>  
  
##  <a name="data-quality-server-log-file"></a><a name="DQSServer"></a><span data-ttu-id="c231d-107">数据质量服务器日志文件</span><span class="sxs-lookup"><span data-stu-id="c231d-107">Data Quality Server Log File</span></span>  
 <span data-ttu-id="c231d-108">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志文件 DQServerLog.DQS_MAIN.log 包含在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上运行的活动的日志。</span><span class="sxs-lookup"><span data-stu-id="c231d-108">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, DQServerLog.DQS_MAIN.log, includes logs of activities that are run on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="c231d-109">如果您安装了 SQL Server 的默认实例，则 DQServerLog.DQS_MAIN.log 文件将位于 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log 下。</span><span class="sxs-lookup"><span data-stu-id="c231d-109">If you installed the default instance of SQL Server, the DQServerLog.DQS_MAIN.log file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log.</span></span> <span data-ttu-id="c231d-110">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志文件包含以下信息部分，每个部分之间用竖线 (|) 分隔：</span><span class="sxs-lookup"><span data-stu-id="c231d-110">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file contains the following pieces of information, each delimited by a pipe (|):</span></span>  
  
-   <span data-ttu-id="c231d-111">日期和时间</span><span class="sxs-lookup"><span data-stu-id="c231d-111">Date and time</span></span>  
  
-   <span data-ttu-id="c231d-112">线程名</span><span class="sxs-lookup"><span data-stu-id="c231d-112">Thread name</span></span>  
  
-   <span data-ttu-id="c231d-113">线程 ID</span><span class="sxs-lookup"><span data-stu-id="c231d-113">Thread ID</span></span>  
  
-   <span data-ttu-id="c231d-114">日志严重性（FATAL、ERROR、WARN、INFO 和 DEBUG）</span><span class="sxs-lookup"><span data-stu-id="c231d-114">Log severity (FATAL, ERROR, WARN, INFO, and DEBUG)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c231d-115">DEBUG 日志记录严重程度与“详细”相同。</span><span class="sxs-lookup"><span data-stu-id="c231d-115">The DEBUG logging severity is same as Verbose.</span></span>  
  
-   <span data-ttu-id="c231d-116">UID（内部 DQS 基础结构 ID）</span><span class="sxs-lookup"><span data-stu-id="c231d-116">UID (internal DQS infrastructure ID)</span></span>  
  
-   <span data-ttu-id="c231d-117">命名空间</span><span class="sxs-lookup"><span data-stu-id="c231d-117">Namespace</span></span>  
  
-   <span data-ttu-id="c231d-118">类和方法</span><span class="sxs-lookup"><span data-stu-id="c231d-118">Class and method</span></span>  
  
-   <span data-ttu-id="c231d-119">Message</span><span class="sxs-lookup"><span data-stu-id="c231d-119">Message</span></span>  
  
 <span data-ttu-id="c231d-120">除了上述信息之外，日志文件还显示与应用程序版本、计算机名称、用户名和操作系统有关的信息。</span><span class="sxs-lookup"><span data-stu-id="c231d-120">Along with these, the log file also displays information about the application version, computer name, user name, and operating system.</span></span>  
  
 <span data-ttu-id="c231d-121">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志文件中的示例条目如下：</span><span class="sxs-lookup"><span data-stu-id="c231d-121">A sample entry in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file looks like the following:</span></span>  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 <span data-ttu-id="c231d-122">DQServerLog.DQS_MAIN.log 文件是一个滚动文件，一旦现有日志文件超出在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志配置设置中指定的滚动文件大小限制，就会创建一个新的日志文件。</span><span class="sxs-lookup"><span data-stu-id="c231d-122">The DQServerLog.DQS_MAIN.log file is a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="c231d-123">有关详细信息，请参阅 [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="c231d-123">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="data-quality-client-log-file"></a><a name="DQSClient"></a><span data-ttu-id="c231d-124">Data Quality Client 日志文件</span><span class="sxs-lookup"><span data-stu-id="c231d-124">Data Quality Client Log File</span></span>  
 <span data-ttu-id="c231d-125">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志文件 DQClientLog.log 包括客户端日志。</span><span class="sxs-lookup"><span data-stu-id="c231d-125">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file, DQClientLog.log, includes the client side logs.</span></span> <span data-ttu-id="c231d-126">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志文件位于 %APPDATA%\SSDQS\Log。</span><span class="sxs-lookup"><span data-stu-id="c231d-126">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="c231d-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志文件包含与服务器日志文件中相似的一组信息，但前者针对的是客户端。</span><span class="sxs-lookup"><span data-stu-id="c231d-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file contains similar set of information as in the server log file, but for the client side.</span></span>  
  
 <span data-ttu-id="c231d-128">与 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志文件一样， [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志文件也是一个滚动文件，一旦现有日志文件超出在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志配置设置中指定的滚动文件大小限制，就会创建一个新的日志文件。</span><span class="sxs-lookup"><span data-stu-id="c231d-128">As with the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is also a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log configuration settings.</span></span> <span data-ttu-id="c231d-129">有关详细信息，请参阅 [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="c231d-129">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="dqs-cleansing-component-log-file"></a><a name="DQSCleansing"></a><span data-ttu-id="c231d-130">DQS 清理组件日志文件</span><span class="sxs-lookup"><span data-stu-id="c231d-130">DQS Cleansing Component Log File</span></span>  
 <span data-ttu-id="c231d-131">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 日志文件 DQSSSISLog.log 包括使用 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]执行的活动的日志。</span><span class="sxs-lookup"><span data-stu-id="c231d-131">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file, DQSSSISLog.log, includes logs of activities performed using the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="c231d-132">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 组件日志文件位于 %APPDATA%\SSDQS\Log。</span><span class="sxs-lookup"><span data-stu-id="c231d-132">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] component log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="c231d-133">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 日志文件包含与服务器日志文件中相似的一组信息，但前者针对的是 [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c231d-133">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file contains similar set of information as in the server log file, but for the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
##  <a name="related-tasks"></a><a name="RT"></a> <span data-ttu-id="c231d-134">相关任务</span><span class="sxs-lookup"><span data-stu-id="c231d-134">Related Tasks</span></span>  
  
|<span data-ttu-id="c231d-135">任务说明</span><span class="sxs-lookup"><span data-stu-id="c231d-135">Task Description</span></span>|<span data-ttu-id="c231d-136">主题</span><span class="sxs-lookup"><span data-stu-id="c231d-136">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c231d-137">介绍如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]为 DQS 日志文件配置日志严重性设置。</span><span class="sxs-lookup"><span data-stu-id="c231d-137">Describes how to configure log severity settings for DQS log files using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="c231d-138">为 DQS 日志文件配置严重级别</span><span class="sxs-lookup"><span data-stu-id="c231d-138">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|<span data-ttu-id="c231d-139">介绍如何为 DQS 日志文件手动配置高级设置。</span><span class="sxs-lookup"><span data-stu-id="c231d-139">Describes how to manually configure advanced settings for DQS log files.</span></span>|[<span data-ttu-id="c231d-140">为 DQS 日志文件配置高级设置</span><span class="sxs-lookup"><span data-stu-id="c231d-140">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c231d-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c231d-141">See Also</span></span>  
 [<span data-ttu-id="c231d-142">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="c231d-142">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
