---
title: 已记录无日志记录修改 |Microsoft Docs
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
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8768acc75d18ea2236f0e9280e5d0c805e688107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693808"
---
# <a name="logged-vs-unlogged-modifications"></a><span data-ttu-id="cfc8f-102">有日志记录的修改与无日志记录的修改</span><span class="sxs-lookup"><span data-stu-id="cfc8f-102">Logged vs. Unlogged Modifications</span></span>
  <span data-ttu-id="cfc8f-103">应用程序可以请求 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序不记录**text**、 **ntext**和**image**修改。</span><span class="sxs-lookup"><span data-stu-id="cfc8f-103">An application can request that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver not log **text**, **ntext**, and **image** modifications.</span></span> <span data-ttu-id="cfc8f-104">但应慎用此选项。</span><span class="sxs-lookup"><span data-stu-id="cfc8f-104">Care should be used with this option, however.</span></span> <span data-ttu-id="cfc8f-105">它仅适用于**文本**、 **ntext**或**图像**数据不重要的情况，数据所有者愿意权衡恢复数据以提高性能的能力。</span><span class="sxs-lookup"><span data-stu-id="cfc8f-105">It should be used only for those situations where the **text**, **ntext**, or **image** data is not critical and data owners are willing to trade off the ability to recover data for higher performance.</span></span>  
  
 <span data-ttu-id="cfc8f-106">通过调用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)并将*属性*参数设置为 SQL_SOPT_SS_ TEXTPTR_LOGGING 并将*将 valueptr*设置为 SQL_TL_ON 或 SQL_TL_OFF，可以控制**text**、 **ntext**和**image**修改的日志记录。</span><span class="sxs-lookup"><span data-stu-id="cfc8f-106">The logging of **text**, **ntext**, and **image** modifications is controlled by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with the *Attribute* parameter set to SQL_SOPT_SS_ TEXTPTR_LOGGING and *ValuePtr* set to either SQL_TL_ON or SQL_TL_OFF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc8f-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cfc8f-107">See Also</span></span>  
 [<span data-ttu-id="cfc8f-108">管理 Text 和 Image 列</span><span class="sxs-lookup"><span data-stu-id="cfc8f-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
