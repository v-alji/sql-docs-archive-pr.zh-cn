---
title: 在数据流中添加或删除组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f041258d2b66e7b8da540a842848ebf70f4ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688076"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a><span data-ttu-id="e800a-102">在数据流中添加或删除组件</span><span class="sxs-lookup"><span data-stu-id="e800a-102">Add or Delete a Component in a Data Flow</span></span>
  <span data-ttu-id="e800a-103">数据流组件是数据流中的源、目标和转换。</span><span class="sxs-lookup"><span data-stu-id="e800a-103">Data flow components are sources, destinations, and transformations in a data flow.</span></span> <span data-ttu-id="e800a-104">包中的控制流必须包含数据流任务，然后才能向数据流添加组件。</span><span class="sxs-lookup"><span data-stu-id="e800a-104">Before you can add components to a data flow, the control flow in the package must include a Data Flow task.</span></span>  
  
 <span data-ttu-id="e800a-105">下面的过程介绍如何在包的数据流中添加或删除组件。</span><span class="sxs-lookup"><span data-stu-id="e800a-105">The following procedures describe how to add or delete a component in the data flow of a package.</span></span>  
  
### <a name="to-add-a-component-to-a-data-flow"></a><span data-ttu-id="e800a-106">向数据流添加组件</span><span class="sxs-lookup"><span data-stu-id="e800a-106">To add a component to a data flow</span></span>  
  
1.  <span data-ttu-id="e800a-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e800a-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e800a-108">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e800a-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e800a-109">单击“控制流”选项卡，然后双击包含要向其添加组件的数据流的数据流任务。 </span><span class="sxs-lookup"><span data-stu-id="e800a-109">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow to which you want to add a component.</span></span>  
  
4.  <span data-ttu-id="e800a-110">在工具箱中，展开 **“数据流源”** 、 **“数据流转换”** 或 **“数据流目标”** ，然后将数据流项拖动到 **“数据流”** 选项卡的设计图面。</span><span class="sxs-lookup"><span data-stu-id="e800a-110">In the Toolbox, expand **Data Flow Sources**, **Data Flow Transformations**, or **Data Flow Destinations**, and then drag a data flow item to the design surface of the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="e800a-111">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="e800a-111">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-component-from-a-data-flow"></a><span data-ttu-id="e800a-112">从数据流删除组件</span><span class="sxs-lookup"><span data-stu-id="e800a-112">To delete a component from a data flow</span></span>  
  
1.  <span data-ttu-id="e800a-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e800a-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e800a-114">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e800a-114">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e800a-115">单击“控制流”选项卡，然后双击包含要从中删除组件的数据流的数据流任务。 </span><span class="sxs-lookup"><span data-stu-id="e800a-115">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow from which you want to delete a component.</span></span>  
  
4.  <span data-ttu-id="e800a-116">右键单击数据流组件，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="e800a-116">Right-click the data flow component, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="e800a-117">确认删除操作。</span><span class="sxs-lookup"><span data-stu-id="e800a-117">Confirm the delete operation.</span></span>  
  
6.  <span data-ttu-id="e800a-118">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="e800a-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e800a-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e800a-119">See Also</span></span>  
 <span data-ttu-id="e800a-120">[连接数据流中的组件](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e800a-120">[Connect Components in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="e800a-121">[在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="e800a-121">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="e800a-122">数据流</span><span class="sxs-lookup"><span data-stu-id="e800a-122">Data Flow</span></span>](data-flow.md)  
  
  
