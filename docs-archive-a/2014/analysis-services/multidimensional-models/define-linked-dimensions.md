---
title: 定义链接维度 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088dda52042a53c252eed8d759e54af4dee1a029
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687287"
---
# <a name="define-linked-dimensions"></a><span data-ttu-id="9da35-102">定义链接维度</span><span class="sxs-lookup"><span data-stu-id="9da35-102">Define Linked Dimensions</span></span>
  <span data-ttu-id="9da35-103">链接维度基于在具有相同版本和兼容性级别的另一个 Analysis Services 数据库中创建和存储的维度。</span><span class="sxs-lookup"><span data-stu-id="9da35-103">A linked dimension is based on a dimension created and stored in another Analysis Services database of the same version and compatibility level.</span></span> <span data-ttu-id="9da35-104">通过使用链接维度，您可以创建、存储以及维护某个数据库上的维度，同时可让多个数据库的用户使用该维度。</span><span class="sxs-lookup"><span data-stu-id="9da35-104">By using a linked dimension, you can create, store, and maintain a dimension on one database, while making it available to users of multiple databases.</span></span> <span data-ttu-id="9da35-105">对于用户，链接维度在外观上就像其他任意维度一样。</span><span class="sxs-lookup"><span data-stu-id="9da35-105">To users, a linked dimension appears like any other dimension.</span></span>  
  
 <span data-ttu-id="9da35-106">链接文档是只读的。</span><span class="sxs-lookup"><span data-stu-id="9da35-106">Linked dimensions are read-only.</span></span> <span data-ttu-id="9da35-107">如果您想要修改维度或创建新关系，则必须更改源维度，然后删除后再重新创建链接的维度及其关系。</span><span class="sxs-lookup"><span data-stu-id="9da35-107">If you want to modify the dimension or create new relationships, you must change the source dimension, then delete and recreate the linked dimension and its relationships.</span></span> <span data-ttu-id="9da35-108">不能刷新某一链接的维度以便从源项目中提取更改。</span><span class="sxs-lookup"><span data-stu-id="9da35-108">You cannot refresh a linked dimension to pick up changes from the source object.</span></span>  
  
 <span data-ttu-id="9da35-109">所有相关的度量值组和维度必须都来自相同的源数据库。</span><span class="sxs-lookup"><span data-stu-id="9da35-109">All related measure groups and dimensions must come from the same source database.</span></span> <span data-ttu-id="9da35-110">不能在本地度量值组和您添加到多维数据集的链接文档之间创建新关系。</span><span class="sxs-lookup"><span data-stu-id="9da35-110">You cannot create new relationships between local measure groups and the linked dimensions you add to your cube.</span></span> <span data-ttu-id="9da35-111">将链接维度和度量值组添加到当前多维数据集后，必须在其源数据库中维护它们之间的关系。</span><span class="sxs-lookup"><span data-stu-id="9da35-111">After linked dimensions and measure groups have been added to the current cube, the relationships between them must be maintained in their source database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9da35-112">因为刷新功能不可用，所以，大多数 Analysis Services 开发人员都是复制维度，而不是链接它们。</span><span class="sxs-lookup"><span data-stu-id="9da35-112">Because refresh is not available, most Analysis Services developers copy dimensions rather than link them.</span></span> <span data-ttu-id="9da35-113">可以跨同一个解决方案中的多个项目复制维度。</span><span class="sxs-lookup"><span data-stu-id="9da35-113">You can copy dimensions across projects within the same solution.</span></span> <span data-ttu-id="9da35-114">有关详细信息，请参阅 [在 SSAS 中刷新链接的维度](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9da35-114">For more information, see [Refresh of a linked dimension in SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9da35-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="9da35-115">Prerequisites</span></span>  
 <span data-ttu-id="9da35-116">提供维度的源数据库和使用维度的当前数据库必须处于相同的版本和兼容级别。</span><span class="sxs-lookup"><span data-stu-id="9da35-116">The source database that provides the dimension and the current database that uses it must be at the same version and compatibility level.</span></span> <span data-ttu-id="9da35-117">有关详细信息，请参阅[设置多维数据库 &#40;Analysis Services&#41;的兼容级别](compatibility-level-of-a-multidimensional-database-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9da35-117">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
 <span data-ttu-id="9da35-118">源数据库必须已部署并且处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="9da35-118">The source database must be deployed and online.</span></span> <span data-ttu-id="9da35-119">发布或恢复链接对象的服务器必须配置为允许该操作（见下文）。</span><span class="sxs-lookup"><span data-stu-id="9da35-119">Servers that publish or consume linked objects must be configured to allow the operation (see below).</span></span>  
  
 <span data-ttu-id="9da35-120">您想要使用的维度本身不能是链接维度。</span><span class="sxs-lookup"><span data-stu-id="9da35-120">The dimension you want to use cannot itself be a linked dimension.</span></span>  
  
## <a name="configure-server-to-allow-linked-objects"></a><span data-ttu-id="9da35-121">配置服务器以便允许链接对象</span><span class="sxs-lookup"><span data-stu-id="9da35-121">Configure server to allow linked objects</span></span>  
  
1.  <span data-ttu-id="9da35-122">在 SQL Server Management Studio 中，连接到 Analysis Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="9da35-122">In SQL Server Management Studio, connect to an Analysis Services server.</span></span> <span data-ttu-id="9da35-123">在对象资源管理器中，右键单击服务器名称，然后选择“方面”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9da35-123">In Object Explorer, right-click the server name and select **Facets**.</span></span>  
  
2.  <span data-ttu-id="9da35-124">将 **LinkedObjectsLinksFromOtherInstancesEnabled** 设置为 **True** ，以便允许服务器对驻留在运行于其他实例上的数据库中的链接对象发出请求。</span><span class="sxs-lookup"><span data-stu-id="9da35-124">Set **LinkedObjectsLinksFromOtherInstancesEnabled** to **True** to allow the server to issue requests for linked objects that reside in databases running on other instances.</span></span>  
  
3.  <span data-ttu-id="9da35-125">将 **LinkedObjectsLinksToOtherInstances** 设置为 **True** ，以便允许服务器请求链接到正在其他实例上运行的数据库的数据。</span><span class="sxs-lookup"><span data-stu-id="9da35-125">Set **LinkedObjectsLinksToOtherInstances** to **True** to allow the server to request data for linked on databases running on other instances.</span></span>  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a><span data-ttu-id="9da35-126">在 SQL Server Data Tools 中创建链接维度</span><span class="sxs-lookup"><span data-stu-id="9da35-126">Create a linked dimension in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="9da35-127">启动向导。</span><span class="sxs-lookup"><span data-stu-id="9da35-127">Start the wizard.</span></span> <span data-ttu-id="9da35-128">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，右键单击 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库或项目中的“维度”\*\*\*\* 文件夹，然后单击“新建链接维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9da35-128">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Dimensions** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and then click **New Linked Dimension**.</span></span>  
  
2.  <span data-ttu-id="9da35-129">连接到提供维度的 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="9da35-129">Connect to the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="9da35-130">在链接对象向导的 **“选择数据源”** 页中，选择 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据源或创建一个新数据源。</span><span class="sxs-lookup"><span data-stu-id="9da35-130">On the **Select a Data Source** page of the Linked Object Wizard, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source or create a new one.</span></span>  
  
3.  <span data-ttu-id="9da35-131">在向导的 **“选择对象”** 页中，选择指向远程数据库链接中的维度。</span><span class="sxs-lookup"><span data-stu-id="9da35-131">On the **Select Objects** page of the wizard, choose the dimensions you want to link to in the remote database.</span></span>  
  
4.  <span data-ttu-id="9da35-132">在 **“完成向导”** 页中，可以预览链接对象。</span><span class="sxs-lookup"><span data-stu-id="9da35-132">On the **Completing the Wizard** page, you can preview the linked objects.</span></span> <span data-ttu-id="9da35-133">如果链接的维度与已经存在的维度同名，则将在该名称后追加一个序号（从“1”开始，“1”表示第一个重复名称）。</span><span class="sxs-lookup"><span data-stu-id="9da35-133">If you link a dimension that has the same name as one that already exists, an ordinal number (starting with '1' for the first duplicated name) is appended to the name.</span></span> <span data-ttu-id="9da35-134">完成向导后，该维度将添加到 **“维度”** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="9da35-134">When you complete the wizard, the dimension is added to the **Dimensions** folder.</span></span>  
  
##  <a name="create-a-new-data-source-connection-to-an-analysis-services-database"></a><a name="bkmk_CreateNew"></a> <span data-ttu-id="9da35-135">创建与 Analysis Services 数据库的新数据源连接</span><span class="sxs-lookup"><span data-stu-id="9da35-135">Create a New Data Source Connection to an Analysis Services Database</span></span>  
 <span data-ttu-id="9da35-136">使用“新建数据源”向导以便添加到与提供维度的 Analysis Services 数据库有关的项目连接信息。</span><span class="sxs-lookup"><span data-stu-id="9da35-136">Use the New Data Source wizard to add to your project connection information about the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="9da35-137">您可以通过在“链接对象”向导的“选择数据源”页中单击 **“新建数据源”** ，启用该向导。</span><span class="sxs-lookup"><span data-stu-id="9da35-137">You can start the wizard by clicking **New Data Source** in the Select a Data Source page of the Linked Objects wizard.</span></span>  
  
1.  <span data-ttu-id="9da35-138">在“数据源”向导中的“选择如何定义连接”页上，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="9da35-138">In the Data Source Wizard, on the Select how to define the connection page, click **New**.</span></span>  
  
2.  <span data-ttu-id="9da35-139">在连接管理器中，确保提供程序设置为“本机 OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9da35-139">In Connection Manager, verify that the provider is set to **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="9da35-140">输入服务器的名称 (将*servername* \\ *instancename*用于命名实例) <sup>1</sup> ，或键入**localhost**以连接到在同一台计算机上运行的 Analysis Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="9da35-140">Enter the name of the server (use *servername*\\*instancename* for a named instance)<sup>1</sup> or type **localhost** to connect to an Analysis Services server that is running on the same computer.</span></span>  
  
4.  <span data-ttu-id="9da35-141">使用 Windows 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="9da35-141">Use Windows authentication for the connection.</span></span>  
  
5.  <span data-ttu-id="9da35-142">在 **“初始目录”** 中，单击向下箭头以选择此服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="9da35-142">In **Initial catalog**, click the down arrow to select a database on this server.</span></span>  
  
6.  <span data-ttu-id="9da35-143">在“数据源向导”中，单击 **“下一步”** 以继续。</span><span class="sxs-lookup"><span data-stu-id="9da35-143">On the Data Source Wizard, click **Next** to continue.</span></span>  
  
7.  <span data-ttu-id="9da35-144">在“模拟信息”页中，单击 **“使用服务帐户”**。</span><span class="sxs-lookup"><span data-stu-id="9da35-144">On the Impersonation Information page, click **Use the service account**.</span></span> <span data-ttu-id="9da35-145">单击 **“下一步”**，然后完成向导。</span><span class="sxs-lookup"><span data-stu-id="9da35-145">Click **Next**, and then finish the wizard.</span></span> <span data-ttu-id="9da35-146">将在“链接对象”向导中选择您刚定义的连接。</span><span class="sxs-lookup"><span data-stu-id="9da35-146">The connection you just defined will be selected in the Linked Objects Wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9da35-147">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9da35-147">Next Steps</span></span>  
 <span data-ttu-id="9da35-148">您不能更改链接维度的结构，因此无法使用维度设计器的 **“维度结构”** 选项卡来进行查看。</span><span class="sxs-lookup"><span data-stu-id="9da35-148">You cannot change the structure of a linked dimension, so you cannot view it with the **Dimension Structure** tab of Dimension Designer.</span></span> <span data-ttu-id="9da35-149">处理链接维度后，可以在**浏览器**选项卡中查看它。你还可以更改其名称，并创建名称的翻译。</span><span class="sxs-lookup"><span data-stu-id="9da35-149">After processing the linked dimension, you can view it with the **Browser** tab. You can also change its name and create a translation for the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da35-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9da35-150">See Also</span></span>  
 <span data-ttu-id="9da35-151">[设置多维数据库 &#40;Analysis Services 的兼容级别&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9da35-151">[Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span></span>  
 <span data-ttu-id="9da35-152">[链接度量值组](linked-measure-groups.md) </span><span class="sxs-lookup"><span data-stu-id="9da35-152">[Linked Measure Groups](linked-measure-groups.md) </span></span>  
 [<span data-ttu-id="9da35-153">维度关系</span><span class="sxs-lookup"><span data-stu-id="9da35-153">Dimension Relationships</span></span>](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
