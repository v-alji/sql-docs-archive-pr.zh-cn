---
title: 模糊分组转换编辑器 (连接管理器选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2a8b0af9f36fdd386f7da375184fd4e4ec5c4be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589761"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a><span data-ttu-id="56f57-102">模糊分组转换编辑器（“连接管理器”选项卡）</span><span class="sxs-lookup"><span data-stu-id="56f57-102">Fuzzy Grouping Transformation Editor (Connection Manager Tab)</span></span>
  <span data-ttu-id="56f57-103">使用 **“模糊分组转换编辑器”** 对话框的 **“连接管理器”** 选项卡可以选择现有连接或创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="56f57-103">Use the **Connection Manager** tab of the **Fuzzy Grouping Transformation Editor** dialog box to select an existing connection or create a new one.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56f57-104">连接指定的服务器必须正在运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56f57-104">The server specified by the connection must be running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="56f57-105">模糊分组转换会在 tempdb 中创建临时数据对象，这些对象的大小可能与为此转换输入的所有内容完全一致。</span><span class="sxs-lookup"><span data-stu-id="56f57-105">The Fuzzy Grouping transformation creates temporary data objects in tempdb that may be as large as the full input to the transformation.</span></span> <span data-ttu-id="56f57-106">在执行转换时，该转换将对这些临时对象发出服务器查询。</span><span class="sxs-lookup"><span data-stu-id="56f57-106">While the transformation executes, it issues server queries against these temporary objects.</span></span> <span data-ttu-id="56f57-107">这会影响服务器的总体性能。</span><span class="sxs-lookup"><span data-stu-id="56f57-107">This can affect overall server performance.</span></span>  
  
 <span data-ttu-id="56f57-108">若要了解有关模糊分组转换的详细信息，请参阅 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="56f57-108">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="56f57-109">选项</span><span class="sxs-lookup"><span data-stu-id="56f57-109">Options</span></span>  
 <span data-ttu-id="56f57-110">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="56f57-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="56f57-111">使用列表框选择现有的 OLE DB 连接管理器，或使用“新建”按钮创建新的连接。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="56f57-111">Select an existing OLE DB connection manager by using the list box, or create a new connection by using the **New** button.</span></span>  
  
 <span data-ttu-id="56f57-112">**新建**</span><span class="sxs-lookup"><span data-stu-id="56f57-112">**New**</span></span>  
 <span data-ttu-id="56f57-113">通过使用“配置 OLE DB 连接管理器”  对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="56f57-113">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f57-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56f57-114">See Also</span></span>  
 <span data-ttu-id="56f57-115">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="56f57-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="56f57-116">使用模糊分组转换标识相似数据行</span><span class="sxs-lookup"><span data-stu-id="56f57-116">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
