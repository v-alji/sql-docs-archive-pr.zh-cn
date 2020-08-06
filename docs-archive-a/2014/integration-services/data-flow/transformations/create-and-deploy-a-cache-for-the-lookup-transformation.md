---
title: 为查找转换创建和部署缓存 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- creating cache files for Lookup transformation
- deploying cache files for Lookup transformation
- Lookup transformation cache files
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33b00b84f1f1448c2ee80882aedc3a330ba0a5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576894"
---
# <a name="create-and-deploy-a-cache-for-the-lookup-transformation"></a><span data-ttu-id="90dbf-102">为查找转换创建和部署缓存</span><span class="sxs-lookup"><span data-stu-id="90dbf-102">Create and Deploy a Cache for the Lookup Transformation</span></span>
  <span data-ttu-id="90dbf-103">可以为查找转换创建和部署缓存文件 (.caw)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-103">You can create and deploy a cache file (.caw) for the Lookup transformation.</span></span> <span data-ttu-id="90dbf-104">引用数据集存储在缓存文件中。</span><span class="sxs-lookup"><span data-stu-id="90dbf-104">The reference dataset is stored in the cache file.</span></span>  
  
 <span data-ttu-id="90dbf-105">查找转换通过将所连接数据源输入列中的数据和引用数据集中的列进行联接来执行查找。</span><span class="sxs-lookup"><span data-stu-id="90dbf-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference dataset.</span></span>  
  
 <span data-ttu-id="90dbf-106">可以使用缓存连接管理器和“缓存转换”转换来创建缓存文件。</span><span class="sxs-lookup"><span data-stu-id="90dbf-106">You create a cache file by using a Cache connection manager and a Cache Transform transformation.</span></span> <span data-ttu-id="90dbf-107">有关详细信息，请参阅 [缓存连接管理器](../../connection-manager/cache-connection-manager.md) 和 [缓存转换](cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-107">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
 <span data-ttu-id="90dbf-108">若要了解查找转换和缓存文件的更多信息，请参阅 [Lookup Transformation](lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-108">To learn more about the Lookup transformation and cache files, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
### <a name="to-create-a-cache-file"></a><span data-ttu-id="90dbf-109">创建缓存文件</span><span class="sxs-lookup"><span data-stu-id="90dbf-109">To create a cache file</span></span>  
  
1.  <span data-ttu-id="90dbf-110">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目，再打开该包。</span><span class="sxs-lookup"><span data-stu-id="90dbf-110">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="90dbf-111">在 **“控制流”** 选项卡上，添加数据流任务。</span><span class="sxs-lookup"><span data-stu-id="90dbf-111">On the **Control Flow** tab, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="90dbf-112">在 **“数据流”** 选项卡上，向数据流添加“缓存转换”转换，再将该转换连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="90dbf-112">On the **Data Flow** tab, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="90dbf-113">根据需要配置数据源。</span><span class="sxs-lookup"><span data-stu-id="90dbf-113">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="90dbf-114">双击缓存转换，在“缓存转换编辑器”  中的“连接管理器”  页上单击“新建”  ，创建一个新的缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="90dbf-114">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="90dbf-115">在 **“缓存连接管理器编辑器”** 的 **“常规”** 选项卡上，选择以下选项对缓存连接管理器进行配置，以保存缓存：</span><span class="sxs-lookup"><span data-stu-id="90dbf-115">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to save the cache by selecting the following options:</span></span>  
  
    1.  <span data-ttu-id="90dbf-116">选择 **“使用文件缓存”** 。</span><span class="sxs-lookup"><span data-stu-id="90dbf-116">Select **Use file cache**.</span></span>  
  
    2.  <span data-ttu-id="90dbf-117">在 **“文件名”** 中，键入文件路径。</span><span class="sxs-lookup"><span data-stu-id="90dbf-117">For **File name**, type the file path.</span></span>  
  
     <span data-ttu-id="90dbf-118">运行包时，系统会创建该文件。</span><span class="sxs-lookup"><span data-stu-id="90dbf-118">The system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="90dbf-119">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="90dbf-119">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="90dbf-120">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="90dbf-120">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="90dbf-121">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="90dbf-121">You should enable access only to certain accounts.</span></span> <span data-ttu-id="90dbf-122">有关详细信息，请参阅 [访问包使用的文件](../../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-122">For more information, see [Access to Files Used by Packages](../../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="90dbf-123">单击 **“列”** 选项卡，然后使用 **“索引位置”** 选项来指定哪些列是索引列。</span><span class="sxs-lookup"><span data-stu-id="90dbf-123">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="90dbf-124">对于非索引列，索引位置是 0。</span><span class="sxs-lookup"><span data-stu-id="90dbf-124">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="90dbf-125">对于索引列，索引位置是连续的正数。</span><span class="sxs-lookup"><span data-stu-id="90dbf-125">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="90dbf-126">当将查找转换配置为使用缓存连接管理器时，则仅引用数据集中的索引列能够映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="90dbf-126">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="90dbf-127">此外，还必须对所有索引列进行映射。</span><span class="sxs-lookup"><span data-stu-id="90dbf-127">Also all index columns must be mapped.</span></span>  
  
     <span data-ttu-id="90dbf-128">有关详细信息，请参阅 [Cache Connection Manager Editor](../../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-128">For more information, see [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="90dbf-129">根据需要配置缓存转换。</span><span class="sxs-lookup"><span data-stu-id="90dbf-129">Configure the Cache Transform as needed.</span></span>  
  
     <span data-ttu-id="90dbf-130">有关详细信息，请参阅[缓存转换编辑器（“连接管理器”页）](../../cache-transformation-editor-connection-manager-page.md)和[缓存转换编辑器（“映射”页）](../../cache-transformation-editor-mappings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-130">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="90dbf-131">运行包。</span><span class="sxs-lookup"><span data-stu-id="90dbf-131">Run the package.</span></span>  
  
### <a name="to-deploy-a-cache-file"></a><span data-ttu-id="90dbf-132">部署缓存文件</span><span class="sxs-lookup"><span data-stu-id="90dbf-132">To deploy a cache file</span></span>  
  
1.  <span data-ttu-id="90dbf-133">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目，再打开该包。</span><span class="sxs-lookup"><span data-stu-id="90dbf-133">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="90dbf-134">创建包配置（可选）。</span><span class="sxs-lookup"><span data-stu-id="90dbf-134">Optionally, create a package configuration.</span></span> <span data-ttu-id="90dbf-135">有关详细信息，请参阅 [创建包配置](../../create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-135">For more information, see [Create Package Configurations](../../create-package-configurations.md).</span></span>  
  
3.  <span data-ttu-id="90dbf-136">执行以下操作将缓存文件添加到项目：</span><span class="sxs-lookup"><span data-stu-id="90dbf-136">Add the cache file to the project by doing the following:</span></span>  
  
    1.  <span data-ttu-id="90dbf-137">在解决方案资源管理器中，选择在步骤 1 中打开的项目。</span><span class="sxs-lookup"><span data-stu-id="90dbf-137">In Solution Explorer, select the project you opened in step 1.</span></span>  
  
    2.  <span data-ttu-id="90dbf-138">在“项目”  菜单上，单击“添加现有项”  。</span><span class="sxs-lookup"><span data-stu-id="90dbf-138">On the **Project** menu, click **AddExisting Item**.</span></span>  
  
    3.  <span data-ttu-id="90dbf-139">选择缓存文件，再单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="90dbf-139">Select the cache file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="90dbf-140">该文件将显示在解决方案资源管理器中的 **“杂项”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="90dbf-140">The file appears in the **Miscellaneous** folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="90dbf-141">配置项目以创建一个部署实用工具，再生成项目。</span><span class="sxs-lookup"><span data-stu-id="90dbf-141">Configure the project to create a deployment utility, and then build the project.</span></span> <span data-ttu-id="90dbf-142">有关详细信息，请参阅 [Create a Deployment Utility](../../create-a-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-142">For more information, see [Create a Deployment Utility](../../create-a-deployment-utility.md).</span></span>  
  
     <span data-ttu-id="90dbf-143">将创建一个清单文件 \<*project name*>.SSISDeploymentManifest.xml，其中列出了项目、包及包配置中的杂项文件。</span><span class="sxs-lookup"><span data-stu-id="90dbf-143">A manifest file, \<*project name*>.SSISDeploymentManifest.xml, is created that lists the miscellaneous files in the project, the packages, and the package configurations.</span></span>  
  
5.  <span data-ttu-id="90dbf-144">将包部署到文件系统。</span><span class="sxs-lookup"><span data-stu-id="90dbf-144">Deploy the package to the file system.</span></span> <span data-ttu-id="90dbf-145">有关详细信息，请参阅 [Deploy Packages by Using the Deployment Utility](../../deploy-packages-by-using-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="90dbf-145">For more information, see [Deploy Packages by Using the Deployment Utility](../../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90dbf-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90dbf-146">See Also</span></span>  
 [<span data-ttu-id="90dbf-147">创建部署实用工具</span><span class="sxs-lookup"><span data-stu-id="90dbf-147">Create a Deployment Utility</span></span>](../../create-a-deployment-utility.md)  
  
  
