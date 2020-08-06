---
title: 确定 Analysis Services 实例的服务器模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9e556fb1-ca37-4f06-8f8f-f187cb0fdb37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1ec68383d00441e4b1212c2fc03d07f1aa143313
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689111"
---
# <a name="determine-the-server-mode-of-an-analysis-services-instance"></a><span data-ttu-id="9ec85-102">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="9ec85-102">Determine the Server Mode of an Analysis Services Instance</span></span>
  <span data-ttu-id="9ec85-103">Analysis Services 可以安装在以下三种服务器模式之一下：多维和数据挖掘（默认模式）、PowerPivot for SharePoint 和表格。</span><span class="sxs-lookup"><span data-stu-id="9ec85-103">Analysis Services can be installed in one of three server modes: Multidimensional and Data Mining (default), PowerPivot for SharePoint, and Tabular.</span></span> <span data-ttu-id="9ec85-104">Analysis Services 实例的服务器模式在安装过程中在您选择用于安装服务器的选项时确定。</span><span class="sxs-lookup"><span data-stu-id="9ec85-104">The server mode of an Analysis Services instance is determined during setup when you choose options for installing the server.</span></span>  
  
 <span data-ttu-id="9ec85-105">服务器模式确定您创建和部署的解决方案的类型。</span><span class="sxs-lookup"><span data-stu-id="9ec85-105">The server mode determines the type of solution that you create and deploy.</span></span> <span data-ttu-id="9ec85-106">如果您没有安装服务器软件并且想要知道服务器安装在哪一模式下，则可以使用本主题中的信息确定该模式。</span><span class="sxs-lookup"><span data-stu-id="9ec85-106">If you did not install the server software and you want to know in which mode the server was installed, you can use the information in this topic to determine the mode.</span></span> <span data-ttu-id="9ec85-107">有关特定模式中功能可用性的详细信息，请参阅[比较表格和多维解决方案 (SSAS)](../comparing-tabular-and-multidimensional-solutions-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec85-107">For more information about feature availability in a specific mode, see [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](../comparing-tabular-and-multidimensional-solutions-ssas.md).</span></span>  
  
 <span data-ttu-id="9ec85-108">如果您不想使用所安装的服务器模式，则必须卸载后再重新安装该软件，并且选择想要的模式。</span><span class="sxs-lookup"><span data-stu-id="9ec85-108">If you do not want to use the server mode that you installed, you must uninstall and then reinstall the software, choosing the mode that you prefer.</span></span> <span data-ttu-id="9ec85-109">或者，您可以在同一台计算机上安装 Analysis Services 的其他实例，以便您具有运行不同模式的多个实例。</span><span class="sxs-lookup"><span data-stu-id="9ec85-109">Alternatively, you can install an additional instance of Analysis Services on the same computer so that you have multiple instances running different modes.</span></span>  
  
## <a name="server-icons-in-object-explorer"></a><span data-ttu-id="9ec85-110">对象资源管理器中的服务器图标</span><span class="sxs-lookup"><span data-stu-id="9ec85-110">Server Icons in Object Explorer</span></span>  
 <span data-ttu-id="9ec85-111">确定服务器模式的最简单方法是在 SQL Server Management Studio 中连接到该服务器，并且在对象资源管理器中注意服务器名称旁的图标。</span><span class="sxs-lookup"><span data-stu-id="9ec85-111">The easiest way to determine server mode is to connect to the server in SQL Server Management Studio and note the icon next to the server name in Object Explorer.</span></span> <span data-ttu-id="9ec85-112">下图显示在多维、表格和 PowerPivot 模式下部署的三个 Analysis Services 实例：</span><span class="sxs-lookup"><span data-stu-id="9ec85-112">The following illustration shows three instances of Analysis Services deployed in Multidimensional, Tabular, and PowerPivot modes:</span></span>  
  
 <span data-ttu-id="9ec85-113">![每个服务器模式的对象资源管理器图标](../media/ssas-ssms-servermodes.gif "每个服务器模式的对象资源管理器图标")</span><span class="sxs-lookup"><span data-stu-id="9ec85-113">![Object Explorer icons for each server mode](../media/ssas-ssms-servermodes.gif "Object Explorer icons for each server mode")</span></span>  
  
## <a name="viewing-deploymentmode-property-in-msmdsrvini-file"></a><span data-ttu-id="9ec85-114">在 MSMDSRV.INI 文件中查看 DeploymentMode 属性</span><span class="sxs-lookup"><span data-stu-id="9ec85-114">Viewing DeploymentMode Property in MSMDSRV.INI File</span></span>  
 <span data-ttu-id="9ec85-115">或者，您可以在包含在每个 Analysis Services 实例中的 msmdsrv.ini 文件中查看 `DeploymentMode` 属性。</span><span class="sxs-lookup"><span data-stu-id="9ec85-115">Alternatively, you can check the `DeploymentMode` property in the msmdsrv.ini file that is included in every Analysis Services instance.</span></span> <span data-ttu-id="9ec85-116">该属性的值标识服务器模式。</span><span class="sxs-lookup"><span data-stu-id="9ec85-116">The value of this property identifies the server mode.</span></span> <span data-ttu-id="9ec85-117">有效值为 0（多维）、1 (SharePoint) 或 2（表格）。</span><span class="sxs-lookup"><span data-stu-id="9ec85-117">Valid values are 0 (Multidimensional), 1 (SharePoint), or 2 (Tabular).</span></span> <span data-ttu-id="9ec85-118">你必须是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理员（即，服务器角色的成员）才可以打开 msmdsrv.ini 文件。</span><span class="sxs-lookup"><span data-stu-id="9ec85-118">You must be an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator (that is, a member of the Server role) to open the msmdsrv.ini file.</span></span> <span data-ttu-id="9ec85-119">此文件包含结构化的 XML。</span><span class="sxs-lookup"><span data-stu-id="9ec85-119">This file contains structured XML.</span></span> <span data-ttu-id="9ec85-120">可以使用记事本或其他文本编辑器查看该文件。</span><span class="sxs-lookup"><span data-stu-id="9ec85-120">You can use Notepad or another text editor to view the file.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9ec85-121">不要更改 `DeploymentMode` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="9ec85-121">Do not change the value of the `DeploymentMode` property.</span></span> <span data-ttu-id="9ec85-122">不支持在安装服务器后手动更改该属性。</span><span class="sxs-lookup"><span data-stu-id="9ec85-122">Changing the property manually after the server is installed is not supported.</span></span>  
  
## <a name="about-the-deploymentmode-property"></a><span data-ttu-id="9ec85-123">关于 DeploymentMode 属性</span><span class="sxs-lookup"><span data-stu-id="9ec85-123">About the DeploymentMode Property</span></span>  
 <span data-ttu-id="9ec85-124">`DeploymentMode` 属性确定 Analysis Services 服务器实例的操作上下文。</span><span class="sxs-lookup"><span data-stu-id="9ec85-124">`DeploymentMode` property determines the operational context of an Analysis Services server instance.</span></span> <span data-ttu-id="9ec85-125">此属性在对话框、消息和文档中称为 "服务器模式"。</span><span class="sxs-lookup"><span data-stu-id="9ec85-125">This property is referred to as 'server mode' in dialog boxes, messages, and documentation.</span></span> <span data-ttu-id="9ec85-126">此属性基于您安装 Analysis Services 的方式由安装程序启动。</span><span class="sxs-lookup"><span data-stu-id="9ec85-126">This property is initialized by Setup based on how you install Analysis Services.</span></span> <span data-ttu-id="9ec85-127">只应考虑在内部使用此属性，并且始终使用安装程序指定的值。</span><span class="sxs-lookup"><span data-stu-id="9ec85-127">This property should be considered internal only, always using the value specified by Setup.</span></span>  
  
 <span data-ttu-id="9ec85-128">此属性的有效值包括以下项：</span><span class="sxs-lookup"><span data-stu-id="9ec85-128">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="9ec85-129">值</span><span class="sxs-lookup"><span data-stu-id="9ec85-129">Value</span></span>|<span data-ttu-id="9ec85-130">说明</span><span class="sxs-lookup"><span data-stu-id="9ec85-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ec85-131">0</span><span class="sxs-lookup"><span data-stu-id="9ec85-131">0</span></span>|<span data-ttu-id="9ec85-132">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="9ec85-132">This is the default value.</span></span> <span data-ttu-id="9ec85-133">它指定多维模式，用于支持使用 MOLAP、HOLAP 和 ROLAP 存储以及数据挖掘模型的多维数据库。</span><span class="sxs-lookup"><span data-stu-id="9ec85-133">It specifies multidimensional mode, used to service multidimensional databases that use MOLAP, HOLAP, and ROLAP storage, as well as data mining models.</span></span>|  
|<span data-ttu-id="9ec85-134">1</span><span class="sxs-lookup"><span data-stu-id="9ec85-134">1</span></span>|<span data-ttu-id="9ec85-135">指定 Analysis Services 实例已作为 PowerPivot for SharePoint 部署的一部分安装。</span><span class="sxs-lookup"><span data-stu-id="9ec85-135">Specifies Analysis Services instances that were installed as part of a PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="9ec85-136">不要更改作为 PowerPivot for SharePoint 安装的一部分的 Analysis Services 实例的部署模式属性。</span><span class="sxs-lookup"><span data-stu-id="9ec85-136">Do not change the deployment mode property of Analysis Services instance that is part of a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="9ec85-137">如果您更改该模式，PowerPivot 数据将不再在该服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="9ec85-137">PowerPivot data will no longer run on the server if you change the mode.</span></span>|  
|<span data-ttu-id="9ec85-138">2</span><span class="sxs-lookup"><span data-stu-id="9ec85-138">2</span></span>|<span data-ttu-id="9ec85-139">指定用于承载使用内存中存储或 DirectQuery 存储的表格模型数据库的表格模式。</span><span class="sxs-lookup"><span data-stu-id="9ec85-139">Specifies Tabular mode used for hosting tabular model databases that use in-memory storage or DirectQuery storage.</span></span>|  
  
 <span data-ttu-id="9ec85-140">每个模式与其他模式都是互斥的。</span><span class="sxs-lookup"><span data-stu-id="9ec85-140">Each mode is exclusive of the other.</span></span> <span data-ttu-id="9ec85-141">配置为表格模式的服务器不能运行包含多维数据集和维度的 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="9ec85-141">A server that is configured for tabular mode cannot run Analysis Services databases that contain cubes and dimensions.</span></span> <span data-ttu-id="9ec85-142">如果基础计算机硬件能够支持，则您可以在同一台计算机上安装 Analysis Services 的多个实例并且对每个实例进行配置以便使用不同的部署模式。</span><span class="sxs-lookup"><span data-stu-id="9ec85-142">If the underlying computer hardware can support it, you can install multiple instances of Analysis Services on the same computer and configure each instance to use a different deployment mode.</span></span> <span data-ttu-id="9ec85-143">请记住，Analysis Services 是一种消耗大量资源的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9ec85-143">Remember that Analysis Services is a resource intensive application.</span></span> <span data-ttu-id="9ec85-144">仅推荐对于高端服务器，才在同一个系统上部署多个实例。</span><span class="sxs-lookup"><span data-stu-id="9ec85-144">Deploying multiple instances on the same system is recommended only for high-end servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec85-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ec85-145">See Also</span></span>  
 <span data-ttu-id="9ec85-146">[在表格模式下安装 Analysis Services](install-windows/install-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9ec85-146">[Install Analysis Services in Tabular Mode](install-windows/install-analysis-services.md) </span></span>  
 <span data-ttu-id="9ec85-147">[在多维和数据挖掘模式下安装 Analysis Services](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span><span class="sxs-lookup"><span data-stu-id="9ec85-147">[Install Analysis Services in Multidimensional and Data Mining Mode](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span></span>  
 <span data-ttu-id="9ec85-148">[PowerPivot for SharePoint 2010 安装](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md) </span><span class="sxs-lookup"><span data-stu-id="9ec85-148">[PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md) </span></span>  
 <span data-ttu-id="9ec85-149">[连接到 Analysis Services](connect-to-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9ec85-149">[Connect to Analysis Services](connect-to-analysis-services.md) </span></span>  
 <span data-ttu-id="9ec85-150">[&#40;SSAS 表格&#41;的表格模型解决方案](../tabular-model-solutions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="9ec85-150">[Tabular Model Solutions &#40;SSAS Tabular&#41;](../tabular-model-solutions-ssas-tabular.md) </span></span>  
 <span data-ttu-id="9ec85-151">[&#40;SSAS&#41;的多维模型解决方案](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="9ec85-151">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="9ec85-152">挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="9ec85-152">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../data-mining/mining-models-analysis-services-data-mining.md)  
  
  