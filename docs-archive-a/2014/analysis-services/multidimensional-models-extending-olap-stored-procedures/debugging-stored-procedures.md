---
title: 调试存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689655"
---
# <a name="debugging-stored-procedures"></a><span data-ttu-id="34435-102">调试存储过程</span><span class="sxs-lookup"><span data-stu-id="34435-102">Debugging Stored Procedures</span></span>
  <span data-ttu-id="34435-103">实际上，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 存储过程是使用 C#（或任何其他 CLR 或 COM 语言）编写的 CLR 或 COM 库（通常为 DLL）。</span><span class="sxs-lookup"><span data-stu-id="34435-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stored procedures are actually CLR or COM libraries (normally DLLs) that are written in C# (or any other CLR or COM language).</span></span> <span data-ttu-id="34435-104">因此，调试存储过程类似于在 Visual Studio 调试环境中调试任何其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="34435-104">Therefore, debugging a stored procedure is much like debugging any other application in the Visual Studio debugging environment.</span></span> <span data-ttu-id="34435-105">您可以使用集成调试功能在 Visual Studio 开发环境中调试存储过程。</span><span class="sxs-lookup"><span data-stu-id="34435-105">You debug stored procedures in the Visual Studio development environment using the integrated debugging functions.</span></span> <span data-ttu-id="34435-106">您可以使用这些功能执行下列操作：在过程位置停止、检查内存和注册值、更改变量、观察消息流量以及密切监视代码的运行状况。</span><span class="sxs-lookup"><span data-stu-id="34435-106">These allow you to stop at procedure locations, inspect memory and register values, change variables, observe message traffic and get a close look at how your code works.</span></span>  
  
### <a name="to-debug-a-stored-procedure"></a><span data-ttu-id="34435-107">调试存储过程</span><span class="sxs-lookup"><span data-stu-id="34435-107">To debug a stored procedure</span></span>  
  
1.  <span data-ttu-id="34435-108">在 Visual Studio 中打开用于创建 DLL 的项目。</span><span class="sxs-lookup"><span data-stu-id="34435-108">Open the project used to create the DLL in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="34435-109">使用要调试的过程相应的方法或函数创建断点。</span><span class="sxs-lookup"><span data-stu-id="34435-109">Create breakpoints in the method or function corresponding to the procedure you want to debug.</span></span>  
  
3.  <span data-ttu-id="34435-110">使用 Visual Studio 创建存储过程 DLL 的调试版本。</span><span class="sxs-lookup"><span data-stu-id="34435-110">Use Visual Studio to create a debug build of a stored procedure DLL.</span></span>  
  
4.  <span data-ttu-id="34435-111">将 DLL 部署到服务器中。</span><span class="sxs-lookup"><span data-stu-id="34435-111">Deploy the DLL to the server.</span></span> <span data-ttu-id="34435-112">有关将 DLL 部署到服务器的详细信息，请参阅[创建存储过程](creating-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="34435-112">For more information about deploying the DLL to the server, see [Creating Stored Procedures](creating-stored-procedures.md).</span></span>  
  
5.  <span data-ttu-id="34435-113">您需要一个调用要进行测试的存储过程的应用程序。</span><span class="sxs-lookup"><span data-stu-id="34435-113">You need an application that calls the stored procedure that you want to test.</span></span> <span data-ttu-id="34435-114">如果没有此类可用的应用程序，则可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 MDX 查询编辑器创建调用要进行测试的存储过程的 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="34435-114">If you do not have one ready, you can use the MDX Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create an MDX query that calls the stored procedure that you want to test.</span></span>  
  
6.  <span data-ttu-id="34435-115">在 Visual Studio 中，附加到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进程 (Msmdsrv.exe)。</span><span class="sxs-lookup"><span data-stu-id="34435-115">In Visual Studio, attach to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process (Msmdsrv.exe).</span></span>  
  
    1.  <span data-ttu-id="34435-116">从 "**调试**" 菜单中，选择 "**附加 toProcess**"。</span><span class="sxs-lookup"><span data-stu-id="34435-116">From the **Debug** menu, choose **Attatch toProcess**.</span></span>  
  
    2.  <span data-ttu-id="34435-117">在 "**附加 toProcess** " 对话框中，选择 "**显示所有用户的进程**"。</span><span class="sxs-lookup"><span data-stu-id="34435-117">In the **Attatch toProcess** dialog box, select **Show processes from all users**.</span></span>  
  
    3.  <span data-ttu-id="34435-118">在 "**可用进程**" 列表的 "**处理**" 列中，单击 " **Msmdsrv.exe**"。</span><span class="sxs-lookup"><span data-stu-id="34435-118">In the **Available Processes** list, in the **Process** column, click **Msmdsrv.exe**.</span></span> <span data-ttu-id="34435-119">如果服务器上运行多个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，则需要通过要使用的实例的 ID 标识进程。</span><span class="sxs-lookup"><span data-stu-id="34435-119">If there is more than one instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running on the server, you need to identify the process by the ID of the instance you want to use.</span></span>  
  
    4.  <span data-ttu-id="34435-120">在 "**附加到**" 文本框中，确保选择了适当的程序类型。</span><span class="sxs-lookup"><span data-stu-id="34435-120">In the **Attach to** text box, make sure that the appropriate program type is selected.</span></span> <span data-ttu-id="34435-121">对于 CLR DLL，依次单击 "**选择**"、"**调试以下代码类型**" 和 "**托管**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="34435-121">For a CLR DLL, click **Select**, then click **Debug these code types**, then click **Managed**, then click **OK**.</span></span> <span data-ttu-id="34435-122">对于 COM DLL，单击 "**选择**"，单击 "**调试以下代码类型**"，单击 "**本机**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="34435-122">For a COM DLL, click **Select**, then click **Debug these code types**, then click **Native**, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="34435-123">单击 **“附加”** 。</span><span class="sxs-lookup"><span data-stu-id="34435-123">Click **Attach**.</span></span>  
  
7.  <span data-ttu-id="34435-124">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，调用程序或 MDX 脚本（用于调用存储过程）。</span><span class="sxs-lookup"><span data-stu-id="34435-124">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], invoke the program or MDX script that calls the stored procedure.</span></span> <span data-ttu-id="34435-125">当调试程序到达包含断点的某行时，便会中断。</span><span class="sxs-lookup"><span data-stu-id="34435-125">The debugger breaks when it reaches a line containing a breakpoint.</span></span> <span data-ttu-id="34435-126">您可以在监视窗口中计算变量，查看局部变量并逐句检查代码。</span><span class="sxs-lookup"><span data-stu-id="34435-126">You can evaluate variables in the watch window, view locals, and step through the code.</span></span>  
  
 <span data-ttu-id="34435-127">如果在调试库时出现问题，则确保已将对应的程序数据库 (PDB) 文件复制到服务器中的部署位置。</span><span class="sxs-lookup"><span data-stu-id="34435-127">If you have problems debugging a library, make sure that the corresponding program database (PDB) file was copied to the deployment location on the server.</span></span> <span data-ttu-id="34435-128">如果在注册或部署过程中没有复制该文件，则必须手动将其复制到 DLL 所在的位置。</span><span class="sxs-lookup"><span data-stu-id="34435-128">If this file was not copied during registration or deployment, you must copy it manually to the same location as the DLL.</span></span> <span data-ttu-id="34435-129">对于本机代码 (COM DLL)，PDB 文件驻留在 \debug 子目录中。</span><span class="sxs-lookup"><span data-stu-id="34435-129">For native code (COM DLL), the PDB file resides in the \debug subdirectory.</span></span> <span data-ttu-id="34435-130">对于托管代码 (CLR DLL)，该文件驻留在 \WINDEBUG 子目录中。</span><span class="sxs-lookup"><span data-stu-id="34435-130">For managed code (CLR DLL), it resides in the \WINDEBUG subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34435-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34435-131">See Also</span></span>  
 <span data-ttu-id="34435-132">[多维模型程序集管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="34435-132">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="34435-133">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="34435-133">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  
