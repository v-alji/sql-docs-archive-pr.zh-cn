---
title: 设置用户定义变量的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf53be469e3d377f7efb379f78e85e31b26767b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694026"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a><span data-ttu-id="3bf2f-102">设置用户定义变量的属性</span><span class="sxs-lookup"><span data-stu-id="3bf2f-102">Set the Properties of a User-Defined Variable</span></span>
  <span data-ttu-id="3bf2f-103">若要在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中设置用户定义的变量的属性，可以使用下列功能之一：</span><span class="sxs-lookup"><span data-stu-id="3bf2f-103">To set the properties of a user-defined variable in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can use one of the following features:</span></span>  
  
-   <span data-ttu-id="3bf2f-104">“变量”窗口。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-104">Variables window.</span></span>  
  
-   <span data-ttu-id="3bf2f-105">属性窗口。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-105">Properties window.</span></span> <span data-ttu-id="3bf2f-106">“属性”\*\*\*\* 窗口中列出了用于配置“变量”\*\*\*\* 窗口中不可用变量的属性：Description、EvaluateAsExpression、Expression、ReadOnly、ValueType 和 IncludeInDebugDump。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-106">The **Properties** window lists properties for configuring variables that are not available in the **Variables** window: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType, and IncludeInDebugDump.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="3bf2f-107">还提供了一组无法更新属性的系统变量，但 RaiseChangedEvent 属性例外。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-107">also provides a set of system variables whose properties cannot be updated, with the exception of the RaiseChangedEvent property.</span></span>  
  
 <span data-ttu-id="3bf2f-108">**对变量设置表达式**</span><span class="sxs-lookup"><span data-stu-id="3bf2f-108">**Setting Expressions on Variables**</span></span>  
  
 <span data-ttu-id="3bf2f-109">使用\*\*\*\*“属性”窗口对用户定义变量设置表达式时：</span><span class="sxs-lookup"><span data-stu-id="3bf2f-109">When you use the **Properties** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="3bf2f-110">可通过 Value 属性或 Expression 属性来设置变量的值。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-110">The value of a variable can be set by the Value or the Expression property.</span></span> <span data-ttu-id="3bf2f-111">默认情况下，EvaluateAsExpression 属性设置为 `False` ，变量的值由 value 属性设置。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-111">By default, the EvaluateAsExpression property is set to `False` and the value of the variable is set by the Value property.</span></span> <span data-ttu-id="3bf2f-112">若要使用表达式来设置值，必须首先将 EvaluateAsExpression 设置为 `True` ，然后在 expression 属性中提供一个表达式。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-112">To use an expression to set the value, you must first set EvaluateAsExpression to `True`, and then provide an expression in the Expression property.</span></span> <span data-ttu-id="3bf2f-113">Value 属性自动设置为该表达式的计算结果。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-113">The Value property is automatically set to the evaluation result of the expression.</span></span>  
  
-   <span data-ttu-id="3bf2f-114">ValueType 属性包含 Value 属性中的值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-114">The ValueType property contains the data type of the value in the Value property.</span></span> <span data-ttu-id="3bf2f-115">通过表达式设置 Value 时，ValueType 将自动更新为与该表达式的计算结果兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-115">When Value is set by an expression, ValueType is automatically updated to a data type that is compatible with the evaluation result of the expression.</span></span> <span data-ttu-id="3bf2f-116">例如，如果 Value 包含0，ValueType 属性包含**Int32** ，然后将 Expression 设置为 GETDATE ( # A1，则 value 包含当前日期和时间，ValueType 设置为 `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-116">For example, if Value contains 0 and ValueType property contains **Int32** and you then set Expression to GETDATE(), Value contains the current date and time and ValueType is set to `DateTime`.</span></span>  
  
-   <span data-ttu-id="3bf2f-117">通过变量的 **“属性”** 窗口，可以访问 **“表达式生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-117">The **Properties** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="3bf2f-118">使用该工具可以生成、验证和计算表达式。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-118">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="3bf2f-119">有关详细信息，请参阅[表达式生成器](expressions/expression-builder.md)和 [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-119">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="3bf2f-120">使用\*\*\*\*“变量”窗口对用户定义变量设置表达式时：</span><span class="sxs-lookup"><span data-stu-id="3bf2f-120">When you use the **Variables** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="3bf2f-121">若要使用表达式来设置变量值，首先请确认变量数据类型与表达式的计算结果兼容，然后在 "变量" 窗口的列中提供一个表达式 `Expression` 。 **Variables**</span><span class="sxs-lookup"><span data-stu-id="3bf2f-121">To use an expression to set the variable value, first confirm that the variable data type is compatible with the evaluation result of the expression and then provide an expression in the `Expression` column of the **Variables** window.</span></span> <span data-ttu-id="3bf2f-122">"**属性**" 窗口中的 EvaluateAsExpression 属性会自动设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-122">The EvaluateAsExpression property in the **Properties** window is automatically set to `True`.</span></span>  
  
-   <span data-ttu-id="3bf2f-123">如果为变量指定了表达式，则该变量旁边将显示一个特殊图标标记。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-123">When you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="3bf2f-124">这个特殊的图标标记还显示在设置有表达式的连接管理器和任务旁边。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-124">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
-   <span data-ttu-id="3bf2f-125">通过变量的 **“变量”** 窗口，可以访问 **“表达式生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-125">The **Variables** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="3bf2f-126">使用该工具可以生成、验证和计算表达式。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-126">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="3bf2f-127">有关详细信息，请参阅[表达式生成器](expressions/expression-builder.md)和 [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-127">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="3bf2f-128">在 "**变量**" 和 "**属性**" 窗口中，如果为变量指定了表达式，并且将 `EvaluateAsExpression` 设置为 `True` ，则无法更改变量数据类型。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-128">In both the **Variables** and **Properties** window, if you assign an expression to the variable, and `EvaluateAsExpression` is set to `True`, you cannot change the variable data type.</span></span>  
  
 <span data-ttu-id="3bf2f-129">**设置 Namespace 和 Name 属性**</span><span class="sxs-lookup"><span data-stu-id="3bf2f-129">**Setting the Namespace and Name Properties**</span></span>  
  
 <span data-ttu-id="3bf2f-130">`Name` 和 `Namespace` 属性的值必须以 Unicode 标准 2.0 定义的字母字符或下划线 (_) 开头。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-130">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="3bf2f-131">后续字符可以是在 Unicode 标准 2.0 中定义的字母或数字，或是下划线 (\_)。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-131">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="using-the-variables-window-to-set-properties"></a><span data-ttu-id="3bf2f-132">使用变量窗口设置属性</span><span class="sxs-lookup"><span data-stu-id="3bf2f-132">Using the Variables Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a><span data-ttu-id="3bf2f-133">使用变量窗口设置变量的属性</span><span class="sxs-lookup"><span data-stu-id="3bf2f-133">To set the properties of a variable by using the Variables window</span></span>  
  
1.  <span data-ttu-id="3bf2f-134">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-134">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="3bf2f-135">在解决方案资源管理器中，右键单击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-135">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="3bf2f-136">在 **SSIS** 菜单上单击 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-136">On the **SSIS** menu, click **Variables**.</span></span>  
  
     <span data-ttu-id="3bf2f-137">您可以通过将 View.Variables 命令映射到在 **“选项”** 对话框的 **“键盘”** 页上选择的组合键来显示 **“变量”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-137">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="3bf2f-138">或者，在 **“变量”** 窗口中单击 **“网格选项”**，然后选择要出现在 **“变量”** 窗口中的列，并选择要应用到变量列表的筛选器。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-138">Optionally, in the **Variables** window click **Grid Options**, and then select the columns to appear in the **Variables** window and select the filters to apply to the list of variables.</span></span>  
  
5.  <span data-ttu-id="3bf2f-139">在列表中选择变量，然后更新 `Name` 、"**数据类型**"、、、" `Value` `Namespace` **引发更改事件**"、"**说明" 和 "** 列 `Expression` " 中的值。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-139">Select the variable in the list, and then update values in the `Name`, **Data Type**, `Value`, `Namespace`, **Raise Change Event**, **Description,** and `Expression` columns.</span></span>  
  
6.  <span data-ttu-id="3bf2f-140">在列表中选择变量，然后单击 **“移动变量”** 以更改作用域。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-140">Select the variable in the list, and then click **Move Variable** to change the scope.</span></span>  
  
7.  <span data-ttu-id="3bf2f-141">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-141">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="using-the-properties-window-to-set-properties"></a><span data-ttu-id="3bf2f-142">使用属性窗口设置属性</span><span class="sxs-lookup"><span data-stu-id="3bf2f-142">Using the Properties Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a><span data-ttu-id="3bf2f-143">使用属性窗口设置变量的属性</span><span class="sxs-lookup"><span data-stu-id="3bf2f-143">To set the properties of a variable by using the Properties window</span></span>  
  
1.  <span data-ttu-id="3bf2f-144">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-144">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="3bf2f-145">在解决方案资源管理器中，右键单击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-145">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="3bf2f-146">在 **“视图”** 菜单上，单击 **“属性窗口”** 。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-146">On the **View** menu, click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="3bf2f-147">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“包资源管理器”** 选项卡，并展开“包”节点。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-147">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Package Explorer** tab and expand the Package node.</span></span>  
  
5.  <span data-ttu-id="3bf2f-148">若要修改包范围内的变量，请展开“变量”节点，如果看不到该节点，请展开“事件处理程序”或“可执行文件”节点，直到找到包含要修改的变量的“变量”节点。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-148">To modify variables with package scope, expand the Variables node; otherwise, expand the Event Handlers or Executables nodes until you locate the Variables node that contains the variable that you want to modify.</span></span>  
  
6.  <span data-ttu-id="3bf2f-149">单击要修改其属性的变量。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-149">Click the variable whose properties you want to modify.</span></span>  
  
7.  <span data-ttu-id="3bf2f-150">在\*\*\*\*“属性”窗口中，更改读/写变量属性。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-150">In the **Properties** window, update the read/write variable properties.</span></span> <span data-ttu-id="3bf2f-151">对于用户定义的变量而言，某些属性为可读/只读。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-151">Some properties are read/read only for user-defined variables.</span></span>  
  
     <span data-ttu-id="3bf2f-152">有关属性的详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-152">For more information about the properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
8.  <span data-ttu-id="3bf2f-153">若要保存已更新的包，请在 **“文件”** 菜单中单击 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="3bf2f-153">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf2f-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bf2f-154">See Also</span></span>  
 <span data-ttu-id="3bf2f-155">[Integration Services (SSIS) 变量](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3bf2f-155">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="3bf2f-156">[使用包中的变量](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="3bf2f-156">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="3bf2f-157">添加、删除、更改包中用户定义变量的作用域</span><span class="sxs-lookup"><span data-stu-id="3bf2f-157">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
