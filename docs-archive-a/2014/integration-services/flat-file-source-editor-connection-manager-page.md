---
title: "\"平面文件源编辑器\" (\"连接管理器\" 页) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c1693c001dad2c8e90211b065eda208c42a07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578337"
---
# <a name="flat-file-source-editor-connection-manager-page"></a><span data-ttu-id="837e0-102">平面文件源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="837e0-102">Flat File Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="837e0-103">可以使用 **“平面文件源编辑器”** 对话框的 **“连接管理器”** 页，选择平面文件源将使用的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="837e0-103">Use the **Connection Manager** page of the **Flat File Source Editor** dialog box to select the connection manager that the Flat File source will use.</span></span> <span data-ttu-id="837e0-104">平面文件源从文本文件中读取数据，文本文件可以采用分隔符分隔、固定宽度或混合格式。</span><span class="sxs-lookup"><span data-stu-id="837e0-104">The Flat File source reads data from a text file, which can be in a delimited, fixed width, or mixed format.</span></span>  
  
 <span data-ttu-id="837e0-105">平面文件源可以使用下列类型的连接管理器之一：</span><span class="sxs-lookup"><span data-stu-id="837e0-105">A Flat File source can use one of the following types of connection managers:</span></span>  
  
-   <span data-ttu-id="837e0-106">如果源是单个平面文件，则使用平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="837e0-106">A Flat File connection manager if the source is a single flat file.</span></span> <span data-ttu-id="837e0-107">有关详细信息，请参阅 [Flat File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="837e0-107">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
-   <span data-ttu-id="837e0-108">如果源是多平面文件并且数据流任务在循环容器（例如 For 循环容器）内，则使用多平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="837e0-108">A Multiple Flat Files connection manager if the source is multiple flat files and the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="837e0-109">在容器的每个循环中，平面文件源从多平面文件连接管理器提供的下一个文件名加载数据。</span><span class="sxs-lookup"><span data-stu-id="837e0-109">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span> <span data-ttu-id="837e0-110">有关详细信息，请参阅 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="837e0-110">For more information, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
 <span data-ttu-id="837e0-111">若要了解有关平面文件源的详细信息，请参阅 [Flat File Source](data-flow/flat-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="837e0-111">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="837e0-112">选项</span><span class="sxs-lookup"><span data-stu-id="837e0-112">Options</span></span>  
 <span data-ttu-id="837e0-113">**平面文件连接管理器**</span><span class="sxs-lookup"><span data-stu-id="837e0-113">**Flat file connection manager**</span></span>  
 <span data-ttu-id="837e0-114">从列表中选择现有的连接管理器，或单击“新建”\*\*\*\* 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="837e0-114">Select an existing connection manager from the list, or create a new connection manager by clicking **New**.</span></span>  
  
 <span data-ttu-id="837e0-115">**新建**</span><span class="sxs-lookup"><span data-stu-id="837e0-115">**New**</span></span>  
 <span data-ttu-id="837e0-116">通过使用“平面文件连接管理器编辑器”\*\*\*\* 对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="837e0-116">Create a new connection manager by using the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="837e0-117">**在数据流中保留源中的空值**</span><span class="sxs-lookup"><span data-stu-id="837e0-117">**Retain null values from the source as null values in the data flow**</span></span>  
 <span data-ttu-id="837e0-118">指定提取数据时是否保留空值。</span><span class="sxs-lookup"><span data-stu-id="837e0-118">Specify whether to keep null values when data is extracted.</span></span> <span data-ttu-id="837e0-119">此属性的默认值为 **false**。</span><span class="sxs-lookup"><span data-stu-id="837e0-119">The default value of this property is **false**.</span></span> <span data-ttu-id="837e0-120">当此值为 F`alse` 时，平面文件源使用每列的相应默认值替换源数据中的空值，例如，对于字符串列使用空字符串，对于数值列使用零。</span><span class="sxs-lookup"><span data-stu-id="837e0-120">When this value is f`alse`, the Flat File source replaces null values from the source data with appropriate default values for each column, such as empty strings for string columns and zero for numeric columns.</span></span>  
  
 <span data-ttu-id="837e0-121">**预览**</span><span class="sxs-lookup"><span data-stu-id="837e0-121">**Preview**</span></span>  
 <span data-ttu-id="837e0-122">通过使用“数据视图”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="837e0-122">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="837e0-123">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="837e0-123">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837e0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="837e0-124">See Also</span></span>  
 <span data-ttu-id="837e0-125">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="837e0-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="837e0-126">["平面文件源编辑器 &#40;列" 页&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="837e0-126">[Flat File Source Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="837e0-127">["平面文件源编辑器" &#40;"错误输出" 页&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="837e0-127">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="837e0-128">平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="837e0-128">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
