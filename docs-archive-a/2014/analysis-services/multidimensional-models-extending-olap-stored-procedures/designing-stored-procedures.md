---
title: 设计存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b33873d6bdf28f7f702bcf186d681f57d6024d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689654"
---
# <a name="designing-stored-procedures"></a><span data-ttu-id="3a0c7-102">设计存储过程</span><span class="sxs-lookup"><span data-stu-id="3a0c7-102">Designing Stored Procedures</span></span>
  <span data-ttu-id="3a0c7-103">管理对象模型 Analysis Management Objects (AMO) 和面向客户端的对象模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® 数据对象（多维）(ADO MD) 在存储过程中都可用。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-103">Both the administrative object model Analysis Management Objects (AMO) and the client oriented object model [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (Multidimensional) (ADO MD) are available in stored procedures.</span></span>  
  
 <span data-ttu-id="3a0c7-104">存储过程必须在作用域（服务器或数据库）内，才可以在要调用的多维表达式 (MDX) 级别中可见。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-104">Stored procedures must be in scope (either the server or the database) to be visible at the Multidimensional Expressions (MDX) level to be called.</span></span> <span data-ttu-id="3a0c7-105">但是，调用存储过程后，它的作用域将不再限于其父级下的操作。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-105">However, once a stored procedure is invoked, its scope is not limited to actions under its parent.</span></span> <span data-ttu-id="3a0c7-106">存储过程可能会在服务器的任何位置进行更改或修改，并且只有调用它的用户进程的安全性会对其进行限制，或者只有它所操作的事务对其进行限制。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-106">A stored procedure may make changes or modifications anywhere on the server, subject only to the security limitations of the user process that invokes it or to the limitations of the transaction in which it is operating.</span></span>  
  
 <span data-ttu-id="3a0c7-107">在服务器的所有上下文中，服务器作用域过程都是可用的。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-107">Server scope procedures are available in all contexts on the server.</span></span> <span data-ttu-id="3a0c7-108">数据库作用域存储过程只在定义它们的数据库的数据库上下文中是可见的。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-108">Database scope stored procedures are visible only in the database context of the database in which they are defined.</span></span>  
  
 <span data-ttu-id="3a0c7-109">与任何 MDX 函数一样，必须先解析存储过程，然后 MDX 会话才能继续；存储过程在执行时将锁定 MDX 会话。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-109">As with any MDX function, stored procedure must be resolved before an MDX session can continue; stored procedures lock MDX sessions while executing.</span></span> <span data-ttu-id="3a0c7-110">除非出于特定的原因要停止 MDX 会话，以挂起用户交互，否则禁止进行用户交互（例如，对话框）。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-110">Unless a specific reason exists to halt an MDX session pending user interaction, then user interactions (such as dialog boxes) are discouraged.</span></span>  
  
## <a name="dependent-assemblies"></a><span data-ttu-id="3a0c7-111">依赖程序集</span><span class="sxs-lookup"><span data-stu-id="3a0c7-111">Dependent Assemblies</span></span>  
 <span data-ttu-id="3a0c7-112">必须将所有依赖程序集加载到公共语言运行时 (CLR) 要查找的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-112">All dependent assemblies must be loaded into an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to be found by the common language runtime (CLR).</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3a0c7-113">将依赖程序集存储在与主程序集相同的文件夹中，因此 CLR 将自动解析针对这些程序集中函数的所有函数引用。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-113">stores the dependent assemblies in the same folder as the main assembly, so the CLR automatically resolves all function references to functions in those assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0c7-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a0c7-114">See Also</span></span>  
 <span data-ttu-id="3a0c7-115">[多维模型程序集管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="3a0c7-115">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="3a0c7-116">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="3a0c7-116">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
