---
title: 重命名报表服务器计算机 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe8f699c17f9e5f1e11406ac6e5c161488767ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591131"
---
# <a name="rename-a-report-server-computer"></a><span data-ttu-id="74744-102">重命名报表服务器计算机</span><span class="sxs-lookup"><span data-stu-id="74744-102">Rename a Report Server Computer</span></span>
  <span data-ttu-id="74744-103">重命名计算机将导致相应地更改 Web 服务器和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称（如果是在同一台计算机上）。</span><span class="sxs-lookup"><span data-stu-id="74744-103">Renaming a computer causes a corresponding name change for the Web server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (if it is on the same computer).</span></span> <span data-ttu-id="74744-104">在某些情况下，在计算机名称发生更改之后，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可能无法访问。</span><span class="sxs-lookup"><span data-stu-id="74744-104">In some cases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] may not be accessible after a computer name change.</span></span> <span data-ttu-id="74744-105">请使用本主题中提供的步骤在计算机名称更改之后重新配置报表服务器。</span><span class="sxs-lookup"><span data-stu-id="74744-105">Use the steps provided in this topic to reconfigure a report server after a computer name change.</span></span>  
  
## <a name="renaming-a-sql-server-database-engine"></a><span data-ttu-id="74744-106">重命名 SQL Server 数据库引擎</span><span class="sxs-lookup"><span data-stu-id="74744-106">Renaming a SQL Server Database Engine</span></span>  
 <span data-ttu-id="74744-107">如果要重命名运行报表服务器数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="74744-107">If you rename the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance that runs the report server database, do the following:</span></span>  
  
1.  <span data-ttu-id="74744-108">启动 Reporting Services 配置工具，并连接到使用重命名的服务器中的报表服务器数据库的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="74744-108">Start the Reporting Services Configuration tool and connect to the report server that uses the report server database on the renamed server.</span></span>  
  
2.  <span data-ttu-id="74744-109">打开“数据库安装”页。</span><span class="sxs-lookup"><span data-stu-id="74744-109">Open the Database Setup page.</span></span>  
  
3.  <span data-ttu-id="74744-110">在 **“服务器名称”** 中，键入或选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名称，再单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="74744-110">In **Server Name**, type or select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="74744-111">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="74744-111">Click **Apply**.</span></span>  
  
 <span data-ttu-id="74744-112">如果报表服务器使用的是本地 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，则可以使用 *(local)* 或 *(local)\instancename* 来指定服务器。</span><span class="sxs-lookup"><span data-stu-id="74744-112">If the report server is using a local [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you can use *(local)* or *(local)\instancename* to specify the server.</span></span> <span data-ttu-id="74744-113">如果使用 *(local)* 表示服务器，则可以重命名服务器，同时连接将继续工作。</span><span class="sxs-lookup"><span data-stu-id="74744-113">If you use *(local)* to refer to the server, you can rename the server and the connections will continue to work.</span></span> <span data-ttu-id="74744-114">如果使用的是远程服务器，或使用服务器名称配置了 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，则每次更改服务器名称时都必须更新数据库连接信息。</span><span class="sxs-lookup"><span data-stu-id="74744-114">If you are using a remote server, or if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is configured using the server name, you must update the database connection information whenever the server name is changed.</span></span>  
  
## <a name="renaming-a-report-server-computer"></a><span data-ttu-id="74744-115">重命名报表服务器计算机</span><span class="sxs-lookup"><span data-stu-id="74744-115">Renaming a Report Server Computer</span></span>  
 <span data-ttu-id="74744-116">如果要重命名运行报表服务器的计算机，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="74744-116">If you rename a computer that runs a report server, do the following:</span></span>  
  
1.  <span data-ttu-id="74744-117">在文本编辑器中打开**RSReportServer.config** ，并修改 `UrlRoot` 设置以反映新的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="74744-117">Open **RSReportServer.config** in a text editor and modify the `UrlRoot` setting to reflect the new server name.</span></span> <span data-ttu-id="74744-118">传递扩展插件使用 `UrlRoot` 设置来编写在访问存储于报表服务器中的项时所使用的 URL。</span><span class="sxs-lookup"><span data-stu-id="74744-118">The `UrlRoot` setting is used by delivery extensions to compose the URL used to access items stored on the report server.</span></span> <span data-ttu-id="74744-119">更改报表服务器 URL 地址时需要更新 `UrlRoot` 设置，以便订阅可以继续按预期方式传递报表。</span><span class="sxs-lookup"><span data-stu-id="74744-119">Changing the report server URL address requires that you update the `UrlRoot` setting so that subscriptions continue to deliver reports as expected.</span></span>  
  
2.  <span data-ttu-id="74744-120">在同一个文件中，修改 `ReportServerUrl` 设置（如果对其进行了配置），使其反映新服务器名称。</span><span class="sxs-lookup"><span data-stu-id="74744-120">In the same file, if it is set, modify the `ReportServerUrl` setting to reflect the new server name.</span></span> <span data-ttu-id="74744-121">注意，并非每次安装时都会使用此设置。</span><span class="sxs-lookup"><span data-stu-id="74744-121">Note that this setting is not used in every installation.</span></span> <span data-ttu-id="74744-122">如果此设置为空，则无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="74744-122">If it is empty, do nothing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="74744-123">如果在企业网络中使用的是 Windows Internet 名称服务 (WINS)，则在一段时间内仍可以通过以前的名称使用报表服务器和报表管理器。</span><span class="sxs-lookup"><span data-stu-id="74744-123">If you are using Windows Internet Naming Service (WINS) on your corporate network, the report server and Report Manager may continue to be available under the previous name for a period of time.</span></span> <span data-ttu-id="74744-124">WINS 向它所服务的每一台计算机映射一个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="74744-124">WINS maps an IP address to each computer it services.</span></span> <span data-ttu-id="74744-125">WINS 为重命名的计算机刷新 IP 地址之后，将无法再使用旧的计算机名称访问报表服务器或报表管理器。</span><span class="sxs-lookup"><span data-stu-id="74744-125">After WINS refreshes the IP address for the renamed computer, the old computer name can no longer be used to access a report server or Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74744-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74744-126">See Also</span></span>  
 <span data-ttu-id="74744-127">[Rsreportserver.config 配置文件](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="74744-127">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="74744-128">[Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="74744-128">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="74744-129">[Reporting Services 报表服务器（本机模式）](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="74744-129">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="74744-130">[启动和停止报表服务器服务](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="74744-130">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="74744-131">rsconfig 实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="74744-131">rsconfig Utility &#40;SSRS&#41;</span></span>](../tools/rsconfig-utility-ssrs.md)  
  
  
