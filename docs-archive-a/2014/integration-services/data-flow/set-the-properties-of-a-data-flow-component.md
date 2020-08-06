---
title: 设置数据流组件的属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], properties
ms.assetid: 73000ef6-52a2-4dec-8320-0e79acf0c2c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1fd045ba076eed2d65d801015b881a477976f5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589815"
---
# <a name="set-the-properties-of-a-data-flow-component"></a><span data-ttu-id="32603-102">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="32603-102">Set the Properties of a Data Flow Component</span></span>
  <span data-ttu-id="32603-103">若要设置数据流组件（包括源、目标和转换）的属性，请使用下列功能之一：</span><span class="sxs-lookup"><span data-stu-id="32603-103">To set the properties of data flow components, which include sources, destinations, and transformations, use one of the following features:</span></span>  
  
-   <span data-ttu-id="32603-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的组件编辑器。</span><span class="sxs-lookup"><span data-stu-id="32603-104">The component editors that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="32603-105">这些编辑器仅包含每个数据流组件的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="32603-105">These editors include only the custom properties of each data flow component.</span></span>  
  
-   <span data-ttu-id="32603-106">“属性”  窗口列出每个元素的组件级自定义属性以及所有数据流元素通用的属性。</span><span class="sxs-lookup"><span data-stu-id="32603-106">The **Properties** window lists the component-level custom properties of each element, as well as the properties common to all data flow elements.</span></span>  
  
-   <span data-ttu-id="32603-107">通过 **“高级编辑器”** 对话框可以访问每个组件的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="32603-107">The **Advanced Editor** dialog box provides access to custom properties for each component.</span></span> <span data-ttu-id="32603-108">通过“高级编辑器”对话框，还可以访问所有数据流组件通用的属性，包括输入属性、输出属性、错误输出属性、列属性和外部列属性  。</span><span class="sxs-lookup"><span data-stu-id="32603-108">The **Advanced Editor** dialog box also provides access to the properties common to all data flow components-the properties of inputs, outputs, error outputs, columns, and external columns.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-a-component-editor"></a><span data-ttu-id="32603-109">使用组件编辑器设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="32603-109">To set the properties of a data flow component by using a component editor</span></span>  
  
1.  <span data-ttu-id="32603-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="32603-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="32603-111">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="32603-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="32603-112">单击“控制流”  选项卡，然后双击数据流任务，此任务包含带有要查看和修改属性的组件的数据流。</span><span class="sxs-lookup"><span data-stu-id="32603-112">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow with the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="32603-113">双击数据流组件。</span><span class="sxs-lookup"><span data-stu-id="32603-113">Double-click the data flow component.</span></span>  
  
5.  <span data-ttu-id="32603-114">在组件编辑器中查看或修改属性值，然后关闭编辑器。</span><span class="sxs-lookup"><span data-stu-id="32603-114">In the component editor, view or modify the property values, and then close the editor.</span></span>  
  
6.  <span data-ttu-id="32603-115">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="32603-115">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-properties-window"></a><span data-ttu-id="32603-116">使用“属性”窗口设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="32603-116">To set the properties of a data flow component by using the Properties window</span></span>  
  
1.  <span data-ttu-id="32603-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="32603-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="32603-118">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="32603-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="32603-119">单击“控制流”  选项卡，然后双击包含要查看和修改其属性的组件的数据流任务。</span><span class="sxs-lookup"><span data-stu-id="32603-119">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="32603-120">双击数据流组件，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="32603-120">Right-click the data flow component, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="32603-121">查看或修改属性值，然后关闭 **“属性”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="32603-121">View or modify the property values, and then close the **Properties** window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32603-122">许多属性为只读，因此不能修改。</span><span class="sxs-lookup"><span data-stu-id="32603-122">Many properties are read-only, and cannot be modified.</span></span>  
  
6.  <span data-ttu-id="32603-123">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="32603-123">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-advanced-editor"></a><span data-ttu-id="32603-124">使用高级编辑器设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="32603-124">To set the properties of a data flow component by using the Advanced Editor</span></span>  
  
1.  <span data-ttu-id="32603-125">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="32603-125">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="32603-126">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="32603-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="32603-127">单击“控制流”  选项卡，然后双击包含要查看或修改的组件的数据流任务。</span><span class="sxs-lookup"><span data-stu-id="32603-127">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component you want to view or modify.</span></span>  
  
4.  <span data-ttu-id="32603-128">在数据流设计器中，右键单击数据流组件，然后单击“显示高级编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="32603-128">In the data flow designer, right-click the data flow component, and then click **Show Advanced Editor**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32603-129">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，支持多个输入的数据流组件不能使用“高级编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="32603-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data flow components that support multiple inputs cannot use the **Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="32603-130">在 **“高级编辑器”** 对话框中，执行下列任意步骤：</span><span class="sxs-lookup"><span data-stu-id="32603-130">In the **Advanced Editor** dialog box, do any of the following steps:</span></span>  
  
    -   <span data-ttu-id="32603-131">若要查看和指定组件使用的连接，请单击 **“连接管理器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="32603-131">To view and specify the connection that the component uses, click the **Connection Managers** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="32603-132">“连接管理器”  选项卡仅对使用连接管理器连接到数据源（如文件和数据库）的数据流组件可用</span><span class="sxs-lookup"><span data-stu-id="32603-132">The **Connection Managers** tab is available only to data flow components that use connection managers to connect to data sources such as files and databases</span></span>  
  
    -   <span data-ttu-id="32603-133">若要查看和修改组件级属性，请单击“组件属性”选项卡  。</span><span class="sxs-lookup"><span data-stu-id="32603-133">To view and modify component-level properties, click the **Component Properties** tab.</span></span>  
  
    -   <span data-ttu-id="32603-134">若要查看和修改外部列和可用输出之间的映射，请单击 **“列映射”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="32603-134">To view and modify mappings between external columns and the available output, click the **Column Mappings** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="32603-135">“列映射”  选项卡仅在查看或编辑源或者目标时可用。</span><span class="sxs-lookup"><span data-stu-id="32603-135">The **Column Mappings** tab is available only when viewing or editing sources or destinations.</span></span>  
  
    -   <span data-ttu-id="32603-136">若要查看可用输入列的列表并更新输出列的名称，请单击 **“输入列”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="32603-136">To view a list of the available input columns and to update the names of output columns, click the **Input Columns** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="32603-137">输入列选项卡只在对转换或目标进行操作时可用。</span><span class="sxs-lookup"><span data-stu-id="32603-137">The Input Columns tab is available only when working with transformations or destinations.</span></span> <span data-ttu-id="32603-138">有关详细信息，请参阅 [Integration Services Transformations](transformations/integration-services-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="32603-138">For more information, see [Integration Services Transformations](transformations/integration-services-transformations.md).</span></span>  
  
    -   <span data-ttu-id="32603-139">若要查看和修改输入、输出和错误输出的属性以及它们包含的列的属性，请单击 **“输入属性和输出属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="32603-139">To view and modify the properties of inputs, outputs, and error outputs, and the properties of the columns they contain, click the **Input and Output Properties** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="32603-140">源没有输入。</span><span class="sxs-lookup"><span data-stu-id="32603-140">Sources have no inputs.</span></span> <span data-ttu-id="32603-141">除了一个可选错误输出之外，目标没有输出。</span><span class="sxs-lookup"><span data-stu-id="32603-141">Destinations have no outputs, except for an optional error output.</span></span>  
  
6.  <span data-ttu-id="32603-142">查看或修改属性值。</span><span class="sxs-lookup"><span data-stu-id="32603-142">View or modify the property values.</span></span>  
  
7.  <span data-ttu-id="32603-143">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="32603-143">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="32603-144">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="32603-144">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32603-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32603-145">See Also</span></span>  
 [<span data-ttu-id="32603-146">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="32603-146">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
