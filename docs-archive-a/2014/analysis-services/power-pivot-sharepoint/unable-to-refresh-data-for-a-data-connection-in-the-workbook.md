---
title: 无法刷新工作簿中用于数据连接的数据。 请重试，或与系统管理员联系。 以下连接无法刷新： PowerPivot 数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c25c2597bbc7aa16fb8b66d4ffddbf0df14515e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691924"
---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook-try-again-or-contact-your-system-administrator-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="421f2-104">无法刷新工作簿中用于数据连接的数据。</span><span class="sxs-lookup"><span data-stu-id="421f2-104">Unable to refresh data for a data connection in the workbook.</span></span> <span data-ttu-id="421f2-105">请重试，或与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="421f2-105">Try again or contact your system administrator.</span></span> <span data-ttu-id="421f2-106">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="421f2-106">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="421f2-107">对于包含 PowerPivot 数据的 Excel 工作簿，如果 Excel Services 提交对某一 PowerPivot 服务器的连接请求并且该请求失败，则会返回此错误。</span><span class="sxs-lookup"><span data-stu-id="421f2-107">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it submits a connection request to a PowerPivot server and the request fails.</span></span>  
  
## <a name="details"></a><span data-ttu-id="421f2-108">详细信息</span><span class="sxs-lookup"><span data-stu-id="421f2-108">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="421f2-109">适用于：</span><span class="sxs-lookup"><span data-stu-id="421f2-109">Applies to:</span></span>|<span data-ttu-id="421f2-110">PowerPivot for SharePoint 安装</span><span class="sxs-lookup"><span data-stu-id="421f2-110">PowerPivot for SharePoint installation</span></span>|  
|<span data-ttu-id="421f2-111">产品版本</span><span class="sxs-lookup"><span data-stu-id="421f2-111">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="421f2-112">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="421f2-112">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="421f2-113">原因</span><span class="sxs-lookup"><span data-stu-id="421f2-113">Cause</span></span>|<span data-ttu-id="421f2-114">请参阅下文。</span><span class="sxs-lookup"><span data-stu-id="421f2-114">See below.</span></span>|  
|<span data-ttu-id="421f2-115">消息正文</span><span class="sxs-lookup"><span data-stu-id="421f2-115">Message Text</span></span>|<span data-ttu-id="421f2-116">无法刷新工作簿中用于数据连接的数据。</span><span class="sxs-lookup"><span data-stu-id="421f2-116">Unable to refresh data for a data connection in the workbook.</span></span> <span data-ttu-id="421f2-117">请重试，或与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="421f2-117">Try again or contact your system administrator.</span></span> <span data-ttu-id="421f2-118">以下连接无法刷新：PowerPivot 数据</span><span class="sxs-lookup"><span data-stu-id="421f2-118">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation-and-resolution"></a><span data-ttu-id="421f2-119">说明和解决方法</span><span class="sxs-lookup"><span data-stu-id="421f2-119">Explanation and Resolution</span></span>  
 <span data-ttu-id="421f2-120">Excel Services 无法连接到或加载 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="421f2-120">Excel Services cannot connect to or load the PowerPivot data.</span></span> <span data-ttu-id="421f2-121">在下列情况下会出现此错误：</span><span class="sxs-lookup"><span data-stu-id="421f2-121">Conditions that cause this error to occur include the following:</span></span>  
  
 <span data-ttu-id="421f2-122">**应用场景 1：服务未启动**</span><span class="sxs-lookup"><span data-stu-id="421f2-122">**Scenario 1: Service is not started**</span></span>  
  
 <span data-ttu-id="421f2-123">SQL Server Analysis Services (PowerPivot) 实例未启动。</span><span class="sxs-lookup"><span data-stu-id="421f2-123">The SQL Server Analysis Services (PowerPivot) instance is not started.</span></span> <span data-ttu-id="421f2-124">到期的密码将导致服务停止运行。</span><span class="sxs-lookup"><span data-stu-id="421f2-124">An expired password will cause the service to stop running.</span></span> <span data-ttu-id="421f2-125">有关更改密码的详细信息，请参阅[配置 PowerPivot 服务帐户](configure-power-pivot-service-accounts.md)和[启动或停止 PowerPivot for SharePoint 服务器](start-or-stop-a-power-pivot-for-sharepoint-server.md)。</span><span class="sxs-lookup"><span data-stu-id="421f2-125">For more information about changing the password, see [Configure PowerPivot Service Accounts](configure-power-pivot-service-accounts.md) and [Start or Stop a PowerPivot for SharePoint Server](start-or-stop-a-power-pivot-for-sharepoint-server.md).</span></span>  
  
 <span data-ttu-id="421f2-126">**应用程序 2a：在服务器中打开早期版本的工作簿**</span><span class="sxs-lookup"><span data-stu-id="421f2-126">**Scenario 2a: Opening an earlier version workbook n the server**</span></span>  
  
 <span data-ttu-id="421f2-127">您正尝试打开的工作簿可能是在 SQL Server 2008 R2 版本的 PowerPivot for Excel 中创建的。</span><span class="sxs-lookup"><span data-stu-id="421f2-127">The workbook you are attempting to open might have been created in the SQL Server 2008 R2 version of PowerPivot for Excel.</span></span> <span data-ttu-id="421f2-128">数据连接字符串中指定的 Analysis Services 数据访问接口很可能在要处理请求的计算机上不存在。</span><span class="sxs-lookup"><span data-stu-id="421f2-128">Most likely, the Analysis Services data provider that is specified in the data connection string is not present on the computer that is handling the request.</span></span>  
  
 <span data-ttu-id="421f2-129">如果是这种情况，你将在 ULS 日志中找到此消息： "刷新工作簿 ' ' 中的 ' PowerPivot 数据 ' 失败" \<URL to workbook> ，后跟 "无法获取连接"。</span><span class="sxs-lookup"><span data-stu-id="421f2-129">If this is the case, you will find this message in the ULS log: "Refresh failed for 'PowerPivot Data' in the workbook '\<URL to workbook>'", followed by "Unable to get a connection".</span></span>  
  
 <span data-ttu-id="421f2-130">若要确定工作簿的版本，请在 Excel 中打开它，然后查看连接字符串中指定的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="421f2-130">To determine the version of the workbook, open it in Excel and check which data provider is specified in the connection string.</span></span> <span data-ttu-id="421f2-131">SQL Server 2008 R2 工作簿将 MSOLAP.4 用作其数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="421f2-131">A SQL Server 2008 R2 workbook uses MSOLAP.4 as its data provider.</span></span>  
  
 <span data-ttu-id="421f2-132">若要解决此问题，可以升级工作簿。</span><span class="sxs-lookup"><span data-stu-id="421f2-132">To work around this issue, you can upgrade the workbook.</span></span> <span data-ttu-id="421f2-133">或者，可以在运行 PowerPivot for SharePoint 或 Excel Services 的物理计算机上安装 SQL Server 2008 R2 版本的 Analysis Services 中的客户端库：</span><span class="sxs-lookup"><span data-stu-id="421f2-133">Alternatively, you can install client libraries from the SQL Server 2008 R2 version of Analysis Services on the physical computers running PowerPivot for SharePoint or Excel Services:</span></span>  
  
 [<span data-ttu-id="421f2-134">在 SharePoint 服务器上安装 Analysis Services OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="421f2-134">Install the Analysis Services OLE DB Provider on SharePoint Servers</span></span>](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 <span data-ttu-id="421f2-135">**应用场景 2b：Excel Services 正在具有错误版本的客户端库的应用程序服务器上运行**</span><span class="sxs-lookup"><span data-stu-id="421f2-135">**Scenario 2b: Excel Services is running on an application server that has the wrong version of the client libraries**</span></span>  
  
 <span data-ttu-id="421f2-136">默认情况下，SharePoint Server 2010 会在运行 Excel Services 的应用程序服务器上安装 SQL Server 2008 版本的 Analysis Services OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="421f2-136">By default, SharePoint Server 2010 installs the SQL Server 2008 version of the Analysis Services OLE DB provider on application servers that run Excel Services.</span></span> <span data-ttu-id="421f2-137">在支持 PowerPivot 数据访问的场中，运行请求 PowerPivot 数据的应用程序（如 Excel Services 和 PowerPivot for SharePoint）的所有物理服务器都必须使用更高版本的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="421f2-137">In a farm that supports PowerPivot data access, all physical servers running applications that request PowerPivot data, such as Excel Services and PowerPivot for SharePoint, must use a later version of the data provider.</span></span>  
  
 <span data-ttu-id="421f2-138">运行 PowerPivot for SharePoint 的服务器将自动获取更新后的 OLE DB 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="421f2-138">Servers that run PowerPivot for SharePoint get the updated OLE DB data provider automatically.</span></span> <span data-ttu-id="421f2-139">必须对其他服务器（例如运行独立 Excel Services 实例、但在同一台计算机上没有 PowerPivot for SharePoint 的服务器）进行修补才能使用更高版本的客户端库。</span><span class="sxs-lookup"><span data-stu-id="421f2-139">Other servers, such as those running a standalone instance Excel Services without PowerPivot for SharePoint on the same computer, must be patched to use the newer client libraries.</span></span> <span data-ttu-id="421f2-140">有关详细信息，请参阅 [在 SharePoint 服务器上安装 Analysis Services OLE DB 提供程序](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="421f2-140">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
 <span data-ttu-id="421f2-141">**应用场景 3：域控制器不可用**</span><span class="sxs-lookup"><span data-stu-id="421f2-141">**Scenario 3: Domain controller is unavailable**</span></span>  
  
 <span data-ttu-id="421f2-142">原因可能是域控制器不可用于确认用户标识。</span><span class="sxs-lookup"><span data-stu-id="421f2-142">The cause might be that a domain controller is not available to validate the user identity.</span></span> <span data-ttu-id="421f2-143">Claims to Windows Token Service 要求域控制器针对每个连接验证 SharePoint 用户的身份。</span><span class="sxs-lookup"><span data-stu-id="421f2-143">A domain controller is required by the Claims to Windows Token Service to authenticate the SharePoint user on each connection.</span></span> <span data-ttu-id="421f2-144">Claims to Windows Token Service 不使用缓存凭据。</span><span class="sxs-lookup"><span data-stu-id="421f2-144">The Claims to Windows Token Service does not use cached credentials.</span></span> <span data-ttu-id="421f2-145">它会验证每个连接的用户标识。</span><span class="sxs-lookup"><span data-stu-id="421f2-145">It validates the user identity for each connection.</span></span>  
  
 <span data-ttu-id="421f2-146">您可以通过查看 SharePoint 日志文件确认导致此错误的原因。</span><span class="sxs-lookup"><span data-stu-id="421f2-146">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="421f2-147">如果 SharePoint 日志包括消息“Failed to get WindowsIdentity from IClaimsIdentity”，则无法对该用户标识进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="421f2-147">If the SharePoint logs include the message "Failed to get WindowsIdentity from IClaimsIdentity", the user identity could not be authenticated.</span></span>  
  
 <span data-ttu-id="421f2-148">若要解决此问题，请将计算机加入到与 PowerPivot 服务器相同的域中，或在本地计算机上安装一个域控制器。</span><span class="sxs-lookup"><span data-stu-id="421f2-148">To work around this problem, join the computer to the same domain as the PowerPivot server, or install a domain controller on your local computer.</span></span> <span data-ttu-id="421f2-149">第二种解决方案是安装域控制器，这将要求您为所有服务和用户创建本地域帐户。</span><span class="sxs-lookup"><span data-stu-id="421f2-149">The second solution, installing the domain controller, will require you to create local domain accounts for all services and users.</span></span> <span data-ttu-id="421f2-150">您将需要为您定义的帐户配置服务帐户和 SharePoint 权限。</span><span class="sxs-lookup"><span data-stu-id="421f2-150">You will need to configure service accounts and SharePoint permissions for the accounts you define.</span></span>  
  
 <span data-ttu-id="421f2-151">如果您的目标是在脱机状态下使用 PowerPivot for SharePoint，则在计算机上安装域控制器将非常有用。</span><span class="sxs-lookup"><span data-stu-id="421f2-151">Installing a domain controller on your computer is useful if your objective is to use PowerPivot for SharePoint in an offline state.</span></span> <span data-ttu-id="421f2-152">有关如何脱机使用 PowerPivot 的详细说明，请参阅中的 "从网络中获取 PowerPivot 服务器" 博客条目 [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241) 。</span><span class="sxs-lookup"><span data-stu-id="421f2-152">For detailed instructions on how to use PowerPivot offline, see the blog entry for "Taking your PowerPivot server off the network" on [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241).</span></span>  
  
 <span data-ttu-id="421f2-153">**应用场景 4：服务器不稳定**</span><span class="sxs-lookup"><span data-stu-id="421f2-153">**Scenario 4: Unstable server**</span></span>  
  
 <span data-ttu-id="421f2-154">一个或多个服务可能处于不一致的状态。</span><span class="sxs-lookup"><span data-stu-id="421f2-154">One or more services might be in an inconsistent state.</span></span> <span data-ttu-id="421f2-155">在某些情况下，运行 IISRESET 将会解决该问题。</span><span class="sxs-lookup"><span data-stu-id="421f2-155">In some cases, running IISRESET will resolve the problem.</span></span>  
  
  
