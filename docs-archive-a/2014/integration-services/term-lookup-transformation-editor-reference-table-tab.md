---
title: 字词查找转换编辑器 (引用表选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.referencetable.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 86ccec6d-615b-4f84-9226-ff80d8012f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f76f15d894896e70139ef80cb2ebad7004ef47ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590908"
---
# <a name="term-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="2f1ec-102">字词查找转换编辑器（“引用表”选项卡）</span><span class="sxs-lookup"><span data-stu-id="2f1ec-102">Term Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="2f1ec-103">可以使用“字词查找转换编辑器”对话框的“引用表”选项卡指定到引用（查找）表的连接。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-103">Use the **Reference Table** tab of the **Term Lookup Transformation Editor** dialog box to specify the connection to the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="2f1ec-104">若要了解有关字词查找转换的详细信息，请参阅 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f1ec-105">选项</span><span class="sxs-lookup"><span data-stu-id="2f1ec-105">Options</span></span>  
 <span data-ttu-id="2f1ec-106">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="2f1ec-106">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="2f1ec-107">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-107">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="2f1ec-108">**新建**</span><span class="sxs-lookup"><span data-stu-id="2f1ec-108">**New**</span></span>  
 <span data-ttu-id="2f1ec-109">通过使用“配置 OLE DB 连接管理器”  对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-109">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="2f1ec-110">**引用表的名称**</span><span class="sxs-lookup"><span data-stu-id="2f1ec-110">**Reference table name**</span></span>  
 <span data-ttu-id="2f1ec-111">通过从该列表中选择项，可以从数据库中选择查找表或视图。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-111">Select a lookup table or view from the database by selecting an item from the list.</span></span> <span data-ttu-id="2f1ec-112">查找表或视图应包含具有现有字词列表的列，以便源列中的文本可以与这些字词进行比较。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-112">The table or view should contain a column with an existing list of terms that the text in the source column can be compared to.</span></span>  
  
 <span data-ttu-id="2f1ec-113">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="2f1ec-113">**Configure Error Output**</span></span>  
 <span data-ttu-id="2f1ec-114">使用 [配置错误输出](../../2014/integration-services/configure-error-output.md) 对话框可以为导致错误的行指定错误处理方式选项。</span><span class="sxs-lookup"><span data-stu-id="2f1ec-114">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1ec-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f1ec-115">See Also</span></span>  
 <span data-ttu-id="2f1ec-116">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2f1ec-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="2f1ec-117">[字词查找转换编辑器 &#40;术语查找选项卡&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span><span class="sxs-lookup"><span data-stu-id="2f1ec-117">[Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span></span>  
 <span data-ttu-id="2f1ec-118">[字词查找转换编辑器 &#40;高级 "选项卡&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="2f1ec-118">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="2f1ec-119">字词提取转换</span><span class="sxs-lookup"><span data-stu-id="2f1ec-119">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
