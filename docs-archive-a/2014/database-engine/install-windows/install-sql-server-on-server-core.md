---
title: 在 Server Core 上安装 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2614c43bb763757db7db46b1c7a966221da96f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688187"
---
# <a name="install-sql-server-2014-on-server-core"></a><span data-ttu-id="5d450-102">在 Server Core 上安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="5d450-102">Install SQL Server 2014 on Server Core</span></span>
  <span data-ttu-id="5d450-103">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安装上安装 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d450-103">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="5d450-104">本主题提供用于在 Server Core 上安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的特定于安装的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5d450-104">This topic provides setup-specific details for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core.</span></span>  
  
 <span data-ttu-id="5d450-105">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 操作系统的 Server Core 安装选项提供了用于运行特定服务器角色的最小环境。</span><span class="sxs-lookup"><span data-stu-id="5d450-105">The Server Core installation option for the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] operating system provides a minimal environment for running specific server roles.</span></span> <span data-ttu-id="5d450-106">这将有助于减少维护和管理需求以及针对这些服务器角色的攻击面。</span><span class="sxs-lookup"><span data-stu-id="5d450-106">This helps to reduce maintenance and management requirements and the attack surface for those server roles.</span></span> <span data-ttu-id="5d450-107">有关在上实施的服务器核心的详细信息 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] ，请参阅[server Core For Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (https://go.microsoft.com/fwlink/?LinkId=202439) 。</span><span class="sxs-lookup"><span data-stu-id="5d450-107">For more information on Server Core as implemented on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], see [Server Core for Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (https://go.microsoft.com/fwlink/?LinkId=202439).</span></span> <span data-ttu-id="5d450-108">有关在 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]上实现 Server Core 的详细信息，请参阅 [Server Core for Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="5d450-108">For more information on Server Core as implemented on [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Server Core for Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5d450-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="5d450-109">Prerequisites</span></span>  
  
|<span data-ttu-id="5d450-110">要求</span><span class="sxs-lookup"><span data-stu-id="5d450-110">Requirement</span></span>|<span data-ttu-id="5d450-111">如何安装</span><span class="sxs-lookup"><span data-stu-id="5d450-111">How to install</span></span>|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="5d450-112">2.0 SP2</span><span class="sxs-lookup"><span data-stu-id="5d450-112">2.0 SP2</span></span>|<span data-ttu-id="5d450-113">包含在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 和 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的 Server Core 安装中。</span><span class="sxs-lookup"><span data-stu-id="5d450-113">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="5d450-114">如果未启用，则安装程序将在默认情况下启用它。</span><span class="sxs-lookup"><span data-stu-id="5d450-114">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="5d450-115">无法在计算机上并行运行 2.0、3.0 和 3.5 版。</span><span class="sxs-lookup"><span data-stu-id="5d450-115">It is not possible to run versions 2.0, 3.0, and 3.5 side by side on a computer.</span></span> <span data-ttu-id="5d450-116">在安装 .NET Framework 3.5 SP1 时，将自动获得 2.0 和 3.0 层。</span><span class="sxs-lookup"><span data-stu-id="5d450-116">When you install the .NET Framework 3.5 SP1, you get the 2.0 and 3.0 layers automatically.</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="5d450-117">3.5 SP1 完整配置文件</span><span class="sxs-lookup"><span data-stu-id="5d450-117">3.5 SP1 Full Profile</span></span>|<span data-ttu-id="5d450-118">包含在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 的 Server Core 安装中。</span><span class="sxs-lookup"><span data-stu-id="5d450-118">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> <span data-ttu-id="5d450-119">如果未启用，则安装程序将在默认情况下启用它。</span><span class="sxs-lookup"><span data-stu-id="5d450-119">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="5d450-120">在安装有 Windows Server 操作系统的计算机上，您必须在运行安装程序前下载并安装 .NET Framework 3.5 SP1，以便安装依赖于 .NET 3.5 SP1 的组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-120">On a computer with Windows server operating system you must download and install .NET Framework 3.5 SP1 before you run Setup, to install components dependent on .NET 3.5 SP1.</span></span><br /><br /> <span data-ttu-id="5d450-121">有关如何在中获取和启用 .NET Framework 3.5 的建议和指南的详细信息 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] ，请参阅 ([Microsoft .NET Framework 3.5 部署注意事项](https://msdn.microsoft.com/library/windows/hardware/hh975396) https://msdn.microsoft.com/library/windows/hardware/hh975396) 。</span><span class="sxs-lookup"><span data-stu-id="5d450-121">For more information about the recommendations and guidance on how to acquire and enable .NET Framework 3.5 in [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Microsoft .NET Framework 3.5 Deployment Considerations](https://msdn.microsoft.com/library/windows/hardware/hh975396) (https://msdn.microsoft.com/library/windows/hardware/hh975396).</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="5d450-122">4 Server Core 配置文件</span><span class="sxs-lookup"><span data-stu-id="5d450-122">4 Server Core Profile</span></span>|<span data-ttu-id="5d450-123">除 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之外，所有 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]版本的安装程序均将 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core 配置文件作为必备组件进行安装。</span><span class="sxs-lookup"><span data-stu-id="5d450-123">For all editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], Setup installs the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile as a prerequisite.</span></span><br /><br /> <span data-ttu-id="5d450-124">对于 [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] ，请 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 从[Microsoft .NET Framework 4 (独立安装程序) ](https://www.microsoft.com/download/details.aspx?id=17718)中下载 4 server core 配置文件以获取服务器核心 (https://www.microsoft.com/download/details.aspx?id=17718) ，并在继续安装之前安装它。</span><span class="sxs-lookup"><span data-stu-id="5d450-124">For [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)], download the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile from [Microsoft .NET Framework 4 (Standalone Installer) for Server Core](https://www.microsoft.com/download/details.aspx?id=17718) (https://www.microsoft.com/download/details.aspx?id=17718), and install it before you proceed with the setup.</span></span>|  
|<span data-ttu-id="5d450-125">Windows Installer 4.5</span><span class="sxs-lookup"><span data-stu-id="5d450-125">Windows Installer 4.5</span></span>|<span data-ttu-id="5d450-126">随 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 和 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的 Server Core 一同提供。</span><span class="sxs-lookup"><span data-stu-id="5d450-126">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
|<span data-ttu-id="5d450-127">Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="5d450-127">Windows PowerShell 2.0</span></span>|<span data-ttu-id="5d450-128">随 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 和 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的 Server Core 一同提供。</span><span class="sxs-lookup"><span data-stu-id="5d450-128">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
  
##  <a name="supported-features"></a><a name="BK_SupportedFeatures"></a><span data-ttu-id="5d450-129">支持的功能</span><span class="sxs-lookup"><span data-stu-id="5d450-129">Supported Features</span></span>  
 <span data-ttu-id="5d450-130">使用下表可以查找 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安装上的 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]所支持的功能。</span><span class="sxs-lookup"><span data-stu-id="5d450-130">Use the following table to find which features are supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|<span data-ttu-id="5d450-131">Feature</span><span class="sxs-lookup"><span data-stu-id="5d450-131">Feature</span></span>|<span data-ttu-id="5d450-132">支持</span><span class="sxs-lookup"><span data-stu-id="5d450-132">Supported</span></span>|  
|-------------|---------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="5d450-133">服务</span><span class="sxs-lookup"><span data-stu-id="5d450-133">Services</span></span>|<span data-ttu-id="5d450-134">是</span><span class="sxs-lookup"><span data-stu-id="5d450-134">Yes</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d450-135">Replication</span><span class="sxs-lookup"><span data-stu-id="5d450-135">Replication</span></span>|<span data-ttu-id="5d450-136">是</span><span class="sxs-lookup"><span data-stu-id="5d450-136">Yes</span></span>|  
|<span data-ttu-id="5d450-137">全文搜索</span><span class="sxs-lookup"><span data-stu-id="5d450-137">Full Text Search</span></span>|<span data-ttu-id="5d450-138">是</span><span class="sxs-lookup"><span data-stu-id="5d450-138">Yes</span></span>|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|<span data-ttu-id="5d450-139">是</span><span class="sxs-lookup"><span data-stu-id="5d450-139">Yes</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|<span data-ttu-id="5d450-140">否</span><span class="sxs-lookup"><span data-stu-id="5d450-140">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d450-141">Data Tools (SSDT)</span><span class="sxs-lookup"><span data-stu-id="5d450-141">Data Tools (SSDT)</span></span>|<span data-ttu-id="5d450-142">否</span><span class="sxs-lookup"><span data-stu-id="5d450-142">No</span></span>|  
|<span data-ttu-id="5d450-143">客户端工具连接</span><span class="sxs-lookup"><span data-stu-id="5d450-143">Client Tools Connectivity</span></span>|<span data-ttu-id="5d450-144">是</span><span class="sxs-lookup"><span data-stu-id="5d450-144">Yes</span></span>|  
|<span data-ttu-id="5d450-145">Integration Services Server<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="5d450-145">Integration Services Server<sup>[1]</sup></span></span>|<span data-ttu-id="5d450-146">是</span><span class="sxs-lookup"><span data-stu-id="5d450-146">Yes</span></span>|  
|<span data-ttu-id="5d450-147">客户端工具向后兼容性</span><span class="sxs-lookup"><span data-stu-id="5d450-147">Client Tools Backward Compatibility</span></span>|<span data-ttu-id="5d450-148">否</span><span class="sxs-lookup"><span data-stu-id="5d450-148">No</span></span>|  
|<span data-ttu-id="5d450-149">客户端工具 SDK</span><span class="sxs-lookup"><span data-stu-id="5d450-149">Client Tools SDK</span></span>|<span data-ttu-id="5d450-150">否</span><span class="sxs-lookup"><span data-stu-id="5d450-150">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d450-151">联机丛书</span><span class="sxs-lookup"><span data-stu-id="5d450-151">Books Online</span></span>|<span data-ttu-id="5d450-152">否</span><span class="sxs-lookup"><span data-stu-id="5d450-152">No</span></span>|  
|<span data-ttu-id="5d450-153">管理工具 - 基本</span><span class="sxs-lookup"><span data-stu-id="5d450-153">Management Tools - Basic</span></span>|<span data-ttu-id="5d450-154">仅限远程<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="5d450-154">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="5d450-155">管理工具 - 完整</span><span class="sxs-lookup"><span data-stu-id="5d450-155">Management Tools - Complete</span></span>|<span data-ttu-id="5d450-156">仅限远程<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="5d450-156">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="5d450-157">Distributed Replay 控制器</span><span class="sxs-lookup"><span data-stu-id="5d450-157">Distributed Replay Controller</span></span>|<span data-ttu-id="5d450-158">否</span><span class="sxs-lookup"><span data-stu-id="5d450-158">No</span></span>|  
|<span data-ttu-id="5d450-159">Distributed Replay 客户端</span><span class="sxs-lookup"><span data-stu-id="5d450-159">Distributed Replay Client</span></span>|<span data-ttu-id="5d450-160">仅限远程<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="5d450-160">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="5d450-161">SQL 客户端连接 SDK</span><span class="sxs-lookup"><span data-stu-id="5d450-161">SQL Client Connectivity SDK</span></span>|<span data-ttu-id="5d450-162">是</span><span class="sxs-lookup"><span data-stu-id="5d450-162">Yes</span></span>|  
|<span data-ttu-id="5d450-163">Microsoft Sync Framework</span><span class="sxs-lookup"><span data-stu-id="5d450-163">Microsoft Sync Framework</span></span>|<span data-ttu-id="5d450-164">是<sup>[3]</sup></span><span class="sxs-lookup"><span data-stu-id="5d450-164">Yes<sup>[3]</sup></span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|<span data-ttu-id="5d450-165">否</span><span class="sxs-lookup"><span data-stu-id="5d450-165">No</span></span>|  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|<span data-ttu-id="5d450-166">否</span><span class="sxs-lookup"><span data-stu-id="5d450-166">No</span></span>|  
  
 <span data-ttu-id="5d450-167"><sup>[1]</sup>有关中新 Integration Services 服务器及其功能的详细信息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，请参阅[INTEGRATION SERVICES &#40;SSIS&#41; 服务器](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5d450-167"><sup>[1]</sup>For more information about the new Integration Services Server and its features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Integration Services &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="5d450-168"><sup>[2]</sup>不支持在 Server Core 上安装这些功能。</span><span class="sxs-lookup"><span data-stu-id="5d450-168"><sup>[2]</sup>Installation of these features on Server Core is not supported.</span></span> <span data-ttu-id="5d450-169">可以在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 之外的服务器上安装这些组件，然后将这些组件连接到 Server Core 上安装的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="5d450-169">These components can be installed on a different server that is not [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, and connected to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] services installed on Server Core.</span></span>  
  
 <span data-ttu-id="5d450-170"><sup>[3]</sup>Microsoft Sync Framework 未包含在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装包中。</span><span class="sxs-lookup"><span data-stu-id="5d450-170"><sup>[3]</sup>Microsoft Sync Framework is not included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation package.</span></span> <span data-ttu-id="5d450-171">你可以从该[Microsoft 下载中心](https://go.microsoft.com/fwlink/?LinkId=221788) (页面下载适当版本的 Sync Framework https://go.microsoft.com/fwlink/?LinkId=221788) ，并将其安装在运行 SP1 或的 Server Core 安装的计算机上 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d450-171">You can download the appropriate version of Sync Framework from this [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=221788) (https://go.microsoft.com/fwlink/?LinkId=221788) page and install it on a computer that is running Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
## <a name="supported-scenario-matrix"></a><span data-ttu-id="5d450-172">支持的方案矩阵</span><span class="sxs-lookup"><span data-stu-id="5d450-172">Supported Scenario Matrix</span></span>  
 <span data-ttu-id="5d450-173">下表显示在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安装上安装 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]时支持的方案矩阵。</span><span class="sxs-lookup"><span data-stu-id="5d450-173">The following table shows the supported scenario matrix for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d450-174">版本</span><span class="sxs-lookup"><span data-stu-id="5d450-174">editions</span></span>|<span data-ttu-id="5d450-175">所有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64 位版本<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="5d450-175">All [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64-bit editions<sup>[1]</sup></span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d450-176">语言</span><span class="sxs-lookup"><span data-stu-id="5d450-176">language</span></span>|<span data-ttu-id="5d450-177">所有语言</span><span class="sxs-lookup"><span data-stu-id="5d450-177">All languages</span></span>|  
|<span data-ttu-id="5d450-178">操作系统语言/区域设置（组合）上的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 语言</span><span class="sxs-lookup"><span data-stu-id="5d450-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] language on OS language/locale (combination)</span></span>|<span data-ttu-id="5d450-179">JPN（日语）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-179">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on JPN (Japanese) Windows</span></span><br /><br /> <span data-ttu-id="5d450-180">GER（德语）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-180">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on GER (German) Windows</span></span><br /><br /> <span data-ttu-id="5d450-181">CHS（中文 - 中国）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-181">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on CHS (Chinese-China) Windows</span></span><br /><br /> <span data-ttu-id="5d450-182">ARA（阿拉伯语 (SA)）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-182">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ARA (Arabic (SA)) Windows</span></span><br /><br /> <span data-ttu-id="5d450-183">THA（泰语）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-183">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on THA (Thai) Windows</span></span><br /><br /> <span data-ttu-id="5d450-184">TRK（土耳其语）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-184">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on TRK (Turkish) Windows</span></span><br /><br /> <span data-ttu-id="5d450-185">pt-PT（葡萄牙语 - 葡萄牙）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-185">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on pt-PT (Portuguese Portugal) Windows</span></span><br /><br /> <span data-ttu-id="5d450-186">ENG（英语）Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-186">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ENG (English) Windows</span></span>|  
|<span data-ttu-id="5d450-187">Windows 版本</span><span class="sxs-lookup"><span data-stu-id="5d450-187">Windows edition</span></span>|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="5d450-188">64 位 x64 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5d450-188">64-bit x64 Datacenter</span></span><br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="5d450-189">64 位 x64 Standard</span><span class="sxs-lookup"><span data-stu-id="5d450-189">64-bit x64 Standard</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="5d450-190">SP1 64 位 x64 Data Center Server Core</span><span class="sxs-lookup"><span data-stu-id="5d450-190">SP1 64-bit x64 Data Center Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="5d450-191">SP1 64 位 x64 Enterprise Server Core</span><span class="sxs-lookup"><span data-stu-id="5d450-191">SP1 64-bit x64 Enterprise Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="5d450-192">SP1 64 位 x64 Standard Server Core</span><span class="sxs-lookup"><span data-stu-id="5d450-192">SP1 64-bit x64 Standard Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="5d450-193">SP1 64 位 x64 Web Server Core</span><span class="sxs-lookup"><span data-stu-id="5d450-193">SP1 64-bit x64 Web Server Core</span></span>|  
  
 <span data-ttu-id="5d450-194"><sup>[1]</sup>[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]不支持在 Server Core 上安装版本32位版本。</span><span class="sxs-lookup"><span data-stu-id="5d450-194"><sup>[1]</sup>Installing the 32-bit version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] editions is not supported on Server Core.</span></span>  
  
## <a name="upgrading"></a><span data-ttu-id="5d450-195">正在升级</span><span class="sxs-lookup"><span data-stu-id="5d450-195">Upgrading</span></span>  
 <span data-ttu-id="5d450-196">在 Server Core 安装上，支持从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 升级到 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d450-196">On Server Core installations, upgrading from [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] is supported.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="5d450-197">安装</span><span class="sxs-lookup"><span data-stu-id="5d450-197">Installation</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="5d450-198">不支持在 Server Core 操作系统上使用安装向导进行安装。</span><span class="sxs-lookup"><span data-stu-id="5d450-198">does not support setup by using the installation wizard on the Server Core operating system.</span></span> <span data-ttu-id="5d450-199">在 Server Core 上进行安装时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序支持完全静默模式（通过使用 /Q 参数）或简单静默模式（通过使用 /QS 参数）。</span><span class="sxs-lookup"><span data-stu-id="5d450-199">When installing on Server Core, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup supports full quiet mode by using the /Q parameter, or Quiet Simple mode by using the /QS parameter.</span></span> <span data-ttu-id="5d450-200">有关详细信息，请参阅 [从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="5d450-200">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="5d450-201">不能在运行 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 的计算机上与早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起并行安装。</span><span class="sxs-lookup"><span data-stu-id="5d450-201">cannot be installed side-by-side with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core.</span></span>  
  
 <span data-ttu-id="5d450-202">无论使用哪种安装方法，您都需要作为个人或代表实体确认接受软件许可条款，除非您对于软件的使用受单独的协议（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 批量许可协议或与 ISV 或 OEM 之间的第三方协议）管辖。</span><span class="sxs-lookup"><span data-stu-id="5d450-202">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="5d450-203">将在安装程序用户界面中显示许可条款，供您审核审阅和接受。</span><span class="sxs-lookup"><span data-stu-id="5d450-203">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="5d450-204">使用 /Q 或 /QS 参数进行无人参与安装时，必须包含 /IACCEPTSQLSERVERLICENSETERMS 参数。</span><span class="sxs-lookup"><span data-stu-id="5d450-204">Unattended installations (using the /Q or /QS parameters) must include the /IACCEPTSQLSERVERLICENSETERMS parameter.</span></span> <span data-ttu-id="5d450-205">可以通过 [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkId=148209)（Microsoft 软件许可条款）单独查看许可条款。</span><span class="sxs-lookup"><span data-stu-id="5d450-205">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkId=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d450-206">根据您接收软件的方式（例如，通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 批量许可），您对软件的使用可能受其他条款和条件约束。</span><span class="sxs-lookup"><span data-stu-id="5d450-206">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
 <span data-ttu-id="5d450-207">若要安装特定功能，请使用 /FEATURES 参数并指定父功能或功能值。</span><span class="sxs-lookup"><span data-stu-id="5d450-207">To install specific features, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="5d450-208">有关功能参数及其用法的详细信息，请参阅以下部分。</span><span class="sxs-lookup"><span data-stu-id="5d450-208">For more information about feature parameters and their use, see the following sections.</span></span>  
  
### <a name="feature-parameters"></a><span data-ttu-id="5d450-209">功能参数</span><span class="sxs-lookup"><span data-stu-id="5d450-209">Feature Parameters</span></span>  
  
|<span data-ttu-id="5d450-210">功能参数</span><span class="sxs-lookup"><span data-stu-id="5d450-210">Feature parameter</span></span>|<span data-ttu-id="5d450-211">说明</span><span class="sxs-lookup"><span data-stu-id="5d450-211">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="5d450-212">SQLENGINE</span><span class="sxs-lookup"><span data-stu-id="5d450-212">SQLENGINE</span></span>|<span data-ttu-id="5d450-213">仅安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d450-213">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="5d450-214">复制</span><span class="sxs-lookup"><span data-stu-id="5d450-214">REPLICATION</span></span>|<span data-ttu-id="5d450-215">将复制组件与 [!INCLUDE[ssDE](../../includes/ssde-md.md)]一起安装。</span><span class="sxs-lookup"><span data-stu-id="5d450-215">Installs the Replication component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="5d450-216">FULLTEXT</span><span class="sxs-lookup"><span data-stu-id="5d450-216">FULLTEXT</span></span>|<span data-ttu-id="5d450-217">将全文组件与 [!INCLUDE[ssDE](../../includes/ssde-md.md)]一起安装。</span><span class="sxs-lookup"><span data-stu-id="5d450-217">Installs the FullText component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="5d450-218">AS</span><span class="sxs-lookup"><span data-stu-id="5d450-218">AS</span></span>|<span data-ttu-id="5d450-219">安装所有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-219">Installs all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="5d450-220">IS</span><span class="sxs-lookup"><span data-stu-id="5d450-220">IS</span></span>|<span data-ttu-id="5d450-221">安装所有的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-221">Installs all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="5d450-222">CONN</span><span class="sxs-lookup"><span data-stu-id="5d450-222">CONN</span></span>|<span data-ttu-id="5d450-223">安装连接组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-223">Installs the connectivity components.</span></span>|  
  
 <span data-ttu-id="5d450-224">请参阅以下的功能参数用法示例：</span><span class="sxs-lookup"><span data-stu-id="5d450-224">See the following examples of the usage of feature parameters:</span></span>  
  
|<span data-ttu-id="5d450-225">参数和值</span><span class="sxs-lookup"><span data-stu-id="5d450-225">Parameter and values</span></span>|<span data-ttu-id="5d450-226">说明</span><span class="sxs-lookup"><span data-stu-id="5d450-226">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="5d450-227">/FEATURES=SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5d450-227">/FEATURES=SQLEngine</span></span>|<span data-ttu-id="5d450-228">仅安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d450-228">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="5d450-229">/FEATURES=SQLEngine,FullText</span><span class="sxs-lookup"><span data-stu-id="5d450-229">/FEATURES=SQLEngine,FullText</span></span>|<span data-ttu-id="5d450-230">安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和全文组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-230">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and full-text.</span></span>|  
|<span data-ttu-id="5d450-231">/FEATURES=SQLEngine,Conn</span><span class="sxs-lookup"><span data-stu-id="5d450-231">/FEATURES=SQLEngine,Conn</span></span>|<span data-ttu-id="5d450-232">安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和连接组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-232">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the connectivity components.</span></span>|  
|<span data-ttu-id="5d450-233">/FEATURES=SQLEngine,AS,IS,Conn</span><span class="sxs-lookup"><span data-stu-id="5d450-233">/FEATURES=SQLEngine,AS,IS,Conn</span></span>|<span data-ttu-id="5d450-234">安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]和连接组件。</span><span class="sxs-lookup"><span data-stu-id="5d450-234">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and the connectivity components.</span></span>|  
  
### <a name="installation-options"></a><span data-ttu-id="5d450-235">安装选项</span><span class="sxs-lookup"><span data-stu-id="5d450-235">Installation Options</span></span>  
 <span data-ttu-id="5d450-236">在 Server Core 操作系统上安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 时，安装程序支持以下安装选项：</span><span class="sxs-lookup"><span data-stu-id="5d450-236">The Setup supports the following installation options while installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core operating system:</span></span>  
  
1.  <span data-ttu-id="5d450-237">**从命令行安装**</span><span class="sxs-lookup"><span data-stu-id="5d450-237">**Installation from Command Line**</span></span>  
  
     <span data-ttu-id="5d450-238">若要使用命令提示符安装选项安装特定功能，请使用 /FEATURES 参数并指定父功能或功能值。</span><span class="sxs-lookup"><span data-stu-id="5d450-238">To install specific features using the command prompt installation option, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="5d450-239">以下是在命令行中使用参数的示例：</span><span class="sxs-lookup"><span data-stu-id="5d450-239">The following is an example of using the parameters from the command line:</span></span>  
  
    ```cmd
    setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  <span data-ttu-id="5d450-240">**使用配置文件安装**</span><span class="sxs-lookup"><span data-stu-id="5d450-240">**Installation using Configuration File**</span></span>  
  
     <span data-ttu-id="5d450-241">安装程序仅支持通过命令提示符使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="5d450-241">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="5d450-242">配置文件是具有基本参数结构（名称/值对）和说明性注释的文本文件。</span><span class="sxs-lookup"><span data-stu-id="5d450-242">The configuration file is a text file with the basic structure of a parameter (name/value pair) and a descriptive comment.</span></span> <span data-ttu-id="5d450-243">在命令提示符处指定的配置文件应该具有 .INI 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="5d450-243">The configuration file specified at the command prompt should have an .INI file name extension.</span></span> <span data-ttu-id="5d450-244">请参阅以下 ConfigurationFile.INI 示例：</span><span class="sxs-lookup"><span data-stu-id="5d450-244">See the following examples of ConfigurationFile.INI:</span></span>  
  
    -   <span data-ttu-id="5d450-245">安装 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d450-245">Installing [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
         <span data-ttu-id="5d450-246">以下示例说明了如何安装包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] 的新的独立实例：</span><span class="sxs-lookup"><span data-stu-id="5d450-246">The following example shows how to install a new stand-alone instance that includes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"
        ```  
  
    -   <span data-ttu-id="5d450-247">安装连接组件</span><span class="sxs-lookup"><span data-stu-id="5d450-247">Installing connectivity components</span></span>  
  
         <span data-ttu-id="5d450-248">以下示例说明如何安装连接组件：</span><span class="sxs-lookup"><span data-stu-id="5d450-248">The following example shows how to install the connectivity components:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True
        ```  
  
    -   <span data-ttu-id="5d450-249">安装所有支持的功能</span><span class="sxs-lookup"><span data-stu-id="5d450-249">Installing all supported features</span></span>  
  
         <span data-ttu-id="5d450-250">以下示例说明如何在 Server Core 上安装所有支持的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能：</span><span class="sxs-lookup"><span data-stu-id="5d450-250">The following example shows how to install all supported features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     <span data-ttu-id="5d450-251">以下示例介绍了如何使用配置文件启动安装程序。</span><span class="sxs-lookup"><span data-stu-id="5d450-251">The following examples show how you can launch the Setup using a configuration file.</span></span>  
  
    -   <span data-ttu-id="5d450-252">配置文件</span><span class="sxs-lookup"><span data-stu-id="5d450-252">Configuration file</span></span>  
  
         <span data-ttu-id="5d450-253">以下是有关如何使用配置文件的一些示例：</span><span class="sxs-lookup"><span data-stu-id="5d450-253">Following are some examples of how to use the configuration file:</span></span>  
  
        -   <span data-ttu-id="5d450-254">在命令提示符处指定配置文件：</span><span class="sxs-lookup"><span data-stu-id="5d450-254">To specify the configuration file at the command prompt:</span></span>  
  
        ```cmd
        setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
        -   <span data-ttu-id="5d450-255">在命令提示符处而不是配置文件中指定密码：</span><span class="sxs-lookup"><span data-stu-id="5d450-255">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
        ```cmd
        setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   <span data-ttu-id="5d450-256">DefaultSetup.ini</span><span class="sxs-lookup"><span data-stu-id="5d450-256">DefaultSetup.ini</span></span>  
  
         <span data-ttu-id="5d450-257">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源媒体的根级别的 \x86 和 \x64 文件夹中包含 DefaultSetup.ini 文件，请打开该 DefaultSetup.ini 文件，然后将 *Features* 参数添加到该文件中。</span><span class="sxs-lookup"><span data-stu-id="5d450-257">If you have the DefaultSetup.ini file in the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media, open the DefaultSetup.ini file, and then add the *Features* parameter to the file.</span></span>  
  
         <span data-ttu-id="5d450-258">如果 DefaultSetup.ini 文件不存在，您可以创建该文件并将其复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源介质根级别的 \x86 和 \x64 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d450-258">If the DefaultSetup.ini file does not exist, you can create it and copy it to the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media.</span></span>  
  
## <a name="configuring-remote-access-of-ssnoversion-running-on-server-core"></a><span data-ttu-id="5d450-259">配置运行在 Server Core 上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的远程访问</span><span class="sxs-lookup"><span data-stu-id="5d450-259">Configuring Remote Access of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Running on Server Core</span></span>  
 <span data-ttu-id="5d450-260">执行下述操作以配置运行在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安装上的 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]实例的远程访问。</span><span class="sxs-lookup"><span data-stu-id="5d450-260">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
### <a name="enable-remote-connections-on-the-instance-of-ssnoversion"></a><span data-ttu-id="5d450-261">启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上的远程连接</span><span class="sxs-lookup"><span data-stu-id="5d450-261">Enable remote connections on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="5d450-262">若要启用远程连接，请在本地使用 SQLCMD.exe 并对 Server Core 实例执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="5d450-262">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-ssnoversion-browser-service"></a><span data-ttu-id="5d450-263">启用并启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务</span><span class="sxs-lookup"><span data-stu-id="5d450-263">Enable and start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service</span></span>  
 <span data-ttu-id="5d450-264">默认情况下，Browser 服务是禁用的。</span><span class="sxs-lookup"><span data-stu-id="5d450-264">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="5d450-265">如果在 Server Core 上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例禁用了该服务，请从命令提示符运行以下命令来启用它：</span><span class="sxs-lookup"><span data-stu-id="5d450-265">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="5d450-266">在启用该服务后，请从命令提示符运行以下命令来启动该服务：</span><span class="sxs-lookup"><span data-stu-id="5d450-266">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="5d450-267">在 Windows 防火墙中创建例外</span><span class="sxs-lookup"><span data-stu-id="5d450-267">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="5d450-268">若要在 Windows 防火墙中创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问的例外，请执行 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)中指定的步骤。</span><span class="sxs-lookup"><span data-stu-id="5d450-268">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-the-instance-of-ssnoversion"></a><span data-ttu-id="5d450-269">在实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上启用 TCP/IP</span><span class="sxs-lookup"><span data-stu-id="5d450-269">Enable TCP/IP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="5d450-270">可以在 Server Core 上通过 Windows PowerShell 为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例启用 TCP/IP 协议。</span><span class="sxs-lookup"><span data-stu-id="5d450-270">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="5d450-271">执行以下步骤:</span><span class="sxs-lookup"><span data-stu-id="5d450-271">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="5d450-272">在运行 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 的计算机上，启动任务管理器。</span><span class="sxs-lookup"><span data-stu-id="5d450-272">On the computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="5d450-273">在 **“应用程序”** 选项卡上，单击 **“新建任务”** 。</span><span class="sxs-lookup"><span data-stu-id="5d450-273">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="5d450-274">在 **“创建新任务”** 对话框上的 **“打开”** 字段中键入 **sqlps.exe** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="5d450-274">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="5d450-275">这将打开\*\* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell\*\*窗口。</span><span class="sxs-lookup"><span data-stu-id="5d450-275">This opens the **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="5d450-276">在 **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** 窗口中，运行以下脚本以启用 TCP/IP 协议：</span><span class="sxs-lookup"><span data-stu-id="5d450-276">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = New-Object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a><span data-ttu-id="5d450-277">卸载</span><span class="sxs-lookup"><span data-stu-id="5d450-277">Uninstallation</span></span>  
 <span data-ttu-id="5d450-278">登录到运行 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 的计算机之后，您将拥有一个带有管理员命令提示符的受限制桌面环境。</span><span class="sxs-lookup"><span data-stu-id="5d450-278">After you log on to a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, you have a limited desktop environment with an Administrator command prompt.</span></span> <span data-ttu-id="5d450-279">您可以使用此命令提示符来启动 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例的卸载。</span><span class="sxs-lookup"><span data-stu-id="5d450-279">You can use this command prompt to initiate uninstallation of an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5d450-280">若要卸载 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例，请从命令提示符以完全静默模式（通过使用 /Q 参数）或简单静默模式（通过使用 /QS 参数）启动卸载。</span><span class="sxs-lookup"><span data-stu-id="5d450-280">To uninstall an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], launch the uninstallation from the command prompt in full quiet mode by using the /Q parameter, or quiet simple mode by using the /QS parameter.</span></span> <span data-ttu-id="5d450-281">/QS 参数将通过用户界面显示进度，但是不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="5d450-281">The /QS parameter shows progress through the UI, but does not accept any input.</span></span> <span data-ttu-id="5d450-282">/Q 在没有任何用户界面的情况下以静默模式运行。</span><span class="sxs-lookup"><span data-stu-id="5d450-282">/Q runs in a quiet mode without any user interface.</span></span>  
  
 <span data-ttu-id="5d450-283">卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的现有实例：</span><span class="sxs-lookup"><span data-stu-id="5d450-283">To uninstall an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```cmd
setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 <span data-ttu-id="5d450-284">若要删除命名实例，请指定实例名称，而不是前面示例中的“MSSQLSERVER”。</span><span class="sxs-lookup"><span data-stu-id="5d450-284">To remove a named instance, specify the name of the instance instead of "MSSQLSERVER" in the preceding example.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5d450-285">如果您无意中关闭了命令提示符，可以使用以下步骤启动一个新的命令提示符：</span><span class="sxs-lookup"><span data-stu-id="5d450-285">If you accidentally close the command prompt, you can start a new command prompt by following these steps:</span></span>  
> 
>  1.  <span data-ttu-id="5d450-286">按 Ctrl+Shift+Esc 以显示任务管理器。</span><span class="sxs-lookup"><span data-stu-id="5d450-286">Press Ctrl+Shift+Esc to display Task Manager.</span></span>  
> 2.  <span data-ttu-id="5d450-287">在 **“应用程序”** 选项卡上，单击 **“新建任务”** 。</span><span class="sxs-lookup"><span data-stu-id="5d450-287">On the **Applications** tab, click **New Task**.</span></span>  
> 3.  <span data-ttu-id="5d450-288">在“创建新任务”  对话框上的“打开”  字段中键入 **cmd** ，然后 [!INCLUDE[clickOK](../../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d450-288">In the **Create New Task** dialog box, type **cmd** in the **Open** field and then [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d450-289">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d450-289">See Also</span></span>  
 <span data-ttu-id="5d450-290">[使用配置文件安装 SQL Server 2014](install-sql-server-using-a-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="5d450-290">[Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md) </span></span>  
 <span data-ttu-id="5d450-291">[从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="5d450-291">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="5d450-292">[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="5d450-292">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="5d450-293">[服务器核心安装选项入门指南](https://go.microsoft.com/fwlink/?LinkId=221422) </span><span class="sxs-lookup"><span data-stu-id="5d450-293">[Server Core Installation Option Getting Started Guide](https://go.microsoft.com/fwlink/?LinkId=221422) </span></span>  
 <span data-ttu-id="5d450-294">[配置服务器核心安装：概述](https://go.microsoft.com/fwlink/?LinkId=221423) </span><span class="sxs-lookup"><span data-stu-id="5d450-294">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=221423) </span></span>  
 <span data-ttu-id="5d450-295">[Windows PowerShell 中按任务焦点列出的故障转移群集 Cmdlet](https://go.microsoft.com/fwlink/?LinkId=221419) </span><span class="sxs-lookup"><span data-stu-id="5d450-295">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://go.microsoft.com/fwlink/?LinkId=221419) </span></span>  
 [<span data-ttu-id="5d450-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters</span><span class="sxs-lookup"><span data-stu-id="5d450-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters</span></span>](https://go.microsoft.com/fwlink/?LinkId=221421)  
