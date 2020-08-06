---
title: 处理 SMO 异常 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
ms.openlocfilehash: f4ae9e475a019c9bf874ee3f8365f3f3ac8e19d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590682"
---
# <a name="handling-smo-exceptions"></a><span data-ttu-id="64404-102">处理 SMO 异常</span><span class="sxs-lookup"><span data-stu-id="64404-102">Handling SMO Exceptions</span></span>
  <span data-ttu-id="64404-103">在托管代码中，如果出现错误，便会引发异常。</span><span class="sxs-lookup"><span data-stu-id="64404-103">In managed code, exceptions are thrown when an error occurs.</span></span> <span data-ttu-id="64404-104">SMO 方法和属性不在返回值中报告成功或失败信息。</span><span class="sxs-lookup"><span data-stu-id="64404-104">SMO methods and properties do not report success or failure in the return value.</span></span> <span data-ttu-id="64404-105">相反，可以通过异常处理程序捕获和处理异常。</span><span class="sxs-lookup"><span data-stu-id="64404-105">Instead, exceptions can be caught and handled by an exception handler.</span></span>  
  
 <span data-ttu-id="64404-106">SMO 中存在多种不同的异常类。</span><span class="sxs-lookup"><span data-stu-id="64404-106">Different exception classes exist in the SMO.</span></span> <span data-ttu-id="64404-107">可以从提供与异常相关的文字信息的异常属性（例如 `Message` 属性）中提取出关于异常的信息。</span><span class="sxs-lookup"><span data-stu-id="64404-107">Information about the exception can be extracted from the exception properties such as the `Message` property that gives a text message about the exception.</span></span>  
  
 <span data-ttu-id="64404-108">异常处理语句是特定于编程语言的。</span><span class="sxs-lookup"><span data-stu-id="64404-108">The exception handling statements are specific to the programming language.</span></span> <span data-ttu-id="64404-109">例如，在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 中，该语句为 `Catch` 语句。</span><span class="sxs-lookup"><span data-stu-id="64404-109">For example, in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic it is the `Catch` statement.</span></span>  
  
## <a name="inner-exceptions"></a><span data-ttu-id="64404-110">内部异常</span><span class="sxs-lookup"><span data-stu-id="64404-110">Inner Exceptions</span></span>  
 <span data-ttu-id="64404-111">异常可能是常规异常，也可能是特定异常。</span><span class="sxs-lookup"><span data-stu-id="64404-111">Exceptions can either be general or specific.</span></span> <span data-ttu-id="64404-112">常规异常包含一组特定异常。</span><span class="sxs-lookup"><span data-stu-id="64404-112">General exceptions contain a set of specific exceptions.</span></span> <span data-ttu-id="64404-113">可使用几条 `Catch` 语句处理预计可能出现的错误，并使用常规异常处理代码处理其余错误。</span><span class="sxs-lookup"><span data-stu-id="64404-113">Several `Catch` statements can be used to handle anticipated errors and let remaining errors fall through to general exception handling code.</span></span> <span data-ttu-id="64404-114">通常，异常按照级联顺序发生。</span><span class="sxs-lookup"><span data-stu-id="64404-114">Exceptions often occur in a cascading sequence.</span></span> <span data-ttu-id="64404-115">很多情况下，SMO 异常可能是由 SQL 异常导致的。</span><span class="sxs-lookup"><span data-stu-id="64404-115">Frequently, an SMO exception might have been caused by an SQL exception.</span></span> <span data-ttu-id="64404-116">检测是否为这种情况的方法便是连续使用 `InnerException` 属性确定导致最终顶级异常的原始异常。</span><span class="sxs-lookup"><span data-stu-id="64404-116">The way to detect this is to use the `InnerException` property successively to determine the original exception that caused the final, top-level exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64404-117">此 `SQLException` 异常在**SqlClient**命名空间中声明。</span><span class="sxs-lookup"><span data-stu-id="64404-117">The `SQLException` exception is declared in the **System.Data.SqlClient** namespace.</span></span>  
  
 <span data-ttu-id="64404-118">![显示级别的关系图](../../../database-engine/dev-guide/media/exception-flow.gif "显示级别的关系图")</span><span class="sxs-lookup"><span data-stu-id="64404-118">![A diagram that shows the levels from which an excp](../../../database-engine/dev-guide/media/exception-flow.gif "A diagram that shows the levels from which an excp")</span></span>  
  
 <span data-ttu-id="64404-119">此图显示了异常通过各应用程序层的流程。</span><span class="sxs-lookup"><span data-stu-id="64404-119">The diagram shows the flow of exceptions through the layers of the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64404-120">示例</span><span class="sxs-lookup"><span data-stu-id="64404-120">Example</span></span>  
 <span data-ttu-id="64404-121">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="64404-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="64404-122">有关详细信息，请参阅[在 Visual studio .net 中创建 Visual C&#35; SMO 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)或[在 visual Studio .net 中创建 Visual Basic SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="64404-122">For more information, see [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) or [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="catching-an-exception-in-visual-basic"></a><span data-ttu-id="64404-123">在 Visual Basic 中捕获异常</span><span class="sxs-lookup"><span data-stu-id="64404-123">Catching an Exception in Visual Basic</span></span>  
 <span data-ttu-id="64404-124">此代码示例演示如何使用 `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 语句捕获 SMO 异常。</span><span class="sxs-lookup"><span data-stu-id="64404-124">This code example shows how to use the `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] statement to catch a SMO exception.</span></span> <span data-ttu-id="64404-125">所有 SMO 异常的类型均为 SmoException，并且均列出在 SMO 引用中。</span><span class="sxs-lookup"><span data-stu-id="64404-125">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="64404-126">显示内部异常的顺序的目的在于揭示错误的根源。</span><span class="sxs-lookup"><span data-stu-id="64404-126">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="64404-127">有关详细信息，请参阅 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET 文档。</span><span class="sxs-lookup"><span data-stu-id="64404-127">For more information, see the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET documentation.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a><span data-ttu-id="64404-128">在 Visual C# 中捕获异常</span><span class="sxs-lookup"><span data-stu-id="64404-128">Catching an Exception in Visual C#</span></span>  
 <span data-ttu-id="64404-129">此代码示例演示如何使用 `Try...Catch...Finally` Visual C# 语句捕获 SMO 异常。</span><span class="sxs-lookup"><span data-stu-id="64404-129">This code example shows how to use the `Try...Catch...Finally` Visual C# statement to catch a SMO exception.</span></span> <span data-ttu-id="64404-130">所有 SMO 异常的类型均为 SmoException，并且均列出在 SMO 引用中。</span><span class="sxs-lookup"><span data-stu-id="64404-130">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="64404-131">显示内部异常的顺序的目的在于揭示错误的根源。</span><span class="sxs-lookup"><span data-stu-id="64404-131">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="64404-132">有关详细信息，请参阅 Visual C# 文档。</span><span class="sxs-lookup"><span data-stu-id="64404-132">For more information, see the Visual C# documentation.</span></span>  
  
```  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
