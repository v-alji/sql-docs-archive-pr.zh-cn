---
title: 编写扩展存储过程的编程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- gateway applications [SQL Server]
- extended stored procedures [SQL Server], about extended stored procedures
- Open Data Services [SQL Server]
- ODS [SQL Server]
ms.assetid: 561305cd-c803-48af-9eec-2c19f4d311ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 30792cc2b431e35a8f7df5ff7bbb2c228892d5c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589095"
---
# <a name="programming-extended-stored-procedures"></a><span data-ttu-id="81616-102">编写扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="81616-102">Programming Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="81616-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="81616-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="81616-104">过去，程序员使用开放式数据服务编写服务器应用程序，比如到非 SQL 服务器数据库环境的网关。</span><span class="sxs-lookup"><span data-stu-id="81616-104">In the past, Open Data Services was used to write server applications, such as gateways to non-SQL Server database environments.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="81616-105">不 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持开放式数据服务 API 已过时的部分。</span><span class="sxs-lookup"><span data-stu-id="81616-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support the obsolete portions of the Open Data Services API.</span></span> <span data-ttu-id="81616-106">在原始的开放式数据服务 API 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仍然支持的唯一部分是扩展存储过程函数，因此该 API 已重命名为扩展存储过程 API。</span><span class="sxs-lookup"><span data-stu-id="81616-106">The only part of the original Open Data Services API still supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are the extended stored procedure functions, so the API has been renamed to the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="81616-107">随着诸如分布式查询和 CLR 集成这样更新和功能更强大的技术的出现，对扩展存储过程 API 应用程序的需求已大幅减少。</span><span class="sxs-lookup"><span data-stu-id="81616-107">With the emergence of newer and more powerful technologies, such as distributed queries and CLR Integration, the need for Extended Stored Procedure API applications has largely been replaced.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81616-108">如果您有现成的网关应用程序，则无法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 附带的 opends60.dll 运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="81616-108">If you have existing gateway applications, you cannot use the opends60.dll that ships with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run the applications.</span></span> <span data-ttu-id="81616-109">网关应用程序不再受支持。</span><span class="sxs-lookup"><span data-stu-id="81616-109">Gateway applications are no longer supported.</span></span>  
  
## <a name="extended-stored-procedures-vs-clr-integration"></a><span data-ttu-id="81616-110">扩展存储过程与 CLR 集成的对比</span><span class="sxs-lookup"><span data-stu-id="81616-110">Extended Stored Procedures vs. CLR Integration</span></span>  
 <span data-ttu-id="81616-111">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本中，当数据库应用程序开发人员要编写那些很难表达或不可能用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 编写的服务器端逻辑时，扩展存储过程 (XP) 为其提供了唯一的机制。</span><span class="sxs-lookup"><span data-stu-id="81616-111">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], extended stored procedures (XPs) provided the only mechanism that was available for database application developers to write server-side logic that was either hard to express or impossible to write in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="81616-112">CLR 集成为编写这样的存储过程提供了更可靠的替代选择。</span><span class="sxs-lookup"><span data-stu-id="81616-112">CLR Integration provides a more robust alternative to writing such stored procedures.</span></span> <span data-ttu-id="81616-113">此外，通过使用 CLR 集成，过去经常以存储过程的形式编写的逻辑现在通常可以更好地表达为表值函数，这样就可以将 SELECT 语句嵌入 FROM 子句中从而使用该 SELECT 语句对该函数所构造的结果进行查询。</span><span class="sxs-lookup"><span data-stu-id="81616-113">Furthermore, with CLR Integration, logic that used to be written in the form of stored procedures is often better expressed as table-valued functions, which allow the results constructed by the function to be queried in SELECT statements by embedding them in the FROM clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81616-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81616-114">See Also</span></span>  
 <span data-ttu-id="81616-115">[公共语言运行时 &#40;CLR&#41; 集成概述](../clr-integration/common-language-runtime-integration-overview.md) </span><span class="sxs-lookup"><span data-stu-id="81616-115">[Common Language Runtime &#40;CLR&#41; Integration Overview](../clr-integration/common-language-runtime-integration-overview.md) </span></span>  
 [<span data-ttu-id="81616-116">CLR 表值函数</span><span class="sxs-lookup"><span data-stu-id="81616-116">CLR Table-Valued Functions</span></span>](../clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
  
  
