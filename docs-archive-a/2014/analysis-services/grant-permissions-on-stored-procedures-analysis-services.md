---
title: 授予对存储过程的权限 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13d75ca8b6ff6e7d482e9d69894091518aa9469e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580450"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a><span data-ttu-id="8656c-102">授予对存储过程的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8656c-102">Grant permissions on stored procedures (Analysis Services)</span></span>
  <span data-ttu-id="8656c-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中的存储过程或程序集是使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET 编程语言编写的外部例程，扩展了 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="8656c-103">Stored procedures, or assemblies, in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] are external routines, written in a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET programming language, that extend the capabilities of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8656c-104">通过程序集，开发人员可以利用跨语言集成、异常处理、版本支持、部署支持以及调试支持。</span><span class="sxs-lookup"><span data-stu-id="8656c-104">Assemblies let the developer take advantage of cross-language integration, exception handling, versioning support, deployment support, and debugging support.</span></span>  
  
 <span data-ttu-id="8656c-105">你必须是服务器管理员才能注册程序集。</span><span class="sxs-lookup"><span data-stu-id="8656c-105">You must be a Server Administrator to register an assembly.</span></span> <span data-ttu-id="8656c-106">请参阅[&#40;Analysis Services&#41;授予服务器管理员权限](instances/grant-server-admin-rights-to-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="8656c-106">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
## <a name="security-context-for-stored-procedure-execution"></a><span data-ttu-id="8656c-107">存储过程执行的安全上下文</span><span class="sxs-lookup"><span data-stu-id="8656c-107">Security context for stored procedure execution</span></span>  
 <span data-ttu-id="8656c-108">任何用户都可以调用存储过程。</span><span class="sxs-lookup"><span data-stu-id="8656c-108">Any user can call a stored procedure.</span></span> <span data-ttu-id="8656c-109">根据存储过程配置方式的不同，该过程既可以在调用它的用户的上下文中运行，也可以在匿名用户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="8656c-109">Depending on how the stored procedure was configured, the procedure can run either in the context of the user calling the procedure or in the context of an anonymous user.</span></span> <span data-ttu-id="8656c-110">由于匿名用户没有安全上下文，因此可使用此功能将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例配置为允许进行匿名访问。</span><span class="sxs-lookup"><span data-stu-id="8656c-110">Because an anonymous user has no security context, use this capability together with configuring the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to permit anonymous access.</span></span>  
  
 <span data-ttu-id="8656c-111">在用户调用存储过程之后但在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 运行存储过程之前，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会评估存储过程内的操作。</span><span class="sxs-lookup"><span data-stu-id="8656c-111">After the user calls a stored procedure but before [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] runs the stored procedure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] evaluates the actions within the stored procedure.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="8656c-112">根据授予用户的权限和用于运行过程的权限集的交集来评估存储过程内的操作。</span><span class="sxs-lookup"><span data-stu-id="8656c-112">evaluates the actions in a stored procedure based on the intersection of the permissions granted to the user and the permission set used to run the procedure.</span></span> <span data-ttu-id="8656c-113">如果存储过程包含任意无法由用户的数据库角色执行的操作，则不会执行该操作。</span><span class="sxs-lookup"><span data-stu-id="8656c-113">If the stored procedure contains any action that cannot be performed by the database role for the user, that action will not be performed.</span></span>  
  
 <span data-ttu-id="8656c-114">下面便是用于运行存储过程的权限集：</span><span class="sxs-lookup"><span data-stu-id="8656c-114">Following are the permission sets that are used to run stored procedures:</span></span>  
  
-   <span data-ttu-id="8656c-115">**Safe**使用 Safe 权限集，存储过程无法访问 .NET Framework 中的受保护资源 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8656c-115">**Safe** With the Safe permission set, a stored procedure cannot access the protected resources in the [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="8656c-116">此权限集仅允许执行计算。</span><span class="sxs-lookup"><span data-stu-id="8656c-116">This permission set only allows for computations.</span></span> <span data-ttu-id="8656c-117">它是最安全的权限集；不会将信息泄露到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 之外，不能评估权限，并且最大限度地减低了数据篡改攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="8656c-117">This is the safest permission set; information does not leak outside [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], permissions cannot be elevated, and the risk of data tampering attacks is minimized.</span></span>  
  
-   <span data-ttu-id="8656c-118">**外部访问**使用外部访问权限集，存储过程可以使用托管代码访问外部资源。</span><span class="sxs-lookup"><span data-stu-id="8656c-118">**External Access** With the External Access permission set, a stored procedure can access external resources by using managed code.</span></span> <span data-ttu-id="8656c-119">将存储过程设置为此权限集不会导致可引起服务器不稳定的编程错误。</span><span class="sxs-lookup"><span data-stu-id="8656c-119">Setting a stored procedure to this permission set will not cause programming errors that could lead to server instability.</span></span> <span data-ttu-id="8656c-120">但是，此权限集可能导致信息泄露到服务器之外，并可能导致权限提升以及数据篡改攻击。</span><span class="sxs-lookup"><span data-stu-id="8656c-120">However, this permission set may result in information leaking outside the server, and the possibility of an elevation in permission and data tampering attacks.</span></span>  
  
-   <span data-ttu-id="8656c-121">**无限制**使用无限制权限集，存储过程可以使用任何代码访问外部资源。</span><span class="sxs-lookup"><span data-stu-id="8656c-121">**Unrestricted** With the Unrestricted permission set, a stored procedure can access external resources by using any code.</span></span> <span data-ttu-id="8656c-122">在使用此权限集时，存储过程没有安全性或可靠性保证。</span><span class="sxs-lookup"><span data-stu-id="8656c-122">With this permission set, there are no security or reliability guarantees for stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8656c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8656c-123">See Also</span></span>  
 [<span data-ttu-id="8656c-124">多维模型程序集管理</span><span class="sxs-lookup"><span data-stu-id="8656c-124">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
