---
title: 在数据流组件中配置错误输出 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- errors [Integration Services], data flow components
- components [Integration Services], data flow
- error outputs [Integration Services]
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebd44383e27daa465576bb056a67f6dacad87b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693436"
---
# <a name="configure-an-error-output-in-a-data-flow-component"></a><span data-ttu-id="110f3-102">在数据流组件中配置错误输出</span><span class="sxs-lookup"><span data-stu-id="110f3-102">Configure an Error Output in a Data Flow Component</span></span>
  <span data-ttu-id="110f3-103">很多数据流组件支持错误输出，根据组件的不同， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器提供几种不同的错误输出配置方法。</span><span class="sxs-lookup"><span data-stu-id="110f3-103">Many data flow components support error outputs, and depending on the component, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides different ways to configure an error output.</span></span> <span data-ttu-id="110f3-104">除了配置错误输出外，您还可以配置错误输出的列。</span><span class="sxs-lookup"><span data-stu-id="110f3-104">In addition to configuring an error output, you can also configure the columns of an error output.</span></span> <span data-ttu-id="110f3-105">其中包括配置由该组件添加的 **ErrorCode** 和 **ErrorColumn** 列。</span><span class="sxs-lookup"><span data-stu-id="110f3-105">This includes configuring the **ErrorCode** and **ErrorColumn** columns that are added by the component.</span></span>  
  
## <a name="configuring-an-error-output"></a><span data-ttu-id="110f3-106">配置错误输出</span><span class="sxs-lookup"><span data-stu-id="110f3-106">Configuring an Error Output</span></span>  
 <span data-ttu-id="110f3-107">若要配置错误输出，您有两种选择：</span><span class="sxs-lookup"><span data-stu-id="110f3-107">To configure an error output, you have two options:</span></span>  
  
-   <span data-ttu-id="110f3-108">使用 **“配置错误输出”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="110f3-108">Use the **Configure Error Output** dialog box.</span></span> <span data-ttu-id="110f3-109">可以使用此对话框，在支持错误输出的任意数据流组件中配置错误输出。</span><span class="sxs-lookup"><span data-stu-id="110f3-109">You can use this dialog box to configure an error output on any data flow component that supports an error output.</span></span>  
  
-   <span data-ttu-id="110f3-110">使用组件的编辑器对话框。</span><span class="sxs-lookup"><span data-stu-id="110f3-110">Use the editor dialog box for the component.</span></span> <span data-ttu-id="110f3-111">某些组件允许您直接从其编辑器对话框配置错误输出。</span><span class="sxs-lookup"><span data-stu-id="110f3-111">Some components let you configure error outputs directly from their editor dialog box.</span></span> <span data-ttu-id="110f3-112">但是，您不能从以下组件的编辑器对话框配置错误输出：ADO NET 源、导入列转换、OLE DB 命令转换或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 目标。</span><span class="sxs-lookup"><span data-stu-id="110f3-112">However, you cannot configure error outputs from the editor dialog box for the ADO NET source, the Import Column transformation, the OLE DB Command transformation, or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact destination.</span></span>  
  
 <span data-ttu-id="110f3-113">下面的过程介绍如何使用这些对话框来配置错误输出。</span><span class="sxs-lookup"><span data-stu-id="110f3-113">The following procedures describe how to use these dialog boxes to configure error outputs.</span></span>  
  
#### <a name="to-configure-an-error-output-using-the-configure-error-output-dialog-box"></a><span data-ttu-id="110f3-114">使用“配置错误输出”对话框配置错误输出</span><span class="sxs-lookup"><span data-stu-id="110f3-114">To configure an error output using the Configure Error Output dialog box</span></span>  
  
1.  <span data-ttu-id="110f3-115">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="110f3-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="110f3-116">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="110f3-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="110f3-117">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“数据流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="110f3-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="110f3-118">将红色箭头表示的错误输出从错误源组件拖到数据流中的另一个组件。</span><span class="sxs-lookup"><span data-stu-id="110f3-118">Drag the error output, represented by the red arrow, from the component that is the source of the errors to another component in the data flow.</span></span>  
  
5.  <span data-ttu-id="110f3-119">在 **“配置错误输出”** 对话框中，为组件输入中的每列在 **“错误”** 列和 **“截断”** 列中选择一个操作。</span><span class="sxs-lookup"><span data-stu-id="110f3-119">In the **Configure Error Output** dialog box, select an action in the **Error** and **Truncation** columns for each column in the component input.</span></span>  
  
6.  <span data-ttu-id="110f3-120">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="110f3-120">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
#### <a name="to-add-an-error-output-using-the-editor-dialog-box-for-the-component"></a><span data-ttu-id="110f3-121">使用组件的编辑器对话框添加错误输出</span><span class="sxs-lookup"><span data-stu-id="110f3-121">To add an error output using the editor dialog box for the component</span></span>  
  
1.  <span data-ttu-id="110f3-122">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="110f3-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="110f3-123">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="110f3-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="110f3-124">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“数据流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="110f3-124">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="110f3-125">双击要在其中配置错误输出的数据流组件，然后根据不同组件，执行下列步骤之一：</span><span class="sxs-lookup"><span data-stu-id="110f3-125">Double-click the data flow components in which you want to configure an error output and, depending on the component, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="110f3-126">单击 **“配置错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="110f3-126">Click **Configure Error Output**.</span></span>  
  
    -   <span data-ttu-id="110f3-127">单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="110f3-127">Click **Error Output**.</span></span>  
  
5.  <span data-ttu-id="110f3-128">为每列设置 **“错误”** 选项。</span><span class="sxs-lookup"><span data-stu-id="110f3-128">Set the **Error** option for each column.</span></span>  
  
6.  <span data-ttu-id="110f3-129">为每列设置 **“截断”** 选项。</span><span class="sxs-lookup"><span data-stu-id="110f3-129">Set the **Truncation** option for each column.</span></span>  
  
7.  <span data-ttu-id="110f3-130">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="110f3-130">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="110f3-131">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="110f3-131">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="configuring-error-output-columns"></a><span data-ttu-id="110f3-132">配置错误输出列</span><span class="sxs-lookup"><span data-stu-id="110f3-132">Configuring Error Output Columns</span></span>  
 <span data-ttu-id="110f3-133">若要配置错误输出列，必须使用 **“高级编辑器”** 对话框中的 **“输入属性和输出属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="110f3-133">To configure the error output columns, you have to use the **Input and Output Properties** tab of the **Advanced Editor** dialog box.</span></span>  
  
#### <a name="to-configure-error-output-columns"></a><span data-ttu-id="110f3-134">配置错误输出列</span><span class="sxs-lookup"><span data-stu-id="110f3-134">To configure error output columns</span></span>  
  
1.  <span data-ttu-id="110f3-135">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="110f3-135">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="110f3-136">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="110f3-136">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="110f3-137">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“数据流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="110f3-137">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="110f3-138">右键单击要配置其错误输出列的组件，再单击“显示高级编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="110f3-138">Right-click the component whose error output columns you want to configure and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="110f3-139">单击“输入和输出属性”选项卡并展开“\<component name> 错误输出”，然后展开“输出列”  。</span><span class="sxs-lookup"><span data-stu-id="110f3-139">Click the **Input and Output Properties** tab and expand **\<component name> Error Output** and then expand **Output Columns**.</span></span>  
  
6.  <span data-ttu-id="110f3-140">单击某列，然后更新其属性。</span><span class="sxs-lookup"><span data-stu-id="110f3-140">Click a column and update its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="110f3-141">列的列表中包括组件输入中的列、由以前的错误输出添加的 **ErrorCode** 和 **ErrorColumn** 列，以及由此组件添加的 **ErrorCode** 和 **ErrorColumn** 列。</span><span class="sxs-lookup"><span data-stu-id="110f3-141">The list of columns includes the columns in the component input, the **ErrorCode** and **ErrorColumn** columns added by previous error outputs, and the **ErrorCode** and **ErrorColumn** columns added by this component.</span></span>  
  
7.  <span data-ttu-id="110f3-142">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="110f3-142">Click **OK.**</span></span>  
  
8.  <span data-ttu-id="110f3-143">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="110f3-143">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110f3-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="110f3-144">See Also</span></span>  
 [<span data-ttu-id="110f3-145">数据中的错误处理</span><span class="sxs-lookup"><span data-stu-id="110f3-145">Error Handling in Data</span></span>](data-flow/error-handling-in-data.md)  
  
  
