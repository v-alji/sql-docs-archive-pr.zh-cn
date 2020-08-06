---
title: 查找搜索属性的属性集 GUID 和属性整数 ID | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], configuring
ms.assetid: 7db79165-8bcc-4be6-8d40-12d44deda79f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53c08d3a2f86c7e412fbdb1caa6d55d7d23bf407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689837"
---
# <a name="find-property-set-guids-and-property-integer-ids-for-search-properties"></a><span data-ttu-id="09e06-102">查找搜索属性的属性集 GUID 和属性整数 ID</span><span class="sxs-lookup"><span data-stu-id="09e06-102">Find Property Set GUIDs and Property Integer IDs for Search Properties</span></span>
  <span data-ttu-id="09e06-103">本主题讨论在将属性添加到搜索属性列表且使其可由全文搜索进行搜索之前，如何获取所需的值。</span><span class="sxs-lookup"><span data-stu-id="09e06-103">This topic discusses how to obtain the values that are required before you can add a property to a search property list and make it searchable by full-text search.</span></span> <span data-ttu-id="09e06-104">这些值包括文档属性的属性集 GUID 和属性整数标识符。</span><span class="sxs-lookup"><span data-stu-id="09e06-104">These values include the property set GUID and property integer identifier of a document property.</span></span>  
  
 <span data-ttu-id="09e06-105">Ifilter 从二进制数据（即，存储在中的数据 `varbinary` 、 `varbinary(max)` (包括) 或数据类型列）中提取的文档属性 `FILESTREAM` `image` 可用于全文搜索。</span><span class="sxs-lookup"><span data-stu-id="09e06-105">Document properties that are extracted by IFilters from binary data - that is, from data stored in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` data type column - can be made available for full-text search.</span></span> <span data-ttu-id="09e06-106">若要使提取的属性可供搜索，必须手动将该属性添加到搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="09e06-106">To make an extracted property searchable, the property must be manually added to a search property list.</span></span> <span data-ttu-id="09e06-107">搜索属性列表还必须与一个或多个全文索引相关联。</span><span class="sxs-lookup"><span data-stu-id="09e06-107">The search property list must also be associated with one or more full-text indexes.</span></span> <span data-ttu-id="09e06-108">有关详细信息，请参阅 [使用搜索属性列表搜索文档属性](search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="09e06-108">For more information, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="09e06-109">在向属性列表添加可用属性之前，必须找到有关该属性的 2 段信息：</span><span class="sxs-lookup"><span data-stu-id="09e06-109">Before you can add an available property to a property list, you have to find 2 pieces of information about the property:</span></span>  
  
-   <span data-ttu-id="09e06-110">该属性的属性集 GUID。</span><span class="sxs-lookup"><span data-stu-id="09e06-110">The property set GUID of the property.</span></span>  
  
-   <span data-ttu-id="09e06-111">该属性的整数标识符。</span><span class="sxs-lookup"><span data-stu-id="09e06-111">The integer ID of the property.</span></span>  
  
 <span data-ttu-id="09e06-112">（当将属性添加到属性列表时，还必须提供名称和说明。</span><span class="sxs-lookup"><span data-stu-id="09e06-112">(When you add a property to a property list, you also have to provide a name and description.</span></span> <span data-ttu-id="09e06-113">但是，不一定使用属性的规范名称和说明。）</span><span class="sxs-lookup"><span data-stu-id="09e06-113">However you do not have to use the canonical name and description of the property.)</span></span>  
  
 <span data-ttu-id="09e06-114">本主题介绍可找到有关可用属性的信息的常用方法，尤其是有关 Microsoft 定义的属性。</span><span class="sxs-lookup"><span data-stu-id="09e06-114">This topic describes the commonly-used methods to find information about available properties, especially about properties that are defined by Microsoft.</span></span> <span data-ttu-id="09e06-115">有关由第三方定义的属性的信息，请参阅第三方文档或与该供应商联系。</span><span class="sxs-lookup"><span data-stu-id="09e06-115">For information about properties that have been defined by a third party, refer to the third-party documentation or contact the vendor.</span></span>  
  
##  <a name="finding-information-about-widely-used-well-known-microsoft-properties"></a><a name="wellknown"></a> <span data-ttu-id="09e06-116">查找广泛使用的、众所周知的 Microsoft 属性的信息</span><span class="sxs-lookup"><span data-stu-id="09e06-116">Finding Information about Widely Used, Well-Known Microsoft Properties</span></span>  
 <span data-ttu-id="09e06-117">Microsoft 定义了数百个在多种上下文中使用的文档属性，但这只是每种文件格式使用的可用属性的一小部分。</span><span class="sxs-lookup"><span data-stu-id="09e06-117">Microsoft defines hundreds of document properties for use in many contexts, but only a small subset of the available properties are used by each file format.</span></span> <span data-ttu-id="09e06-118">在常用的 Windows 属性中包括一小部分泛型属性。</span><span class="sxs-lookup"><span data-stu-id="09e06-118">Among the frequently used Windows properties is a small set of generic properties.</span></span> <span data-ttu-id="09e06-119">下表显示了众所周知的泛型属性的一些示例。</span><span class="sxs-lookup"><span data-stu-id="09e06-119">Some examples of well-known generic properties are shown in the following table.</span></span> <span data-ttu-id="09e06-120">下表显示了已知名称、Windows 规范名称（来自 Microsoft 发布的属性说明）、属性集 GUID、属性整数标识符和简短说明。</span><span class="sxs-lookup"><span data-stu-id="09e06-120">The table shows the well-known name, the Windows canonical name (from the property description published by Microsoft), the property set GUID, the property integer identifier, and a brief description.</span></span>  
  
|<span data-ttu-id="09e06-121">已知名称</span><span class="sxs-lookup"><span data-stu-id="09e06-121">Well-known name</span></span>|<span data-ttu-id="09e06-122">Windows 规范名称</span><span class="sxs-lookup"><span data-stu-id="09e06-122">Windows canonical name</span></span>|<span data-ttu-id="09e06-123">属性集 GUID</span><span class="sxs-lookup"><span data-stu-id="09e06-123">Property set GUID</span></span>|<span data-ttu-id="09e06-124">整数标识符</span><span class="sxs-lookup"><span data-stu-id="09e06-124">Integer ID</span></span>|<span data-ttu-id="09e06-125">说明</span><span class="sxs-lookup"><span data-stu-id="09e06-125">Description</span></span>|  
|----------------------|----------------------------|-----------------------|----------------|-----------------|  
|<span data-ttu-id="09e06-126">Authors</span><span class="sxs-lookup"><span data-stu-id="09e06-126">Authors</span></span>|`System.Author`|<span data-ttu-id="09e06-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="09e06-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="09e06-128">4</span><span class="sxs-lookup"><span data-stu-id="09e06-128">4</span></span>|<span data-ttu-id="09e06-129">给定项的一个或多个创作者。</span><span class="sxs-lookup"><span data-stu-id="09e06-129">Author or authors of a given item.</span></span>|  
|<span data-ttu-id="09e06-130">标记</span><span class="sxs-lookup"><span data-stu-id="09e06-130">Tags</span></span>|`System.Keywords`|<span data-ttu-id="09e06-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="09e06-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="09e06-132">5</span><span class="sxs-lookup"><span data-stu-id="09e06-132">5</span></span>|<span data-ttu-id="09e06-133">分配给该项的一组关键字（也称为标记）。</span><span class="sxs-lookup"><span data-stu-id="09e06-133">Set of keywords (also known as tags) assigned to the item.</span></span>|  
|<span data-ttu-id="09e06-134">类型</span><span class="sxs-lookup"><span data-stu-id="09e06-134">Type</span></span>|`System.PerceivedType`|<span data-ttu-id="09e06-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span><span class="sxs-lookup"><span data-stu-id="09e06-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span></span>|<span data-ttu-id="09e06-136">9</span><span class="sxs-lookup"><span data-stu-id="09e06-136">9</span></span>|<span data-ttu-id="09e06-137">假设的文件类型，基于其规范类型。</span><span class="sxs-lookup"><span data-stu-id="09e06-137">Perceived file type based on its canonical type.</span></span>|  
|<span data-ttu-id="09e06-138">标题</span><span class="sxs-lookup"><span data-stu-id="09e06-138">Title</span></span>|`System.Title`|<span data-ttu-id="09e06-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="09e06-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="09e06-140">2</span><span class="sxs-lookup"><span data-stu-id="09e06-140">2</span></span>|<span data-ttu-id="09e06-141">项的标题。</span><span class="sxs-lookup"><span data-stu-id="09e06-141">Title of the item.</span></span> <span data-ttu-id="09e06-142">例如，文档的标题、邮件的主题、照片的题注或音乐曲目的名称。</span><span class="sxs-lookup"><span data-stu-id="09e06-142">For example, the title of a document, the subject of a message, the caption of a photo, or the name of a music track.</span></span>|  
  
 <span data-ttu-id="09e06-143">为了提倡在文件格式之间保持一致性，Microsoft 为几类文档确定了部分常用的高优先级文档属性。</span><span class="sxs-lookup"><span data-stu-id="09e06-143">To encourage consistency among file formats, Microsoft has identified subsets of frequently used, high-priority document properties for several categories of documents.</span></span> <span data-ttu-id="09e06-144">其中包括通信、联系人、文档、音乐文件、图片和视频。</span><span class="sxs-lookup"><span data-stu-id="09e06-144">These include communications, contacts, documents, music files, pictures, and videos.</span></span> <span data-ttu-id="09e06-145">有关每个类别排名靠前的属性的详细信息，请参阅 Windows 搜索文档中的 [system-defined properties for custom file formats](https://go.microsoft.com/fwlink/?LinkId=144336) （自定义文件格式的系统定义属性）。</span><span class="sxs-lookup"><span data-stu-id="09e06-145">For more information about the top-ranked properties for each category, see [system-defined properties for custom file formats](https://go.microsoft.com/fwlink/?LinkId=144336) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="09e06-146">特定的文件格式可能实现三种类型的属性：</span><span class="sxs-lookup"><span data-stu-id="09e06-146">A specific file format might implement properties of three types:</span></span>  
  
-   <span data-ttu-id="09e06-147">由 [!INCLUDE[msCoName](../../includes/msconame-md.md)]定义的泛型属性。</span><span class="sxs-lookup"><span data-stu-id="09e06-147">Generic properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="09e06-148">由 [!INCLUDE[msCoName](../../includes/msconame-md.md)]定义的特定于类别的属性。</span><span class="sxs-lookup"><span data-stu-id="09e06-148">Category-specific properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="09e06-149">由软件供应商定义的特定于应用程序的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="09e06-149">Custom, application-specific properties defined by the software vendor.</span></span>  
  
##  <a name="finding-information-about-available-properties-by-using-filtdumpexe"></a><a name="filtdump"></a> <span data-ttu-id="09e06-150">通过使用 FILTDUMP.EXE 查找有关可用属性的信息</span><span class="sxs-lookup"><span data-stu-id="09e06-150">Finding Information about Available Properties by using FILTDUMP.EXE</span></span>  
 <span data-ttu-id="09e06-151">若要了解哪些属性是由安装的 IFilter 发现和提取的，可安装并运行属于 **Windows SDK 的** filtdump.exe [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实用工具。</span><span class="sxs-lookup"><span data-stu-id="09e06-151">To learn what properties are discovered and extracted by an installed IFilter, you can install and run the **filtdump.exe** utility, which is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK.</span></span>  
  
 <span data-ttu-id="09e06-152">从命令提示符运行 **filtdump.exe** 并提供一个参数。</span><span class="sxs-lookup"><span data-stu-id="09e06-152">You run **filtdump.exe** from the command prompt and provide a single argument.</span></span> <span data-ttu-id="09e06-153">此参数是具有特定文件类型的单独文件的名称，该文件类型是安装 IFilter 所针对的目标文件类型。</span><span class="sxs-lookup"><span data-stu-id="09e06-153">This argument is the name of an individual file that has a file type for which an IFilter is installed.</span></span> <span data-ttu-id="09e06-154">该实用工具显示文档中由 IFilter 发现的所有属性的列表及其属性集 GUID、整数标识符以及其他信息。</span><span class="sxs-lookup"><span data-stu-id="09e06-154">The utility displays a list of all the properties discovered by the IFilter in the document, with their property set GUIDs, integer IDs, and additional information.</span></span>  
  
 <span data-ttu-id="09e06-155">有关安装此软件的信息，请参阅 [Microsoft Windows SDK for Windows 7 and .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=8279)（用于 Windows 7 和 .NET Framework 4 的 Microsoft Windows SDK）。</span><span class="sxs-lookup"><span data-stu-id="09e06-155">For information about installing this software, see [Microsoft Windows SDK for Windows 7 and .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=8279).</span></span> <span data-ttu-id="09e06-156">在下载并安装该 SDK 后，请在下列文件夹中查找 filtdump.exe 实用工具。</span><span class="sxs-lookup"><span data-stu-id="09e06-156">After you download and install the SDK, look in the following folders for the filtdump.exe utility.</span></span>  
  
-   <span data-ttu-id="09e06-157">对于 64 位版本，请查看 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`。</span><span class="sxs-lookup"><span data-stu-id="09e06-157">For the 64-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`.</span></span>  
  
-   <span data-ttu-id="09e06-158">对于 32 位版本，请查看 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`。</span><span class="sxs-lookup"><span data-stu-id="09e06-158">For the 32-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`.</span></span>  
  
##  <a name="finding-values-for-a-search-property-from-a-windows-property-description"></a><a name="propdesc"></a><span data-ttu-id="09e06-159">从 Windows 属性说明查找搜索属性的值</span><span class="sxs-lookup"><span data-stu-id="09e06-159">Finding Values for a Search Property from a Windows Property Description</span></span>  
 <span data-ttu-id="09e06-160">对于众所周知的 Windows 搜索属性，可以从属性说明 (`formatID`) 的 `propID` 和 `propertyDescription` 特性中获取您需要的信息。</span><span class="sxs-lookup"><span data-stu-id="09e06-160">For a well-known Windows search property, you can obtain the information that you need from the `formatID` and `propID` attributes of the property description (`propertyDescription`).</span></span>  
  
 <span data-ttu-id="09e06-161">下面的示例显示了典型的 Microsoft 属性说明的相关部分，在此示例中为 `System.Author` 属性的说明。</span><span class="sxs-lookup"><span data-stu-id="09e06-161">The following example shows the relevant part of a typical Microsoft property description, in this case, of the `System.Author` property.</span></span> <span data-ttu-id="09e06-162">`formatID` 特性指定属性集 GUID `F29F85E0-4FF9-1068-AB91-08002B27B3D9`， `propID` 特性指定属性整数 ID `4.` 。请注意， `name` 特性指定 Windows 规范属性名称 `System.Author`。</span><span class="sxs-lookup"><span data-stu-id="09e06-162">The `formatID` attribute specifies the property set GUID, `F29F85E0-4FF9-1068-AB91-08002B27B3D9`, and the `propID` attribute specifies the property integer ID, `4.` Notice that the `name` attribute specifies the Windows canonical property name, `System.Author`.</span></span> <span data-ttu-id="09e06-163">（此示例中省略了不相关的属性描述部分。）</span><span class="sxs-lookup"><span data-stu-id="09e06-163">(This example omits portions of the property description that are not relevant.)</span></span>  
  
```  
.  
propertyDescription  
name = System.Author  
...  
formatID = F29F85E0-4FF9-1068-AB91-08002B27B3D9  
propID = 4  
...  
```  
  
 <span data-ttu-id="09e06-164">有关该属性的完整说明，请参阅 Windows 搜索文档中的 [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) 。</span><span class="sxs-lookup"><span data-stu-id="09e06-164">For the complete description of this property, see [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="09e06-165">有关 Windows 属性的完整列表，请参阅也在 Windows 搜索文档中的 [Windows 属性](https://go.microsoft.com/fwlink/?LinkId=215013)。</span><span class="sxs-lookup"><span data-stu-id="09e06-165">For a complete list of Windows properties, see [Windows Properties](https://go.microsoft.com/fwlink/?LinkId=215013), also in the Windows Search documentation.</span></span>  
  
##  <a name="adding-a-property-to-a-search-property-list"></a><a name="examples"></a> <span data-ttu-id="09e06-166">将属性添加到搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="09e06-166">Adding a Property to a Search Property List</span></span>  
 <span data-ttu-id="09e06-167">下面的示例说明如何将属性添加到搜索属性列表中。</span><span class="sxs-lookup"><span data-stu-id="09e06-167">The following example shows how to add a property to a search property list.</span></span> <span data-ttu-id="09e06-168">该示例使用 [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) 语句将 `System.Author` 属性添加到名为 `PropertyList1`的搜索属性列表，并为属性 `Author`提供用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="09e06-168">The example uses an [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add the `System.Author` property to a search property list named `PropertyList1`, and provides a user friendly name for the property, `Author`.</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST PropertyList1   
  ADD 'Author'  
    WITH (  
          PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',  
          PROPERTY_INT_ID = 4,   
          PROPERTY_DESCRIPTION = 'System.Author - the author or authors of the item'   
         )  
GO  
```  
  
 <span data-ttu-id="09e06-169">有关创建搜索属性列表并将其与全文索引相关联的详细信息，请参阅 [使用搜索属性列表搜索文档属性](search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="09e06-169">For more information about creating a search property list and associating it with a full-text index, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e06-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09e06-170">See Also</span></span>  
 <span data-ttu-id="09e06-171">[用搜索属性列表搜索文档属性](search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="09e06-171">[Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="09e06-172">配置和管理搜索筛选器</span><span class="sxs-lookup"><span data-stu-id="09e06-172">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
