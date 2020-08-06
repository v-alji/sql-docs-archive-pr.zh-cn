---
title: SQL Server 属性（“高级”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2ffd10fd-bac1-478f-9cff-96ed6c8b787f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a9a77fd0a43627b49bb8719f6fa943408f64fcca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577177"
---
# <a name="sql-server-properties-advanced-tab"></a><span data-ttu-id="51f61-102">SQL Server 属性（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="51f61-102">SQL Server Properties (Advanced Tab)</span></span>
  <span data-ttu-id="51f61-103">默认情况下， **“高级”** 选项卡中会显示下列属性。</span><span class="sxs-lookup"><span data-stu-id="51f61-103">The following properties appear on the **Advanced** tab by default.</span></span> <span data-ttu-id="51f61-104">如果定义了自定义属性，则这些属性及其值将显示在此选项卡上。</span><span class="sxs-lookup"><span data-stu-id="51f61-104">If custom properties are defined, they also appear on this tab, with their values.</span></span>  
  
## <a name="options"></a><span data-ttu-id="51f61-105">选项</span><span class="sxs-lookup"><span data-stu-id="51f61-105">Options</span></span>  
 <span data-ttu-id="51f61-106">**群集**</span><span class="sxs-lookup"><span data-stu-id="51f61-106">**Clustered**</span></span>  
 <span data-ttu-id="51f61-107">指示此服务是否作为群集服务器的资源进行安装。</span><span class="sxs-lookup"><span data-stu-id="51f61-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="51f61-108">**客户反馈报告**</span><span class="sxs-lookup"><span data-stu-id="51f61-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="51f61-109">指示是否已对此服务启用服务质量监视。</span><span class="sxs-lookup"><span data-stu-id="51f61-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="51f61-110">有关客户反馈报告的详细信息，请在联机丛书中搜索主题“错误和使用报告设置”。</span><span class="sxs-lookup"><span data-stu-id="51f61-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="51f61-111">**数据路径**</span><span class="sxs-lookup"><span data-stu-id="51f61-111">**Data Path**</span></span>  
 <span data-ttu-id="51f61-112">显示所安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]二进制文件路径。</span><span class="sxs-lookup"><span data-stu-id="51f61-112">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="51f61-113">**转储目录**</span><span class="sxs-lookup"><span data-stu-id="51f61-113">**Dump Directory**</span></span>  
 <span data-ttu-id="51f61-114">显示发生错误时内存转储的存放位置。</span><span class="sxs-lookup"><span data-stu-id="51f61-114">Displays the location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="51f61-115">**错误报告**</span><span class="sxs-lookup"><span data-stu-id="51f61-115">**Error Reporting**</span></span>  
 <span data-ttu-id="51f61-116">当设置为“是”  时，如果发生严重错误，Dr. Watson 程序将把相关信息转发给 [!INCLUDE[msCoName](../../includes/msconame-md.md)]，或转发给错误服务器。</span><span class="sxs-lookup"><span data-stu-id="51f61-116">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="51f61-117">有关错误报告的详细信息，请在联机丛书中搜索主题“错误和使用报告设置”。</span><span class="sxs-lookup"><span data-stu-id="51f61-117">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span> <span data-ttu-id="51f61-118">若要更改此值，请在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器中右键单击服务器，再单击“属性”  ，然后单击“**杂项”。服务器设置”** 页。</span><span class="sxs-lookup"><span data-stu-id="51f61-118">To change this value, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click your server, click **Properties**, and then click the **Misc. Server Settings** page.</span></span> <span data-ttu-id="51f61-119">这些选项将显示在 **“信息报告”** 区域中。</span><span class="sxs-lookup"><span data-stu-id="51f61-119">The options are presented in the **Information Reporting** area.</span></span>  
  
 <span data-ttu-id="51f61-120">**文件版本**</span><span class="sxs-lookup"><span data-stu-id="51f61-120">**File Version**</span></span>  
 <span data-ttu-id="51f61-121">显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可执行文件的版本。</span><span class="sxs-lookup"><span data-stu-id="51f61-121">Displays the version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable.</span></span>  
  
 <span data-ttu-id="51f61-122">**安装路径**</span><span class="sxs-lookup"><span data-stu-id="51f61-122">**Install Path**</span></span>  
 <span data-ttu-id="51f61-123">显示所安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]二进制文件路径。</span><span class="sxs-lookup"><span data-stu-id="51f61-123">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="51f61-124">**实例 ID**</span><span class="sxs-lookup"><span data-stu-id="51f61-124">**Instance ID**</span></span>  
 <span data-ttu-id="51f61-125">指示使用此服务的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="51f61-125">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this service.</span></span>  
  
 <span data-ttu-id="51f61-126">**语言**</span><span class="sxs-lookup"><span data-stu-id="51f61-126">**Language**</span></span>  
 <span data-ttu-id="51f61-127">显示服务器消息的默认语言。</span><span class="sxs-lookup"><span data-stu-id="51f61-127">Displays the default language for server messages.</span></span>  
  
 <span data-ttu-id="51f61-128">**注册表根目录**</span><span class="sxs-lookup"><span data-stu-id="51f61-128">**Registry Root**</span></span>  
 <span data-ttu-id="51f61-129">显示此应用程序所使用的注册表项的位置。</span><span class="sxs-lookup"><span data-stu-id="51f61-129">Displays the location of the registry keys used by this application.</span></span>  
  
 <span data-ttu-id="51f61-130">**Service Pack 级别**</span><span class="sxs-lookup"><span data-stu-id="51f61-130">**Service Pack Level**</span></span>  
 <span data-ttu-id="51f61-131">显示此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的 Service Pack 级别。</span><span class="sxs-lookup"><span data-stu-id="51f61-131">Displays the service pack level of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="51f61-132">**SKU 名称**</span><span class="sxs-lookup"><span data-stu-id="51f61-132">**SKU Name**</span></span>  
 <span data-ttu-id="51f61-133">显示产品的单品 (SKU)，有时称为产品版本。</span><span class="sxs-lookup"><span data-stu-id="51f61-133">Displays the product stock keeping unit (SKU), sometimes called the product edition.</span></span>  
  
 <span data-ttu-id="51f61-134">**引导参数**</span><span class="sxs-lookup"><span data-stu-id="51f61-134">**Startup Parameters**</span></span>  
 <span data-ttu-id="51f61-135">列出此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例使用的所有引导参数。</span><span class="sxs-lookup"><span data-stu-id="51f61-135">Lists any startup parameters that are used by this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51f61-136">这些参数以分号分隔。</span><span class="sxs-lookup"><span data-stu-id="51f61-136">Parameters are separated by semi-colons.</span></span> <span data-ttu-id="51f61-137">默认参数包括 master 数据库的数据文件 (`master.mdf`)、master 数据库的日志文件 (`mastlog.ldf`) 和错误日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="51f61-137">The default parameters include the paths to the data file for the master database (`master.mdf`), the log file for the master database (`mastlog.ldf`), and the error log file.</span></span> <span data-ttu-id="51f61-138">有关引导参数的语法，请在联机丛书中搜索主题“使用 SQL Server 服务启动选项”主题 </span><span class="sxs-lookup"><span data-stu-id="51f61-138">For the syntax of startup parameters, search Books Online for the topic **Using the SQL Server Service Startup Options.**</span></span>  
  
 <span data-ttu-id="51f61-139">**单品**</span><span class="sxs-lookup"><span data-stu-id="51f61-139">**Stock Keeping Unit**</span></span>  
 <span data-ttu-id="51f61-140">显示产品的单品 (SKU) 编号。</span><span class="sxs-lookup"><span data-stu-id="51f61-140">Displays the product stock keeping unit (SKU) number.</span></span>  
  
 <span data-ttu-id="51f61-141">**版本**</span><span class="sxs-lookup"><span data-stu-id="51f61-141">**Version**</span></span>  
 <span data-ttu-id="51f61-142">显示此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的版本号。</span><span class="sxs-lookup"><span data-stu-id="51f61-142">Displays the version number of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="51f61-143">**虚拟服务器名称**</span><span class="sxs-lookup"><span data-stu-id="51f61-143">**Virtual Server Name**</span></span>  
 <span data-ttu-id="51f61-144">在群集服务器上安装**后的** 虚拟服务器名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="51f61-144">**Virtual Server Name** when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a clustered server.</span></span>  
  
  
