---
title: 缓存连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 38a858217925496d8dd937d684368bdb2e061b14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590331"
---
# <a name="cache-connection-manager-editor"></a><span data-ttu-id="bded0-102">缓存连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="bded0-102">Cache Connection Manager Editor</span></span>
  <span data-ttu-id="bded0-103">缓存连接管理器从缓存转换或缓存文件 (.caw) 中读取引用数据集，并且可以将数据保存到缓存文件中。</span><span class="sxs-lookup"><span data-stu-id="bded0-103">The Cache connection manager reads a reference dataset from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="bded0-104">这些数据始终存储在内存中。</span><span class="sxs-lookup"><span data-stu-id="bded0-104">The data is always stored in memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bded0-105">缓存连接管理器不支持二进制大型对象 (BLOB) 数据类型 DT_TEXT、DT_NTEXT 和 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="bded0-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="bded0-106">如果引用数据集包含 BLOB 数据类型，则运行包时该组件将失败。</span><span class="sxs-lookup"><span data-stu-id="bded0-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="bded0-107">可以使用 **“缓存连接管理器编辑器”** 修改列数据类型。</span><span class="sxs-lookup"><span data-stu-id="bded0-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span>  
  
 <span data-ttu-id="bded0-108">查找转换在引用数据集上执行查找。</span><span class="sxs-lookup"><span data-stu-id="bded0-108">The Lookup transformation performs lookups on the reference dataset.</span></span>  
  
 <span data-ttu-id="bded0-109">“缓存连接管理器编辑器”\*\*\*\* 对话框包含以下选项卡：</span><span class="sxs-lookup"><span data-stu-id="bded0-109">The **Cache Connection ManagerEditor** dialog box includes the following tabs:</span></span>  
  
-   [<span data-ttu-id="bded0-110">常规选项卡</span><span class="sxs-lookup"><span data-stu-id="bded0-110">General tab</span></span>](#generaltab)  
  
-   [<span data-ttu-id="bded0-111">列选项卡</span><span class="sxs-lookup"><span data-stu-id="bded0-111">Columns tab</span></span>](#columnstab)  
  
 <span data-ttu-id="bded0-112">若要了解有关缓存连接管理器的详细信息，请参阅[缓存连接管理器](connection-manager/cache-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="bded0-112">To learn more about the Cache Connection Manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
##  <a name="general-tab"></a><a name="generaltab"></a><span data-ttu-id="bded0-113">常规选项卡</span><span class="sxs-lookup"><span data-stu-id="bded0-113">General Tab</span></span>  
 <span data-ttu-id="bded0-114">“缓存连接管理器编辑器”对话框的“常规”选项卡用于指示是从文件读取缓存还是将缓存保存到文件\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bded0-114">Use the **General** tab of the **Cache Connection ManagerEditor** dialog box to indicate whether to read the cache from a file or save the cache to a file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="bded0-115">选项</span><span class="sxs-lookup"><span data-stu-id="bded0-115">Options</span></span>  
 <span data-ttu-id="bded0-116">**连接管理器名称**</span><span class="sxs-lookup"><span data-stu-id="bded0-116">**Connection manager name**</span></span>  
 <span data-ttu-id="bded0-117">为工作流中的缓存连接提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="bded0-117">Provide a unique name for the cache connection in the workflow.</span></span> <span data-ttu-id="bded0-118">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="bded0-118">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="bded0-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="bded0-119">**Description**</span></span>  
 <span data-ttu-id="bded0-120">描述此连接。</span><span class="sxs-lookup"><span data-stu-id="bded0-120">Describe the connection.</span></span> <span data-ttu-id="bded0-121">最好根据连接的用途对其进行说明，以使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="bded0-121">As a best practice, describe the connection according to its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="bded0-122">**使用文件缓存**</span><span class="sxs-lookup"><span data-stu-id="bded0-122">**Use file cache**</span></span>  
 <span data-ttu-id="bded0-123">指示是否使用缓存文件。</span><span class="sxs-lookup"><span data-stu-id="bded0-123">Indicate whether to use a cache file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bded0-124">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="bded0-124">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="bded0-125">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="bded0-125">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="bded0-126">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="bded0-126">You should enable access only to certain accounts.</span></span> <span data-ttu-id="bded0-127">有关详细信息，请参阅 [访问包使用的文件](../../2014/integration-services/access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="bded0-127">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="bded0-128">如果将缓存连接管理器配置为使用缓存文件，则连接管理器将执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="bded0-128">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
-   <span data-ttu-id="bded0-129">若将“缓存转换”转换配置为将数据从数据流中的某个数据源写入缓存连接管理器，则将数据保存到该文件。</span><span class="sxs-lookup"><span data-stu-id="bded0-129">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span> <span data-ttu-id="bded0-130">有关详细信息，请参阅 [Cache Transform](data-flow/transformations/cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="bded0-130">For more information, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="bded0-131">从缓存文件读取数据。</span><span class="sxs-lookup"><span data-stu-id="bded0-131">Read data from the cache file.</span></span>  
  
 <span data-ttu-id="bded0-132">**文件名**</span><span class="sxs-lookup"><span data-stu-id="bded0-132">**File name**</span></span>  
 <span data-ttu-id="bded0-133">键入缓存文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="bded0-133">Type the path and file name of the cache file.</span></span>  
  
 <span data-ttu-id="bded0-134">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="bded0-134">**Browse**</span></span>  
 <span data-ttu-id="bded0-135">定位缓存文件。</span><span class="sxs-lookup"><span data-stu-id="bded0-135">Locate the cache file.</span></span>  
  
 <span data-ttu-id="bded0-136">**刷新元数据**</span><span class="sxs-lookup"><span data-stu-id="bded0-136">**Refresh Metadata**</span></span>  
 <span data-ttu-id="bded0-137">删除缓存连接管理器中的列元数据，然后用所选缓存文件中的列元数据重新填充缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="bded0-137">Delete the column metadata in the Cache connection manager and repopulate the Cache connection manager with column metadata from a selected cache file.</span></span>  
  
##  <a name="columns-tab"></a><a name="columnstab"></a><span data-ttu-id="bded0-138">列选项卡</span><span class="sxs-lookup"><span data-stu-id="bded0-138">Columns Tab</span></span>  
 <span data-ttu-id="bded0-139">**“缓存连接管理器编辑器”** 对话框的 **“列”** 选项卡用于配置缓存中各列的属性。</span><span class="sxs-lookup"><span data-stu-id="bded0-139">Use the **Columns** tab of the **Cache Connection Manager Editor** dialog box to configure the properties of each column in the cache.</span></span>  
  
### <a name="options"></a><span data-ttu-id="bded0-140">选项</span><span class="sxs-lookup"><span data-stu-id="bded0-140">Options</span></span>  
 <span data-ttu-id="bded0-141">**列**</span><span class="sxs-lookup"><span data-stu-id="bded0-141">**Column**</span></span>  
 <span data-ttu-id="bded0-142">指定列名。</span><span class="sxs-lookup"><span data-stu-id="bded0-142">Specify the column name.</span></span>  
  
 <span data-ttu-id="bded0-143">**索引位置**</span><span class="sxs-lookup"><span data-stu-id="bded0-143">**Index Position**</span></span>  
 <span data-ttu-id="bded0-144">通过指定各列的索引位置指定哪些列是索引列。</span><span class="sxs-lookup"><span data-stu-id="bded0-144">Specify which columns are index columns by specifying the index position of each column.</span></span> <span data-ttu-id="bded0-145">索引是一列或多个列的集合。</span><span class="sxs-lookup"><span data-stu-id="bded0-145">The index is a collection of one or more columns.</span></span>  
  
 <span data-ttu-id="bded0-146">对于非索引列，索引位置是 0。</span><span class="sxs-lookup"><span data-stu-id="bded0-146">For non-index columns, the index position is 0.</span></span>  
  
 <span data-ttu-id="bded0-147">对于索引列，索引位置是连续的正数。</span><span class="sxs-lookup"><span data-stu-id="bded0-147">For index columns, the index position is a sequential, positive number.</span></span> <span data-ttu-id="bded0-148">此数字指示查找转换将引用数据集中的行与输入数据源中的行进行比较的顺序。</span><span class="sxs-lookup"><span data-stu-id="bded0-148">This number indicates the order in which the Lookup transformation compares rows in the reference dataset to rows in the input data source.</span></span> <span data-ttu-id="bded0-149">具有最多唯一值的列应当具有最低的索引位置。</span><span class="sxs-lookup"><span data-stu-id="bded0-149">The column with the most unique values should have the lowest index position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bded0-150">当将查找转换配置为使用缓存连接管理器时，则仅引用数据集中的索引列能够映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="bded0-150">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="bded0-151">此外，还必须对所有索引列进行映射。</span><span class="sxs-lookup"><span data-stu-id="bded0-151">Also, all index columns must be mapped.</span></span>  
  
 <span data-ttu-id="bded0-152">**Type**</span><span class="sxs-lookup"><span data-stu-id="bded0-152">**Type**</span></span>  
 <span data-ttu-id="bded0-153">指定列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="bded0-153">Specify the data type of the column.</span></span>  
  
 `Length`  
 <span data-ttu-id="bded0-154">指定列数据类型。</span><span class="sxs-lookup"><span data-stu-id="bded0-154">Specifies the column data type.</span></span> <span data-ttu-id="bded0-155">如果适用于该数据类型，则可更新`Length`。</span><span class="sxs-lookup"><span data-stu-id="bded0-155">If applicable to the data type, you can update `Length`.</span></span>  
  
 `Precision`  
 <span data-ttu-id="bded0-156">指定特定列数据类型的精度。</span><span class="sxs-lookup"><span data-stu-id="bded0-156">Specifies the precision for certain column data types.</span></span> <span data-ttu-id="bded0-157">精度指数字的位数。</span><span class="sxs-lookup"><span data-stu-id="bded0-157">Precision is the number of digits in a number.</span></span> <span data-ttu-id="bded0-158">如果适用于该数据类型，则可更新`Precision`。</span><span class="sxs-lookup"><span data-stu-id="bded0-158">If applicable to the data type, you can update `Precision`.</span></span>  
  
 `Scale`  
 <span data-ttu-id="bded0-159">指定特定列数据类型的小数位数。</span><span class="sxs-lookup"><span data-stu-id="bded0-159">Specifies the scale for certain column data types.</span></span> <span data-ttu-id="bded0-160">小数位数指小数点后的数字位数。</span><span class="sxs-lookup"><span data-stu-id="bded0-160">Scale is the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="bded0-161">如果适用于该数据类型，则可更新`Scale`。</span><span class="sxs-lookup"><span data-stu-id="bded0-161">If applicable to the data type, you can update `Scale`.</span></span>  
  
 `Code Page`  
 <span data-ttu-id="bded0-162">指定列类型的代码页。</span><span class="sxs-lookup"><span data-stu-id="bded0-162">Specifies the code page for the column type.</span></span> <span data-ttu-id="bded0-163">如果适用于该数据类型，则可更新`Code Page`。</span><span class="sxs-lookup"><span data-stu-id="bded0-163">If applicable to the data type, you can update `Code Page`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bded0-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bded0-164">See Also</span></span>  
 [<span data-ttu-id="bded0-165">查找转换</span><span class="sxs-lookup"><span data-stu-id="bded0-165">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
