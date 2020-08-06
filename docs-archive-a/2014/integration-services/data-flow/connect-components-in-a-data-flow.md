---
title: 连接数据流中的组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc4a2fa81e9b110c27ea63b16d835d069bf12cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682997"
---
# <a name="connect-components-in-a-data-flow"></a><span data-ttu-id="691da-102">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="691da-102">Connect Components in a Data Flow</span></span>
  <span data-ttu-id="691da-103">本过程介绍如何将数据流中的组件输出连接到同一数据流中的其他组件。</span><span class="sxs-lookup"><span data-stu-id="691da-103">This procedure describes how to connect the output of components in a data flow to other components within the same data flow.</span></span>  
  
### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="691da-104">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="691da-104">To connect components in a data flow</span></span>  
  
1.  <span data-ttu-id="691da-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="691da-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="691da-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="691da-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="691da-107">单击“控制流”\*\*\*\* 选项卡，然后双击包含要连接的组件所在数据流的数据流任务。</span><span class="sxs-lookup"><span data-stu-id="691da-107">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow in which you want to connect components.</span></span>  
  
4.  <span data-ttu-id="691da-108">在 **“数据流”** 选项卡的设计图面上，选择要连接的转换或源。</span><span class="sxs-lookup"><span data-stu-id="691da-108">On the design surface of the **Data Flow** tab, select the transformation or source that you want to connect.</span></span>  
  
5.  <span data-ttu-id="691da-109">将转换或源的绿色输出箭头拖动到转换或目标。</span><span class="sxs-lookup"><span data-stu-id="691da-109">Drag the green output arrow of a transformation or a source to a transformation or to a destination.</span></span> <span data-ttu-id="691da-110">某些数据流组件有错误输出，这些输出可通过同样方式连接。</span><span class="sxs-lookup"><span data-stu-id="691da-110">Some data flow components have error outputs that you can connect in the same way.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="691da-111">某些数据流组件可能有多个输出，您可以将每一个输出连接到不同的转换或目标。</span><span class="sxs-lookup"><span data-stu-id="691da-111">Some data flow components can have multiple outputs and you can connect each output to a different transformation or destination.</span></span>  
  
6.  <span data-ttu-id="691da-112">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="691da-112">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691da-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="691da-113">See Also</span></span>  
 <span data-ttu-id="691da-114">[在数据流中添加或删除组件](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="691da-114">[Add or Delete a Component in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="691da-115">[在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="691da-115">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="691da-116">数据流</span><span class="sxs-lookup"><span data-stu-id="691da-116">Data Flow</span></span>](data-flow.md)  
  
  
