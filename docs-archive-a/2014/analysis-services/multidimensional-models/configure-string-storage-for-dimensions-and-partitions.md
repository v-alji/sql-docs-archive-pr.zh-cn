---
title: 配置维度和分区的字符串存储 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987f6cfc-da82-4b2e-96ef-a8af88339e5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2817af382599d4495dddbd8951a72a47629cf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691981"
---
# <a name="configure-string-storage-for-dimensions-and-partitions"></a><span data-ttu-id="8ac5d-102">配置维度和分区的字符串存储</span><span class="sxs-lookup"><span data-stu-id="8ac5d-102">Configure String Storage for Dimensions and Partitions</span></span>
  <span data-ttu-id="8ac5d-103">可以重新配置字符串存储，以在维度属性或分区中容纳超过 4 GB 文件大小的字符串存储限制的极大字符串。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-103">You can reconfigure string storage to accommodate very large strings in dimension attributes or partitions that exceed the 4 GB file size limit for string stores.</span></span> <span data-ttu-id="8ac5d-104">如果你的维度或分区包含此大小的字符串存储，则对于本地和链接（本地或远程）对象，你可以通过在维度或分区级别更改“StringStoresCompatibilityLevel”\*\*\*\* 属性来解决文件大小限制。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-104">If your dimensions or partitions include string stores of this size, you can work around the file size constraint by changing the **StringStoresCompatibilityLevel** property at the dimension or partition level, for local as well as linked (local or remote) objects.</span></span>  
  
 <span data-ttu-id="8ac5d-105">请注意，你可以只在需要额外容量的对象上增加字符串存储空间。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-105">Note that you can increase string storage on just those objects that require additional capacity.</span></span> <span data-ttu-id="8ac5d-106">在大多数的多维模型中，字符串数据与维度相关联。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-106">In most multidimensional models, string data is associated with dimensions.</span></span> <span data-ttu-id="8ac5d-107">但是，此设置对包含基于字符串的非重复计数度量值的分区也非常有用。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-107">However, partitions that contain distinct count measures on top of strings can also benefit from this setting.</span></span> <span data-ttu-id="8ac5d-108">因为此设置针对字符串，所以数字数据不受影响。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-108">Because the setting is for strings, numeric data is unaffected.</span></span>  
  
 <span data-ttu-id="8ac5d-109">此属性的有效值包括以下项：</span><span class="sxs-lookup"><span data-stu-id="8ac5d-109">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="8ac5d-110">值</span><span class="sxs-lookup"><span data-stu-id="8ac5d-110">Value</span></span>|<span data-ttu-id="8ac5d-111">说明</span><span class="sxs-lookup"><span data-stu-id="8ac5d-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ac5d-112">**1050**</span><span class="sxs-lookup"><span data-stu-id="8ac5d-112">**1050**</span></span>|<span data-ttu-id="8ac5d-113">指定默认的字符串存储体系结构，即受到每个存储 4 GB 的最大文件大小的约束。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-113">Specifies the default string storage architecture, subject to a 4 GB maximum file size per store.</span></span>|  
|<span data-ttu-id="8ac5d-114">**1100**</span><span class="sxs-lookup"><span data-stu-id="8ac5d-114">**1100**</span></span>|<span data-ttu-id="8ac5d-115">指定较大的字符串存储空间，支持每个存储区最多 40 亿个唯一字符串。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-115">Specifies larger string storage, supports up to 4 billion unique strings per store.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ac5d-116">更改某一对象的字符串存储设置要求您重新处理该对象本身以及任何依赖对象。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-116">Changing the string storage settings of an object requires that you reprocess the object itself and any dependent object.</span></span> <span data-ttu-id="8ac5d-117">处理是完成这个过程所必需的。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-117">Processing is required to complete the procedure.</span></span>  
  
 <span data-ttu-id="8ac5d-118">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="8ac5d-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="8ac5d-119">关于字符串存储</span><span class="sxs-lookup"><span data-stu-id="8ac5d-119">About String Stores</span></span>](#bkmk_background)  
  
-   [<span data-ttu-id="8ac5d-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="8ac5d-120">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="8ac5d-121">步骤 1：在 SQL Server Data Tools 中设置 StringStoreCompatiblityLevel 属性</span><span class="sxs-lookup"><span data-stu-id="8ac5d-121">Step 1: Set the StringStoreCompatiblityLevel Property in SQL Server Data Tools</span></span>](#bkmk_step1)  
  
-   [<span data-ttu-id="8ac5d-122">步骤 2：处理对象</span><span class="sxs-lookup"><span data-stu-id="8ac5d-122">Step 2: Process the Objects</span></span>](#bkmk_step2)  
  
##  <a name="about-string-stores"></a><a name="bkmk_background"></a><span data-ttu-id="8ac5d-123">关于字符串存储</span><span class="sxs-lookup"><span data-stu-id="8ac5d-123">About String Stores</span></span>  
 <span data-ttu-id="8ac5d-124">字符串存储配置是可选的，这意味着即使是你创建的新数据库，也可以使用受到 4 GB 最大文件大小限制的默认字符串存储体系结构。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-124">String storage configuration is optional, which means that even new databases that you create use the default string store architecture that is subject to the 4 GB maximum file size.</span></span> <span data-ttu-id="8ac5d-125">使用较大的字符串存储体系结构对性能的影响虽然很小，但也是较为明显的。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-125">Using the larger string storage architecture has a small but noticeable impact on performance.</span></span> <span data-ttu-id="8ac5d-126">只有在您的字符串存储文件接近或达到 4 GB 的上限时，才应使用可缩放字符串存储体系结构。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-126">You should use it only if your string storage files are close to or at the maximum 4 GB limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ac5d-127">此设置不适用于数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-127">This setting does not apply to data mining models.</span></span> <span data-ttu-id="8ac5d-128">当前，对于包含数据挖掘结构的模型，仍可能会遇到 GB 级的文件大小限制。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-128">Currently, it is still possible to encounter the GB file size limitation on models containing data mining structures.</span></span>  
  
 <span data-ttu-id="8ac5d-129">在 Analysis Services 多维数据库中，字符串与数值数据分别进行存储，以便允许基于数据特性进行优化。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-129">In an Analysis Services multidimensional database, strings are stored separately from numeric data to allow for optimizations based on characteristics of the data.</span></span> <span data-ttu-id="8ac5d-130">字符串数据通常位于表示名称或说明的维度属性中。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-130">String data is typically found in dimension attributes that represent names or descriptions.</span></span> <span data-ttu-id="8ac5d-131">在非重复计数度量值中也可能具有字符串数据。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-131">It is also possible to have string data in distinct count measures.</span></span> <span data-ttu-id="8ac5d-132">字符串数据也可以用于键中。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-132">String data can also be used in keys.</span></span>  
  
 <span data-ttu-id="8ac5d-133">您可以按其文件扩展名（例如 asstore、.bstore、.ksstore 或 .string 文件）标识字符串存储。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-133">You can identify a string store by its file extension (for example, asstore, .bstore, .ksstore, or .string files).</span></span> <span data-ttu-id="8ac5d-134">默认情况下，上述每种文件都具有 4 GB 的上限。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-134">By default, each of these files is subject to a maximum 4 GB limit.</span></span> <span data-ttu-id="8ac5d-135">在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中，您可以通过指定允许字符串存储按需增大的其他存储机制，取代这一最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-135">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can override the maximum file size by specifying an alternative storage mechanism that allows a string store to grow as needed.</span></span>  
  
 <span data-ttu-id="8ac5d-136">与限制物理文件大小的默认字符串存储体系结构相反，较大的字符串存储空间基于字符串的最大数目。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-136">In contrast with the default string storage architecture which limits the size of the physical file, larger string storage is based on a maximum number of strings.</span></span> <span data-ttu-id="8ac5d-137">较大的字符串存储空间的上限是 40 亿个唯一字符串或 40 亿条记录（以二者中最先达到限制条件的为准）。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-137">The maximum limit for larger string storage is 4 billion unique strings or 4 billion records, whichever occurs first.</span></span> <span data-ttu-id="8ac5d-138">较大的字符串存储空间创建同样大小的记录，每个记录等于 64K 页。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-138">Larger string storage creates records of an even size, where each record is equal to a 64K page.</span></span> <span data-ttu-id="8ac5d-139">如果您具有在单个记录中放不下的非常长的字符串，则有效限制将小于 40 亿个字符串。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-139">If you have very long strings that do not fit in a single record, your effective limit will be less than 4 billion strings.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="8ac5d-140">先决条件</span><span class="sxs-lookup"><span data-stu-id="8ac5d-140">Prerequisites</span></span>  
 <span data-ttu-id="8ac5d-141">你必须具有 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或更高版本的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-141">You must have a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or later version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8ac5d-142">维度和分区必须使用 MOLAP 存储。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-142">Dimensions and partitions must use MOLAP storage.</span></span>  
  
 <span data-ttu-id="8ac5d-143">数据库的兼容级别必须设置为 1100。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-143">The database compatibility level must be set to 1100.</span></span> <span data-ttu-id="8ac5d-144">如果你使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 和 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或更高版本的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]创建了或部署了某一数据库，则该数据库的兼容级别已设置为 1100。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-144">If you created or deployed a database using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or later version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level is already set to 1100.</span></span> <span data-ttu-id="8ac5d-145">如果你将在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 早期版本中创建的数据库移动到 ssSQL11 或更高版本，则必须更新兼容级别。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-145">If you moved a database created in an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to ssSQL11 or later, you must update the compatibility level.</span></span> <span data-ttu-id="8ac5d-146">对于要移动而不是重新部署的数据库，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来设置兼容级别。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-146">For databases that you are moving, but not redeploying, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to set the compatibility level.</span></span> <span data-ttu-id="8ac5d-147">有关详细信息，请参阅[设置多维数据库 &#40;Analysis Services&#41;的兼容级别](compatibility-level-of-a-multidimensional-database-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-147">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
##  <a name="step-1-set-the-stringstorecompatiblitylevel-property-in-sql-server-data-tools"></a><a name="bkmk_step1"></a><span data-ttu-id="8ac5d-148">步骤1：在 SQL Server Data Tools 中设置 StringStoreCompatiblityLevel 属性</span><span class="sxs-lookup"><span data-stu-id="8ac5d-148">Step 1: Set the StringStoreCompatiblityLevel Property in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="8ac5d-149">使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，打开包含要修改的维度或分区的项目。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-149">Using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the dimensions or partitions you want to modify.</span></span>  
  
2.  <span data-ttu-id="8ac5d-150">若要更改维度的字符串存储，请打开解决方案资源管理器。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-150">To change the string storage for dimensions, open Solution Explorer.</span></span> <span data-ttu-id="8ac5d-151">双击您要修改字符串存储的维度。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-151">Double-click the dimension for which you are modifying string storage.</span></span>  
  
3.  <span data-ttu-id="8ac5d-152">在维度设计器的“属性”窗格中，请确保选择该维度的父节点（例如，如果维度为 Customers，则选择 Customers，而不是其子属性之一）。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-152">In Dimension Designer, in the Attributes pane, make sure that the parent node of the dimension is selected (for example, if the dimension is Customers, select Customers and not one of the child attributes).</span></span>  
  
4.  <span data-ttu-id="8ac5d-153">在“属性”窗格的“高级”部分中，将 **StringStoresCompatibilityLevel** 设置为 **1100**。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-153">In the Properties pane, in the Advanced section, set **StringStoresCompatibilityLevel** to **1100**.</span></span> <span data-ttu-id="8ac5d-154">对于要求较大存储空间的其他维度重复上述设置，否则将其余维度的值保持为 **1050** 。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-154">Repeat for other dimensions that require larger storage, otherwise leave the remaining dimensions at the **1050** value.</span></span>  
  
5.  <span data-ttu-id="8ac5d-155">对于分区，请从解决方案资源管理器中打开一个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-155">For partitions, open a cube from Solution Explorer.</span></span>  
  
6.  <span data-ttu-id="8ac5d-156">单击“分区”选项卡。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-156">Click the Partitions tab.</span></span>  
  
7.  <span data-ttu-id="8ac5d-157">展开分区，选择需要额外存储容量的分区，然后修改 **StringStoresCompatibilityLevel** 属性。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-157">Expand the partition, select the partition that requires extra storage capacity, and then modify the **StringStoresCompatibilityLevel** property.</span></span>  
  
8.  <span data-ttu-id="8ac5d-158">保存文件。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-158">Save the file.</span></span>  
  
##  <a name="step-2-process-the-objects"></a><a name="bkmk_step2"></a><span data-ttu-id="8ac5d-159">步骤2：处理对象</span><span class="sxs-lookup"><span data-stu-id="8ac5d-159">Step 2: Process the Objects</span></span>  
 <span data-ttu-id="8ac5d-160">在您处理对象后，将使用新的存储体系结构。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-160">The new storage architecture will be used after you process the objects.</span></span> <span data-ttu-id="8ac5d-161">处理对象也表明您已成功解决了存储约束问题，因为以前报告字符串存储溢出情况的错误不再出现了。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-161">Processing objects also proves you have successfully resolved storage constraint problem because the error that previously reported a string store overflow condition should no longer occur.</span></span>  
  
-   <span data-ttu-id="8ac5d-162">在解决方案资源管理器中，右键单击刚修改的维度，然后选择“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-162">In Solution Explorer, right-click the dimension or you just modified and select **Process**.</span></span>  
  
 <span data-ttu-id="8ac5d-163">您必须对使用新字符串存储体系结构的每个对象都使用“处理全部”选项。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-163">You must use the Process Full option on each object that is using the new string store architecture.</span></span> <span data-ttu-id="8ac5d-164">在处理前，请确保对维度运行影响分析，以便检查依赖对象是否也要求重新处理。</span><span class="sxs-lookup"><span data-stu-id="8ac5d-164">Before processing, be sure to run an impact analysis on the dimension to check whether dependent objects also require reprocessing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac5d-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ac5d-165">See Also</span></span>  
 <span data-ttu-id="8ac5d-166">[处理 &#40;Analysis Services 的工具和方法&#41;](tools-and-approaches-for-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="8ac5d-166">[Tools and Approaches for Processing &#40;Analysis Services&#41;](tools-and-approaches-for-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="8ac5d-167">[处理选项和设置的 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="8ac5d-167">[Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) </span></span>  
 <span data-ttu-id="8ac5d-168">[分区存储模式和处理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md) </span><span class="sxs-lookup"><span data-stu-id="8ac5d-168">[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md) </span></span>  
 [<span data-ttu-id="8ac5d-169">维度存储</span><span class="sxs-lookup"><span data-stu-id="8ac5d-169">Dimension Storage</span></span>](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)  
  
  
