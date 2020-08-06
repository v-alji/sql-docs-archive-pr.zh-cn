---
title: 原始文件目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledest.f1
helpviewer_keywords:
- append options [Integration Services]
- destinations [Integration Services], Raw File
- raw data [Integration Services]
- writing raw data
- Raw File destination
ms.assetid: d311b458-aefc-4b4d-b1a1-4c0ebbb34214
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc5ce99be6e467ba323137ef885cbb13bfb328ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579657"
---
# <a name="raw-file-destination"></a><span data-ttu-id="92943-102">Raw File Destination</span><span class="sxs-lookup"><span data-stu-id="92943-102">Raw File Destination</span></span>
  <span data-ttu-id="92943-103">原始文件目标将原始数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="92943-103">The Raw File destination writes raw data to a file.</span></span> <span data-ttu-id="92943-104">因为数据的格式是目标的本机格式，所以数据无需转换，并且几乎不需要分析。</span><span class="sxs-lookup"><span data-stu-id="92943-104">Because the format of the data is native to the destination, the data requires no translation and little parsing.</span></span> <span data-ttu-id="92943-105">这意味着原始文件目标可以比其他目标（如平面文件和 OLE DB 目标）更快地写入数据。</span><span class="sxs-lookup"><span data-stu-id="92943-105">This means that the Raw File destination can write data more quickly than other destinations such as the Flat File and the OLE DB destinations.</span></span>  
  
 <span data-ttu-id="92943-106">除了将原始数据写入文件外，还可以使用原始文件目标生成仅包含列的空原始文件（仅元数据文件），而无需运行包。</span><span class="sxs-lookup"><span data-stu-id="92943-106">In addition to writing raw data to a file, you can also use the Raw File destination to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="92943-107">使用原始文件源检索先前由目标写入的原始数据。</span><span class="sxs-lookup"><span data-stu-id="92943-107">You use the Raw File source to retrieve raw data that was previously written by the destination.</span></span> <span data-ttu-id="92943-108">还可以将原始文件源指向仅元数据文件。</span><span class="sxs-lookup"><span data-stu-id="92943-108">You can also point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="92943-109">原始文件格式包含排序信息。</span><span class="sxs-lookup"><span data-stu-id="92943-109">The raw file format contains sort information.</span></span> <span data-ttu-id="92943-110">原始文件目标将保存所有排序信息，包括字符串列的比较标志。</span><span class="sxs-lookup"><span data-stu-id="92943-110">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="92943-111">原始文件源读取和采用排序信息。</span><span class="sxs-lookup"><span data-stu-id="92943-111">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="92943-112">您可以使用高级编辑器选择将原始文件源配置为忽略文件中的排序标志。</span><span class="sxs-lookup"><span data-stu-id="92943-112">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="92943-113">有关比较标志的详细信息，请参阅 [Comparing String Data](comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="92943-113">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="92943-114">可以用下列方式配置原始文件目标：</span><span class="sxs-lookup"><span data-stu-id="92943-114">You can configure the Raw File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="92943-115">指定访问模式，此访问模式可以是原始文件目标要写入的文件的名称，也可以是包含此文件名称的变量。</span><span class="sxs-lookup"><span data-stu-id="92943-115">Specify an access mode which is either the name of the file or a variable that contains the name of the file to which the Raw File destination writes.</span></span>  
  
-   <span data-ttu-id="92943-116">指示原始文件目标是将数据追加到具有相同名称的现有文件中，还是创建新文件。</span><span class="sxs-lookup"><span data-stu-id="92943-116">Indicate whether the Raw File destination appends data to an existing file that has the same name or creates a new file.</span></span>  
  
 <span data-ttu-id="92943-117">原始文件目标经常用于在包执行之间写入经部分处理的数据的中间结果。</span><span class="sxs-lookup"><span data-stu-id="92943-117">The Raw File destination is frequently used to write intermediary results of partly processed data between package executions.</span></span> <span data-ttu-id="92943-118">存储原始数据意味着数据可以由原始文件源快速读取，然后在将其加载到其最终目标之前进一步转换。</span><span class="sxs-lookup"><span data-stu-id="92943-118">Storing raw data means that the data can be read quickly by a Raw File source and then further transformed before it is loaded into its final destination.</span></span> <span data-ttu-id="92943-119">例如，包可能运行多次，每次都将原始数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="92943-119">For example, a package might run several times, and each time write raw data to files.</span></span> <span data-ttu-id="92943-120">随后，其他包可以使用原始文件源从每个文件读取，使用 Union All 转换将数据合并为一个数据集，然后应用其他转换在将数据加载到其最终目标（如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表）之前编写数据摘要。</span><span class="sxs-lookup"><span data-stu-id="92943-120">Later, a different package can use the Raw File source to read from each file, use a Union All transformation to merge the data into one data set, and then apply additional transformations that summarize the data before loading the data into its final destination such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92943-121">原始文件目标支持空数据，但不支持二进制大型对象 (BLOB) 数据。</span><span class="sxs-lookup"><span data-stu-id="92943-121">The Raw File destination supports null data but not binary large object (BLOB) data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92943-122">原始文件目标不使用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="92943-122">The Raw File destination does not use a connection manager.</span></span>  
  
 <span data-ttu-id="92943-123">此源具有一个常规输入。</span><span class="sxs-lookup"><span data-stu-id="92943-123">This source has one regular input.</span></span> <span data-ttu-id="92943-124">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="92943-124">It does not support an error output.</span></span>  
  
## <a name="append-and-new-file-options"></a><span data-ttu-id="92943-125">追加和新建文件选项</span><span class="sxs-lookup"><span data-stu-id="92943-125">Append and New File Options</span></span>  
 <span data-ttu-id="92943-126">WriteOption 属性包含向现有文件中追加数据或创建新文件的选项。</span><span class="sxs-lookup"><span data-stu-id="92943-126">The WriteOption property includes options to append data to an existing file or create a new file.</span></span>  
  
 <span data-ttu-id="92943-127">下表介绍 WriteOption 属性的可用选项。</span><span class="sxs-lookup"><span data-stu-id="92943-127">The following table describes the available options for the WriteOption property.</span></span>  
  
|<span data-ttu-id="92943-128">选项</span><span class="sxs-lookup"><span data-stu-id="92943-128">Option</span></span>|<span data-ttu-id="92943-129">说明</span><span class="sxs-lookup"><span data-stu-id="92943-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="92943-130">附加</span><span class="sxs-lookup"><span data-stu-id="92943-130">Append</span></span>|<span data-ttu-id="92943-131">将数据追加到现有文件中。</span><span class="sxs-lookup"><span data-stu-id="92943-131">Appends data to an existing file.</span></span> <span data-ttu-id="92943-132">追加数据的元数据必须与文件格式匹配。</span><span class="sxs-lookup"><span data-stu-id="92943-132">The metadata of the appended data must match the file format.</span></span>|  
|<span data-ttu-id="92943-133">始终创建</span><span class="sxs-lookup"><span data-stu-id="92943-133">Create always</span></span>|<span data-ttu-id="92943-134">始终创建新文件。</span><span class="sxs-lookup"><span data-stu-id="92943-134">Always creates a new file.</span></span>|  
|<span data-ttu-id="92943-135">创建一次</span><span class="sxs-lookup"><span data-stu-id="92943-135">Create once</span></span>|<span data-ttu-id="92943-136">创建新文件。</span><span class="sxs-lookup"><span data-stu-id="92943-136">Creates a new file.</span></span> <span data-ttu-id="92943-137">如果该文件已经存在，该组件将失败。</span><span class="sxs-lookup"><span data-stu-id="92943-137">If the file exists, the component fails.</span></span>|  
|<span data-ttu-id="92943-138">截断和追加</span><span class="sxs-lookup"><span data-stu-id="92943-138">Truncate and append</span></span>|<span data-ttu-id="92943-139">截断现有文件，然后将数据写入此文件。</span><span class="sxs-lookup"><span data-stu-id="92943-139">Truncates an existing file and then writes the data to the file.</span></span> <span data-ttu-id="92943-140">追加数据的元数据必须与文件格式匹配。</span><span class="sxs-lookup"><span data-stu-id="92943-140">The metadata of the appended data must match the file format.</span></span>|  
  
 <span data-ttu-id="92943-141">以下是有关追加数据的重要事项：</span><span class="sxs-lookup"><span data-stu-id="92943-141">The following are important items about appending data:</span></span>  
  
-   <span data-ttu-id="92943-142">将数据追加到现有原始文件不重新对数据排序。</span><span class="sxs-lookup"><span data-stu-id="92943-142">Appending data to an existing raw file does not re-sort the data.</span></span>  
  
     <span data-ttu-id="92943-143">您需要确保已排序的键保持正确的顺序。</span><span class="sxs-lookup"><span data-stu-id="92943-143">You need to make certain that the sorted keys remain in the correct order.</span></span>  
  
-   <span data-ttu-id="92943-144">将数据追加到现有原始文件不更改文件元数据（排序信息）。</span><span class="sxs-lookup"><span data-stu-id="92943-144">Appending data to an existing raw file does not change the file metadata (sort information).</span></span>  
  
 <span data-ttu-id="92943-145">例如，包读取针对 ProductKey (PK) 排序的数据。</span><span class="sxs-lookup"><span data-stu-id="92943-145">For example, a package reads data sorted on the ProductKey (PK).</span></span> <span data-ttu-id="92943-146">包数据流将数据追加到现有原始文件。</span><span class="sxs-lookup"><span data-stu-id="92943-146">The package data flow appends the data to an existing raw file.</span></span> <span data-ttu-id="92943-147">首次运行包时，收到三行 (PK 1000, 1100, 1200)。</span><span class="sxs-lookup"><span data-stu-id="92943-147">The first time the package runs, three rows are received (PK 1000, 1100, 1200).</span></span> <span data-ttu-id="92943-148">原始文件现在包含以下数据：</span><span class="sxs-lookup"><span data-stu-id="92943-148">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="92943-149">1000, productA</span><span class="sxs-lookup"><span data-stu-id="92943-149">1000, productA</span></span>  
  
-   <span data-ttu-id="92943-150">1100, productB</span><span class="sxs-lookup"><span data-stu-id="92943-150">1100, productB</span></span>  
  
-   <span data-ttu-id="92943-151">1200, productC</span><span class="sxs-lookup"><span data-stu-id="92943-151">1200, productC</span></span>  
  
 <span data-ttu-id="92943-152">第二次运行包时，收到新的两行 (PK 1001, 1300)。</span><span class="sxs-lookup"><span data-stu-id="92943-152">The second time the package runs, two new rows are received (PK 1001, 1300).</span></span> <span data-ttu-id="92943-153">原始文件现在包含以下数据：</span><span class="sxs-lookup"><span data-stu-id="92943-153">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="92943-154">1000, productA</span><span class="sxs-lookup"><span data-stu-id="92943-154">1000, productA</span></span>  
  
-   <span data-ttu-id="92943-155">1100, productB</span><span class="sxs-lookup"><span data-stu-id="92943-155">1100, productB</span></span>  
  
-   <span data-ttu-id="92943-156">1200, productC</span><span class="sxs-lookup"><span data-stu-id="92943-156">1200, productC</span></span>  
  
-   <span data-ttu-id="92943-157">1001, productD</span><span class="sxs-lookup"><span data-stu-id="92943-157">1001, productD</span></span>  
  
-   <span data-ttu-id="92943-158">1300, productE</span><span class="sxs-lookup"><span data-stu-id="92943-158">1300, productE</span></span>  
  
 <span data-ttu-id="92943-159">将新数据追加到原始文件末尾，已排序的键 (PK) 顺序打乱。</span><span class="sxs-lookup"><span data-stu-id="92943-159">The new data is appended to the end of the raw file, and the sorted keys (PK) are out of order.</span></span> <span data-ttu-id="92943-160">此外，追加操作没有更改文件元数据（排序信息）。</span><span class="sxs-lookup"><span data-stu-id="92943-160">In addition, the append operation didn't change the file metadata (sort information).</span></span> <span data-ttu-id="92943-161">如果使用原始文件源读取文件，该组件指示文件仍针对 PK 排序，即使文件中的数据顺序不再正确。</span><span class="sxs-lookup"><span data-stu-id="92943-161">If you read the file by using the Raw File source, the component indicates that the file is still sorted on PK even though the data in the file is no longer in the correct order.</span></span>  
  
 <span data-ttu-id="92943-162">为了在追加数据时使已排序的键保持正确的顺序，可以按以下方式设计包数据流：</span><span class="sxs-lookup"><span data-stu-id="92943-162">To keep the sorted keys in the correct order while appending data, you can design the package data flow as follows:</span></span>  
  
1.  <span data-ttu-id="92943-163">使用源 A 检索新行。</span><span class="sxs-lookup"><span data-stu-id="92943-163">Retrieve new rows by using Source A.</span></span>  
  
2.  <span data-ttu-id="92943-164">使用源 B 从 RawFile1 检索现有行。</span><span class="sxs-lookup"><span data-stu-id="92943-164">Retrieve existing rows from RawFile1 using Source B.</span></span>  
  
3.  <span data-ttu-id="92943-165">使用 Union All 转换合并源 A 和源 B 中的输入。</span><span class="sxs-lookup"><span data-stu-id="92943-165">Combine the inputs from Source A and Source B by using the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="92943-166">针对 PK 排序。</span><span class="sxs-lookup"><span data-stu-id="92943-166">Sort on PK.</span></span>  
  
5.  <span data-ttu-id="92943-167">使用原始文件目标写入 RawFile2。</span><span class="sxs-lookup"><span data-stu-id="92943-167">Write to RawFile2 by using the Raw File destination.</span></span>  
  
     <span data-ttu-id="92943-168">RawFile1 被锁定，因为在数据流中正在读取它。</span><span class="sxs-lookup"><span data-stu-id="92943-168">RawFile1 is locked because it's being read from, in the data flow.</span></span>  
  
6.  <span data-ttu-id="92943-169">使用 RawFile2 替换 RawFile1。</span><span class="sxs-lookup"><span data-stu-id="92943-169">Replace RawFile1 with RawFile2.</span></span>  
  
### <a name="using-the-raw-file-destination-in-a-loop"></a><span data-ttu-id="92943-170">在循环中使用原始文件目标</span><span class="sxs-lookup"><span data-stu-id="92943-170">Using the Raw File Destination in a Loop</span></span>  
 <span data-ttu-id="92943-171">如果使用原始文件目标的数据流位于循环中，您可能要创建一次文件，然后在循环重复时向该文件中追加数据。</span><span class="sxs-lookup"><span data-stu-id="92943-171">If the data flow that uses the Raw File destination is in a loop, you may want to create the file once and then append data to the file when the loop repeats.</span></span> <span data-ttu-id="92943-172">若要向该文件中追加数据，要追加的数据必须与现有的文件格式匹配。</span><span class="sxs-lookup"><span data-stu-id="92943-172">To append data to the file, the data that is appended must match the format of the existing file.</span></span>  
  
 <span data-ttu-id="92943-173">若要在循环的第一次迭代中创建文件，然后在循环的后续迭代中追加行，您需要在设计时执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="92943-173">To create the file in the first iteration of the loop, and then append rows in the subsequent iterations of the loop, you need to do the following at design time:</span></span>  
  
1.  <span data-ttu-id="92943-174">将 WriteOption 属性设置为 **CreateOnce** 或 **CreateAlways**并运行循环的一次迭代过程。</span><span class="sxs-lookup"><span data-stu-id="92943-174">Set the WriteOption property to **CreateOnce** or **CreateAlways**and run one iteration of the loop.</span></span> <span data-ttu-id="92943-175">此时将创建文件。</span><span class="sxs-lookup"><span data-stu-id="92943-175">The file is created.</span></span> <span data-ttu-id="92943-176">这可确保追加数据的元数据与文件匹配。</span><span class="sxs-lookup"><span data-stu-id="92943-176">This ensures that the metadata of appended data and the file matches.</span></span>  
  
2.  <span data-ttu-id="92943-177">将 WriteOption 属性重置为**Append** ，并将 ValidateExternalMetadata 属性设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="92943-177">Reset the WriteOption property to **Append** and set the ValidateExternalMetadata property to `False`.</span></span>  
  
 <span data-ttu-id="92943-178">如果使用 **TruncateAppend** 选项而不是 **“追加”** 选项，此操作将截断以前的任何迭代过程中所添加的行，然后追加新行。</span><span class="sxs-lookup"><span data-stu-id="92943-178">If you use the **TruncateAppend** option instead of the **Append** option, it will truncate rows that were added in any previous iteration, and then append new rows.</span></span> <span data-ttu-id="92943-179">使用 **TruncateAppend** 选项也要求数据与文件格式相匹配。</span><span class="sxs-lookup"><span data-stu-id="92943-179">Using the **TruncateAppend** option also requires that the data matches the file format.</span></span>  
  
## <a name="configuration-of-the-raw-file-destination"></a><span data-ttu-id="92943-180">原始文件目标的配置</span><span class="sxs-lookup"><span data-stu-id="92943-180">Configuration of the Raw File Destination</span></span>  
 <span data-ttu-id="92943-181">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="92943-181">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="92943-182">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="92943-182">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="92943-183">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="92943-183">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="92943-184">Common Properties</span><span class="sxs-lookup"><span data-stu-id="92943-184">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="92943-185">原始文件自定义属性</span><span class="sxs-lookup"><span data-stu-id="92943-185">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="92943-186">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="92943-186">Related Tasks</span></span>  
 <span data-ttu-id="92943-187">有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="92943-187">For information about how to set properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="92943-188">相关内容</span><span class="sxs-lookup"><span data-stu-id="92943-188">Related Content</span></span>  
 <span data-ttu-id="92943-189">sqlservercentral.com 上的博客文章： [原始文件令人生畏](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)。</span><span class="sxs-lookup"><span data-stu-id="92943-189">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92943-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92943-190">See Also</span></span>  
 <span data-ttu-id="92943-191">[原始文件源](raw-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="92943-191">[Raw File Source](raw-file-source.md) </span></span>  
 [<span data-ttu-id="92943-192">数据流</span><span class="sxs-lookup"><span data-stu-id="92943-192">Data Flow</span></span>](data-flow.md)  
  
  
