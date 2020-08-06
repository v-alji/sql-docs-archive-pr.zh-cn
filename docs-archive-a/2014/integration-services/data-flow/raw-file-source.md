---
title: 原始文件源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbc5800c4fb2b90b74e66b6ff161118b2b550f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579655"
---
# <a name="raw-file-source"></a><span data-ttu-id="b4547-102">原始文件源</span><span class="sxs-lookup"><span data-stu-id="b4547-102">Raw File Source</span></span>
  <span data-ttu-id="b4547-103">原始文件源从文件中读取原始数据。</span><span class="sxs-lookup"><span data-stu-id="b4547-103">The Raw File source reads raw data from a file.</span></span> <span data-ttu-id="b4547-104">因为数据的表示方式是源所固有的，所以数据无需转换，并且几乎不需要分析。</span><span class="sxs-lookup"><span data-stu-id="b4547-104">Because the representation of the data is native to the source, the data requires no translation and almost no parsing.</span></span> <span data-ttu-id="b4547-105">这意味着原始文件源可以比其他源（如平面文件和 OLE DB 源）更快地读取数据。</span><span class="sxs-lookup"><span data-stu-id="b4547-105">This means that the Raw File source can read data more quickly than other sources such as the Flat File and the OLE DB sources.</span></span>  
  
 <span data-ttu-id="b4547-106">原始文件源用于检索先前由原始文件目标写入的原始数据。</span><span class="sxs-lookup"><span data-stu-id="b4547-106">The Raw File source is used to retrieve raw data that was previously written by the Raw File destination.</span></span> <span data-ttu-id="b4547-107">您还可以将原始文件源指向一个仅包含列的空原始文件（仅元数据文件）。</span><span class="sxs-lookup"><span data-stu-id="b4547-107">You can also point the Raw File source to an empty raw file that contains only the columns (metadata-only file).</span></span> <span data-ttu-id="b4547-108">使用原始文件目标生成仅元数据文件而无需运行包。</span><span class="sxs-lookup"><span data-stu-id="b4547-108">You use the Raw File destination to generate the metadata-only file without having to run the package.</span></span> <span data-ttu-id="b4547-109">有关详细信息，请参阅 [Raw File Destination](raw-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="b4547-109">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
 <span data-ttu-id="b4547-110">原始文件格式包含排序信息。</span><span class="sxs-lookup"><span data-stu-id="b4547-110">The raw file format contains sort information.</span></span> <span data-ttu-id="b4547-111">原始文件目标将保存所有排序信息，包括字符串列的比较标志。</span><span class="sxs-lookup"><span data-stu-id="b4547-111">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="b4547-112">原始文件源读取和采用排序信息。</span><span class="sxs-lookup"><span data-stu-id="b4547-112">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="b4547-113">您可以使用高级编辑器选择将原始文件源配置为忽略文件中的排序标志。</span><span class="sxs-lookup"><span data-stu-id="b4547-113">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="b4547-114">有关比较标志的详细信息，请参阅 [Comparing String Data](comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b4547-114">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="b4547-115">可以通过指定原始文件源所读取的文件的名称来配置原始文件。</span><span class="sxs-lookup"><span data-stu-id="b4547-115">You configure the Raw File by specifying the name of the name of the file that the Raw File source reads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4547-116">此源不使用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b4547-116">This source does not use a connection manager.</span></span>  
  
 <span data-ttu-id="b4547-117">此源具有一个输出。</span><span class="sxs-lookup"><span data-stu-id="b4547-117">This source has one output.</span></span> <span data-ttu-id="b4547-118">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="b4547-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-raw-file-source"></a><span data-ttu-id="b4547-119">原始文件源的配置</span><span class="sxs-lookup"><span data-stu-id="b4547-119">Configuration of the Raw File Source</span></span>  
 <span data-ttu-id="b4547-120">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="b4547-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b4547-121">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="b4547-121">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="b4547-122">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="b4547-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b4547-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b4547-123">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="b4547-124">原始文件自定义属性</span><span class="sxs-lookup"><span data-stu-id="b4547-124">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="b4547-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b4547-125">Related Tasks</span></span>  
 <span data-ttu-id="b4547-126">有关如何设置该组件属性的信息，请参阅 [设置数据流组件属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b4547-126">For information about how to set the properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b4547-127">相关内容</span><span class="sxs-lookup"><span data-stu-id="b4547-127">Related Content</span></span>  
  
-   <span data-ttu-id="b4547-128">sqlservercentral.com 上的博客文章： [原始文件令人生畏](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)。</span><span class="sxs-lookup"><span data-stu-id="b4547-128">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4547-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4547-129">See Also</span></span>  
 <span data-ttu-id="b4547-130">[原始文件目标](raw-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="b4547-130">[Raw File Destination](raw-file-destination.md) </span></span>  
 [<span data-ttu-id="b4547-131">数据流</span><span class="sxs-lookup"><span data-stu-id="b4547-131">Data Flow</span></span>](data-flow.md)  
  
  
