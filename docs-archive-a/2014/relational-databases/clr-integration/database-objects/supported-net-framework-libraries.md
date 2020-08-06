---
title: 支持的 .NET Framework 库 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f92e3eadccc869452cf35534f786724c8e259a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576823"
---
# <a name="supported-net-framework-libraries"></a><span data-ttu-id="e2a7d-102">支持的 .NET Framework 库</span><span class="sxs-lookup"><span data-stu-id="e2a7d-102">Supported .NET Framework Libraries</span></span>
  <span data-ttu-id="e2a7d-103">借助驻留在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的公共语言运行时 (CLR)，您可以采用托管代码创作存储过程、触发器、用户定义函数、用户定义类型和用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-103">With the common language runtime (CLR) hosted in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="e2a7d-104">利用 .NET Framework 类库中的功能，您可以访问提供字符串操作、高级数学运算、文件访问和密码系统等功能的预建类。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-104">With the functionality found in the .NET Framework class libraries, you have access to pre-built classes that provide functionality for string manipulation, advanced math operations, file access, cryptography, and more.</span></span> <span data-ttu-id="e2a7d-105">可通过任何托管存储过程、用户定义类型、触发器、用户定义函数或用户定义聚合访问这些类。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-105">These classes can be accessed from any managed stored procedure, user-defined type, trigger, user-defined function, or user-defined aggregate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2a7d-106">如果在全局程序集缓存中服务或升级不受支持的程序集 (GAC) ，则为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-106">If you service or upgrade unsupported assemblies in the global assembly cache (GAC), your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e2a7d-107">如果程序集在 CLR 集成中同时存在，则为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-107">If an assembly exists both in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span> <span data-ttu-id="e2a7d-108">如果在 GAC 中提供服务或升级的任何程序集（包括不支持的 .NET Framework 程序集）同时已在数据库中注册，请确保使用 `ALTER ASSEMBLY` 语句对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中的程序集副本同时提供相应服务或升级。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-108">If you service or upgrade any assemblies in the GAC that are also registered in the database, including unsupported .NET Framework assemblies, make sure to also service or upgrade the copy of the assembly inside your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases with the `ALTER ASSEMBLY` statement.</span></span> <span data-ttu-id="e2a7d-109">有关详细信息，请参阅[知识库文章 949080](https://support.microsoft.com/kb/949080)。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-109">For more information, see [Knowledge Base article 949080](https://support.microsoft.com/kb/949080).</span></span>  
  
## <a name="supported-libraries"></a><span data-ttu-id="e2a7d-110">支持的库</span><span class="sxs-lookup"><span data-stu-id="e2a7d-110">Supported Libraries</span></span>  
 <span data-ttu-id="e2a7d-111">从开始 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] ，提供了受支持的 .NET Framework 库列表，已经过测试，可确保它们满足与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 从全局程序集缓存中直接从全局程序集缓存加载它们的可靠性和安全性标准 (GAC) 。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-111">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] has a list of supported .NET Framework libraries, which have been tested to ensure that they meet reliability and security standards for interaction with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads them directly from the Global Assembly Cache (GAC).</span></span>  
  
 <span data-ttu-id="e2a7d-112">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，CLR 集成支持的库/命名空间包括：</span><span class="sxs-lookup"><span data-stu-id="e2a7d-112">The libraries/namespaces supported by CLR integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="e2a7d-113">CustomMarshalers</span><span class="sxs-lookup"><span data-stu-id="e2a7d-113">CustomMarshalers</span></span>  
  
-   <span data-ttu-id="e2a7d-114">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="e2a7d-114">Microsoft.VisualBasic</span></span>  
  
-   <span data-ttu-id="e2a7d-115">Microsoft.VisualC</span><span class="sxs-lookup"><span data-stu-id="e2a7d-115">Microsoft.VisualC</span></span>  
  
-   <span data-ttu-id="e2a7d-116">mscorlib</span><span class="sxs-lookup"><span data-stu-id="e2a7d-116">mscorlib</span></span>  
  
-   <span data-ttu-id="e2a7d-117">System</span><span class="sxs-lookup"><span data-stu-id="e2a7d-117">System</span></span>  
  
-   <span data-ttu-id="e2a7d-118">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="e2a7d-118">System.Configuration</span></span>  
  
-   <span data-ttu-id="e2a7d-119">System.Data</span><span class="sxs-lookup"><span data-stu-id="e2a7d-119">System.Data</span></span>  
  
-   <span data-ttu-id="e2a7d-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="e2a7d-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="e2a7d-121">System.Data.SqlXml</span><span class="sxs-lookup"><span data-stu-id="e2a7d-121">System.Data.SqlXml</span></span>  
  
-   <span data-ttu-id="e2a7d-122">System.Deployment</span><span class="sxs-lookup"><span data-stu-id="e2a7d-122">System.Deployment</span></span>  
  
-   <span data-ttu-id="e2a7d-123">System.Security</span><span class="sxs-lookup"><span data-stu-id="e2a7d-123">System.Security</span></span>  
  
-   <span data-ttu-id="e2a7d-124">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="e2a7d-124">System.Transactions</span></span>  
  
-   <span data-ttu-id="e2a7d-125">System.Web.Services</span><span class="sxs-lookup"><span data-stu-id="e2a7d-125">System.Web.Services</span></span>  
  
-   <span data-ttu-id="e2a7d-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e2a7d-126">System.Xml</span></span>  
  
-   <span data-ttu-id="e2a7d-127">System.Core.dll</span><span class="sxs-lookup"><span data-stu-id="e2a7d-127">System.Core.dll</span></span>  
  
-   <span data-ttu-id="e2a7d-128">System.Xml.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="e2a7d-128">System.Xml.Linq.dll</span></span>  
  
## <a name="unsupported-libraries"></a><span data-ttu-id="e2a7d-129">不支持的库</span><span class="sxs-lookup"><span data-stu-id="e2a7d-129">Unsupported Libraries</span></span>  
 <span data-ttu-id="e2a7d-130">通过托管存储过程、触发器、用户定义函数、用户定义类型和用户定义聚合仍可以调用不支持的库。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-130">Unsupported libraries can still be called from your managed stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates.</span></span> <span data-ttu-id="e2a7d-131">必须首先使用 `CREATE ASSEMBLY` 语句在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中注册不支持的库，然后才能在代码中使用它们。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-131">The unsupported library must first be registered in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, using the `CREATE ASSEMBLY` statement, before it can be used in your code.</span></span> <span data-ttu-id="e2a7d-132">对于在服务器上注册和运行的任何不支持的库，应检查和测试其安全性和可靠性。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-132">Any unsupported library that is registered and run on the server should be reviewed and tested for security and reliability.</span></span>  
  
 <span data-ttu-id="e2a7d-133">例如，不支持 `System.DirectoryServices` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-133">For example, the `System.DirectoryServices` namespace is not supported.</span></span> <span data-ttu-id="e2a7d-134">您必须使用 `UNSAFE` 权限注册 System.DirectoryServices.dll 程序集，然后才能从代码中调用它。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-134">You must register the System.DirectoryServices.dll assembly with `UNSAFE` permissions before you can call it from your code.</span></span> <span data-ttu-id="e2a7d-135">`UNSAFE` 权限是必需的，这是因为 `System.DirectoryServices` 命名空间中的类不满足 `SAFE` 或 `EXTERNAL_ACCESS` 要求。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-135">The `UNSAFE` permission is necessary because classes in the `System.DirectoryServices` namespace do not meet the requirements for `SAFE` or `EXTERNAL_ACCESS`.</span></span> <span data-ttu-id="e2a7d-136">有关详细信息，请参阅[Clr 集成编程模型限制](clr-integration-programming-model-restrictions.md)和[Clr 集成代码访问安全性](../security/clr-integration-code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-136">For more information, see [CLR Integration Programming Model Restrictions](clr-integration-programming-model-restrictions.md) and [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a7d-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2a7d-137">See Also</span></span>  
 <span data-ttu-id="e2a7d-138">[创建程序集](../assemblies/creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="e2a7d-138">[Creating an Assembly](../assemblies/creating-an-assembly.md) </span></span>  
 <span data-ttu-id="e2a7d-139">[CLR 集成代码访问安全性](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="e2a7d-139">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 [<span data-ttu-id="e2a7d-140">CLR 集成编程模型限制</span><span class="sxs-lookup"><span data-stu-id="e2a7d-140">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
  
  
