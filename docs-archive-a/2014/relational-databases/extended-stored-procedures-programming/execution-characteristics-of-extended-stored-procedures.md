---
title: 扩展存储过程的执行特征 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.openlocfilehash: edbd73797699d65f694e91bc3035e0dc9366c9d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578217"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a><span data-ttu-id="2ed82-102">扩展存储过程的执行特征</span><span class="sxs-lookup"><span data-stu-id="2ed82-102">Execution Characteristics of Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="2ed82-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="2ed82-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="2ed82-104">执行扩展存储过程具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="2ed82-104">The execution of an extended stored procedure has these characteristics:</span></span>  
  
-   <span data-ttu-id="2ed82-105">扩展存储过程函数在的安全上下文中执行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2ed82-105">The extended stored procedure function is executed under the security context of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2ed82-106">扩展存储过程函数在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的进程空间中运行。</span><span class="sxs-lookup"><span data-stu-id="2ed82-106">The extended stored procedure function runs in the process space of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2ed82-107">与执行扩展存储过程关联的线程和用于客户端连接的线程相同。</span><span class="sxs-lookup"><span data-stu-id="2ed82-107">The thread associated with the execution of the extended stored procedure is the same one used for the client connection.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2ed82-108">在将扩展存储过程添加到服务器和授予其他用户执行权限之前，系统管理员应该彻底检查每个扩展存储过程以确保它不含有有害的或恶意的代码。</span><span class="sxs-lookup"><span data-stu-id="2ed82-108">Before adding extended stored procedures to the server and granting execute permissions to other users, the system administrator should thoroughly review each extended stored procedure to make sure that it does not contain harmful or malicious code.</span></span>  
  
-  
  
 <span data-ttu-id="2ed82-109">加载扩展存储过程 DLL 后，DLL 将在服务器的地址空间中保持加载状态，直到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 停止或管理员使用 DBCC *DLL_NAME* (免费) 显式卸载 DLL。</span><span class="sxs-lookup"><span data-stu-id="2ed82-109">After the extended stored procedure DLL is loaded, the DLL remains loaded in the address space of the server until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is stopped or the administrator explicitly unloads the DLL by using DBCC *DLL_name* (FREE).</span></span>  
  
 <span data-ttu-id="2ed82-110">使用 EXECUTE 语句，可以通过 [!INCLUDE[tsql](../../includes/tsql-md.md)] 将扩展存储过程作为存储过程来执行：</span><span class="sxs-lookup"><span data-stu-id="2ed82-110">The extended stored procedure can be executed from [!INCLUDE[tsql](../../includes/tsql-md.md)] as a stored procedure by using the EXECUTE statement:</span></span>  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ed82-111">参数</span><span class="sxs-lookup"><span data-stu-id="2ed82-111">Parameters</span></span>  
 <span data-ttu-id="2ed82-112">\@ *retval*</span><span class="sxs-lookup"><span data-stu-id="2ed82-112">\@ *retval*</span></span>  
 <span data-ttu-id="2ed82-113">为返回值。</span><span class="sxs-lookup"><span data-stu-id="2ed82-113">Is a return value.</span></span>  
  
 <span data-ttu-id="2ed82-114">\@*param1*</span><span class="sxs-lookup"><span data-stu-id="2ed82-114">\@ *param1*</span></span>  
 <span data-ttu-id="2ed82-115">输入参数。</span><span class="sxs-lookup"><span data-stu-id="2ed82-115">Is an input parameter.</span></span>  
  
 <span data-ttu-id="2ed82-116">\@*param2*</span><span class="sxs-lookup"><span data-stu-id="2ed82-116">\@ *param2*</span></span>  
 <span data-ttu-id="2ed82-117">输入/输出参数。</span><span class="sxs-lookup"><span data-stu-id="2ed82-117">Is an input/output parameter.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2ed82-118">扩展存储过程提供性能增强功能，并扩展了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="2ed82-118">Extended stored procedures offer performance enhancements and extend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="2ed82-119">但是，由于扩展存储过程 DLL 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共享相同的地址空间，发生问题的过程可能反过来影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 运行。</span><span class="sxs-lookup"><span data-stu-id="2ed82-119">However, because the extended stored procedure DLL and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] share the same address space, a problem procedure can adversely affect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functioning.</span></span> <span data-ttu-id="2ed82-120">虽然扩展存储过程 DLL 引发的异常是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处理的，但是仍可能损坏 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据区域。</span><span class="sxs-lookup"><span data-stu-id="2ed82-120">Although exceptions thrown by the extended stored procedure DLL are handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible to damage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data areas.</span></span> <span data-ttu-id="2ed82-121">作为一种安全预防措施，只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员才能向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 添加扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="2ed82-121">As a security precaution, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrators can add extended stored procedures to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2ed82-122">应彻底测试这些过程，然后才能进行安装。</span><span class="sxs-lookup"><span data-stu-id="2ed82-122">These procedures should be thoroughly tested before they are installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed82-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ed82-123">See Also</span></span>  
 <span data-ttu-id="2ed82-124">[扩展存储过程编程](database-engine-extended-stored-procedures-programming.md) </span><span class="sxs-lookup"><span data-stu-id="2ed82-124">[Programming Extended Stored Procedures](database-engine-extended-stored-procedures-programming.md) </span></span>  
 [<span data-ttu-id="2ed82-125">查询 SQL Server 中安装的扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="2ed82-125">Querying Extended Stored Procedures Installed in SQL Server</span></span>](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
