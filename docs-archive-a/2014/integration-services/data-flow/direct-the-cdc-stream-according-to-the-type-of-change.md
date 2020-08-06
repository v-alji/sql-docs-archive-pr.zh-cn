---
title: 根据更改的类型定向 CDC 流 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a9b4e0c6a196669e4cedafcecf0477b228f3001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579685"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="b0ceb-102">根据更改的类型定向 CDC 流</span><span class="sxs-lookup"><span data-stu-id="b0ceb-102">Direct the CDC Stream According to the Type of Change</span></span>
  <span data-ttu-id="b0ceb-103">若要添加并配置 CDC 拆分器转换，包必须包含至少一个数据流任务和一个 CDC 源。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-103">To add and configure a CDC splitter Transformation, the package must contain at least one Data Flow task and a CDC source.</span></span>  
  
 <span data-ttu-id="b0ceb-104">添加到包的 CDC 源必须选择了 NetCDC 处理模式。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-104">The CDC source added to the package must have a NetCDC processing mode selected.</span></span> <span data-ttu-id="b0ceb-105">有关选择处理模式的详细信息，请参阅 [CDC 源编辑器（“连接管理器”页）](../cdc-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-105">For more information on selecting processing modes, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="b0ceb-106">根据更改的类型定向 CDC 流</span><span class="sxs-lookup"><span data-stu-id="b0ceb-106">To direct the CDC stream according to the type of change</span></span>  
  
1.  <span data-ttu-id="b0ceb-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，打开包含所需包的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b0ceb-108">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b0ceb-109">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 把 CDC 拆分器拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC splitter to the design surface.</span></span>  
  
4.  <span data-ttu-id="b0ceb-110">将在包中包含的 CDC 源连接到 CDC 拆分器。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-110">Connect the CDC source that is included in the package to the CDC Splitter.</span></span>  
  
5.  <span data-ttu-id="b0ceb-111">将 CDC 拆分器连接到一个或多个目标。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-111">Connect the CDC splitter to one or more destinations.</span></span> <span data-ttu-id="b0ceb-112">您可以连接最多三个不同的输出。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-112">You can connect up to three different outputs.</span></span>  
  
6.  <span data-ttu-id="b0ceb-113">选择以下输出之一：</span><span class="sxs-lookup"><span data-stu-id="b0ceb-113">Select one of the following outputs:</span></span>  
  
    -   <span data-ttu-id="b0ceb-114">删除输出：定向 DELETE 更改行的输出。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-114">Delete output: The output where DELETE change rows are directed.</span></span>  
  
    -   <span data-ttu-id="b0ceb-115">插入输出：定向 INSERT 更改行的输出。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-115">Insert output: The output where INSERT change rows are directed.</span></span>  
  
    -   <span data-ttu-id="b0ceb-116">更新输出：之前/之后 UPDATE 更改行和 Merge 更改行定向的输出。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-116">Update output: The output where before/after UPDATE change rows and Merge change rows are directed.</span></span>  
  
7.  <span data-ttu-id="b0ceb-117">或者，您可以使用 **“高级编辑器”** 对话框配置高级属性。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-117">Optionally, you can configure the advanced properties using the **Advanced Editor** dialog box.</span></span>  
  
     <span data-ttu-id="b0ceb-118">**“高级编辑器”** 对话框包含可通过编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-118">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
     <span data-ttu-id="b0ceb-119">打开 **“高级编辑器”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="b0ceb-119">To open the **Advanced Editor** dialog box:</span></span>  
  
    -   <span data-ttu-id="b0ceb-120">在您的 **项目的** “数据流” [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 屏幕上，右键单击 CDC 拆分器，然后选择 **“显示高级编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-120">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
     <span data-ttu-id="b0ceb-121">有关使用 CDC 拆分器的详细信息，请参阅 Microsoft SQL Server Integration Services 的 CDC 组件。</span><span class="sxs-lookup"><span data-stu-id="b0ceb-121">For more information about using the CDC splitter see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ceb-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0ceb-122">See Also</span></span>  
 [<span data-ttu-id="b0ceb-123">CDC 拆分器</span><span class="sxs-lookup"><span data-stu-id="b0ceb-123">CDC Splitter</span></span>](cdc-splitter.md)  
  
  
