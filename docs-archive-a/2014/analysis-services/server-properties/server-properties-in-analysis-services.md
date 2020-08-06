---
title: 在 Analysis Services 中配置服务器属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
author: minewiskan
ms.author: owend
ms.openlocfilehash: 087154756960c6d53fbd66ca4c111ac157503a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586000"
---
# <a name="configure-server-properties-in-analysis-services"></a><span data-ttu-id="7a79d-102">在 Analysis Services 中配置服务器属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-102">Configure Server Properties in Analysis Services</span></span>
  <span data-ttu-id="7a79d-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理员可以修改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的默认服务器配置属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator can modify default server configuration properties for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="7a79d-104">每个实例都有自己的配置属性，可以独立于同一服务器上的其他实例进行设置。</span><span class="sxs-lookup"><span data-stu-id="7a79d-104">Each instance has its own configuration properties that can be set independently of other instances on the same server.</span></span>  
  
 <span data-ttu-id="7a79d-105">若要设置服务器属性，请使用 SQL Server Management Studio 或编辑特定实例的 msmdsrv.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="7a79d-105">To set server properties, use SQL Server Management Studio or edit the msmdsrv.ini file of a specific instance.</span></span>  
  
 <span data-ttu-id="7a79d-106">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="7a79d-106">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="7a79d-107">配置服务器（实例）属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-107">Configure Server (Instance) Properties</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="7a79d-108">服务器属性参考</span><span class="sxs-lookup"><span data-stu-id="7a79d-108">Server Property Reference</span></span>](#bkmk_ref)  
  
##  <a name="configure-server-instance-properties"></a><a name="bkmk_config"></a><span data-ttu-id="7a79d-109">) 属性配置服务器 (实例</span><span class="sxs-lookup"><span data-stu-id="7a79d-109">Configure Server (Instance) Properties</span></span>  
 <span data-ttu-id="7a79d-110">SQL Server Management Studio 中的属性页包含一部分可用的属性，仅显示可能要修改的那些属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-110">The property pages in SQL Server Management Studio contain a subset of the available properties, showing only those properties that are more likely to be modified.</span></span> <span data-ttu-id="7a79d-111">msmdsrv.ini 文件中提供了一组完整的属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-111">The full set of properties can be found in the msmdsrv.ini file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a79d-112">本主题未说明 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的部署配置属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-112">This topic does not document the deployment configuration properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="7a79d-113">有关部署配置的详细信息，请参阅[为解决方案部署指定配置设置](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="7a79d-113">For more information about deployment configuration, see [Specifying Configuration Settings for Solution Deployment](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).</span></span>  
  
#### <a name="view-or-set-configuration-properties-in-management-studio"></a><span data-ttu-id="7a79d-114">在 Management Studio 中查看或设置配置属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-114">View or set configuration properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="7a79d-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="7a79d-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="7a79d-116">在对象资源管理器中，右键单击 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，再单击\*\*\*\*“属性”。</span><span class="sxs-lookup"><span data-stu-id="7a79d-116">In Object Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and then click **Properties**.</span></span> <span data-ttu-id="7a79d-117">随即出现“常规”页，显示更为常用的属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-117">The General page appears, displaying the more commonly used properties.</span></span>  
  
2.  <span data-ttu-id="7a79d-118">若要查看更多属性，请选中该页底部的\*\*\*\*“显示高级(全部)属性”复选框。</span><span class="sxs-lookup"><span data-stu-id="7a79d-118">To view additional properties, click the **Show Advanced (All) Properties** checkbox at the bottom of the page.</span></span>  
  
     <span data-ttu-id="7a79d-119">只有表格模式服务器和多维模式服务器才支持修改服务器属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-119">Modifying server properties is supported only for tabular mode and multidimensional mode servers.</span></span> <span data-ttu-id="7a79d-120">如果安装了 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，请始终使用默认值，除非 Microsoft 产品支持工程师另有说明。</span><span class="sxs-lookup"><span data-stu-id="7a79d-120">If you installed [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], always use the default values unless you are directed otherwise by a Microsoft product support engineer.</span></span>  
  
     <span data-ttu-id="7a79d-121">对于如何通过属性解决操作或性能问题的指导，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="7a79d-121">For guidance on how to address operational or performance issues through server properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
     <span data-ttu-id="7a79d-122">也可以在 Microsoft 白皮书 [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102)（SQL Server 2005 Analysis Services (SSAS) 服务器属性）中查阅服务器属性（这些属性在最近几个版本中大多没有发生变化）的信息。</span><span class="sxs-lookup"><span data-stu-id="7a79d-122">You can also read about server properties (many of which are unchanged over the last several releases) in this Microsoft white paper, [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a79d-123">某些属性只能在 msmdrsrv.ini 文件中进行设置。</span><span class="sxs-lookup"><span data-stu-id="7a79d-123">Some properties can only be set in the msmdrsrv.ini file.</span></span> <span data-ttu-id="7a79d-124">如果在显示高级属性后仍然看不见要设置的属性，则可能需要直接编辑 msmdsrv.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="7a79d-124">If the property you want to set is not visible even after you show advanced properties, you might need to edit the msmdsrv.ini file directly.</span></span>  
  
#### <a name="view-or-edit-configuration-properties-in-the-msmdsrvini-file"></a><span data-ttu-id="7a79d-125">在 msmdsrv.ini 文件中查看或编辑配置属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-125">View or edit configuration properties in the msmdsrv.ini file</span></span>  
  
1.  <span data-ttu-id="7a79d-126">开始之前，请在 Management Studio 的“常规”属性页中检查 **DataDir** 属性以确认 Analysis Services 程序文件（包括 msmdsrv.ini 文件）的位置。</span><span class="sxs-lookup"><span data-stu-id="7a79d-126">Before you begin, check the **DataDir** property in the General property page in Management Studio to verify the location of the Analysis Services program files, including the msmdsrv.ini file.</span></span> <span data-ttu-id="7a79d-127">确认程序文件位置可确保您修改的就是所需的文件。</span><span class="sxs-lookup"><span data-stu-id="7a79d-127">Verifying the location of the program files will ensure that you are modifying the correct file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a79d-128">在默认安装中，该文件可能位于 \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7a79d-128">In a default installation, the file can be found in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder</span></span>  
  
2.  <span data-ttu-id="7a79d-129">创建该文件的备份，以备将来恢复原始文件时使用。</span><span class="sxs-lookup"><span data-stu-id="7a79d-129">Create a backup of the file in case you need to revert to the original file.</span></span>  
  
3.  <span data-ttu-id="7a79d-130">使用文本编辑器查看或编辑 msmdsrv.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="7a79d-130">Use a text editor to view or edit the msmdsrv.ini file.</span></span>  
  
4.  <span data-ttu-id="7a79d-131">在保存该文件后，您必须重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="7a79d-131">After you save the file, you must restart the service.</span></span>  
  
##  <a name="server-property-reference"></a><a name="bkmk_ref"></a><span data-ttu-id="7a79d-132">服务器属性参考</span><span class="sxs-lookup"><span data-stu-id="7a79d-132">Server Property Reference</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="7a79d-133">配置属性对于微调系统非常重要。</span><span class="sxs-lookup"><span data-stu-id="7a79d-133">configuration properties are important for fine tuning your system.</span></span> <span data-ttu-id="7a79d-134">例如，为了使查询日志行为与您的要求相一致，您可以设置相关的属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-134">For example, to make query log behavior consistent with your requirements, you can set the relevant properties.</span></span>  
  
 <span data-ttu-id="7a79d-135">以下主题介绍了各种 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置属性：</span><span class="sxs-lookup"><span data-stu-id="7a79d-135">The following topics explain the various [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] configuration properties:</span></span>  
  
|<span data-ttu-id="7a79d-136">主题</span><span class="sxs-lookup"><span data-stu-id="7a79d-136">Topic</span></span>|<span data-ttu-id="7a79d-137">说明</span><span class="sxs-lookup"><span data-stu-id="7a79d-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7a79d-138">常规属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-138">General Properties</span></span>](general-properties.md)|<span data-ttu-id="7a79d-139">常规属性既是基本属性，又是高级属性，包括定义数据目录、备份目录和其他服务器行为的属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-139">The general properties are both basic and advanced properties, and include properties that define the data directory, backup directory, and other server behaviors.</span></span>|  
|[<span data-ttu-id="7a79d-140">数据挖掘属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-140">Data Mining Properties</span></span>](data-mining-properties.md)|<span data-ttu-id="7a79d-141">数据挖掘属性控制着启用和禁用哪些数据挖掘算法。</span><span class="sxs-lookup"><span data-stu-id="7a79d-141">The data mining properties control which data mining algorithms are enabled and which are disabled.</span></span> <span data-ttu-id="7a79d-142">默认情况下，启用所有算法。</span><span class="sxs-lookup"><span data-stu-id="7a79d-142">By default, all of the algorithms are enabled.</span></span>|  
|<span data-ttu-id="7a79d-143">DSO</span><span class="sxs-lookup"><span data-stu-id="7a79d-143">DSO</span></span>|<span data-ttu-id="7a79d-144">不再支持 DSO。</span><span class="sxs-lookup"><span data-stu-id="7a79d-144">DSO is no longer supported.</span></span> <span data-ttu-id="7a79d-145">忽略 DSO 属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-145">DSO properties are ignored.</span></span>|  
|[<span data-ttu-id="7a79d-146">Feature 属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-146">Feature Properties</span></span>](feature-properties.md)|<span data-ttu-id="7a79d-147">功能属性与产品功能有关，大多数是高级属性，包括控制服务器实例之间的链接的属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-147">The feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>|  
|[<span data-ttu-id="7a79d-148">每个属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-148">Filestore Properties</span></span>](filestore-properties.md)|<span data-ttu-id="7a79d-149">文件存储属性仅用于高级用途。</span><span class="sxs-lookup"><span data-stu-id="7a79d-149">The file store properties are for advanced use only.</span></span> <span data-ttu-id="7a79d-150">其中包括高级内存管理设置。</span><span class="sxs-lookup"><span data-stu-id="7a79d-150">They include advanced memory management settings.</span></span>|  
|[<span data-ttu-id="7a79d-151">锁管理器属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-151">Lock Manager Properties</span></span>](lock-manager-properties.md)|<span data-ttu-id="7a79d-152">锁管理器属性定义与锁定和超时有关的服务器行为。</span><span class="sxs-lookup"><span data-stu-id="7a79d-152">The lock manager properties define server behaviors pertaining to locking and timeouts.</span></span> <span data-ttu-id="7a79d-153">这些属性多数仅适用于高级用途。</span><span class="sxs-lookup"><span data-stu-id="7a79d-153">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="7a79d-154">日志属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-154">Log Properties</span></span>](log-properties.md)|<span data-ttu-id="7a79d-155">日志属性控制是否在服务器上记录事件以及记录事件的位置和方式。</span><span class="sxs-lookup"><span data-stu-id="7a79d-155">The log properties controls if, where, and how events are logged on the server.</span></span> <span data-ttu-id="7a79d-156">其中包括错误日志记录、异常日志记录、网络流量记录器、查询日志记录和跟踪。</span><span class="sxs-lookup"><span data-stu-id="7a79d-156">This includes error logging, exception logging, flight recorder, query logging, and traces.</span></span>|  
|[<span data-ttu-id="7a79d-157">内存属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-157">Memory Properties</span></span>](memory-properties.md)|<span data-ttu-id="7a79d-158">内存属性控制服务器如何使用内存。</span><span class="sxs-lookup"><span data-stu-id="7a79d-158">The memory properties control how the server uses memory.</span></span> <span data-ttu-id="7a79d-159">这些属性主要用于高级用途。</span><span class="sxs-lookup"><span data-stu-id="7a79d-159">They are primarily for advanced use.</span></span>|  
|[<span data-ttu-id="7a79d-160">网络属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-160">Network Properties</span></span>](network-properties.md)|<span data-ttu-id="7a79d-161">网络属性控制与网络有关的服务器行为，包括控制压缩和二进制 XML 的属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-161">The network properties control server behavior pertaining to networking, including properties that control compression and binary XML.</span></span> <span data-ttu-id="7a79d-162">这些属性多数仅适用于高级用途。</span><span class="sxs-lookup"><span data-stu-id="7a79d-162">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="7a79d-163">OLAP 属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-163">OLAP Properties</span></span>](olap-properties.md)|<span data-ttu-id="7a79d-164">OLAP 属性控制多维数据集和维度处理、迟缓处理、数据缓存和查询行为。</span><span class="sxs-lookup"><span data-stu-id="7a79d-164">The OLAP properties control cube and dimension processing, lazy processing, data caching, and query behavior.</span></span> <span data-ttu-id="7a79d-165">其中既包括基本属性，也包括高级属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-165">These include both basic and advanced properties.</span></span>|  
|[<span data-ttu-id="7a79d-166">安全属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-166">Security Properties</span></span>](security-properties.md)|<span data-ttu-id="7a79d-167">安全部分包含定义访问权限的基本属性和高级属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-167">The security section contains both basic and advanced properties that define access permissions.</span></span> <span data-ttu-id="7a79d-168">其中包括与管理员和用户有关的设置。</span><span class="sxs-lookup"><span data-stu-id="7a79d-168">This includes settings pertaining to administrators and users.</span></span>|  
|[<span data-ttu-id="7a79d-169">线程池属性</span><span class="sxs-lookup"><span data-stu-id="7a79d-169">Thread Pool Properties</span></span>](thread-pool-properties.md)|<span data-ttu-id="7a79d-170">线程池属性控制服务器创建多少线程。</span><span class="sxs-lookup"><span data-stu-id="7a79d-170">The thread pool properties control how many threads the server creates.</span></span> <span data-ttu-id="7a79d-171">这些属性主要是高级属性。</span><span class="sxs-lookup"><span data-stu-id="7a79d-171">These are primarily advanced properties.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a79d-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a79d-172">See Also</span></span>  
 <span data-ttu-id="7a79d-173">[Analysis Services 实例管理](../instances/analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="7a79d-173">[Analysis Services Instance Management](../instances/analysis-services-instance-management.md) </span></span>  
 [<span data-ttu-id="7a79d-174">为解决方案部署指定配置设置</span><span class="sxs-lookup"><span data-stu-id="7a79d-174">Specifying Configuration Settings for Solution Deployment</span></span>](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
