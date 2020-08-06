---
title: 程序异常消息框 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9d49bdf8c73f86b2c334018d40510b4ae67c85ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693453"
---
# <a name="program-exception-message-box"></a><span data-ttu-id="89909-102">对异常消息框编程</span><span class="sxs-lookup"><span data-stu-id="89909-102">Program Exception Message Box</span></span>
  <span data-ttu-id="89909-103">可以使用应用程序中的异常消息框，它与 <xref:System.Windows.Forms.MessageBox> 类相比，可以大大提高对消息传送的控制。</span><span class="sxs-lookup"><span data-stu-id="89909-103">You can use the exception message box in your applications to provide significantly more control over the messaging experience than is provided by the <xref:System.Windows.Forms.MessageBox> class.</span></span> <span data-ttu-id="89909-104">有关详细信息，请参阅[异常消息框编程](../../../2014/database-engine/dev-guide/exception-message-box-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="89909-104">For more information, see [Exception Message Box Programming](../../../2014/database-engine/dev-guide/exception-message-box-programming.md).</span></span> <span data-ttu-id="89909-105">有关如何获取和部署异常消息框 .dll 的信息，请参阅 [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md)。</span><span class="sxs-lookup"><span data-stu-id="89909-105">For information about how to obtain and deploy the exception message box .dll, see [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="89909-106">过程</span><span class="sxs-lookup"><span data-stu-id="89909-106">Procedure</span></span>  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a><span data-ttu-id="89909-107">通过使用异常消息框处理异常</span><span class="sxs-lookup"><span data-stu-id="89909-107">To handle an exception by using the exception message box</span></span>  
  
1.  <span data-ttu-id="89909-108">将托管代码项目中的某个引用添加到 Microsoft.ExceptionMessageBox.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="89909-108">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="89909-109"> (可选) 添加 `using` (c # ) 或 `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .net) 指令以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="89909-109">(Optional) Add a `using` (C#) or `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="89909-110">创建 try-catch 块处理预期异常。</span><span class="sxs-lookup"><span data-stu-id="89909-110">Create a try-catch block to handle the anticipated exception.</span></span>  
  
4.  <span data-ttu-id="89909-111">在 `catch` 块中，创建 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="89909-111">Within the `catch` block, create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="89909-112">传递 <xref:System.Exception> 由块处理的对象 `try` - `catch` 。</span><span class="sxs-lookup"><span data-stu-id="89909-112">Pass the <xref:System.Exception> object handled by the `try`-`catch` block.</span></span>  
  
5.  <span data-ttu-id="89909-113">（可选）为 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 设置下列一个或多个属性：</span><span class="sxs-lookup"><span data-stu-id="89909-113">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="89909-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>枚举，指定要在异常消息框中显示的按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>枚举，用于指定异常消息框的默认按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>枚举，用于控制异常消息框的其他行为。</span><span class="sxs-lookup"><span data-stu-id="89909-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>枚举，指定要在异常消息框中显示的符号。</span><span class="sxs-lookup"><span data-stu-id="89909-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
6.  <span data-ttu-id="89909-118">调用 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="89909-118">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="89909-119">传递异常消息框所属的父窗口。</span><span class="sxs-lookup"><span data-stu-id="89909-119">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="89909-120"> (可选) <xref:System.Windows.Forms.DialogResult> 如果需要确定用户单击的是哪个按钮，请注意返回的枚举值。</span><span class="sxs-lookup"><span data-stu-id="89909-120">(Optional) Note the value of returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a><span data-ttu-id="89909-121">显示没有异常的异常消息框</span><span class="sxs-lookup"><span data-stu-id="89909-121">To display the exception message box without an exception</span></span>  
  
1.  <span data-ttu-id="89909-122">将托管代码项目中的某个引用添加到 Microsoft.ExceptionMessageBox.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="89909-122">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="89909-123"> (可选) 添加 `using` (c # ) 或 `Imports` (Visual Basic .net) 指令以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="89909-123">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="89909-124">创建的 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="89909-124">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="89909-125">将消息文本作为 <xref:System.String> 值传递。</span><span class="sxs-lookup"><span data-stu-id="89909-125">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="89909-126">（可选）为 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 设置下列一个或多个属性：</span><span class="sxs-lookup"><span data-stu-id="89909-126">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="89909-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>枚举，指定要在异常消息框中显示的按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - 异常消息框的对话框标题。</span><span class="sxs-lookup"><span data-stu-id="89909-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - Dialog box caption of the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>枚举，用于指定异常消息框对话框的默认按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the dialog box of the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>枚举，用于控制异常消息框的其他行为。</span><span class="sxs-lookup"><span data-stu-id="89909-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="89909-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>枚举，指定要在异常消息框中显示的符号。</span><span class="sxs-lookup"><span data-stu-id="89909-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
5.  <span data-ttu-id="89909-132">调用 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="89909-132">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="89909-133">传递异常消息框所属的父窗口。</span><span class="sxs-lookup"><span data-stu-id="89909-133">Pass the parent window to which the exception message box belongs.</span></span>  
  
6.  <span data-ttu-id="89909-134">（可选）如果需要确定用户单击的按钮，请注明返回的 <xref:System.Windows.Forms.DialogResult> 枚举值。</span><span class="sxs-lookup"><span data-stu-id="89909-134">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a><span data-ttu-id="89909-135">显示具有自定义按钮的异常消息框</span><span class="sxs-lookup"><span data-stu-id="89909-135">To display the exception message box with customized buttons</span></span>  
  
1.  <span data-ttu-id="89909-136">将托管代码项目中的某个引用添加到 Microsoft.ExceptionMessageBox.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="89909-136">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="89909-137"> (可选) 添加 `using` (c # ) 或 `Imports` (Visual Basic .net) 指令以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="89909-137">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="89909-138">按以下两种方式之一创建 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 类的实例：</span><span class="sxs-lookup"><span data-stu-id="89909-138">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="89909-139">传递 <xref:System.Exception> 由块处理的对象 `try` - `catch` 。</span><span class="sxs-lookup"><span data-stu-id="89909-139">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="89909-140">将消息文本作为 <xref:System.String> 值传递。</span><span class="sxs-lookup"><span data-stu-id="89909-140">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="89909-141">为 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> 设置以下值之一：</span><span class="sxs-lookup"><span data-stu-id="89909-141">Set one of the following values for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>:</span></span>  
  
    -   <span data-ttu-id="89909-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore>-显示 "**中止**"、"**重试**" 和 "**忽略**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> - displays the **Abort**, **Retry**, and **Ignore** buttons.</span></span>  
  
    -   <span data-ttu-id="89909-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - 显示自定义按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - displays custom buttons.</span></span>  
  
    -   <span data-ttu-id="89909-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK>-显示 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> - displays the **OK** button.</span></span>  
  
    -   <span data-ttu-id="89909-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel>-显示 **"确定" 和 "** **取消**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> - displays the **OK** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="89909-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel>-显示 "**重试**" 和 "**取消**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> - displays the **Retry** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="89909-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo>-显示 **"是" 和 "** **否**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> - displays **Yes** and **No** buttons.</span></span>  
  
    -   <span data-ttu-id="89909-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel>-显示 **"是**"、"**否**" 和 "**取消**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> - displays **Yes**, **No**, and **Cancel** buttons.</span></span>  
  
5.  <span data-ttu-id="89909-149">（可选）如果使用自定义按钮，请调用 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> 方法的重载之一以指定最多五个自定义按钮的文本。</span><span class="sxs-lookup"><span data-stu-id="89909-149">(Optional) If you use custom buttons, call one of the overloads of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> method to specify text for up to five custom buttons.</span></span>  
  
6.  <span data-ttu-id="89909-150">调用 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="89909-150">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="89909-151">传递异常消息框所属的父窗口。</span><span class="sxs-lookup"><span data-stu-id="89909-151">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="89909-152">（可选）如果需要确定用户单击的按钮，请注明返回的 <xref:System.Windows.Forms.DialogResult> 枚举值。</span><span class="sxs-lookup"><span data-stu-id="89909-152">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span> <span data-ttu-id="89909-153">如果使用自定义按钮，请注明 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> 属性的 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> 值以确定用户单击的自定义按钮。</span><span class="sxs-lookup"><span data-stu-id="89909-153">If you use custom buttons, note the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> for the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> property to determine which of the custom buttons the user clicked.</span></span>  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a><span data-ttu-id="89909-154">允许用户决定是否要显示异常消息框</span><span class="sxs-lookup"><span data-stu-id="89909-154">To allow users to decide whether to show the exception message box</span></span>  
  
1.  <span data-ttu-id="89909-155">将托管代码项目中的某个引用添加到 Microsoft.ExceptionMessageBox.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="89909-155">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="89909-156"> (可选) 添加 `using` (c # ) 或 `Imports` (Visual Basic .net) 指令以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="89909-156">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="89909-157">按以下两种方式之一创建 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 类的实例：</span><span class="sxs-lookup"><span data-stu-id="89909-157">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="89909-158">传递 <xref:System.Exception> 由块处理的对象 `try` - `catch` 。</span><span class="sxs-lookup"><span data-stu-id="89909-158">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="89909-159">将消息文本作为 <xref:System.String> 值传递。</span><span class="sxs-lookup"><span data-stu-id="89909-159">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="89909-160">将 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="89909-160">Set the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="89909-161">（可选）指定请用户决定以后是否还为 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A> 显示异常消息框的文本。</span><span class="sxs-lookup"><span data-stu-id="89909-161">(Optional) Specify the text that asks the user to decide whether to show the exception message box again for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>.</span></span> <span data-ttu-id="89909-162">默认文本为“不再显示此消息”。</span><span class="sxs-lookup"><span data-stu-id="89909-162">The default text is "Do not show this message again."</span></span>  
  
6.  <span data-ttu-id="89909-163">如果需要仅在应用程序执行期间保留用户的决定，请将 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> 的值设置为全局 <xref:System.Boolean> 变量。</span><span class="sxs-lookup"><span data-stu-id="89909-163">If you need to keep the user's decision only for the duration of the application's execution, set the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> to a global <xref:System.Boolean> variable.</span></span> <span data-ttu-id="89909-164">在创建异常消息框的实例前计算此值。</span><span class="sxs-lookup"><span data-stu-id="89909-164">Evaluate this value before creating an instance of the exception message box.</span></span>  
  
7.  <span data-ttu-id="89909-165">如果需要永久存储用户的决定，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="89909-165">If you need to store a user's decision permanently, do the following:</span></span>  
  
    1.  <span data-ttu-id="89909-166">调用 CreateSubKey 方法以打开你的应用程序使用的自定义注册表项，然后将 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> 设置为返回的 RegistryKey 对象。</span><span class="sxs-lookup"><span data-stu-id="89909-166">Call the CreateSubKey method to open a custom registry key that your application uses, and set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> to the returned RegistryKey object.</span></span>  
  
    2.  <span data-ttu-id="89909-167">将 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> 设置为使用的注册表值的名称。</span><span class="sxs-lookup"><span data-stu-id="89909-167">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> to the name of the registry value that is used.</span></span>  
  
    3.  <span data-ttu-id="89909-168">将 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="89909-168">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> to `true`.</span></span>  
  
    4.  <span data-ttu-id="89909-169">调用 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="89909-169">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="89909-170">计算指定的注册表项，仅当注册表项中存储的数据为 0 时才显示异常消息框。</span><span class="sxs-lookup"><span data-stu-id="89909-170">The specified registry key is evaluated, and the exception message box is displayed only if the data stored in the registry key is 0.</span></span> <span data-ttu-id="89909-171">如果显示对话框且用户在单击按钮前选中复选框，则注册表项中的数据设置为 1。</span><span class="sxs-lookup"><span data-stu-id="89909-171">If the dialog box is displayed and the user selects the check box before clicking a button, the data in the registry key is set to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89909-172">示例</span><span class="sxs-lookup"><span data-stu-id="89909-172">Example</span></span>  
 <span data-ttu-id="89909-173">此示例使用带有 **"确定"** 按钮的异常消息框，以显示应用程序异常中的信息，该异常包含处理的异常以及其他特定于应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="89909-173">This example uses the exception message box with only the **OK** button to display information from an application exception that includes the handled exception along with additional application-specific information.</span></span>  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a><span data-ttu-id="89909-174">示例</span><span class="sxs-lookup"><span data-stu-id="89909-174">Example</span></span>  
 <span data-ttu-id="89909-175">此示例使用具有 **"是"** 和 "**否**" 按钮的异常消息框，用户从中选择。</span><span class="sxs-lookup"><span data-stu-id="89909-175">This example uses the exception message box with **Yes** and **No** buttons from which the user chooses.</span></span>  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a><span data-ttu-id="89909-176">示例</span><span class="sxs-lookup"><span data-stu-id="89909-176">Example</span></span>  
 <span data-ttu-id="89909-177">以下示例使用具有自定义按钮的异常消息框。</span><span class="sxs-lookup"><span data-stu-id="89909-177">This example uses the exception message box with custom buttons.</span></span>  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a><span data-ttu-id="89909-178">示例</span><span class="sxs-lookup"><span data-stu-id="89909-178">Example</span></span>  
 <span data-ttu-id="89909-179">以下示例使用复选框来确定是否显示异常消息框。</span><span class="sxs-lookup"><span data-stu-id="89909-179">This example uses the check box to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a><span data-ttu-id="89909-180">示例</span><span class="sxs-lookup"><span data-stu-id="89909-180">Example</span></span>  
 <span data-ttu-id="89909-181">以下示例使用复选框和注册表项来确定是否显示异常消息框。</span><span class="sxs-lookup"><span data-stu-id="89909-181">This example uses the check box and a registry key to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a><span data-ttu-id="89909-182">示例</span><span class="sxs-lookup"><span data-stu-id="89909-182">Example</span></span>  
 <span data-ttu-id="89909-183">以下示例使用异常消息框来显示对排除故障或调试有帮助的其他信息。</span><span class="sxs-lookup"><span data-stu-id="89909-183">This example uses the exception message box to show additional information that is helpful when troubleshooting or debugging.</span></span>  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
