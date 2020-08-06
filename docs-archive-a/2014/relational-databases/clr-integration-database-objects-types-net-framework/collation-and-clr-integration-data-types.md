---
title: 排序规则和 CLR 集成数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a5b0367487aeb80355b8c5c976818e1b6c1ac04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693981"
---
# <a name="collation-and-clr-integration-data-types"></a><span data-ttu-id="6a1bc-102">排序规则和 CLR 集成数据类型</span><span class="sxs-lookup"><span data-stu-id="6a1bc-102">Collation and CLR Integration Data Types</span></span>
  <span data-ttu-id="6a1bc-103">在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中，`CompareInfo` 对象处理排序规则。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-103">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], the `CompareInfo` object handles collations.</span></span> <span data-ttu-id="6a1bc-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 字符串应用程序编程接口 (API) 使用与当前线程的 `CompareInfo` 对象关联的 `CultureInfo` 属性来执行字符串比较。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-104">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] string application programming interfaces (APIs) use the `CompareInfo` property associated with the `CultureInfo` object of the current thread to perform string comparisons.</span></span> <span data-ttu-id="6a1bc-105">对象的默认设置 `CultureInfo` 基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 运行的计算机的 Windows 区域设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-105">The default setting of the `CultureInfo` object is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows locale setting for the computer on which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="6a1bc-106">该设置在未显式指定 `CultureInfo` 的情况下确定比较 `System.String` 值的默认比较语义。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-106">This determines the default comparison semantics, if no explicit `CultureInfo` is specified, for comparisons of `System.String` values.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6a1bc-107">不会显式更改数据库或服务器排序规则的 `CompareInfo` 属性</span><span class="sxs-lookup"><span data-stu-id="6a1bc-107">does not explicitly change the `CompareInfo` property to the database or server collation.</span></span> <span data-ttu-id="6a1bc-108">用户必须根据需要在其例程中设置相应的 `CompareInfo` 属性。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-108">If required, users must set the appropriate `CompareInfo` property in their routines.</span></span>  
  
## <a name="parameter-collation"></a><span data-ttu-id="6a1bc-109">参数排序规则</span><span class="sxs-lookup"><span data-stu-id="6a1bc-109">Parameter Collation</span></span>  
 <span data-ttu-id="6a1bc-110">当创建公共语言运行时 (CLR) 例程时，如果绑定到该例程的 CLR 方法的参数类型为 `SQLString`，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 则创建一个参数实例，该实例采用包含调用例程的数据库的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-110">When you create a common language runtime (CLR) routine, and a parameter of a CLR method bound to the routine is of type `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates an instance of the parameter with the default collation of the database containing the calling routine.</span></span> <span data-ttu-id="6a1bc-111">如果参数不是 `SqlType`（例如，该类型为 `String` 而不是 `SQLString`），数据库的排序规则信息则不与该参数关联。</span><span class="sxs-lookup"><span data-stu-id="6a1bc-111">If a parameter is not a `SqlType` (for example, `String` rather than `SQLString`), the collation information from the database is not associated with the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1bc-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a1bc-112">See Also</span></span>  
 [<span data-ttu-id="6a1bc-113">.NET Framework 中的 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="6a1bc-113">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
