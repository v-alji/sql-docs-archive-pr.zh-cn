---
title: 游标类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: rothja
ms.author: jroth
ms.openlocfilehash: 6937dbb9ce42cd5631201e0c97be42b211742ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580270"
---
# <a name="cursor-types"></a><span data-ttu-id="91680-102">游标类型</span><span class="sxs-lookup"><span data-stu-id="91680-102">Cursor Types</span></span>
  <span data-ttu-id="91680-103">ODBC 定义 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序支持的四种游标类型。</span><span class="sxs-lookup"><span data-stu-id="91680-103">ODBC defines four cursor types supported by Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="91680-104">这些游标的功能不同于检测对结果集及其消耗的资源（如**tempdb**中的内存和空间）的更改。</span><span class="sxs-lookup"><span data-stu-id="91680-104">These cursors vary in their ability to detect changes to the result set and in the resources they consume, such as memory and space in **tempdb**.</span></span> <span data-ttu-id="91680-105">游标仅当尝试重新提取行时才会检测到对这些行的更改；数据源无法通知游标对当前提取行的更改。</span><span class="sxs-lookup"><span data-stu-id="91680-105">A cursor can detect changes to rows only when it tries to refetch those rows; there is no way for the data source to notify the cursor of changes to the currently fetched rows.</span></span> <span data-ttu-id="91680-106">游标检测并非由游标执行的更改的功能也受事务隔离级别的影响。</span><span class="sxs-lookup"><span data-stu-id="91680-106">A cursor's ability to detect changes that were not made through the cursor is also influenced by the transaction isolation level.</span></span>  
  
 <span data-ttu-id="91680-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持以下四种 ODBC 游标类型：</span><span class="sxs-lookup"><span data-stu-id="91680-107">These are the four ODBC cursor types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="91680-108">只进游标不支持滚动；它们只支持游标按从头到尾的顺序提取行。</span><span class="sxs-lookup"><span data-stu-id="91680-108">Forward-only cursors do not support scrolling; they only support fetching rows serially from the start to the end of the cursor.</span></span>  
  
-   <span data-ttu-id="91680-109">静态游标在打开游标时在**tempdb**中生成。</span><span class="sxs-lookup"><span data-stu-id="91680-109">Static cursors are built in **tempdb** when the cursor is opened.</span></span> <span data-ttu-id="91680-110">它们始终显示打开游标时的结果集。</span><span class="sxs-lookup"><span data-stu-id="91680-110">They always display the result set as it was when the cursor was opened.</span></span> <span data-ttu-id="91680-111">它们从不会反映对数据的更改。</span><span class="sxs-lookup"><span data-stu-id="91680-111">They never reflect changes to the data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="91680-112">静态游标始终是只读的。</span><span class="sxs-lookup"><span data-stu-id="91680-112">static cursors are always read-only.</span></span> <span data-ttu-id="91680-113">由于静态服务器游标是在**tempdb**中作为工作表生成的，因此游标结果集的大小不能超过所允许的最大行大小 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="91680-113">Because a static server cursor is built as a work table in **tempdb**, the size of the cursor result set cannot exceed the maximum row size allowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="91680-114">打开由键集驱动的游标时，该游标的结果集中各行的成员身份和顺序是固定的。</span><span class="sxs-lookup"><span data-stu-id="91680-114">Keyset-driven cursors have the membership and order of rows in the result set fixed when the cursor is opened.</span></span> <span data-ttu-id="91680-115">可通过游标显示对非键列的更改。</span><span class="sxs-lookup"><span data-stu-id="91680-115">Changes to nonkey columns are visible through the cursor.</span></span>  
  
-   <span data-ttu-id="91680-116">动态游标与静态游标相对。</span><span class="sxs-lookup"><span data-stu-id="91680-116">Dynamic cursors are the opposite of static cursors.</span></span> <span data-ttu-id="91680-117">动态游标反映对结果集中的行的所有更改。</span><span class="sxs-lookup"><span data-stu-id="91680-117">Dynamic cursors reflect all changes made to the rows in their result set.</span></span> <span data-ttu-id="91680-118">结果集中的行数据值、顺序和成员在每次提取时都会改变。</span><span class="sxs-lookup"><span data-stu-id="91680-118">The data values, order, and membership of the rows in the result set can change on each fetch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91680-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91680-119">See Also</span></span>  
 [<span data-ttu-id="91680-120">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="91680-120">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
