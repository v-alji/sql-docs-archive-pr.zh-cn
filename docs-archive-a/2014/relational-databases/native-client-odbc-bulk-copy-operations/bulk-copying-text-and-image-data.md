---
title: 大容量复制文本和图像数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: rothja
ms.author: jroth
ms.openlocfilehash: 9240fd0eb8c32ed39613824ea5a07764e277160c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591323"
---
# <a name="bulk-copying-text-and-image-data"></a><span data-ttu-id="ae921-102">大容量复制文本和图像数据</span><span class="sxs-lookup"><span data-stu-id="ae921-102">Bulk Copying Text and Image Data</span></span>
  <span data-ttu-id="ae921-103">使用[bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)函数大容量复制较大的**text**、 **ntext**和**image**值。</span><span class="sxs-lookup"><span data-stu-id="ae921-103">Large **text**, **ntext**, and **image** values are bulk copied using the [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) function.</span></span> <span data-ttu-id="ae921-104">为**text**、 **ntext**或**image**列编写[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) ，并将*pData*指针设置为 NULL，指示将使用**bcp_moretext**提供数据。</span><span class="sxs-lookup"><span data-stu-id="ae921-104">You code [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for the **text**, **ntext**, or **image** column with a *pData* pointer set to NULL indicating the data will be provided with **bcp_moretext**.</span></span> <span data-ttu-id="ae921-105">务必指定为每个大容量复制行中的每个**text**、 **ntext**或**image**列提供的数据的准确长度。</span><span class="sxs-lookup"><span data-stu-id="ae921-105">It is important to specify the exact length of data supplied for each **text**, **ntext**,or **image** column in each bulk-copied row.</span></span> <span data-ttu-id="ae921-106">如果列的数据长度与[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)中指定的列长度不同，则使用[bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)将长度设置为正确的值。</span><span class="sxs-lookup"><span data-stu-id="ae921-106">If the length of the data for a column is different from the column length specified in [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), use [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) to set the length to the proper value.</span></span> <span data-ttu-id="ae921-107">[Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)发送所有非**文本**、非**ntext**和非**图像**数据;然后，调用**bcp_moretext**以单独的单位发送**text**、 **ntext**或**image**数据。</span><span class="sxs-lookup"><span data-stu-id="ae921-107">A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sends all the non-**text**, non-**ntext**, and non-**image** data; you then call **bcp_moretext** to send the **text**, **ntext**, or **image** data in separate units.</span></span> <span data-ttu-id="ae921-108">大容量复制函数确定当通过**bcp_moretext**发送的数据的长度之和等于最新**bcp_collen**或**bcp_bind**中指定的长度时，已发送当前**text**、 **ntext**或**image**列的所有数据。</span><span class="sxs-lookup"><span data-stu-id="ae921-108">Bulk copy functions determine that all data has been sent for the current **text**, **ntext**, or **image** column when the sum of the lengths of data sent through **bcp_moretext** equals the length specified in the latest **bcp_collen** or **bcp_bind**.</span></span>  
  
 <span data-ttu-id="ae921-109">**bcp_moretext**没有用于标识列的参数。</span><span class="sxs-lookup"><span data-stu-id="ae921-109">**bcp_moretext** has no parameter to identify a column.</span></span> <span data-ttu-id="ae921-110">如果一行中有多个**text**、 **ntext**或**image**列， **bcp_moretext**将对以具有最低序号的列执行运算，并使用最大序号的列执行对**text**、 **ntext**或**image**列的运算。</span><span class="sxs-lookup"><span data-stu-id="ae921-110">When there are multiple **text**, **ntext**, or **image** columns in a row, **bcp_moretext** operates on the **text**, **ntext**, or **image** columns starting with the column having the lowest ordinal number and proceeding to the column with the highest ordinal number.</span></span> <span data-ttu-id="ae921-111">当发送的数据的长度与最新的 bcp_collen 中指定的长度等于当前列的最新**bcp_collen**或**bcp_bind**时， **bcp_moretext**将从一列转到下一列。</span><span class="sxs-lookup"><span data-stu-id="ae921-111">**bcp_moretext** goes from one column to the next when the sum of the lengths of data sent equals the length specified in the latest **bcp_collen** or **bcp_bind** for the current column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae921-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae921-112">See Also</span></span>  
 [<span data-ttu-id="ae921-113">&#40;ODBC&#41;执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="ae921-113">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
