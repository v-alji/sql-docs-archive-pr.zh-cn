---
title: 用路径连接组件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e11955601406406abe48b53197e95c8224762fee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692486"
---
# <a name="connect-components-with-paths"></a><span data-ttu-id="c5820-102">使用路径连接组件</span><span class="sxs-lookup"><span data-stu-id="c5820-102">Connect Components with Paths</span></span>
  <span data-ttu-id="c5820-103">在 **设计器中** “数据流” [!INCLUDE[ssIS](../includes/ssis-md.md)] 选项卡的设计图面上构造包中的数据流。</span><span class="sxs-lookup"><span data-stu-id="c5820-103">You construct the data flow in a package on the design surface of the **Data Flow** tab in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="c5820-104">如果数据流包含两个数据流组件，则可以将源或转换的输出连接到转换或目标的输入，以连接这两个组件。</span><span class="sxs-lookup"><span data-stu-id="c5820-104">If a data flow contains two data flow components, you can connect them by connecting the output of a source or transformation to the input of a transformation or destination.</span></span> <span data-ttu-id="c5820-105">两个数据流组件之间的连接器称为路径。</span><span class="sxs-lookup"><span data-stu-id="c5820-105">The connector between two data flow components is called a path.</span></span>

 <span data-ttu-id="c5820-106">下面的关系图显示一个简单的数据流，它具有一个源组件、两个转换、一个目标组件以及连接它们的路径。</span><span class="sxs-lookup"><span data-stu-id="c5820-106">The following diagram shows a simple data flow with a source component, two transformations, a destination component, and the paths that connect them.</span></span>

 <span data-ttu-id="c5820-107">![数据流](media/mw-dts-08.gif "数据流")</span><span class="sxs-lookup"><span data-stu-id="c5820-107">![Data flow](media/mw-dts-08.gif "Data flow")</span></span>

 <span data-ttu-id="c5820-108">连接两个组件后，即可在 **“数据流路径编辑器”** 中查看通过路径移动的数据的元数据以及路径的属性。</span><span class="sxs-lookup"><span data-stu-id="c5820-108">After two components are connected, you can view the metadata of the data that moves through the path and the properties of the path in **Data Flow Path Editor**.</span></span> <span data-ttu-id="c5820-109">有关详细信息，请参阅 [Integration Services Paths](data-flow/integration-services-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="c5820-109">For more information, see [Integration Services Paths](data-flow/integration-services-paths.md).</span></span>

 <span data-ttu-id="c5820-110">还可以将数据查看器添加到路径。</span><span class="sxs-lookup"><span data-stu-id="c5820-110">You can also add data viewers to paths.</span></span> <span data-ttu-id="c5820-111">数据查看器使您可以在包运行时查看在数据流组件间移动的数据。</span><span class="sxs-lookup"><span data-stu-id="c5820-111">A data viewer makes it possible to view data moving between data flow components when the package is run.</span></span>

### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="c5820-112">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="c5820-112">To connect components in a data flow</span></span>

-   [<span data-ttu-id="c5820-113">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="c5820-113">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a><span data-ttu-id="c5820-114">设置路径属性</span><span class="sxs-lookup"><span data-stu-id="c5820-114">To set path properties</span></span>

-   [<span data-ttu-id="c5820-115">使用数据流路径编辑器设置路径属性</span><span class="sxs-lookup"><span data-stu-id="c5820-115">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="c5820-116">查看路径元数据</span><span class="sxs-lookup"><span data-stu-id="c5820-116">To view path metadata</span></span>

-   [<span data-ttu-id="c5820-117">在数据流路径编辑器中查看路径元数据</span><span class="sxs-lookup"><span data-stu-id="c5820-117">View Path Metadata in the Data Flow Path Editor</span></span>](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="c5820-118">查看路径元数据</span><span class="sxs-lookup"><span data-stu-id="c5820-118">To view path metadata</span></span>

-   [<span data-ttu-id="c5820-119">将数据查看器添加到数据流</span><span class="sxs-lookup"><span data-stu-id="c5820-119">Add a Data Viewer to a Data Flow</span></span>](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a><span data-ttu-id="c5820-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5820-120">See Also</span></span>
 <span data-ttu-id="c5820-121">数据流[任务](control-flow/data-flow-task.md)数据流转换数据[时转换数据](data-flow/data-flow.md)中[的](data-flow/transformations/transform-data-with-transformations.md)[错误处理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="c5820-121">[Data Flow Task](control-flow/data-flow-task.md) [Data Flow](data-flow/data-flow.md) [Transform Data with Transformations](data-flow/transformations/transform-data-with-transformations.md) [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>


