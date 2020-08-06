---
title: 管理文本和图像列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d7d5b0f48c68e8ac911f5e274c9afdb8cfe17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693805"
---
# <a name="managing-text-and-image-columns"></a><span data-ttu-id="9e730-102">管理 Text 和 Image 列</span><span class="sxs-lookup"><span data-stu-id="9e730-102">Managing Text and Image Columns</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9e730-103">**text**、 **ntext**和**image**数据 (也称为长数据) 是可以保存数据值太大，无法放入**char**、 **varchar**、 **binary**或**varbinary**列的字符或二进制字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="9e730-103">**text**, **ntext**, and **image** data (also referred to as long data) are character or binary string data types that can hold data values too large to fit into **char**, **varchar**, **binary**, or **varbinary** columns.</span></span> <span data-ttu-id="9e730-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text**数据类型映射到 ODBC SQL_LONGVARCHAR 数据类型;**ntext**映射到 SQL_WLONGVARCHAR;和**图像**映射到 SQL_LONGVARBINARY。</span><span class="sxs-lookup"><span data-stu-id="9e730-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **text** data type maps to the ODBC SQL_LONGVARCHAR data type; **ntext** maps to SQL_WLONGVARCHAR; and **image** maps to SQL_LONGVARBINARY.</span></span> <span data-ttu-id="9e730-105">某些数据项（例如很长的文档或大位图）可能因太大而无法在内存中合理存储。</span><span class="sxs-lookup"><span data-stu-id="9e730-105">Some data items, such as long documents or large bitmaps, may be too large to store reasonably in memory.</span></span> <span data-ttu-id="9e730-106">若要从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连续部分中检索长数据， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序允许应用程序调用[SQLGetData](../native-client-odbc-api/sqlgetdata.md)。</span><span class="sxs-lookup"><span data-stu-id="9e730-106">To retrieve long data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in sequential parts, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to call [SQLGetData](../native-client-odbc-api/sqlgetdata.md).</span></span> <span data-ttu-id="9e730-107">若要以连续部分发送长数据，应用程序可以调用[SQLPutData](../native-client-odbc-api/sqlputdata.md)。</span><span class="sxs-lookup"><span data-stu-id="9e730-107">To send long data in sequential parts, the application can call [SQLPutData](../native-client-odbc-api/sqlputdata.md).</span></span> <span data-ttu-id="9e730-108">在执行时发送其数据的参数称为执行时数据参数。</span><span class="sxs-lookup"><span data-stu-id="9e730-108">Parameters for which data is sent at execution time are known as data-at-execution parameters.</span></span>  
  
 <span data-ttu-id="9e730-109">尽管只能在部分中发送或检索**字符**和**二进制**数据，但应用程序实际上可以使用**SQLPutData**或**SQLGetData**来写入或检索任何类型的数据， (不只是长数据) 。</span><span class="sxs-lookup"><span data-stu-id="9e730-109">An application can actually write or retrieve any type of data (not just long data) with **SQLPutData** or **SQLGetData**, although only **character** and **binary** data can be sent or retrieved in parts.</span></span> <span data-ttu-id="9e730-110">但是，如果数据太小，足以容纳在单个缓冲区中，通常没有理由使用**SQLPutData**或**SQLGetData**。</span><span class="sxs-lookup"><span data-stu-id="9e730-110">However, if the data is small enough to fit in a single buffer, there is generally no reason to use **SQLPutData** or **SQLGetData**.</span></span> <span data-ttu-id="9e730-111">将单一缓冲区绑定到参数或列更简单。</span><span class="sxs-lookup"><span data-stu-id="9e730-111">It is much easier to bind the single buffer to the parameter or column.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e730-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="9e730-112">In This Section</span></span>  
  
-   [<span data-ttu-id="9e730-113">绑定与未绑定的 Text 和 Image 列</span><span class="sxs-lookup"><span data-stu-id="9e730-113">Bound vs. Unbound Text and Image Columns</span></span>](bound-vs-unbound-text-and-image-columns.md)  
  
-   [<span data-ttu-id="9e730-114">有日志记录的修改与无日志记录的修改</span><span class="sxs-lookup"><span data-stu-id="9e730-114">Logged vs. Unlogged Modifications</span></span>](logged-vs-unlogged-modifications.md)  
  
-   [<span data-ttu-id="9e730-115">执行时数据和 Text、ntext 或 Image 列</span><span class="sxs-lookup"><span data-stu-id="9e730-115">Data-at-Execution and Text, ntext, or Image Columns</span></span>](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e730-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e730-116">See Also</span></span>  
 [<span data-ttu-id="9e730-117">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="9e730-117">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
