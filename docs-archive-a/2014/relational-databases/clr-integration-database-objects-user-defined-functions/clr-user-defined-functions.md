---
title: CLR 用户定义函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: ba7a4a983ec0cb36ef0fd79df44491f7f23f7648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589148"
---
# <a name="clr-user-defined-functions"></a><span data-ttu-id="2bef1-102">CLR 用户定义函数</span><span class="sxs-lookup"><span data-stu-id="2bef1-102">CLR User-Defined Functions</span></span>
  <span data-ttu-id="2bef1-103">用户定义函数是可采用参数、执行计算或其他操作并返回结果的例程。</span><span class="sxs-lookup"><span data-stu-id="2bef1-103">User-defined functions are routines that can take parameters, perform calculations or other actions, and return a result.</span></span> <span data-ttu-id="2bef1-104">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，可以使用任何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 编程语言（例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#）编写用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="2bef1-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can write user-defined functions in any [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework programming language, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="2bef1-105">有两种类型的函数：标量，用于返回单个值；表值，用于返回一组行。</span><span class="sxs-lookup"><span data-stu-id="2bef1-105">There are two types of functions: scalar, which returns a single value, and table-valued, which returns a set of rows.</span></span>  
  
 <span data-ttu-id="2bef1-106">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="2bef1-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="2bef1-107">CLR 标量值函数</span><span class="sxs-lookup"><span data-stu-id="2bef1-107">CLR Scalar-Valued Functions</span></span>](clr-scalar-valued-functions.md)  
 <span data-ttu-id="2bef1-108">包含标量值函数的实现要求和示例。</span><span class="sxs-lookup"><span data-stu-id="2bef1-108">Covers implementation requirements and examples of scalar-valued functions.</span></span>  
  
 [<span data-ttu-id="2bef1-109">CLR 表值函数</span><span class="sxs-lookup"><span data-stu-id="2bef1-109">CLR Table-Valued Functions</span></span>](clr-table-valued-functions.md)  
 <span data-ttu-id="2bef1-110">讨论如何实现和使用表值函数 (TVF)，以及 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和公共语言运行时 (CLR) TVF 的区别。</span><span class="sxs-lookup"><span data-stu-id="2bef1-110">Discusses how to implement and use table-valued functions (TVFs), as well as differences between [!INCLUDE[tsql](../../includes/tsql-md.md)] and common language runtime (CLR) TVFs.</span></span>  
  
 [<span data-ttu-id="2bef1-111">CLR 用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="2bef1-111">CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates.md)  
 <span data-ttu-id="2bef1-112">说明如何实现和使用用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="2bef1-112">Describes how to implement and use user-defined aggregates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bef1-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2bef1-113">See Also</span></span>  
 [<span data-ttu-id="2bef1-114">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="2bef1-114">User-Defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)  
  
  
