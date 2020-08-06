---
title: 使用数据流路径编辑器设置路径的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 512249a4-83a6-4087-980d-a4344da48371
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e01565ef6cb70f3ac52187a6cc8d22d05508db4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694031"
---
# <a name="set-the-properties-of-a-path-by-using-the-data-flow-path-editor"></a><span data-ttu-id="62306-102">使用数据流路径编辑器设置路径属性</span><span class="sxs-lookup"><span data-stu-id="62306-102">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>
  <span data-ttu-id="62306-103">路径连接两个数据流组件。</span><span class="sxs-lookup"><span data-stu-id="62306-103">Paths connect two data flow components.</span></span> <span data-ttu-id="62306-104">数据流必须包含至少两个已连接的数据流组件，才能设置路径属性。</span><span class="sxs-lookup"><span data-stu-id="62306-104">Before you can set path properties, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="62306-105">有关详细信息，请参阅 [在数据流中添加或删除组件](data-flow/add-or-delete-a-component-in-a-data-flow.md) 和 [连接数据流中的组件](data-flow/connect-components-in-a-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="62306-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-set-path-properties"></a><span data-ttu-id="62306-106">设置路径属性</span><span class="sxs-lookup"><span data-stu-id="62306-106">To set path properties</span></span>  
  
1.  <span data-ttu-id="62306-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="62306-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="62306-108">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="62306-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="62306-109">单击“数据流”\*\*\*\* 选项卡，然后双击路径。</span><span class="sxs-lookup"><span data-stu-id="62306-109">Click the **Data Flow** tab, and then double-click a path.</span></span>  
  
4.  <span data-ttu-id="62306-110">在 **“数据流路径编辑器”** 中，单击 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="62306-110">In **Data Flow Path Editor**, click **General**.</span></span> <span data-ttu-id="62306-111">然后，可以编辑默认的路径名称并提供路径说明。</span><span class="sxs-lookup"><span data-stu-id="62306-111">You can then edit the default name of the path and provide a description of the path.</span></span> <span data-ttu-id="62306-112">还可以修改 PathAnnotation 属性。</span><span class="sxs-lookup"><span data-stu-id="62306-112">You can also modify the PathAnnotation property.</span></span>  
  
5.  <span data-ttu-id="62306-113">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="62306-113">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="62306-114">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="62306-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62306-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62306-115">See Also</span></span>  
 <span data-ttu-id="62306-116">[Integration Services 路径](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="62306-116">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="62306-117">数据流</span><span class="sxs-lookup"><span data-stu-id="62306-117">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
