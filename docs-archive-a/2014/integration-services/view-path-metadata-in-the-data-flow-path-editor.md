---
title: 在数据流路径编辑器中查看路径元数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d84e14c2bc42ac4b831a4d1a3321d3e8b4acf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576876"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a><span data-ttu-id="62c56-102">在数据流路径编辑器中查看路径元数据</span><span class="sxs-lookup"><span data-stu-id="62c56-102">View Path Metadata in the Data Flow Path Editor</span></span>
  <span data-ttu-id="62c56-103">路径连接两个数据流组件。</span><span class="sxs-lookup"><span data-stu-id="62c56-103">Paths connect two data flow components.</span></span> <span data-ttu-id="62c56-104">若要查看路径元数据，数据流必须包含至少两个已连接的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="62c56-104">Before you can view path metadata, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="62c56-105">有关详细信息，请参阅 [在数据流中添加或删除组件](data-flow/add-or-delete-a-component-in-a-data-flow.md) 和 [连接数据流中的组件](data-flow/connect-components-in-a-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="62c56-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-view-path-metadata"></a><span data-ttu-id="62c56-106">查看路径元数据</span><span class="sxs-lookup"><span data-stu-id="62c56-106">To view path metadata</span></span>  
  
1.  <span data-ttu-id="62c56-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="62c56-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="62c56-108">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="62c56-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="62c56-109">单击“数据流”\*\*\*\* 选项卡，并双击路径。</span><span class="sxs-lookup"><span data-stu-id="62c56-109">Click the **Data Flow** tab and double-click a path.</span></span>  
  
4.  <span data-ttu-id="62c56-110">在 **“数据流路径编辑器”** 对话框中，单击 **“元数据”**。</span><span class="sxs-lookup"><span data-stu-id="62c56-110">In **Data Flow Path Editor** dialog box, click **Metadata**.</span></span>  
  
5.  <span data-ttu-id="62c56-111">查看路径元数据，包括列名称、数据类型、精度、小数位、长度、代码页和每列源组件的名称。</span><span class="sxs-lookup"><span data-stu-id="62c56-111">View path metadata, including the column names, data type, precision, scale, length, code page, and the name of the source component of each column.</span></span>  
  
6.  <span data-ttu-id="62c56-112">若要复制元数据，请单击 **“复制到剪贴板”**。</span><span class="sxs-lookup"><span data-stu-id="62c56-112">To copy the metadata, click **Copy to Clipboard**.</span></span>  
  
7.  <span data-ttu-id="62c56-113">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="62c56-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c56-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62c56-114">See Also</span></span>  
 <span data-ttu-id="62c56-115">[Integration Services 路径](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="62c56-115">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="62c56-116">数据流</span><span class="sxs-lookup"><span data-stu-id="62c56-116">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
