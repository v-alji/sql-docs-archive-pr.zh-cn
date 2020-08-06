---
title: Change Data Capture Service for Oracle by Attunity | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68e68e9edd91bd1d0c718b32e29c3b29f74778c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587560"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="44619-102">Change Data Capture Service for Oracle by Attunity</span><span class="sxs-lookup"><span data-stu-id="44619-102">Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="44619-103">Oracle CDC 服务是一种 Windows 服务，该服务将扫描 Oracle 事务日志并将对有关 Oracle 表的更改捕获到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更改表中。</span><span class="sxs-lookup"><span data-stu-id="44619-103">The CDC Service for Oracle is a Windows service that scans Oracle transaction logs and captures changes to Oracle tables of interest into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables.</span></span> <span data-ttu-id="44619-104">存储从 Oracle 捕获的更改的 SQL 更改表具有与本机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 变更数据捕获功能使用的更改表相同的类型。</span><span class="sxs-lookup"><span data-stu-id="44619-104">The SQL change tables where the changes captured from Oracle are stored are the same type of change tables used in the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Change Data Capture feature.</span></span> <span data-ttu-id="44619-105">这使得使用这些更改就像使用对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库进行的更改一样简单。</span><span class="sxs-lookup"><span data-stu-id="44619-105">This makes consuming these changes as easy as consuming changes made to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="44619-106">安装</span><span class="sxs-lookup"><span data-stu-id="44619-106">Installation</span></span>  
 <span data-ttu-id="44619-107">Oracle CDC 服务可以安装在对要捕获的源 Oracle 数据库以及目标 CDC 数据库所在的目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例具有访问权限的任何支持的 Windows 计算机上。</span><span class="sxs-lookup"><span data-stu-id="44619-107">The CDC Service for Oracle can be installed on any supported Windows computer with access to the source Oracle database(s) being captured and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the target CDC database resides.</span></span> <span data-ttu-id="44619-108">CDC 服务不需要 Oracle 数据库或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的本地安装，只需要其支持的客户端。</span><span class="sxs-lookup"><span data-stu-id="44619-108">The CDC Service does not need a local installation of the Oracle database or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, only their supported clients.</span></span> <span data-ttu-id="44619-109">有关安装所需数据库组件的位置的信息，请参阅本主题中的 **数据库必备组件** 。</span><span class="sxs-lookup"><span data-stu-id="44619-109">For information about where to install the required database components, see **Database Prerequisites** in this topic.</span></span>  
  
 <span data-ttu-id="44619-110">用于 Oracle 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 服务的安装会将服务配置 UI 和服务程序放置于所选位置中。</span><span class="sxs-lookup"><span data-stu-id="44619-110">The installation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service for Oracle places the service configuration UI and the service program in the selected location.</span></span> <span data-ttu-id="44619-111">使用 Oracle CDC 服务配置控制台单独配置 Oracle CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="44619-111">The CDC Service for Oracle is configured separately using the Oracle CDC Service Configuration Console.</span></span> <span data-ttu-id="44619-112">有关配置 Oracle CDC 服务的详细信息，请参阅 [Change Data Capture Service for Oracle by Attunity F1 帮助](change-data-capture-service-for-oracle-by-attunity-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="44619-112">For more information on configuring the Oracle CDC Service, see [Change Data Capture Service for Oracle by Attunity F1 Help](change-data-capture-service-for-oracle-by-attunity-f1-help.md).</span></span>  
  
 <span data-ttu-id="44619-113">若要安装 Oracle CDC 服务，请从 SQL Server 安装媒体中手动运行**AttunityOracleCdcService.msi** 。</span><span class="sxs-lookup"><span data-stu-id="44619-113">To install the CDC Service for Oracle, manually run **AttunityOracleCdcService.msi** from the SQL Server installation media.</span></span> <span data-ttu-id="44619-114">适用于 x86 和 x64 的安装包位于 SQL Server 安装媒体上的 \*\*.\Tools\AttunityCDCOracle \\ \*\*中。</span><span class="sxs-lookup"><span data-stu-id="44619-114">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
 <span data-ttu-id="44619-115">Oracle CDC 服务可以安装在安装了 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client 的任何支持的 Windows 计算机上；它无需安装在安装有目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的那一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="44619-115">The CDC Service for Oracle can be installed on any supported Windows computer where the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client is installed; it does not need to be installed on the same computer where the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="44619-116">支持的 Windows 环境</span><span class="sxs-lookup"><span data-stu-id="44619-116">Supported Windows Environments</span></span>  
 <span data-ttu-id="44619-117">Change Data Capture Service for Oracle by Attunity 可在以下 Windows 环境中运行：</span><span class="sxs-lookup"><span data-stu-id="44619-117">The Change Data Capture Service for Oracle by Attunity can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="44619-118">Windows 8</span><span class="sxs-lookup"><span data-stu-id="44619-118">Windows 8</span></span>  
  
-   <span data-ttu-id="44619-119">Windows 7 32 位 (x86) 和 64 位 (x64)</span><span class="sxs-lookup"><span data-stu-id="44619-119">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="44619-120">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="44619-120">Windows Server 2012</span></span>  
  
-   <span data-ttu-id="44619-121">带有 Service Pack 1 的 Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="44619-121">Windows Server 2008 R2 with Service Pack 1</span></span>  
  
-   <span data-ttu-id="44619-122">具有 Service Pack 2 的 Windows Server 2008 32 位 (x86) 和 64 位 (x64)</span><span class="sxs-lookup"><span data-stu-id="44619-122">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="44619-123">数据库必备组件</span><span class="sxs-lookup"><span data-stu-id="44619-123">Database Prerequisites</span></span>  
 <span data-ttu-id="44619-124">若要使用 Oracle CDC 服务，您必须安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle 软件。</span><span class="sxs-lookup"><span data-stu-id="44619-124">To work with the CDC Service for Oracle you must install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle software.</span></span> <span data-ttu-id="44619-125">这是应从 Oracle 获取并在安装 Oracle CDC 服务之前安装的必备组件。</span><span class="sxs-lookup"><span data-stu-id="44619-125">This is a prerequisite that should be obtained from Oracle and installed before installing the Oracle CDC Service.</span></span> <span data-ttu-id="44619-126">此外，您需要使用 SQL Server 安装程序安装 SQL Server ODBC 客户端。</span><span class="sxs-lookup"><span data-stu-id="44619-126">Additionally, you need to install the SQL Server ODBC Client using SQL Server Setup.</span></span>  
  
 <span data-ttu-id="44619-127">Oracle CDC 服务支持以下版本：</span><span class="sxs-lookup"><span data-stu-id="44619-127">The CDC Service for Oracle supports the following versions:</span></span>  
  
### <a name="source-oracle-database"></a><span data-ttu-id="44619-128">源 Oracle 数据库</span><span class="sxs-lookup"><span data-stu-id="44619-128">Source Oracle Database</span></span>  
  
-   <span data-ttu-id="44619-129">Oracle 数据库 11x，任意版本</span><span class="sxs-lookup"><span data-stu-id="44619-129">Oracle Database 11x, any version</span></span>  
  
-   <span data-ttu-id="44619-130">Oracle 数据库 10x，任意版本</span><span class="sxs-lookup"><span data-stu-id="44619-130">Oracle Database 10x, any version</span></span>  
  
### <a name="target-sql-server-database"></a><span data-ttu-id="44619-131">目标 SQL Server 数据库</span><span class="sxs-lookup"><span data-stu-id="44619-131">Target SQL Server Database</span></span>  
 <span data-ttu-id="44619-132">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="44619-132">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="44619-133">运行安装程序</span><span class="sxs-lookup"><span data-stu-id="44619-133">Running the Installation Program</span></span>  
 <span data-ttu-id="44619-134">若要安装 Oracle CDC 服务，请打开针对您正使用的 Windows 平台（32/64 位）的安装向导，并且按照屏幕上的指示执行。</span><span class="sxs-lookup"><span data-stu-id="44619-134">To install the CDC Service for Oracle, open the installation wizard for the Windows platform you are using (32/64-bit) and follow the directions on the screen.</span></span>  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="44619-135">卸载 Change Data Capture Service for Oracle by Attunity</span><span class="sxs-lookup"><span data-stu-id="44619-135">Uninstalling Change Data Capture Service for Oracle by Attunity</span></span>  
 <span data-ttu-id="44619-136">可使用“控制面板”的“程序和功能”卸载 CDC CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="44619-136">You uninstall the CDC Service for Oracle using Control Panel, Programs and Features.</span></span>  
  
 <span data-ttu-id="44619-137">卸载该 CDC 服务不会删除已创建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="44619-137">Uninstalling the CDC Service does not delete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases created.</span></span> <span data-ttu-id="44619-138">若要完全删除该工具，您必须删除已在您使用的目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建的 MSXDBCDC 数据库和特定的 CDC 数据库。</span><span class="sxs-lookup"><span data-stu-id="44619-138">For complete removal of the tool, you must remove the MSXDBCDC database and the specific CDC databases that were created in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you worked with.</span></span>  
  
 <span data-ttu-id="44619-139">如果您从一台计算机卸载该 CDC 服务软件并且将其安装在另一台计算机上，则仅需提供以下定义：</span><span class="sxs-lookup"><span data-stu-id="44619-139">If you uninstall the CDC Service software from one machine and install it on another computer, you only need to provide the following definitions:</span></span>  
  
-   <span data-ttu-id="44619-140">服务帐户</span><span class="sxs-lookup"><span data-stu-id="44619-140">Service account</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="44619-141">连接字符串和凭据</span><span class="sxs-lookup"><span data-stu-id="44619-141">connect string and credentials</span></span>  
  
-   <span data-ttu-id="44619-142">主密码</span><span class="sxs-lookup"><span data-stu-id="44619-142">The master password</span></span>  
  
 <span data-ttu-id="44619-143">所有其他定义均存储于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中并且可从其他计算机上之前的安装获取。</span><span class="sxs-lookup"><span data-stu-id="44619-143">All the other definitions are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and are available from the previous installation on another computer.</span></span>  
  
## <a name="in-this-documentation"></a><span data-ttu-id="44619-144">本文档内容</span><span class="sxs-lookup"><span data-stu-id="44619-144">In This Documentation</span></span>  
  
-   [<span data-ttu-id="44619-145">Change Data Capture Service for Oracle by Attunity 系统体系结构</span><span class="sxs-lookup"><span data-stu-id="44619-145">Change Data Capture Service for Oracle by Attunity System Architecture</span></span>](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [<span data-ttu-id="44619-146">Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="44619-146">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
-   [<span data-ttu-id="44619-147">Change Data Capture Service for Oracle by Attunity F1 帮助</span><span class="sxs-lookup"><span data-stu-id="44619-147">Change Data Capture Service for Oracle by Attunity F1 Help</span></span>](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [<span data-ttu-id="44619-148">Change Data Capture Service for Oracle by Attunity 操作指南</span><span class="sxs-lookup"><span data-stu-id="44619-148">Change Data Capture Service for Oracle by Attunity How to Guide</span></span>](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a><span data-ttu-id="44619-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44619-149">See Also</span></span>  
 [<span data-ttu-id="44619-150">使用 Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="44619-150">Working with the Oracle CDC Service</span></span>](working-with-the-oracle-cdc-service.md)  
  
  
