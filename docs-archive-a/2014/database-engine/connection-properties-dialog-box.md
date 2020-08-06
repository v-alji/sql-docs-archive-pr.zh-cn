---
title: “连接属性”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectionproperties.f1
helpviewer_keywords:
- Connection Properties dialog box
ms.assetid: 6df812ad-4d80-4503-8a23-47719ce85624
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db2817ebaf3f1655f146c060fcb79d550ad0cc8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693061"
---
# <a name="connection-properties-dialog-box"></a><span data-ttu-id="b0894-102">“连接属性”对话框</span><span class="sxs-lookup"><span data-stu-id="b0894-102">Connection Properties Dialog Box</span></span>
  <span data-ttu-id="b0894-103">使用此对话框可以查看当前的连接属性。</span><span class="sxs-lookup"><span data-stu-id="b0894-103">Use this dialog box to view the current connection properties.</span></span> <span data-ttu-id="b0894-104">在不同“对象资源管理器”对话框中单击“查看连接属性”\*\*\*\* 时，可以使用此对话框。</span><span class="sxs-lookup"><span data-stu-id="b0894-104">This dialog box is available when you click **View connection properties** in various Object Explorer dialog boxes.</span></span> <span data-ttu-id="b0894-105">此页上显示的属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="b0894-105">The properties displayed on this page are read-only.</span></span>  
  
 <span data-ttu-id="b0894-106">若要更改属性（如“数据库”\*\*\*\*），请在打开“连接属性”\*\*\*\* 对话框之前，使用“对象资源管理器”连接到所需的数据库。</span><span class="sxs-lookup"><span data-stu-id="b0894-106">To change properties such as **Database**, connect to the desired database with Object Explorer before opening the **Connection Properties** dialog box.</span></span>  
  
 <span data-ttu-id="b0894-107">请注意，SQL Azure 的查询超时期限是 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="b0894-107">Note that the query time-out period for SQL Azure is 30 minutes.</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="b0894-108">身份验证</span><span class="sxs-lookup"><span data-stu-id="b0894-108">Authentication</span></span>  
 <span data-ttu-id="b0894-109">查看当前连接的身份验证属性。</span><span class="sxs-lookup"><span data-stu-id="b0894-109">View authentication properties for the current connection.</span></span> <span data-ttu-id="b0894-110">身份验证属性是指在建立连接时所使用的登录名和身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="b0894-110">Authentication properties are the login and authentication method when the connection was established.</span></span> <span data-ttu-id="b0894-111">若要更改身份验证属性，请断开与的连接， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 然后使用所需的连接选项将对象资源管理器再次连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="b0894-111">To change the authentication properties, disconnect from [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then connect Object Explorer to the server again, using the desired connection options.</span></span>  
  
 <span data-ttu-id="b0894-112">**身份验证方法**</span><span class="sxs-lookup"><span data-stu-id="b0894-112">**Authentication Method**</span></span>  
 <span data-ttu-id="b0894-113">用于当前连接的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="b0894-113">The authentication method used for the current connection.</span></span>  
  
 <span data-ttu-id="b0894-114">**用户名**</span><span class="sxs-lookup"><span data-stu-id="b0894-114">**User Name**</span></span>  
 <span data-ttu-id="b0894-115">用于连接身份验证的登录的用户名。</span><span class="sxs-lookup"><span data-stu-id="b0894-115">The name of the user of login used for the connection authentication.</span></span>  
  
## <a name="connection-category"></a><span data-ttu-id="b0894-116">连接类别</span><span class="sxs-lookup"><span data-stu-id="b0894-116">Connection Category</span></span>  
 <span data-ttu-id="b0894-117">查看当前连接的连接属性。</span><span class="sxs-lookup"><span data-stu-id="b0894-117">View connection properties for the current connection.</span></span> <span data-ttu-id="b0894-118">大多数连接属性都是在连接过程中，在“连接到服务器”\*\*\*\* 对话框的“连接属性”\*\*\*\* 选项卡上选择的。</span><span class="sxs-lookup"><span data-stu-id="b0894-118">Most connection properties were selected on the **Connection Properties** tab of the **Connect to server** dialog box during the connection process.</span></span>  
  
 <span data-ttu-id="b0894-119">**Database**</span><span class="sxs-lookup"><span data-stu-id="b0894-119">**Database**</span></span>  
 <span data-ttu-id="b0894-120">当前连接到的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="b0894-120">The name of the database currently connected to.</span></span> <span data-ttu-id="b0894-121">若要更改此名称，请使用 SQL 编辑器工具栏。</span><span class="sxs-lookup"><span data-stu-id="b0894-121">To change this use, the SQL Editor toolbar.</span></span>  
  
 <span data-ttu-id="b0894-122">**SPID**</span><span class="sxs-lookup"><span data-stu-id="b0894-122">**SPID**</span></span>  
 <span data-ttu-id="b0894-123">服务器为连接所分配的系统进程 ID。</span><span class="sxs-lookup"><span data-stu-id="b0894-123">The system process ID assigned by the server to the connection.</span></span> <span data-ttu-id="b0894-124">不能更改此连接的 SPID。</span><span class="sxs-lookup"><span data-stu-id="b0894-124">This cannot be changed for this connection.</span></span>  
  
 <span data-ttu-id="b0894-125">**网络协议**</span><span class="sxs-lookup"><span data-stu-id="b0894-125">**Network Protocol**</span></span>  
 <span data-ttu-id="b0894-126">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 连接的网络协议。</span><span class="sxs-lookup"><span data-stu-id="b0894-126">The network protocol of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] connection.</span></span> <span data-ttu-id="b0894-127">若要对此进行更改，请使用所需的连接属性再次连接。</span><span class="sxs-lookup"><span data-stu-id="b0894-127">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="b0894-128">**网络数据包大小**</span><span class="sxs-lookup"><span data-stu-id="b0894-128">**Network Packet Size**</span></span>  
 <span data-ttu-id="b0894-129">与服务器通信时所使用的数据包的大小。</span><span class="sxs-lookup"><span data-stu-id="b0894-129">The packet size used when communicating with the server.</span></span> <span data-ttu-id="b0894-130">若要对此进行更改，请使用所需的连接属性再次连接。</span><span class="sxs-lookup"><span data-stu-id="b0894-130">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="b0894-131">**连接超时**</span><span class="sxs-lookup"><span data-stu-id="b0894-131">**Connection Timeout**</span></span>  
 <span data-ttu-id="b0894-132">连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 时，在发生超时并向用户返回连接失败错误之前等待的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="b0894-132">The amount of time is seconds to wait when connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before timing out and returning a failure to connect error to the user.</span></span> <span data-ttu-id="b0894-133">若要对此进行更改，请使用所需的连接属性再次连接。</span><span class="sxs-lookup"><span data-stu-id="b0894-133">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="b0894-134">**执行超时**</span><span class="sxs-lookup"><span data-stu-id="b0894-134">**Execution Timeout**</span></span>  
 <span data-ttu-id="b0894-135">在服务器上完成任务执行之前等待的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="b0894-135">The amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="b0894-136">若要对此进行更改，请使用所需的连接属性再次连接。</span><span class="sxs-lookup"><span data-stu-id="b0894-136">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="b0894-137">**已加密**</span><span class="sxs-lookup"><span data-stu-id="b0894-137">**Encrypted**</span></span>  
 <span data-ttu-id="b0894-138">当前的连接是否经过加密。</span><span class="sxs-lookup"><span data-stu-id="b0894-138">Whether the current connection is encrypted.</span></span> <span data-ttu-id="b0894-139">若要对此进行更改，请使用所需的连接属性再次连接。</span><span class="sxs-lookup"><span data-stu-id="b0894-139">To change this, connect again with the desired connection properties.</span></span>  
  
## <a name="product-category"></a><span data-ttu-id="b0894-140">产品类别</span><span class="sxs-lookup"><span data-stu-id="b0894-140">Product Category</span></span>  
 <span data-ttu-id="b0894-141">查看当前连接的产品属性。</span><span class="sxs-lookup"><span data-stu-id="b0894-141">View product properties for the current connection.</span></span> <span data-ttu-id="b0894-142">这些属性描述服务器产品、版本、实例名和排序规则。</span><span class="sxs-lookup"><span data-stu-id="b0894-142">These properties describe the server product, version, instance name, and collation.</span></span> <span data-ttu-id="b0894-143">这些属性在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装过程中进行设置。</span><span class="sxs-lookup"><span data-stu-id="b0894-143">The properties are set during [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="b0894-144">**产品名称**</span><span class="sxs-lookup"><span data-stu-id="b0894-144">**Product Name**</span></span>  
 <span data-ttu-id="b0894-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的产品名称。</span><span class="sxs-lookup"><span data-stu-id="b0894-145">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product name.</span></span>  
  
 <span data-ttu-id="b0894-146">**产品版本**</span><span class="sxs-lookup"><span data-stu-id="b0894-146">**Product Version**</span></span>  
 <span data-ttu-id="b0894-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的产品版本。</span><span class="sxs-lookup"><span data-stu-id="b0894-147">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product version.</span></span>  
  
 <span data-ttu-id="b0894-148">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="b0894-148">**Server Name**</span></span>  
 <span data-ttu-id="b0894-149">运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="b0894-149">The name of the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b0894-150">**Instance Name**</span><span class="sxs-lookup"><span data-stu-id="b0894-150">**Instance Name**</span></span>  
 <span data-ttu-id="b0894-151">服务器的实例名称。</span><span class="sxs-lookup"><span data-stu-id="b0894-151">The instance name of the server.</span></span> <span data-ttu-id="b0894-152">默认实例为空白。</span><span class="sxs-lookup"><span data-stu-id="b0894-152">The default instance is blank.</span></span>  
  
 <span data-ttu-id="b0894-153">**语言**</span><span class="sxs-lookup"><span data-stu-id="b0894-153">**Language**</span></span>  
 <span data-ttu-id="b0894-154">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 产品的语言版本。</span><span class="sxs-lookup"><span data-stu-id="b0894-154">The language version of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product.</span></span>  
  
 <span data-ttu-id="b0894-155">**排序规则**</span><span class="sxs-lookup"><span data-stu-id="b0894-155">**Collation**</span></span>  
 <span data-ttu-id="b0894-156">服务器的排序规则。</span><span class="sxs-lookup"><span data-stu-id="b0894-156">The collation of the server.</span></span>  
  
## <a name="server-environment-category"></a><span data-ttu-id="b0894-157">服务器环境类别</span><span class="sxs-lookup"><span data-stu-id="b0894-157">Server Environment Category</span></span>  
 <span data-ttu-id="b0894-158">查看当前连接与服务器硬件和操作系统相关的服务器环境属性。</span><span class="sxs-lookup"><span data-stu-id="b0894-158">View server environment properties for the current connection related to the server hardware and operating system.</span></span> <span data-ttu-id="b0894-159">这些属性不能使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]进行配置。</span><span class="sxs-lookup"><span data-stu-id="b0894-159">The properties cannot be configured by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b0894-160">**计算机名称**</span><span class="sxs-lookup"><span data-stu-id="b0894-160">**Computer Name**</span></span>  
 <span data-ttu-id="b0894-161">运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的服务器计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="b0894-161">The name of the server computer that is running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b0894-162">**平台**</span><span class="sxs-lookup"><span data-stu-id="b0894-162">**Platform**</span></span>  
 <span data-ttu-id="b0894-163">服务器的操作系统名称、制造商名称和 CPU 系列。</span><span class="sxs-lookup"><span data-stu-id="b0894-163">The operating system name, manufacturer name, and CPU family of the server.</span></span>  
  
 <span data-ttu-id="b0894-164">**操作系统**</span><span class="sxs-lookup"><span data-stu-id="b0894-164">**Operating System**</span></span>  
 <span data-ttu-id="b0894-165">服务器上安装的 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 的版本。</span><span class="sxs-lookup"><span data-stu-id="b0894-165">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows version installed on the server.</span></span>  
  
 <span data-ttu-id="b0894-166">**Processors**</span><span class="sxs-lookup"><span data-stu-id="b0894-166">**Processors**</span></span>  
 <span data-ttu-id="b0894-167">服务器上处理器的数量。</span><span class="sxs-lookup"><span data-stu-id="b0894-167">The number of processors on the server.</span></span>  
  
 <span data-ttu-id="b0894-168">**Operating System Memory**</span><span class="sxs-lookup"><span data-stu-id="b0894-168">**Operating System Memory**</span></span>  
 <span data-ttu-id="b0894-169">服务器上物理内存的总量 (MB)。</span><span class="sxs-lookup"><span data-stu-id="b0894-169">The total amount of physical memory on the server, in megabytes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0894-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0894-170">See Also</span></span>  
 <span data-ttu-id="b0894-171">[SQL Server Management Studio 中的属性页](../ssms/property-pages-in-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b0894-171">[Property Pages in SQL Server Management Studio](../ssms/property-pages-in-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="b0894-172">连接到服务器（“登录”页）数据库引擎</span><span class="sxs-lookup"><span data-stu-id="b0894-172">Connect to Server &#40;Login Page&#41; Database Engine</span></span>](../ssms/f1-help/connect-to-server-login-page-database-engine.md)  
  
  
