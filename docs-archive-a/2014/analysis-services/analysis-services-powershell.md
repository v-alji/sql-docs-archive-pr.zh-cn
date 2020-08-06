---
title: Analysis Services PowerShell |Microsoft Docs
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56af6f26c29e5c1ddb278b620b6f525c70bd1203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579389"
---
# <a name="analysis-services-powershell"></a><span data-ttu-id="1b67a-102">Analysis Services PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b67a-102">Analysis Services PowerShell</span></span>
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] <span data-ttu-id="1b67a-103">包括 Analysis Services PowerShell (SQLAS) 提供程序和 cmdlet，以便您可以使用 Windows PowerShell 导航、管理和查询 Analysis Services 对象。</span><span class="sxs-lookup"><span data-stu-id="1b67a-103">includes an Analysis Services PowerShell (SQLAS) provider and cmdlets so that you can use Windows PowerShell to navigate, administer, and query Analysis Services objects.</span></span>  
  
 <span data-ttu-id="1b67a-104">Analysis Services PowerShell 由以下组件构成：</span><span class="sxs-lookup"><span data-stu-id="1b67a-104">Analysis Services PowerShell consists of the following:</span></span>  
  
-   <span data-ttu-id="1b67a-105">用于导航分析管理对象 (AMO) 层次结构的 `SQLAS` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="1b67a-105">`SQLAS` provider used for navigating the Analysis Management Object (AMO) hierarchy.</span></span>  
  
-   <span data-ttu-id="1b67a-106">用于执行 MDX、DMX 或 XMLA 脚本的 `Invoke-ASCmd` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b67a-106">`Invoke-ASCmd` cmdlet used for executing MDX, DMX, or XMLA script.</span></span>  
  
-   <span data-ttu-id="1b67a-107">用于日常操作（例如处理、角色管理、分区管理、备份和还原）的特定于任务的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b67a-107">Task-specific cmdlets for routine operations, such as processing, role management, partition management, backup and restore.</span></span>  
  
## <a name="in-this-article"></a><span data-ttu-id="1b67a-108">本文内容</span><span class="sxs-lookup"><span data-stu-id="1b67a-108">In this article</span></span>  
 [<span data-ttu-id="1b67a-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="1b67a-109">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="1b67a-110">Analysis Services 支持的版本和模式</span><span class="sxs-lookup"><span data-stu-id="1b67a-110">Supported Versions and Modes of Analysis Services</span></span>](#bkmk_vers)  
  
 [<span data-ttu-id="1b67a-111">身份验证要求和安全注意事项</span><span class="sxs-lookup"><span data-stu-id="1b67a-111">Authentication Requirements and Security Considerations</span></span>](#bkmk_auth)  
  
 [<span data-ttu-id="1b67a-112">Analysis Services PowerShell 任务</span><span class="sxs-lookup"><span data-stu-id="1b67a-112">Analysis Services PowerShell Tasks</span></span>](#bkmk_tasks)  

<span data-ttu-id="1b67a-113">有关语法和示例的详细信息，请参阅[Analysis Services PowerShell 参考](/sql/analysis-services/powershell/analysis-services-powershell-reference)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-113">For more information about syntax and examples, see [Analysis Services PowerShell Reference](/sql/analysis-services/powershell/analysis-services-powershell-reference).</span></span>

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="1b67a-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="1b67a-114">Prerequisites</span></span>  
 <span data-ttu-id="1b67a-115">必须安装有 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="1b67a-115">Windows PowerShell 2.0 must be installed.</span></span> <span data-ttu-id="1b67a-116">该软件默认安装在 Windows 操作系统的较新版本上。</span><span class="sxs-lookup"><span data-stu-id="1b67a-116">It is installed by default on newer versions of the Windows operating systems.</span></span> <span data-ttu-id="1b67a-117">有关详细信息，请参阅[安装 Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)</span><span class="sxs-lookup"><span data-stu-id="1b67a-117">For more information, see [Install Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)</span></span>

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 <span data-ttu-id="1b67a-118">您必须安装包括 SQL Server PowerShell (SQLPS) 模块和客户端库在内的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="1b67a-118">You must install a SQL Server feature that includes the SQL Server PowerShell (SQLPS) module and client libraries.</span></span> <span data-ttu-id="1b67a-119">最简单的操作方式是安装 SQL Server Management Studio，其中自动包括 PowerShell 功能和客户端库。</span><span class="sxs-lookup"><span data-stu-id="1b67a-119">The easiest way to do this is by installing SQL Server Management Studio, which includes the PowerShell feature and client libraries automatically.</span></span> <span data-ttu-id="1b67a-120">SQL Server PowerShell (SQLPS) 模块包含用于所有 SQL Server 功能的 PowerShell 提供程序和 cmdlet，包括用于导航 Analysis Services 对象层次结构的 SQLASCmdlets 模块和 SQLAS 提供程序。</span><span class="sxs-lookup"><span data-stu-id="1b67a-120">The SQL Server PowerShell (SQLPS) module contains the PowerShell providers and cmdlets for all SQL Server features, including the SQLASCmdlets module and SQLAS provider used for navigating the Analysis Services object hierarchy.</span></span>  
  
 <span data-ttu-id="1b67a-121">你必须导入**SQLPS**模块，然后才能使用该 `SQLAS` 提供程序和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b67a-121">You must import the **SQLPS** module before you can use the `SQLAS` provider and cmdlets.</span></span> <span data-ttu-id="1b67a-122">SQLAS 提供程序是提供程序的扩展 `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="1b67a-122">The SQLAS provider is an extension of the `SQLServer` provider.</span></span> <span data-ttu-id="1b67a-123">有几种方法可以导入 SQLPS 模块。</span><span class="sxs-lookup"><span data-stu-id="1b67a-123">There are several ways to import the SQLPS module.</span></span> <span data-ttu-id="1b67a-124">有关详细信息，请参阅 [导入 SQLPS 模块](../../2014/database-engine/import-the-sqlps-module.md)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-124">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
 <span data-ttu-id="1b67a-125">远程访问 Analysis Services 实例要求您启用远程管理和文件共享。</span><span class="sxs-lookup"><span data-stu-id="1b67a-125">Remote access to an Analysis Services instance requires that you enable remote administration and file sharing.</span></span> <span data-ttu-id="1b67a-126">有关详细信息，请参阅本主题中的[启用远程管理](#bkmk_remote)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-126">For more information, see [Enable Remote Administration](#bkmk_remote) in this topic.</span></span>  
  
##  <a name="supported-versions-and-modes-of-analysis-services"></a><a name="bkmk_vers"></a> <span data-ttu-id="1b67a-127">Analysis Services 的支持的版本和模式</span><span class="sxs-lookup"><span data-stu-id="1b67a-127">Supported Versions and Modes of Analysis Services</span></span>  
 <span data-ttu-id="1b67a-128">目前，在 Windows Server 2008 R2、Windows Server 2008 SP1 或 Windows 7 上运行的任何版本的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services 均支持 Analysis Services PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b67a-128">Currently, Analysis Services PowerShell is supported on any edition of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services running on Windows Server 2008 R2, Windows Server 2008 SP1, or Windows 7.</span></span>  
  
 <span data-ttu-id="1b67a-129">下表显示 Analysis Services PowerShell 在不同环境下的可用性。</span><span class="sxs-lookup"><span data-stu-id="1b67a-129">The following table shows the availability of Analysis Services PowerShell in different contexts.</span></span>  
  
|<span data-ttu-id="1b67a-130">上下文</span><span class="sxs-lookup"><span data-stu-id="1b67a-130">Context</span></span>|<span data-ttu-id="1b67a-131">PowerShell 功能可用性</span><span class="sxs-lookup"><span data-stu-id="1b67a-131">PowerShell Feature Availability</span></span>|  
|-------------|-------------------------------------|  
|<span data-ttu-id="1b67a-132">多维实例和数据库</span><span class="sxs-lookup"><span data-stu-id="1b67a-132">Multidimensional instances and databases</span></span>|<span data-ttu-id="1b67a-133">支持本地和远程管理。</span><span class="sxs-lookup"><span data-stu-id="1b67a-133">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="1b67a-134">合并分区需要具有本地连接。</span><span class="sxs-lookup"><span data-stu-id="1b67a-134">Merge-partition requires a local connection.</span></span>|  
|<span data-ttu-id="1b67a-135">表格实例和数据库</span><span class="sxs-lookup"><span data-stu-id="1b67a-135">Tabular instances and databases</span></span>|<span data-ttu-id="1b67a-136">支持本地和远程管理。</span><span class="sxs-lookup"><span data-stu-id="1b67a-136">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="1b67a-137">有关详细信息，请参阅8月2011博客，了解如何[使用 PowerShell 管理表格模型](https://go.microsoft.com/fwlink/?linkID=227685)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-137">For more information, see an August 2011 blog about [Manage Tabular Models Using PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).</span></span>|  
|<span data-ttu-id="1b67a-138">PowerPivot for SharePoint 实例和数据库</span><span class="sxs-lookup"><span data-stu-id="1b67a-138">PowerPivot for SharePoint instances and databases</span></span>|<span data-ttu-id="1b67a-139">有限支持。</span><span class="sxs-lookup"><span data-stu-id="1b67a-139">Limited support.</span></span> <span data-ttu-id="1b67a-140">您可以使用 HTTP 连接和 SQLAS 提供程序查看实例和数据库信息。</span><span class="sxs-lookup"><span data-stu-id="1b67a-140">You can use HTTP connections and the SQLAS provider to view instance and database information.</span></span><br /><br /> <span data-ttu-id="1b67a-141">但是，不支持使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b67a-141">However, using the cmdlets is not supported.</span></span> <span data-ttu-id="1b67a-142">切勿使用 Analysis Services PowerShell 备份和还原内存中 PowerPivot 数据库，也不应添加或删除角色、处理数据或运行任意 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="1b67a-142">You must not use Analysis Services PowerShell to backup and restore in-memory PowerPivot database, nor should you add or remove roles, process data, or run arbitrary XMLA script.</span></span><br /><br /> <span data-ttu-id="1b67a-143">出于配置目的，PowerPivot for SharePoint 具有单独提供的内置 PowerShell 支持。</span><span class="sxs-lookup"><span data-stu-id="1b67a-143">For configuration purposes, PowerPivot for SharePoint has built-in PowerShell support that is provided separately.</span></span> <span data-ttu-id="1b67a-144">有关详细信息，请参阅[PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-144">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>|  
|<span data-ttu-id="1b67a-145">与本地多维数据集的本机连接</span><span class="sxs-lookup"><span data-stu-id="1b67a-145">Native connections to local cubes</span></span><br /><br /> <span data-ttu-id="1b67a-146">"Data Source = c:\backup\test.cub"</span><span class="sxs-lookup"><span data-stu-id="1b67a-146">"Data Source=c:\backup\test.cub"</span></span>|<span data-ttu-id="1b67a-147">不支持。</span><span class="sxs-lookup"><span data-stu-id="1b67a-147">Not supported.</span></span>|  
|<span data-ttu-id="1b67a-148">与 SharePoint 中的 BI 语义模型 (.bism) 连接文件的 HTTP 连接</span><span class="sxs-lookup"><span data-stu-id="1b67a-148">HTTP connections to BI semantic model (.bism) connection files in SharePoint</span></span><br /><br /> <span data-ttu-id="1b67a-149">"Data Source = http://server/shared_docs/name.bism "</span><span class="sxs-lookup"><span data-stu-id="1b67a-149">"Data Source=http://server/shared_docs/name.bism"</span></span>|<span data-ttu-id="1b67a-150">不支持。</span><span class="sxs-lookup"><span data-stu-id="1b67a-150">Not supported.</span></span>|  
|<span data-ttu-id="1b67a-151">与 PowerPivot 数据库的嵌入式连接</span><span class="sxs-lookup"><span data-stu-id="1b67a-151">Embedded connections to PowerPivot databases</span></span><br /><br /> <span data-ttu-id="1b67a-152">"Data Source = $Embedded $"</span><span class="sxs-lookup"><span data-stu-id="1b67a-152">"Data Source=$Embedded$"</span></span>|<span data-ttu-id="1b67a-153">不支持。</span><span class="sxs-lookup"><span data-stu-id="1b67a-153">Not supported.</span></span>|  
|<span data-ttu-id="1b67a-154">Analysis Services 存储过程中的本地服务器环境</span><span class="sxs-lookup"><span data-stu-id="1b67a-154">Local server context in Analysis Services stored procedures</span></span><br /><br /> <span data-ttu-id="1b67a-155">"Data Source = \*"</span><span class="sxs-lookup"><span data-stu-id="1b67a-155">"Data Source=\*"</span></span>|<span data-ttu-id="1b67a-156">不支持。</span><span class="sxs-lookup"><span data-stu-id="1b67a-156">Not supported.</span></span>|  
  
##  <a name="authentication-requirements-and-security-considerations"></a><a name="bkmk_auth"></a><span data-ttu-id="1b67a-157">身份验证要求和安全注意事项</span><span class="sxs-lookup"><span data-stu-id="1b67a-157">Authentication Requirements and Security Considerations</span></span>  
 <span data-ttu-id="1b67a-158">在连接到 Analysis Services 时，您必须使用 Windows 用户标识建立连接。</span><span class="sxs-lookup"><span data-stu-id="1b67a-158">When connecting to Analysis Services, you must make the connection using a Windows user identity.</span></span> <span data-ttu-id="1b67a-159">多数情况下都使用 Windows 集成安全性建立连接，由当前用户的标识设置执行服务器操作的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="1b67a-159">For the most part, a connection is made using Windows integrated security, where the identity of the current user sets the security context under which server operations are performed.</span></span> <span data-ttu-id="1b67a-160">但是，在配置对 Analysis Services 的 HTTP 访问时，还可以使用其他身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="1b67a-160">However, additional authentication methods become available when you configure HTTP access to Analysis Services.</span></span> <span data-ttu-id="1b67a-161">本节介绍连接类型如何确定您可以使用的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="1b67a-161">This section explains how the type of connection determines which authentication options you can use.</span></span>  
  
 <span data-ttu-id="1b67a-162">Analysis Services 连接可分为本机连接或 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="1b67a-162">Connections to Analysis Services are characterized as either native connections or HTTP connections.</span></span> <span data-ttu-id="1b67a-163">本机连接是从客户端应用程序直接连接服务器。</span><span class="sxs-lookup"><span data-stu-id="1b67a-163">A native connection is a direct connection from a client application to the server.</span></span> <span data-ttu-id="1b67a-164">在 PowerShell 会话中，PowerShell 客户端使用 OLE DB Provider for Analysis Services 直接连接 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="1b67a-164">In a PowerShell session, the PowerShell client uses the OLE DB provider for Analysis Services to connect directly to an Analysis Services instance.</span></span> <span data-ttu-id="1b67a-165">始终使用 Windows 集成安全性建立本机连接，在此连接中 Analysis Services PowerShell 以当前用户身份执行操作。</span><span class="sxs-lookup"><span data-stu-id="1b67a-165">A native connection is always made using Windows integrated security, where Analysis Services PowerShell executes as the current user.</span></span> <span data-ttu-id="1b67a-166">Analysis Services 不支持模拟。</span><span class="sxs-lookup"><span data-stu-id="1b67a-166">Analysis Services does not support impersonation.</span></span> <span data-ttu-id="1b67a-167">如果要以特定用户身份执行某一操作，您必须以该用户的身份启动 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="1b67a-167">If you want to perform an operation as a specific user, you must start the PowerShell session as that user.</span></span>  
  
 <span data-ttu-id="1b67a-168">HTTP 连接是间接通过 IIS 建立的，该连接允许选择其他身份验证选项（如“基本身份验证”）来连接 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="1b67a-168">HTTP connections are made indirectly through IIS, allowing for additional authentication options, such as Basic authentication, to connect to an Analysis Services instance.</span></span> <span data-ttu-id="1b67a-169">由于 IIS 支持模拟，您可以提供包含 IIS 建立连接时用来模拟的凭据的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="1b67a-169">Because IIS supports impersonation, you can provide a connection string that includes credentials IIS will use to impersonate when making a connection.</span></span> <span data-ttu-id="1b67a-170">若要提供凭据，可以使用-Credential 参数。</span><span class="sxs-lookup"><span data-stu-id="1b67a-170">To provide credentials, you can use the -Credential parameter.</span></span>  
  
 <span data-ttu-id="1b67a-171">**在 PowerShell 中使用-Credential 参数**</span><span class="sxs-lookup"><span data-stu-id="1b67a-171">**Using the -Credential Parameter in PowerShell**</span></span>  
  
 <span data-ttu-id="1b67a-172">-Credential 参数使用指定用户名和密码的 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="1b67a-172">The -Credential parameter takes a PSCredential object that specifies a user name and password.</span></span> <span data-ttu-id="1b67a-173">在 Analysis Services PowerShell 中，-Credential 参数适用于发出连接 Analysis Services 请求的 cmdlet，而不是在现有连接的上下文中运行的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b67a-173">In Analysis Services PowerShell, the -Credential parameter is available for cmdlets that make a connection request to Analysis Services, as opposed to cmdlets that run within the context of an existing connection.</span></span> <span data-ttu-id="1b67a-174">发出连接请求的 cmdlet 包括 Invoke-ASCmd、Backup-ASDatabase 和 Restore-ASDatabase。</span><span class="sxs-lookup"><span data-stu-id="1b67a-174">Cmdlets that make a connection request include Invoke-ASCmd, Backup-ASDatabase, and Restore-ASDatabase.</span></span> <span data-ttu-id="1b67a-175">对于这些 cmdlet，可以使用-Credential 参数，假定满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="1b67a-175">For these cmdlets, the -Credential parameter can be used, assuming the following criteria are met:</span></span>  
  
1.  <span data-ttu-id="1b67a-176">已配置服务器用于 HTTP 访问，这表示 IIS 在连接 Analysis Services 时会处理该连接、读取用户名和密码，并模拟用户身份。</span><span class="sxs-lookup"><span data-stu-id="1b67a-176">The server is configured for HTTP access, which means that IIS handles the connection, reads the user name and password, and impersonates that user identity when connecting to Analysis Services.</span></span> <span data-ttu-id="1b67a-177">有关详细信息，请参阅 [在 Internet Information Services (IIS) 8.0 上配置对 Analysis Services 的 HTTP 访问](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-177">For more information, see [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).</span></span>  
  
2.  <span data-ttu-id="1b67a-178">为 Analysis Services HTTP 访问创建的 IIS 虚拟目录配置用于“基本身份验证”。</span><span class="sxs-lookup"><span data-stu-id="1b67a-178">The IIS virtual directory that was created for Analysis Services HTTP access is configured for Basic authentication.</span></span>  
  
3.  <span data-ttu-id="1b67a-179">凭据对象提供的用户名和密码解析为 Windows 用户标识。</span><span class="sxs-lookup"><span data-stu-id="1b67a-179">The user name and password provided by the credential object resolves to a Windows user identity.</span></span> <span data-ttu-id="1b67a-180">Analysis Services 将此标识用作当前用户的标识。</span><span class="sxs-lookup"><span data-stu-id="1b67a-180">Analysis Services uses this identity as the current user.</span></span> <span data-ttu-id="1b67a-181">如果该用户不是 Windows 用户，或是缺少足够的权限来执行请求的操作，该请求将失败。</span><span class="sxs-lookup"><span data-stu-id="1b67a-181">If the user is not a Windows user, or lacks sufficient permissions to perform the requested operation, the request will fail.</span></span>  
  
 <span data-ttu-id="1b67a-182">若要创建凭据对象，您可以使用 Get-Credential cmdlet 从操作员处收集凭据。</span><span class="sxs-lookup"><span data-stu-id="1b67a-182">To create a credential object, you can use the Get-Credential cmdlet to collect the credentials from the operator.</span></span> <span data-ttu-id="1b67a-183">随后可以在连接 Analysis Services 的命令中使用该凭据对象。</span><span class="sxs-lookup"><span data-stu-id="1b67a-183">You can then use the credential object on a command that connects to Analysis Services.</span></span> <span data-ttu-id="1b67a-184">下面的示例演示了一种方法。</span><span class="sxs-lookup"><span data-stu-id="1b67a-184">The following example illustrates one approach.</span></span> <span data-ttu-id="1b67a-185">在此示例中，连接到本地实例 (`SQLSERVER:\SQLAS\HTTP_DS`) 配置为使用 HTTP 访问。</span><span class="sxs-lookup"><span data-stu-id="1b67a-185">In this example, the connection is to a local instance (`SQLSERVER:\SQLAS\HTTP_DS`) configured for HTTP access.</span></span>  
  
```powershell
$cred = Get-Credential adventureworks\dbadmin  
Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 <span data-ttu-id="1b67a-186">在使用“基本身份验证”时，您应始终结合使用 HTTPS 和 SSL，以便通过加密连接发送用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="1b67a-186">When using Basic authentication, you should always use HTTPS with SSL so that username and passwords are sent over an encrypted connection.</span></span> <span data-ttu-id="1b67a-187">有关详细信息，请参阅[在 iis 7.0 中配置安全套接字层](https://go.microsoft.com/fwlink/?linkID=184299)和[ (Iis 7) 配置基本身份验证](https://go.microsoft.com/fwlink/?LinkId=230776)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-187">For more information, see [Configure Secure Sockets Layer in IIS 7.0](https://go.microsoft.com/fwlink/?linkID=184299) and [Configure Basic Authentication (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).</span></span>  
  
 <span data-ttu-id="1b67a-188">请记住，您在 PowerShell 中提供的凭据、查询和命令将原样传递到传输层。</span><span class="sxs-lookup"><span data-stu-id="1b67a-188">Remember that credentials, queries, and commands that you provide in PowerShell are passed unchanged to the transport layer.</span></span> <span data-ttu-id="1b67a-189">在脚本中包括敏感内容会增加恶意注入攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="1b67a-189">Including sensitive content in your scripts increases the risk of a malicious injection attack.</span></span>  
  
 <span data-ttu-id="1b67a-190">**提供作为 Microsoft.Secure.String 对象的密码**</span><span class="sxs-lookup"><span data-stu-id="1b67a-190">**Providing a password as a Microsoft.Secure.String object**</span></span>  
  
 <span data-ttu-id="1b67a-191">某些操作（如备份与还原），支持当您在命令中提供提供密码时激活的加密选项。</span><span class="sxs-lookup"><span data-stu-id="1b67a-191">Some operations, such as backup and restore, support encryption options that are activated when you provide a password in the command.</span></span> <span data-ttu-id="1b67a-192">提供密码即表示 Analysis Services 对备份文件进行加密或解密。</span><span class="sxs-lookup"><span data-stu-id="1b67a-192">Providing the password signals Analysis Services to encrypt or decrypt the backup file.</span></span> <span data-ttu-id="1b67a-193">在 Analysis Services 中，此密码实例化为一个安全字符串对象。</span><span class="sxs-lookup"><span data-stu-id="1b67a-193">In Analysis Services, this password is instantiated as a secure string object.</span></span> <span data-ttu-id="1b67a-194">下例演示了如何在运行时从操作员处收集密码。</span><span class="sxs-lookup"><span data-stu-id="1b67a-194">The following example provides an illustration of how to collect a password from the operator at run time.</span></span>  
  
```powershell
$pwd = read-host -AsSecureString -Prompt "Password"  
$pwd -is [System.IDisposable]  
```  
  
 <span data-ttu-id="1b67a-195">您可以备份和还原已加密的数据库文件，将 $pwd 变量传递给密码参数。</span><span class="sxs-lookup"><span data-stu-id="1b67a-195">You can now backup or restore an encrypted database file, passing the $pwd variable to the password parameter.</span></span> <span data-ttu-id="1b67a-196">若要查看将此插图与其他 cmdlet 组合在一起的完整示例，请参阅[.asdatabase cmdlet](/powershell/module/sqlserver/backup-asdatabase)和[.asdatabase cmdlet](/powershell/module/sqlserver/restore-asdatabase)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-196">To view a complete example that combines this illustration with other cmdlets, see [Backup-ASDatabase cmdlet](/powershell/module/sqlserver/backup-asdatabase) and [Restore-ASDatabase cmdlet](/powershell/module/sqlserver/restore-asdatabase).</span></span>
  
 <span data-ttu-id="1b67a-197">作为后续步骤，需要从会话中删除该密码和变量。</span><span class="sxs-lookup"><span data-stu-id="1b67a-197">As a follow up step, remove both the password and variable from the session.</span></span>  
  
```powershell
$pwd.Dispose()  
Remove-Variable -Name pwd  
```  
  
##  <a name="analysis-services-powershell-tasks"></a><a name="bkmk_tasks"></a><span data-ttu-id="1b67a-198">Analysis Services PowerShell 任务</span><span class="sxs-lookup"><span data-stu-id="1b67a-198">Analysis Services PowerShell Tasks</span></span>  
 <span data-ttu-id="1b67a-199">您可以从 Windows PowerShell Management Shell 或 Windows 命令提示符运行 Analysis Services PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b67a-199">You can run Analysis Services PowerShell from the Windows PowerShell management shell or a Windows command prompt.</span></span> <span data-ttu-id="1b67a-200">不支持从 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 运行 Analysis Services PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b67a-200">Running Analysis Services PowerShell from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is not supported.</span></span>  
  
 <span data-ttu-id="1b67a-201">本节介绍使用 Analysis Services PowerShell 的常见任务。</span><span class="sxs-lookup"><span data-stu-id="1b67a-201">This section describes common tasks for using Analysis Services PowerShell.</span></span>  
  
-   [<span data-ttu-id="1b67a-202">加载 Analysis Services 提供程序和 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b67a-202">Load the Analysis Services Provider and Cmdlets</span></span>](#bkmk_load)  
  
-   [<span data-ttu-id="1b67a-203">启用远程管理</span><span class="sxs-lookup"><span data-stu-id="1b67a-203">Enable Remote Administration</span></span>](#bkmk_remote)  
  
-   [<span data-ttu-id="1b67a-204">连接到 Analysis Services 对象</span><span class="sxs-lookup"><span data-stu-id="1b67a-204">Connect to an Analysis Services Object</span></span>](#bkmk_connect)  
  
-   [<span data-ttu-id="1b67a-205">管理服务</span><span class="sxs-lookup"><span data-stu-id="1b67a-205">Administer the Service</span></span>](#bkmk_admin)  
  
-   [<span data-ttu-id="1b67a-206">获取有关 Analysis Services PowerShell 的帮助</span><span class="sxs-lookup"><span data-stu-id="1b67a-206">Get Help for Analysis Services PowerShell</span></span>](#bkmk_help)  
  
###  <a name="load-the-analysis-services-provider-and-cmdlets"></a><a name="bkmk_load"></a><span data-ttu-id="1b67a-207">加载 Analysis Services 提供程序和 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b67a-207">Load the Analysis Services Provider and Cmdlets</span></span>  
 <span data-ttu-id="1b67a-208">Analysis Services 提供程序是 SQL Server 根提供程序的扩展插件，将在您导入 SQLPS 模块时提供。</span><span class="sxs-lookup"><span data-stu-id="1b67a-208">The Analysis Services provider is an extension of the SQL Server root provider that becomes available when you import the SQLPS module.</span></span> <span data-ttu-id="1b67a-209">Analysis Services cmdlet 同时加载；如果您想要使用这些 cmdlet，但不需要该提供程序，也可以单独加载它们。</span><span class="sxs-lookup"><span data-stu-id="1b67a-209">Analysis Services cmdlets are loaded simultaneously; you can also load them independently if you want to use them without the provider.</span></span>  
  
-   <span data-ttu-id="1b67a-210">运行 Import-module cmdlet 可以加载包括所有 Analysis Services PowerShell 功能的 SQLPS。</span><span class="sxs-lookup"><span data-stu-id="1b67a-210">Run the Import-module cmdlet to load SQLPS that includes all of the Analysis Services PowerShell functionality.</span></span> <span data-ttu-id="1b67a-211">如果您无法导入该模块，则可以出于加载该模块的目的，暂时将执行策略更改为不受限制。</span><span class="sxs-lookup"><span data-stu-id="1b67a-211">If you cannot import the module, you can temporarily change the execution policy to unrestricted for the purpose of the loading the module.</span></span> <span data-ttu-id="1b67a-212">有关详细信息，请参阅 [导入 SQLPS 模块](../../2014/database-engine/import-the-sqlps-module.md)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-212">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
    ```powershell
    Import-Module "sqlps"  
    ```  
  
     <span data-ttu-id="1b67a-213">或者，可以使用 `import-module "sqlps" -disablenamechecking` 禁止显示与未经批准的动词名称有关的警告。</span><span class="sxs-lookup"><span data-stu-id="1b67a-213">Alternatively, use `import-module "sqlps" -disablenamechecking` to suppress the warning about unapproved verb names.</span></span>  
  
-   <span data-ttu-id="1b67a-214">若要仅加载任务特定的 Analysis Services cmdlet，而不加载 Analysis Services 提供程序或 Invoke-ASCmd cmdlet，您可以在单独的操作中加载 SQLASCmdlets 模块。</span><span class="sxs-lookup"><span data-stu-id="1b67a-214">To load just the task-specific Analysis Services cmdlets, without the Analysis Services provider or the Invoke-ASCmd cmdlet, you can load the SQLASCmdlets module as an independent operation.</span></span>  
  
    ```powershell
    Import-Module "sqlascmdlets"  
    ```  
  
###  <a name="enable-remote-administration"></a><a name="bkmk_remote"></a><span data-ttu-id="1b67a-215">启用远程管理</span><span class="sxs-lookup"><span data-stu-id="1b67a-215">Enable Remote Administration</span></span>  
 <span data-ttu-id="1b67a-216">您必须首先启用远程管理和文件共享，然后才能将 Analysis Services PowerShell 用于远程 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="1b67a-216">Before you can use Analysis Services PowerShell with a remote Analysis Services instance, you must first enable remote administration and file sharing.</span></span> <span data-ttu-id="1b67a-217">以下错误表明发生了防火墙配置问题： "RPC 服务器不可用。</span><span class="sxs-lookup"><span data-stu-id="1b67a-217">The following error indicates a firewall configuration issue: "The RPC server is unavailable.</span></span> <span data-ttu-id="1b67a-218">(HRESULT 异常: 0x800706BA)”。</span><span class="sxs-lookup"><span data-stu-id="1b67a-218">(Exception from HRESULT: 0x800706BA)".</span></span>  
  
1.  <span data-ttu-id="1b67a-219">确认本地计算机和远程计算机都具有客户端和服务器工具的 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="1b67a-219">Verify that both local and remote computers have the [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] versions of the client and server tools.</span></span>  
  
2.  <span data-ttu-id="1b67a-220">在承载 Analysis Services 实例的远程服务器上，在 Windows 防火墙中打开 TCP 端口 2383。</span><span class="sxs-lookup"><span data-stu-id="1b67a-220">On the remote server that is hosting an Analysis Services instance, open TCP port 2383 in Windows Firewall.</span></span> <span data-ttu-id="1b67a-221">如果您已将 Analysis Services 作为命名实例安装或者正在使用自定义端口，则该端口号将不同。</span><span class="sxs-lookup"><span data-stu-id="1b67a-221">If you installed Analysis Services as a named instance or are using a custom port, the port number will be different.</span></span> <span data-ttu-id="1b67a-222">有关详细信息，请参阅 [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-222">For more information, see [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
3.  <span data-ttu-id="1b67a-223">在远程服务器上，确认启动了以下服务：远程过程调用 (RPC) 服务、TCP/IP NetBIOS Helper 服务、Windows Management Instrumentation (WMI) 服务、Windows Remote Management (WS-Management) 服务。</span><span class="sxs-lookup"><span data-stu-id="1b67a-223">On the remote server, verify that the followings services are started:  Remote Procedure Call (RPC) service, TCP/IP NetBIOS Helper service, Windows Management Instrumentation (WMI) service, Windows Remote Management (WS-Management) service.</span></span>  
  
4.  <span data-ttu-id="1b67a-224">在远程服务器上，启动组策略对象编辑器管理单元 (gpedit.msc)。</span><span class="sxs-lookup"><span data-stu-id="1b67a-224">On the remote server, start the Group Policy Object Editor snap-in (gpedit.msc).</span></span>  
  
5.  <span data-ttu-id="1b67a-225">依次打开“计算机配置”、“管理模板”、“网络”、“网络连接”、“Windows 防火墙”和“域配置文件”。</span><span class="sxs-lookup"><span data-stu-id="1b67a-225">Open Computer Configuration, open Administrative Templates, open Network, open Network Connections, open Windows Firewall, and then open Domain Profile.</span></span>  
  
6.  <span data-ttu-id="1b67a-226">双击 " **Windows 防火墙：允许入站远程管理例外**"，选择 "**已启用**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1b67a-226">Double-click **Windows Firewall: Allow inbound remote administration exception**, select **Enabled**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="1b67a-227">双击 " **Windows 防火墙：允许入站文件和打印机共享例外**"，选择 "**已启用**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1b67a-227">Double-click **Windows Firewall: Allow inbound file and printer sharing exception**, select **Enabled**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="1b67a-228">在具有客户端工具的本地计算机上，使用以下 cmdlet 验证远程管理，并将实际的服务器名称替换为*远程服务器名称*占位符。</span><span class="sxs-lookup"><span data-stu-id="1b67a-228">On the local computer that has the client tools, use the following cmdlets to verify remote administration, substituting the actual server name for the *remote-server-name* placeholder.</span></span> <span data-ttu-id="1b67a-229">如果 Analysis Services 作为默认实例安装，则省略实例名称。</span><span class="sxs-lookup"><span data-stu-id="1b67a-229">Omit the instance name if Analysis Services is installed as the default instance.</span></span> <span data-ttu-id="1b67a-230">为使该命令正常执行，您必须在之前导入了 SQLPS 模块。</span><span class="sxs-lookup"><span data-stu-id="1b67a-230">You must have previously imported the SQLPS module in order for the command to work.</span></span>  
  
    ```
    PS SQLSERVER:\> cd sqlas
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 <span data-ttu-id="1b67a-231">在某些情况下，可能需要更多的配置。</span><span class="sxs-lookup"><span data-stu-id="1b67a-231">In some cases, additional configuration might be necessary.</span></span> <span data-ttu-id="1b67a-232">您可能需要在远程服务器上键入以下命令，然后才能从其他计算机向其发出命令：</span><span class="sxs-lookup"><span data-stu-id="1b67a-232">You might need to type the following on the remote server before you can issue commands to it from another computer:</span></span>  
  
```powershell
Enable-PSRemoting  
```  
  
  
###  <a name="connect-to-an-analysis-services-object"></a><a name="bkmk_connect"></a><span data-ttu-id="1b67a-233">连接到 Analysis Services 对象</span><span class="sxs-lookup"><span data-stu-id="1b67a-233">Connect to an Analysis Services Object</span></span>  
 <span data-ttu-id="1b67a-234">Analysis Services PowerShell 提供程序支持在 Analysis Services 对象层次结构中导航和为正在运行的命令设置上下文。</span><span class="sxs-lookup"><span data-stu-id="1b67a-234">The Analysis Services PowerShell provider supports navigation of the Analysis Services object hierarchy and sets the context for running commands.</span></span> <span data-ttu-id="1b67a-235">该提供程序是可通过 SQLPS 模块获得的 SQLSERVER 根提供程序的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="1b67a-235">The provider is an extension of the SQLSERVER root provider available through the SQLPS module.</span></span> <span data-ttu-id="1b67a-236">在您加载 SQLPS 模块后，可以导航该路径。</span><span class="sxs-lookup"><span data-stu-id="1b67a-236">After you load the SQLPS module, you can navigate the path.</span></span>  
  
 <span data-ttu-id="1b67a-237">您可以连接到本地或远程实例，但某些 cmdlet 仅在本地实例上运行（即 merge-partition）。</span><span class="sxs-lookup"><span data-stu-id="1b67a-237">You can connect to a local or remote instance, but some cmdlets only run on a local instance (namely, merge-partition).</span></span> <span data-ttu-id="1b67a-238">您可以将本机连接或 HTTP 连接用于为 HTTP 访问配置的 Analysis Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="1b67a-238">You can use a native connection or an HTTP connection for Analysis Services servers that you configured for HTTP access.</span></span> <span data-ttu-id="1b67a-239">下图说明用于本机和 HTTP 连接的导航路径。</span><span class="sxs-lookup"><span data-stu-id="1b67a-239">The following illustrations show the navigation path for native and HTTP connections.</span></span> <span data-ttu-id="1b67a-240">下图说明用于本机和 HTTP 连接的导航路径。</span><span class="sxs-lookup"><span data-stu-id="1b67a-240">The following illustrations show the navigation path for native and HTTP connections.</span></span>  
  
 <span data-ttu-id="1b67a-241">**与 Analysis Services 的本机连接**</span><span class="sxs-lookup"><span data-stu-id="1b67a-241">**Native Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="1b67a-242">![与 Analysis Services 的本机连接](media/ssas-powershell-nativeconnection.gif "与 Analysis Services 的本机连接")</span><span class="sxs-lookup"><span data-stu-id="1b67a-242">![Native connection to Analysis Services](media/ssas-powershell-nativeconnection.gif "Native connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="1b67a-243">下面的示例说明了如何使用本机连接导航对象层次结构。</span><span class="sxs-lookup"><span data-stu-id="1b67a-243">The following example is a demonstration of how to use a native connection to navigate object hierarchy.</span></span> <span data-ttu-id="1b67a-244">通过该提供程序，您可以发出 `dir` 以便查看实例信息。</span><span class="sxs-lookup"><span data-stu-id="1b67a-244">From the provider, you can issue a `dir` to view instance information.</span></span> <span data-ttu-id="1b67a-245">您可以使用 `cd` 查看该实例的对象。</span><span class="sxs-lookup"><span data-stu-id="1b67a-245">You can use `cd` to view objects of that instance.</span></span>  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 <span data-ttu-id="1b67a-246">您应该看到以下连接：程序集、数据库、角色和跟踪。</span><span class="sxs-lookup"><span data-stu-id="1b67a-246">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="1b67a-247">继续使用 `cd` 和 `dir`，您可以查看各连接的内容。</span><span class="sxs-lookup"><span data-stu-id="1b67a-247">Continuing to use `cd` and `dir`, you can view the contents of each collection.</span></span>  
  
 <span data-ttu-id="1b67a-248">**HTTP 连接到 Analysis Services**</span><span class="sxs-lookup"><span data-stu-id="1b67a-248">**HTTP Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="1b67a-249">![与 Analysis Services 的 HTTP 连接](media/ssas-powershell-httpconnection.gif "与 Analysis Services 的 HTTP 连接")</span><span class="sxs-lookup"><span data-stu-id="1b67a-249">![HTTP Connection to Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP Connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="1b67a-250">如果你使用本主题中的说明配置了用于 HTTP 访问的服务器，则 HTTP 连接很有用：[配置 Http 访问以对 Internet Information Services &#40;IIS&#41; 8.0 上的 Analysis Services](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span><span class="sxs-lookup"><span data-stu-id="1b67a-250">HTTP connections are useful if you configured your server for HTTP access using the instructions in this topic: [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span></span>  
  
 <span data-ttu-id="1b67a-251">假设的服务器 URL http://localhost/olap/msmdpump.dll ，连接可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="1b67a-251">Assuming a server URL of http://localhost/olap/msmdpump.dll, a connection might look like the following:</span></span>  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 <span data-ttu-id="1b67a-252">您应该看到以下连接：程序集、数据库、角色和跟踪。</span><span class="sxs-lookup"><span data-stu-id="1b67a-252">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="1b67a-253">如果您无法看到这些连接的内容，则检查 OLAP 虚拟目录上的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="1b67a-253">If you cannot view the contents of these collections, check the authentication settings on the OLAP virtual directory.</span></span> <span data-ttu-id="1b67a-254">请确保禁用了匿名访问。</span><span class="sxs-lookup"><span data-stu-id="1b67a-254">Make sure that Anonymous Access is disabled.</span></span> <span data-ttu-id="1b67a-255">如果您在使用 Windows 身份验证，则应确保您的 Windows 用户帐户对该 Analysis Services 实例具有管理权限。</span><span class="sxs-lookup"><span data-stu-id="1b67a-255">If you are using Windows Authentication, be sure that your Windows user account has administrative permissions on the Analysis Services instance.</span></span>  
  
###  <a name="administer-the-service"></a><a name="bkmk_admin"></a><span data-ttu-id="1b67a-256">管理服务</span><span class="sxs-lookup"><span data-stu-id="1b67a-256">Administer the Service</span></span>  
 <span data-ttu-id="1b67a-257">验证服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="1b67a-257">Verify the service is running.</span></span> <span data-ttu-id="1b67a-258">返回 SQL Server 服务的状态、名称和显示名称，包括 Analysis Services (MSSQLServerOLAPService) 和数据库引擎。</span><span class="sxs-lookup"><span data-stu-id="1b67a-258">Returns status, name, and display name for SQL Server services, including Analysis Services (MSSQLServerOLAPService) and the Database Engine.</span></span>  
  
```powershell
Get-Service mssql*  
```  
  
 <span data-ttu-id="1b67a-259">返回与进程有关的属性，包括进程 ID、处理计数和内存使用情况：</span><span class="sxs-lookup"><span data-stu-id="1b67a-259">Returns properties about a process, including process ID, handle count, and memory usage:</span></span>  
  
```powershell
Get-Process msmdsrv  
```  
  
 <span data-ttu-id="1b67a-260">在您从管理员 shell 发出以下 cmdlet 时重新启动该服务：</span><span class="sxs-lookup"><span data-stu-id="1b67a-260">Restarts the service when you issue the following cmdlet from the administrator shell:</span></span>  
  
```powershell
Restart-Service mssqlserverolapservice  
```  
  
###  <a name="get-help-for-analysis-services-powershell"></a><a name="bkmk_help"></a><span data-ttu-id="1b67a-261">获取 Analysis Services PowerShell 的帮助</span><span class="sxs-lookup"><span data-stu-id="1b67a-261">Get Help for Analysis Services PowerShell</span></span>  
 <span data-ttu-id="1b67a-262">使用以下任何 cmdlet 可以验证 cmdlet 可用性并且获取有关服务、进程和对象的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1b67a-262">Use any of the following cmdlets to verify cmdlet availability and to get more information about services, processes, and objects.</span></span>  
  
1.  <span data-ttu-id="1b67a-263">`Get-Help` 返回针对 Analysis Services cmdlet 的内置帮助，包括示例：</span><span class="sxs-lookup"><span data-stu-id="1b67a-263">`Get-Help` returns the built-in help for an Analysis Services cmdlet, including examples:</span></span>  
  
    ```powershell
    Get-Help invoke-ascmd -Examples  
    ```  
  
2.  <span data-ttu-id="1b67a-264">`Get-Command` 返回由 11 个 Analysis Services PowerShell cmdlet 组成的列表：</span><span class="sxs-lookup"><span data-stu-id="1b67a-264">`Get-Command` returns a list of the eleven Analysis Services PowerShell cmdlets:</span></span>  
  
    ```powershell
    Get-Command -module SQLASCmdlets  
    ```  
  
3.  <span data-ttu-id="1b67a-265">`Get-Member` 返回服务或进程的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="1b67a-265">`Get-Member` returns properties or methods of a service or process.</span></span>  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Property  
    ```  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Method  
    ```  
  
    ```powershell
    Get-Process msmdsrv | Get-Member -Type Property  
    ```  
  
4.  <span data-ttu-id="1b67a-266">`Get-Member` 也可用于返回对象的属性或方法（例如，针对服务器对象的 AMO 方法），使用 SQLAS 提供程序可以指定服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1b67a-266">`Get-Member` can also be used to return properties or methods of an object (for example, AMO methods on the server object) using the SQLAS provider to specify the server instance.</span></span>  
  
    ```
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | Get-Member -Type Method  
    ```  
  
5.  <span data-ttu-id="1b67a-267">`Get-PSdrive` 返回当前安装的提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="1b67a-267">`Get-PSdrive` returns a list of the providers that are currently installed.</span></span> <span data-ttu-id="1b67a-268">如果您导入了 SQLPS 模块，将会在该列表中看到 `SQLServer` 提供程序（SQLAS 是 SQLServer 提供程序的一部分并且永远不会单独出现在该列表中）：</span><span class="sxs-lookup"><span data-stu-id="1b67a-268">If you imported the SQLPS module, you will see the `SQLServer` provider in the list (SQLAS is part of the SQLServer provider and never appears separately in the list):</span></span>  
  
    ```powershell
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1b67a-269">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b67a-269">See Also</span></span>  
 <span data-ttu-id="1b67a-270">[安装 SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="1b67a-270">[Install SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md) </span></span>  
 <span data-ttu-id="1b67a-271">[使用 PowerShell (博客) 管理表格模型](https://go.microsoft.com/fwlink/?linkID=227685) </span><span class="sxs-lookup"><span data-stu-id="1b67a-271">[Manage Tabular Models Using PowerShell (blog)](https://go.microsoft.com/fwlink/?linkID=227685) </span></span>  
 [<span data-ttu-id="1b67a-272">在 Internet Information Services (IIS) 8.0 上配置对 Analysis Services 的 HTTP 访问</span><span class="sxs-lookup"><span data-stu-id="1b67a-272">Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0</span></span>](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
