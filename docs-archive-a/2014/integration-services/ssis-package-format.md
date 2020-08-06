---
title: SSIS 包格式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 524c65ac5682b8efe8c4191697eb540f9acca82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689514"
---
# <a name="ssis-package-format"></a><span data-ttu-id="849a6-102">SSIS 包格式</span><span class="sxs-lookup"><span data-stu-id="849a6-102">SSIS Package Format</span></span>
  <span data-ttu-id="849a6-103">在当前版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中，我们对包格式（.dtsx 文件）进行了重大更改，以方便读取格式和比较包。</span><span class="sxs-lookup"><span data-stu-id="849a6-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], significant changes were made to the package format (.dtsx file) to make it easier to read the format and to compare packages.</span></span> <span data-ttu-id="849a6-104">您还可以更可靠地合并不包含冲突更改或以二进制格式存储的更改的包。</span><span class="sxs-lookup"><span data-stu-id="849a6-104">You can also more reliably merge packages that don't contain conflicting changes or changes stored in binary format.</span></span>  
  
 <span data-ttu-id="849a6-105">若要查看当前的 .DTSX 包文件格式，请参阅[ \[ .Dtsx \] ：数据转换服务包 XML 文件格式规范](https://go.microsoft.com/fwlink/?LinkId=233251)。</span><span class="sxs-lookup"><span data-stu-id="849a6-105">To view the current DTSX package file format, see [\[MS-DTSX\]: Data Transformation Services Package XML File Format Specification](https://go.microsoft.com/fwlink/?LinkId=233251).</span></span>  
  
 <span data-ttu-id="849a6-106">下面的列表概述了这些文件格式更改。</span><span class="sxs-lookup"><span data-stu-id="849a6-106">The following list outlines the file format changes.</span></span> <span data-ttu-id="849a6-107">若要查看这些更改的代码示例，请参阅 [SQL Server 2012 中的包格式更改](https://go.microsoft.com/fwlink/?LinkId=233255)。</span><span class="sxs-lookup"><span data-stu-id="849a6-107">To view code examples of these changes, see [Package Format Changes in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=233255).</span></span>  
  
-   <span data-ttu-id="849a6-108">应用了格式约定以将 .dtsx 文件处理为易于读取和理解的形式。</span><span class="sxs-lookup"><span data-stu-id="849a6-108">Formatting conventions have been applied to make it easier to read and understand the .dtsx file.</span></span>  
  
-   <span data-ttu-id="849a6-109">格式更为简洁。</span><span class="sxs-lookup"><span data-stu-id="849a6-109">The format is more concise.</span></span> <span data-ttu-id="849a6-110">每个属性的单独元素始终作为特性（PackageFormatVersion 除外）。</span><span class="sxs-lookup"><span data-stu-id="849a6-110">Separate elements for each property have been persisted as attributes, with the exception of the PackageFormatVersion.</span></span> <span data-ttu-id="849a6-111">特性将按字母顺序列出，且不再保留具有默认值的属性。</span><span class="sxs-lookup"><span data-stu-id="849a6-111">Attributes are listed alphabetically, and properties that have default values are no longer persisted.</span></span> <span data-ttu-id="849a6-112">最后，可多次出现的元素现已包含在父元素中。</span><span class="sxs-lookup"><span data-stu-id="849a6-112">Finally, elements that can appear multiple times, are now contained within a parent element.</span></span>  
  
-   <span data-ttu-id="849a6-113">可由其他对象引用的包中的大多数对象现具有在包 XML 中定义的 `refId` 属性。</span><span class="sxs-lookup"><span data-stu-id="849a6-113">Most objects within a package that can be referred to by other objects now have a `refId` attribute defined in the package XML.</span></span> <span data-ttu-id="849a6-114">现在将保留 `refID`，而不是保留沿袭 ID。</span><span class="sxs-lookup"><span data-stu-id="849a6-114">Instead of persisting lineage IDs, the `refID` is now persisted.</span></span> <span data-ttu-id="849a6-115">沿袭 ID 仍在运行时使用并在加载包时重新生成。</span><span class="sxs-lookup"><span data-stu-id="849a6-115">Lineage IDs are still used within the runtime and regenerated when the package is loaded.</span></span>  
  
     <span data-ttu-id="849a6-116">与 GUID 或整数值相比，`refId` 值是可读且可理解的唯一字符串。</span><span class="sxs-lookup"><span data-stu-id="849a6-116">The `refId` value is a unique string that is readable and understandable, compared to GUIDs or integer values.</span></span> <span data-ttu-id="849a6-117">此字符串类似于早期版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中用于包配置的路径值。</span><span class="sxs-lookup"><span data-stu-id="849a6-117">The string is similar to path values used for package configurations in previous releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="849a6-118">如果要合并两个包版本之间的更改，可在查找/替换操作中使用 `refId` 来确保已正确更新对该对象的所有引用。</span><span class="sxs-lookup"><span data-stu-id="849a6-118">If you are merging changes between two versions of a package, the `refId` can be used in find/replace operations to ensure that all references to that object have been correctly updated.</span></span>  
  
-   <span data-ttu-id="849a6-119">布局信息已包含在 CData 部分。</span><span class="sxs-lookup"><span data-stu-id="849a6-119">The layout information is contained in a CData section.</span></span>  
  
-   <span data-ttu-id="849a6-120">批注将以明文形式保留。</span><span class="sxs-lookup"><span data-stu-id="849a6-120">Annotations are persisted in cleartext.</span></span> <span data-ttu-id="849a6-121">这样便于提取自动生成的文档的信息。</span><span class="sxs-lookup"><span data-stu-id="849a6-121">This makes it easier to extract the information for automated generation of documentation.</span></span>  
  
  
