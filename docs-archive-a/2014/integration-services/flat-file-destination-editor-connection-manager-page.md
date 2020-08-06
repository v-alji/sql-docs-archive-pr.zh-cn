---
title: "\"平面文件目标编辑器\" (连接管理器页) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledestadapter.connection.f1
helpviewer_keywords:
- Flat File Destination Editor
ms.assetid: b01571fa-bc19-4742-8eed-ac163172a919
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6997b72851c2b7bfc56445e6ddb01cfe6e9b04cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578344"
---
# <a name="flat-file-destination-editor-connection-manager-page"></a><span data-ttu-id="d4e7b-102">平面文件目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="d4e7b-102">Flat File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="d4e7b-103">可以使用 **“平面文件目标编辑器”** 对话框的 **“连接管理器”** 页为目标选择平面文件连接，以及指定是覆盖现有目标文件还是追加到现有目标文件。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-103">Use the **Connection Manager** page of the **Flat File Destination Editor** dialog box to select the flat file connection for the destination, and to specify whether to overwrite or append to the existing destination file.</span></span> <span data-ttu-id="d4e7b-104">平面文件目标可以将数据写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-104">The flat file destination writes data to a text file.</span></span> <span data-ttu-id="d4e7b-105">该文本文件可以采用带分隔符、固定宽度、带有行分隔符的固定宽度或右边未对齐的格式。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-105">This text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="d4e7b-106">若要了解有关平面文件目标的详细信息，请参阅 [Flat File Destination](data-flow/flat-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-106">To learn more about the Flat File destination, see [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4e7b-107">选项</span><span class="sxs-lookup"><span data-stu-id="d4e7b-107">Options</span></span>  
 <span data-ttu-id="d4e7b-108">**平面文件连接管理器**</span><span class="sxs-lookup"><span data-stu-id="d4e7b-108">**Flat File connection manager**</span></span>  
 <span data-ttu-id="d4e7b-109">使用列表框选择现有的连接管理器，或单击“新建”  创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-109">Select an existing connection manager by using the list box, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="d4e7b-110">**新建**</span><span class="sxs-lookup"><span data-stu-id="d4e7b-110">**New**</span></span>  
 <span data-ttu-id="d4e7b-111">使用“平面文件格式”和“平面文件连接管理器编辑器”   对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-111">Create a new connection by using the **Flat File Format** and **Flat File Connection Manager Editor** dialog boxes.</span></span>  
  
 <span data-ttu-id="d4e7b-112">**“平面文件格式”** 对话框中除了提供带分隔符、固定宽度和右边未对齐这三种标准的平面文件格式外，还提供了第四个选项： **“固定宽度并使用行分隔符”** 。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-112">In addition to the standard flat file formats of delimited, fixed width, and ragged right, the **Flat File Format** dialog box has a fourth option, **Fixed width with row delimiters**.</span></span> <span data-ttu-id="d4e7b-113">此选项表示右边未对齐格式的一种特殊情况，在这种格式下， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将添加一个虚列作为最后一个数据列。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-113">This option represents a special case of the ragged-right format in which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] adds a dummy column as the final column of data.</span></span> <span data-ttu-id="d4e7b-114">此虚列可确保最后一列具有固定宽度。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-114">This dummy column ensures that the final column has a fixed width.</span></span>  
  
 <span data-ttu-id="d4e7b-115">**“固定宽度并使用行分隔符”** 选项在 **“平面文件连接管理器编辑器”** 中不可用。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-115">The **Fixed width with row delimiters** option is not available in the **Flat File Connection Manager Editor**.</span></span> <span data-ttu-id="d4e7b-116">如果需要，可以在该编辑器中模拟此选项。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-116">If necessary, you can emulate this option in the editor.</span></span> <span data-ttu-id="d4e7b-117">若要模拟此选项，请在 **“平面文件连接管理器编辑器”** 的 **“常规”** 页上，为 **“格式”** 选择 **“右边未对齐”** 。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-117">To emulate this option, on the **General** page of the **Flat File Connection Manager Editor**, for **Format**, select **Ragged right**.</span></span> <span data-ttu-id="d4e7b-118">然后在该编辑器的 **“高级”** 页上，添加一个新的虚列作为最后一个数据列。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-118">Then on the **Advanced** page of the editor, add a new dummy column as the final column of data.</span></span>  
  
 <span data-ttu-id="d4e7b-119">**覆盖文件中的数据**</span><span class="sxs-lookup"><span data-stu-id="d4e7b-119">**Overwrite data in the file**</span></span>  
 <span data-ttu-id="d4e7b-120">指示是覆盖现有文件还是向现有文件中追加数据。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-120">Indicate whether to overwrite an existing file, or to append data to it.</span></span>  
  
 <span data-ttu-id="d4e7b-121">**标头**</span><span class="sxs-lookup"><span data-stu-id="d4e7b-121">**Header**</span></span>  
 <span data-ttu-id="d4e7b-122">键入在向文件中写入任何数据之前插入到该文件中的文本块。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-122">Type a block of text to insert into the file before any data is written.</span></span> <span data-ttu-id="d4e7b-123">使用此选项可以包括其他信息，如列标题。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-123">Use this option to include additional information, such as column headings.</span></span>  
  
 <span data-ttu-id="d4e7b-124">**预览**</span><span class="sxs-lookup"><span data-stu-id="d4e7b-124">**Preview**</span></span>  
 <span data-ttu-id="d4e7b-125">通过使用“数据视图”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-125">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="d4e7b-126">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="d4e7b-126">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e7b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4e7b-127">See Also</span></span>  
 <span data-ttu-id="d4e7b-128">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d4e7b-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="d4e7b-129">平面文件目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="d4e7b-129">Flat File Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/flat-file-destination-editor-mappings-page.md)  
  
  
