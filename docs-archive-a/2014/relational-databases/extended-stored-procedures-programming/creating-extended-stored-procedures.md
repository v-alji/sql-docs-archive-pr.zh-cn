---
title: 创建扩展存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
ms.openlocfilehash: d243b27b8542ec5fe10d795de1729d6c1fe484c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589094"
---
# <a name="creating-extended-stored-procedures"></a><span data-ttu-id="65a60-102">创建扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="65a60-102">Creating Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="65a60-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="65a60-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="65a60-104">扩展存储过程是带有原型的函数：</span><span class="sxs-lookup"><span data-stu-id="65a60-104">An extended stored procedure is a function with a prototype:</span></span>  
  
 <span data-ttu-id="65a60-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span><span class="sxs-lookup"><span data-stu-id="65a60-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span></span>  
  
 <span data-ttu-id="65a60-106">使用前缀 xp_ 是可选的。</span><span class="sxs-lookup"><span data-stu-id="65a60-106">Using the prefix xp_ is optional.</span></span> <span data-ttu-id="65a60-107">当在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中引用扩展存储过程名称时，名称区分大小写，而与服务器上安装的代码页/排序顺序无关。</span><span class="sxs-lookup"><span data-stu-id="65a60-107">Extended stored procedure names are case sensitive when referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, regardless of code page/sort order installed on the server.</span></span> <span data-ttu-id="65a60-108">当您生成 DLL 时：</span><span class="sxs-lookup"><span data-stu-id="65a60-108">When you build a DLL:</span></span>  
  
-   <span data-ttu-id="65a60-109">如果入口点是必需的，则编写 DllMain 函数。</span><span class="sxs-lookup"><span data-stu-id="65a60-109">If an entry point is necessary, write a DllMain function.</span></span>  
  
     <span data-ttu-id="65a60-110">此函数是可选的；如果您在源代码中未提供此函数，则编译器将链接其自己的版本，此时它仅返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="65a60-110">This function is optional; if you do not provide it in source code, the compiler links its own version, which does nothing but return TRUE.</span></span> <span data-ttu-id="65a60-111">如果您提供了 DllMain 函数，当线程或进程附加到 DLL 或从 DLL 分离时，操作系统将调用此函数。</span><span class="sxs-lookup"><span data-stu-id="65a60-111">If you provide a DllMain function, the operating system calls this function when a thread or process attaches to or detaches from the DLL.</span></span>  
  
-   <span data-ttu-id="65a60-112">必须导出从 DLL 外部调用的所有函数（所有扩展存储过程函数）。</span><span class="sxs-lookup"><span data-stu-id="65a60-112">All functions called from outside the DLL (all extended stored procedure Efunctions) must be exported.</span></span>  
  
     <span data-ttu-id="65a60-113">可以通过在 .def 文件的导出部分中列出函数的名称来导出该函数，也可以在源代码中为函数名称加上前缀 __declspec (dllexport) ，Microsoft 编译器扩展 (请注意，_declspec \_ ( # A4 以两个下划线) 开头。</span><span class="sxs-lookup"><span data-stu-id="65a60-113">You can export a function by listing its name in the EXPORTS section of a .def file, or you can prefix the function name in the source code with __declspec(dllexport), a Microsoft compiler extension (Note that \__declspec() begins with two underscores).</span></span>  
  
 <span data-ttu-id="65a60-114">创建扩展存储过程 DLL 时需要这些文件。</span><span class="sxs-lookup"><span data-stu-id="65a60-114">These files are required for creating an extended stored procedure DLL.</span></span>  
  
|<span data-ttu-id="65a60-115">文件</span><span class="sxs-lookup"><span data-stu-id="65a60-115">File</span></span>|<span data-ttu-id="65a60-116">说明</span><span class="sxs-lookup"><span data-stu-id="65a60-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="65a60-117">Srv.h</span><span class="sxs-lookup"><span data-stu-id="65a60-117">Srv.h</span></span>|<span data-ttu-id="65a60-118">扩展存储过程 API 头文件</span><span class="sxs-lookup"><span data-stu-id="65a60-118">Extended Stored Procedure API header file</span></span>|  
|<span data-ttu-id="65a60-119">Opends60.lib</span><span class="sxs-lookup"><span data-stu-id="65a60-119">Opends60.lib</span></span>|<span data-ttu-id="65a60-120">Opends60.dll 的导入库</span><span class="sxs-lookup"><span data-stu-id="65a60-120">Import library for Opends60.dll</span></span>|  
  
 <span data-ttu-id="65a60-121">若要创建扩展存储过程 DLL，请创建一个类型为动态链接库的项目。</span><span class="sxs-lookup"><span data-stu-id="65a60-121">To create an extended stored procedure DLL, create a project of type Dynamic Link Library.</span></span> <span data-ttu-id="65a60-122">有关创建 DLL 的详细信息，请参阅开发环境文档。</span><span class="sxs-lookup"><span data-stu-id="65a60-122">For more information about creating a DLL, see the development environment documentation.</span></span>  
  
 <span data-ttu-id="65a60-123">强烈建议所有扩展存储过程 DLL 都实现和导出以下函数：</span><span class="sxs-lookup"><span data-stu-id="65a60-123">It is highly recommended that all extended stored procedure DLLs implement and export the following function:</span></span>  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="65a60-124">__declspec(dllexport) 是 Microsoft 特定的编译器扩展名。</span><span class="sxs-lookup"><span data-stu-id="65a60-124">__declspec(dllexport) is a Microsoft-specific compiler extension.</span></span> <span data-ttu-id="65a60-125">如果您的编译器不支持此指令，则应在 DEF 文件的 EXPORTS 部分之下导出此函数。</span><span class="sxs-lookup"><span data-stu-id="65a60-125">If your compiler does not support this directive, you should export this function in your DEF file under the EXPORTS section.</span></span>  
  
 <span data-ttu-id="65a60-126">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用跟踪标志 t260 开始时启动时，或者如果具有系统管理员权限的用户运行 DBCC TRACEON (260) ，并且如果扩展存储过程 DLL 不支持 __GetXpVersion ( # A3，则会出现一条警告消息 (错误8131：扩展存储过程 dll "%" 不会 \_ 将 _GetXpVersion ( # A6 打印到错误日志中。</span><span class="sxs-lookup"><span data-stu-id="65a60-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started with the trace flag -T260 or if a user with system administrator privileges runs DBCC TRACEON (260), and if the extended stored procedure DLL does not support __GetXpVersion(), a warning message (Error 8131: Extended stored procedure DLL '%' does not export \__GetXpVersion().) is printed to the error log.</span></span> <span data-ttu-id="65a60-127"> (请注意， \_ _GetXpVersion ( # A2 以两个下划线开头。 ) </span><span class="sxs-lookup"><span data-stu-id="65a60-127">(Note that \__GetXpVersion() begins with two underscores.)</span></span>  
  
 <span data-ttu-id="65a60-128">如果扩展存储过程 DLL 导出 __GetXpVersion()，但函数返回的版本低于服务器所要求的版本，则会向错误日志中打印一条警告消息，其中说明函数返回的版本和服务器预期的版本。</span><span class="sxs-lookup"><span data-stu-id="65a60-128">If the extended stored procedure DLL exports __GetXpVersion(), but the version returned by the function is less than that required by the server, a warning message stating the version returned by the function and the version expected by the server is printed to the error log.</span></span> <span data-ttu-id="65a60-129">如果收到此消息，则返回的值不是 \_ _GetXpVersion ( # A1，或者正在使用较旧版本的 srv 进行编译。</span><span class="sxs-lookup"><span data-stu-id="65a60-129">If you get this message, you are returning an incorrect value from \__GetXpVersion(), or you are compiling with an older version of srv.h.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65a60-130">SetErrorMode 是一个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 函数，不应在扩展存储过程中调用它。</span><span class="sxs-lookup"><span data-stu-id="65a60-130">SetErrorMode, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 function, should not be called in extended stored procedures.</span></span>  
  
 <span data-ttu-id="65a60-131">建议长时间运行的扩展存储过程应定期调用 srv_got_attention，以便在连接终止或批处理中止时此过程可以终止自身。</span><span class="sxs-lookup"><span data-stu-id="65a60-131">It is recommended that a long-running extended stored procedure should call srv_got_attention periodically so that the procedure can terminate itself if the connection is killed or the batch is aborted.</span></span>  
  
 <span data-ttu-id="65a60-132">若要调试扩展存储过程 DLL，请将其复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn 目录。</span><span class="sxs-lookup"><span data-stu-id="65a60-132">To debug an extended stored procedure DLL, copy it to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn directory.</span></span> <span data-ttu-id="65a60-133">若要为调试会话指定可执行文件，请输入可执行文件的路径和文件名 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (例如，C:\PROGRAM Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe) 。</span><span class="sxs-lookup"><span data-stu-id="65a60-133">To specify the executable for the debugging session, enter the path and file name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable file (for example, C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe).</span></span> <span data-ttu-id="65a60-134">有关 sqlservr.exe 参数的详细信息，请参阅[Sqlservr.exe 应用程序](../../tools/sqlservr-application.md)。</span><span class="sxs-lookup"><span data-stu-id="65a60-134">For information about sqlservr arguments, see [sqlservr Application](../../tools/sqlservr-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a60-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65a60-135">See Also</span></span>  
 [<span data-ttu-id="65a60-136">扩展存储过程 API srv_got_attention &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="65a60-136">srv_got_attention &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
