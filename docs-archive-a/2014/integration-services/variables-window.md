---
title: “变量”窗口 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variables.f1
helpviewer_keywords:
- Variables Window dialog box
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffd6da67386291c14ebf588da9a1cf8f399214b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588596"
---
# <a name="variables-window"></a><span data-ttu-id="e5ed0-102">“变量”窗口</span><span class="sxs-lookup"><span data-stu-id="e5ed0-102">Variables Window</span></span>
  <span data-ttu-id="e5ed0-103">可以使用“变量”窗口创建和修改用户定义变量，以及查看系统变量。 </span><span class="sxs-lookup"><span data-stu-id="e5ed0-103">Use the **Variables** window to create and modify user-defined variables and view system variables.</span></span>  
  
 <span data-ttu-id="e5ed0-104">默认情况下， **“变量”** 窗口位于 **中 SSIS 设计器的** “连接管理器” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]区域之下。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-104">By default, the **Variables** window is located below the **Connection Managers** area in the SSIS Designer, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e5ed0-105">如果看不到“变量”窗口，请单击 SSIS 菜单上的“变量”以显示该窗口    。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-105">If you don't see the **Variables** window, click **Variables** on the **SSIS** menu to display the window.</span></span>  
  
 <span data-ttu-id="e5ed0-106">您可以通过将 View.Variables 命令映射到在 **“选项”** 对话框的 **“键盘”** 页上选择的组合键来显示 **“变量”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-106">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5ed0-107">`Name` 和 `Namespace` 属性的值必须以 Unicode 标准 2.0 定义的字母字符或下划线 (_) 开头。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-107">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="e5ed0-108">后续字符可以是在 Unicode 标准 2.0 中定义的字母或数字，或是下划线 (\_)。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-108">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e5ed0-109">选项</span><span class="sxs-lookup"><span data-stu-id="e5ed0-109">Options</span></span>  
 <span data-ttu-id="e5ed0-110">**添加变量**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-110">**Add Variable**</span></span>  
 <span data-ttu-id="e5ed0-111">添加用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-111">Add a user-defined variable.</span></span>  
  
 <span data-ttu-id="e5ed0-112">**移动变量**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-112">**Move Variable**</span></span>  
 <span data-ttu-id="e5ed0-113">单击列表中的变量，然后单击“移动变量”更改变量作用域。 </span><span class="sxs-lookup"><span data-stu-id="e5ed0-113">Click a variable in the list, and then click **Move Variable** to change the variable scope.</span></span> <span data-ttu-id="e5ed0-114">在 **“选择新作用域”** 对话框中，选择包或包中的容器、任务或事件处理程序，以更改变量作用域。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-114">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
 <span data-ttu-id="e5ed0-115">有关变量作用域的详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)区域之下。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-115">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="e5ed0-116">**删除变量**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-116">**Delete Variable**</span></span>  
 <span data-ttu-id="e5ed0-117">从列表中选择变量，然后单击“删除变量”。 </span><span class="sxs-lookup"><span data-stu-id="e5ed0-117">Select a variable from the list, and then click **Delete Variable**.</span></span>  
  
 <span data-ttu-id="e5ed0-118">**网格选项**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-118">**Grid Options**</span></span>  
 <span data-ttu-id="e5ed0-119">单击此项可打开“变量网格选项”对话框，从中可以更改列选择并对“变量”窗口应用筛选器。  </span><span class="sxs-lookup"><span data-stu-id="e5ed0-119">Click to open the **Variable Grid Options** dialog box where you can change the column selection and apply filters to the **Variables** window.</span></span> <span data-ttu-id="e5ed0-120">有关详细信息，请参阅 [变量网格选项](../../2014/integration-services/variable-grid-options.md)。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-120">For more information, see [Variable Grid Options](../../2014/integration-services/variable-grid-options.md).</span></span>  
  
 `Name`  
 <span data-ttu-id="e5ed0-121">查看变量名称。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-121">View the variable name.</span></span> <span data-ttu-id="e5ed0-122">您可以更新用户定义变量的名称。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-122">You can update the name for user-defined variables.</span></span>  
  
 <span data-ttu-id="e5ed0-123">**范围**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-123">**Scope**</span></span>  
 <span data-ttu-id="e5ed0-124">查看变量的作用域。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-124">View the scope of the variable.</span></span> <span data-ttu-id="e5ed0-125">变量的作用域可以是整个程序包，也可以是容器或任务。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-125">A variable has either the scope of the entire package, or the scope of a container or task.</span></span> <span data-ttu-id="e5ed0-126">变量的作用域必须足够大，以便变量对任何需要读取或设置其值的其他任务或组件都是可见的。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-126">The scope of the variable must be sufficient so that the variable is visible to any other tasks or components that need to read or set its value.</span></span>  
  
 <span data-ttu-id="e5ed0-127">您可以更改作用域，方法是单击该变量，然后单击 **“变量”** 窗口中的 **“移动变量”** 。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-127">You can change the scope by clicking the variable and then clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="e5ed0-128">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-128">**Data Type**</span></span>  
 <span data-ttu-id="e5ed0-129">查看变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-129">View the data type of the variable.</span></span> <span data-ttu-id="e5ed0-130">对于用户定义变量，你可以从列表中选择数据类型。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-130">You can select a data type from the list for user-defined variables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5ed0-131">如果为变量指定表达式，则无法更改数据类型。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-131">If you assign an expression to the variable, you cannot change the data type.</span></span>  
  
 <span data-ttu-id="e5ed0-132">**值**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-132">**Value**</span></span>  
 <span data-ttu-id="e5ed0-133">查看变量值。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-133">View the variable value.</span></span> <span data-ttu-id="e5ed0-134">您可以更新用户定义变量的值。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-134">You can update the value for user-defined variables.</span></span> <span data-ttu-id="e5ed0-135">此值可以是文字或表达式，还可以是多线串。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-135">This value can be a literal or an expression, and the value can be a multi-line string.</span></span> <span data-ttu-id="e5ed0-136">若要为变量指定表达式，请单击 **“变量”** 窗口中的 **“表达式”** 列旁边的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-136">To assign an expression to the variable, click the ellipse button that is next to the **Expression** column in the **Variables** window.</span></span>  
  
 `Namespace`  
 <span data-ttu-id="e5ed0-137">查看命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-137">View the namespace name.</span></span> <span data-ttu-id="e5ed0-138">用户定义变量最初在**user**命名空间中创建，但您可以在字段中更改命名空间名称 `Namespace` 。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-138">User-defined variables are initially created in the **User** namespace, but you can change the namespace name in the `Namespace` field.</span></span> <span data-ttu-id="e5ed0-139">若要显示此列，请单击 **“网格选项”**。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-139">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="e5ed0-140">**引发更改事件**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-140">**Raise Change Event**</span></span>  
 <span data-ttu-id="e5ed0-141">指示在值发生更改时是否引发 `OnVariableValueChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-141">Indicate whether to raise the `OnVariableValueChanged` event when a value changes.</span></span> <span data-ttu-id="e5ed0-142">您可以更新用户定义变量和系统变量的值。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-142">You can update the value for user-defined and system variables.</span></span> <span data-ttu-id="e5ed0-143">默认情况下， **“变量”** 窗口不列出此列。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-143">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="e5ed0-144">若要显示此列，请单击 **“网格选项”**。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-144">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="e5ed0-145">**描述**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-145">**Description**</span></span>  
 <span data-ttu-id="e5ed0-146">查看变量说明。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-146">View the variable description.</span></span> <span data-ttu-id="e5ed0-147">您可以更改用户定义变量的说明。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-147">You can change the description for user-defined variables.</span></span> <span data-ttu-id="e5ed0-148">默认情况下， **“变量”** 窗口不列出此列。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-148">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="e5ed0-149">若要显示此列，请单击 **“网格选项”**。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-149">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="e5ed0-150">**表达式**</span><span class="sxs-lookup"><span data-stu-id="e5ed0-150">**Expression**</span></span>  
 <span data-ttu-id="e5ed0-151">查看为变量指定的表达式。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-151">View the expression assigned to the variable.</span></span> <span data-ttu-id="e5ed0-152">若要指定表达式，请单击省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-152">To assign an expression, click the ellipse button.</span></span>  
  
 <span data-ttu-id="e5ed0-153">如果为变量指定了表达式，该变量旁边将显示特殊的图标标记。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-153">If you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="e5ed0-154">这个特殊的图标标记还显示在设置有表达式的连接管理器和任务旁边。</span><span class="sxs-lookup"><span data-stu-id="e5ed0-154">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ed0-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5ed0-155">See Also</span></span>  
 <span data-ttu-id="e5ed0-156">[Integration Services (SSIS) 变量](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e5ed0-156">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="e5ed0-157">[使用包中的变量](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e5ed0-157">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="e5ed0-158">[Integration Services &#40;SSIS&#41; 表达式](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="e5ed0-158">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="e5ed0-159">生成包执行的转储文件</span><span class="sxs-lookup"><span data-stu-id="e5ed0-159">Generating Dump Files for Package Execution</span></span>](troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
