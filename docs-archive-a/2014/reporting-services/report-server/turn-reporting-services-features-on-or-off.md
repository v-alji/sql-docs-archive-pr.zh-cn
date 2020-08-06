---
title: 打开或关闭 Reporting Services 功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f56f9984b5b02431db23b782652e5575af557bdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586319"
---
# <a name="turn-reporting-services-features-on-or-off"></a><span data-ttu-id="b4438-102">打开或关闭 Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="b4438-102">Turn Reporting Services Features On or Off</span></span>
  <span data-ttu-id="b4438-103">您可以关闭不用作锁定策略一部分的报表服务器功能，以减小生产报表服务器的攻击面。</span><span class="sxs-lookup"><span data-stu-id="b4438-103">You can turn off report server features that you do not use as part of a lockdown strategy for reducing the attack surface of a production report server.</span></span> <span data-ttu-id="b4438-104">在大多数情况下，需要同时运行各种 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能才能使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="b4438-104">In most cases, you will want to run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features concurrently to use all of the functionality provided in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="b4438-105">但是根据所用的部署模型，您可以禁用不需要的功能。</span><span class="sxs-lookup"><span data-stu-id="b4438-105">However, depending on your deployment model, you can disable the features that you do not require.</span></span> <span data-ttu-id="b4438-106">例如，如果所有报表处理均已配置为预定操作，则可以只启用后台处理。</span><span class="sxs-lookup"><span data-stu-id="b4438-106">For example, you can enable only the background processing if all report processing is configured as scheduled operations.</span></span> <span data-ttu-id="b4438-107">同样，如果您只需要交互式的按需报表，则可以只运行报表服务器 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="b4438-107">Similarly, you can run just the Report Server Web service if you only want interactive, on-demand reporting.</span></span>  
  
 <span data-ttu-id="b4438-108">本主题中的过程将为您演示如何关闭本机模式 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="b4438-108">The procedures in this topic show you how to turn off native mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="b4438-109">可以不同的方式配置这些功能，如直接编辑 `RsReportServer.config` 文件或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中基于策略的管理的“Reporting Services 的外围应用配置”方面。</span><span class="sxs-lookup"><span data-stu-id="b4438-109">Features can be configured in different ways, such as by editing the `RsReportServer.config` file directly or by using the **Surface Area Configuration for Reporting Services** facet of Policy-Based Management in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b4438-110">使用以下链接可以找到说明如何打开或关闭相应功能的步骤：</span><span class="sxs-lookup"><span data-stu-id="b4438-110">Use the links to locate the procedure or procedures that explain how to turn a feature on or off:</span></span>  
  
-   [<span data-ttu-id="b4438-111">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b4438-111">Report Server Web service</span></span>](#RSWebSvc)  
  
-   [<span data-ttu-id="b4438-112">预定的事件和处理</span><span class="sxs-lookup"><span data-stu-id="b4438-112">Scheduled events and processing</span></span>](#Sched)  
  
-   [<span data-ttu-id="b4438-113">报表管理器</span><span class="sxs-lookup"><span data-stu-id="b4438-113">Report Manager</span></span>](#ReportManager)  
  
-   [<span data-ttu-id="b4438-114">报表生成器</span><span class="sxs-lookup"><span data-stu-id="b4438-114">Report Builder</span></span>](#ReportBuilder)  
  
-   [<span data-ttu-id="b4438-115">报表数据源的 Windows 集成安全性</span><span class="sxs-lookup"><span data-stu-id="b4438-115">Windows Integrated security for report data sources</span></span>](#WinIntSec)  
  
##  <a name="report-server-web-service"></a><a name="RSWebSvc"></a><span data-ttu-id="b4438-116">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b4438-116">Report Server Web Service</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a><span data-ttu-id="b4438-117">通过编辑配置打开或关闭报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b4438-117">To turn on or off the Report Server Web service by editing configuration</span></span>  
  
1.  <span data-ttu-id="b4438-118">在文本编辑器中打开 `RsReportServer.config` 文件。</span><span class="sxs-lookup"><span data-stu-id="b4438-118">Open the `RsReportServer.config` file in a text editor.</span></span> <span data-ttu-id="b4438-119">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[修改 Reporting Services 配置文件 (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="b4438-119">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="b4438-120">若要打开报表服务器 Web 服务，请将 `IsWebServiceEnabled` 设置为 `true`：</span><span class="sxs-lookup"><span data-stu-id="b4438-120">To turn on the Report Server Web service, set `IsWebServiceEnabled` to `true`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  <span data-ttu-id="b4438-121">若要关闭报表服务器 Web 服务，请将 `IsWebServiceEnabled` 设置为 `false`：</span><span class="sxs-lookup"><span data-stu-id="b4438-121">To turn off the Report Server Web service, set `IsWebServiceEnabled` to `false`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  <span data-ttu-id="b4438-122">保存所做的更改，然后关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="b4438-122">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a><span data-ttu-id="b4438-123">使用 SQL Server Management Studio 打开或关闭报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b4438-123">To turn on or off the Report Server Web service by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b4438-124">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后连接到要配置的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b4438-124">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="b4438-125">在对象资源管理器中，右键单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 节点，指向 "**策略**"，然后单击 "**方面**"。</span><span class="sxs-lookup"><span data-stu-id="b4438-125">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="b4438-126">在 **“方面”** 列表中，选择 **Reporting Services 的外围应用配置器**。</span><span class="sxs-lookup"><span data-stu-id="b4438-126">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="b4438-127">在 **“方面属性”** 下：</span><span class="sxs-lookup"><span data-stu-id="b4438-127">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="b4438-128">若要打开报表服务器 Web 服务，请将**WebServiceAndHTTPAccessEnabled**设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b4438-128">To turn on the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="b4438-129">若要关闭报表服务器 Web 服务，请将**WebServiceAndHTTPAccessEnabled**设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="b4438-129">To turn off the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="scheduled-events-and-delivery"></a><a name="Sched"></a><span data-ttu-id="b4438-130">Scheduled Events 和传递</span><span class="sxs-lookup"><span data-stu-id="b4438-130">Scheduled Events and Delivery</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a><span data-ttu-id="b4438-131">通过编辑配置打开或关闭预定的事件和传递</span><span class="sxs-lookup"><span data-stu-id="b4438-131">To turn on or off scheduled events and delivery by editing configuration</span></span>  
  
1.  <span data-ttu-id="b4438-132">在文本编辑器中打开 RsReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="b4438-132">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="b4438-133">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[修改 Reporting Services 配置文件 (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="b4438-133">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="b4438-134">若要打开预定的报表处理和传递，请将 `IsSchedulingService`、`IsNotificationService` 和 `IsEventService` 设置为 `true`：</span><span class="sxs-lookup"><span data-stu-id="b4438-134">To turn on scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `true`:</span></span>  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  <span data-ttu-id="b4438-135">若要关闭预定的报表处理和传递，请将 `IsSchedulingService`、`IsNotificationService` 和 `IsEventService` 设置为 `false`：</span><span class="sxs-lookup"><span data-stu-id="b4438-135">To turn off scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `false`:</span></span>  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  <span data-ttu-id="b4438-136">保存所做的更改，然后关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="b4438-136">Save your changes and then close the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4438-137">不能完全关闭后台处理，因为它提供执行服务器操作所需的数据库维护功能。</span><span class="sxs-lookup"><span data-stu-id="b4438-137">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a><span data-ttu-id="b4438-138">使用 SQL Server Management Studio 打开或关闭预定的事件和传递</span><span class="sxs-lookup"><span data-stu-id="b4438-138">To turn on or off scheduled events and delivery by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b4438-139">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后连接到要配置的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b4438-139">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="b4438-140">在对象资源管理器中，右键单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 节点，指向 "**策略**"，然后单击 "**方面**"。</span><span class="sxs-lookup"><span data-stu-id="b4438-140">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="b4438-141">在 **“方面”** 列表中，选择 **Reporting Services 的外围应用配置器**。</span><span class="sxs-lookup"><span data-stu-id="b4438-141">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="b4438-142">在 **“方面属性”** 下：</span><span class="sxs-lookup"><span data-stu-id="b4438-142">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="b4438-143">若要启用预定的事件和传递，请将**ScheduleEventsAndReportDeliveryEnabled**设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b4438-143">To turn on scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="b4438-144">若要关闭预定的事件和传递，请将**ScheduleEventsAndReportDeliveryEnabled**设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="b4438-144">To turn off scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="b4438-145">不能完全关闭后台处理，因为它提供执行服务器操作所需的数据库维护功能。</span><span class="sxs-lookup"><span data-stu-id="b4438-145">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
##  <a name="report-manager"></a><a name="ReportManager"></a><span data-ttu-id="b4438-146">报表管理器</span><span class="sxs-lookup"><span data-stu-id="b4438-146">Report Manager</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a><span data-ttu-id="b4438-147">通过编辑配置打开或关闭报表管理器</span><span class="sxs-lookup"><span data-stu-id="b4438-147">To turn on or off Report Manager by editing configuration</span></span>  
  
1.  <span data-ttu-id="b4438-148">在文本编辑器中打开 RsReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="b4438-148">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="b4438-149">有关说明，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[修改 Reporting Services 配置文件 (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="b4438-149">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="b4438-150">若要打开报表管理器，请将 `IsReportManagerEnabled` 设置为 `true`：</span><span class="sxs-lookup"><span data-stu-id="b4438-150">To turn on Report Manager, set `IsReportManagerEnabled` to `true`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  <span data-ttu-id="b4438-151">若要关闭报表管理器，请将 `IsReportManagerEnabled` 设置为 `false`：</span><span class="sxs-lookup"><span data-stu-id="b4438-151">To turn off Report Manager, set `IsReportManagerEnabled` to `false`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  <span data-ttu-id="b4438-152">保存所做的更改，然后关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="b4438-152">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a><span data-ttu-id="b4438-153">使用 SQL Server Management Studio 打开或关闭报表管理器</span><span class="sxs-lookup"><span data-stu-id="b4438-153">To turn on or off Report Manager by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b4438-154">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后连接到要配置的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b4438-154">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="b4438-155">在“对象资源管理器”\*\*\*\* 中右键单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 节点，指向“策略”\*\*\*\*，然后单击“方面”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4438-155">In **Object Explorer**, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="b4438-156">在 **“方面”** 列表中，选择 **Reporting Services 的外围应用配置器**。</span><span class="sxs-lookup"><span data-stu-id="b4438-156">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="b4438-157">在 **“方面属性”** 下：</span><span class="sxs-lookup"><span data-stu-id="b4438-157">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="b4438-158">若要启用报表管理器，请将**ReportManagerEnabled**设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b4438-158">To turn on Report Manager, set **ReportManagerEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="b4438-159">若要关闭报表管理器，请将**ReportManagerEnabled**设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="b4438-159">To turn off Report Manager, set **ReportManagerEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="report-builder"></a><a name="ReportBuilder"></a> <span data-ttu-id="b4438-160">报表生成器</span><span class="sxs-lookup"><span data-stu-id="b4438-160">Report Builder</span></span>  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a><span data-ttu-id="b4438-161">使用 SQL Server Management Studio 打开或关闭报表生成器</span><span class="sxs-lookup"><span data-stu-id="b4438-161">To turn on or off Report Builder by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b4438-162">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后连接到要配置的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b4438-162">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="b4438-163">在对象资源管理器中右键单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 节点，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4438-163">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b4438-164">在 **“服务器属性”** 对话框中，单击 **“选择页”** 下的 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="b4438-164">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="b4438-165">若要打开报表生成器，请选择 **“启用特别报告执行”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b4438-165">To turn on Report Builder, select the **Enable ad hoc report executions** option.</span></span>  
  
    -   <span data-ttu-id="b4438-166">若要关闭报表生成器，请取消选择 **“启用特别报告执行”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b4438-166">To turn off Report Builder, unselect the **Enable ad hoc report executions** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="windows-integrated-security"></a><a name="WinIntSec"></a> <span data-ttu-id="b4438-167">Windows 集成安全性</span><span class="sxs-lookup"><span data-stu-id="b4438-167">Windows Integrated Security</span></span>  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a><span data-ttu-id="b4438-168">使用 SQL Server Management Studio 打开或关闭 Windows 集成安全性</span><span class="sxs-lookup"><span data-stu-id="b4438-168">To turn on or off Windows Integrated security by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b4438-169">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后连接到要配置的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b4438-169">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="b4438-170">在对象资源管理器中右键单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 节点，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4438-170">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b4438-171">在 **“服务器属性”** 对话框中，单击 **“选择页”** 下的 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="b4438-171">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="b4438-172">若要打开 Windows 集成安全性，请选择 **“对报表数据源启用 Windows 集成安全性”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b4438-172">To turn on Windows Integrated security, select the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
    -   <span data-ttu-id="b4438-173">若要关闭 Windows 集成安全性，请取消选择 **“对报表数据源启用 Windows 集成安全性”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b4438-173">To turn off Windows integrated security, unselect the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4438-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4438-174">See Also</span></span>  
 [<span data-ttu-id="b4438-175">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="b4438-175">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
