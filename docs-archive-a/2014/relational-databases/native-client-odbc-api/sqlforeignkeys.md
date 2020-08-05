---
title: SQLForeignKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: rothja
ms.author: jroth
ms.openlocfilehash: a61e80867abb8ecb4d2628b74dc9956051c8e4ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580272"
---
# <a name="sqlforeignkeys"></a><span data-ttu-id="4b0d5-102">SQLForeignKeys</span><span class="sxs-lookup"><span data-stu-id="4b0d5-102">SQLForeignKeys</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4b0d5-103">通过外键约束机制支持级联更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-103">supports cascading updates and deletes through the foreign key constraint mechanism.</span></span> <span data-ttu-id="4b0d5-104">如果在 FOREIGN KEY 约束的 ON UPDATE 和/或 ON DELETE 子句中指定 CASCADE 选项，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将为 UPDATE_RULE 和/或 DELETE_RULE 列返回 SQL_CASCADE。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns SQL_CASCADE for UPDATE_RULE and/or DELETE_RULE columns if CASCADE option is specified on the ON UPDATE and/or ON DELETE clause of the FOREIGN KEY constraints.</span></span> <span data-ttu-id="4b0d5-105">如果未在 FOREIGN KEY 约束的 ON UPDATE 和/或 ON DELETE 子句中指定 NO ACTION 选项，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 则为 UPDATE_RULE 和/或 DELETE_RULE 列返回 SQL_NO_ACTION。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns SQL_NO_ACTION for UPDATE_RULE and/or DELETE_RULE columns if NO ACTION option is specified on the ON UPDATE and/or ON DELETE clause of the FOREIGN KEY constraints.</span></span>  
  
 <span data-ttu-id="4b0d5-106">当任何**SQLForeignKeys**参数中存在无效值时， **SQLForeignKeys**将在执行时返回 SQL_SUCCESS。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-106">When invalid values are present in any **SQLForeignKeys** parameter, **SQLForeignKeys** returns SQL_SUCCESS on execution.</span></span> <span data-ttu-id="4b0d5-107">当在这些参数中使用了无效值时， **SQLFetch**将返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-107">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="4b0d5-108">可以对静态服务器游标执行**SQLForeignKeys** 。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-108">**SQLForeignKeys** can be executed on a static server cursor.</span></span> <span data-ttu-id="4b0d5-109">尝试对可更新的 (动态或键集) 游标执行**SQLForeignKeys**返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-109">An attempt to execute **SQLForeignKeys** on an updatable (dynamic or keyset) cursor returns SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="4b0d5-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序支持链接服务器上表的报告信息，方法是接受由两部分组成的*FKCatalogName*和*PKCatalogName*参数的名称： *Linked_Server_Name。 Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="4b0d5-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *FKCatalogName* and *PKCatalogName* parameters: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0d5-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b0d5-111">See Also</span></span>  
 <span data-ttu-id="4b0d5-112">[SQLForeignKeys 函数](https://go.microsoft.com/fwlink/?LinkId=59344) </span><span class="sxs-lookup"><span data-stu-id="4b0d5-112">[SQLForeignKeys Function](https://go.microsoft.com/fwlink/?LinkId=59344) </span></span>  
 [<span data-ttu-id="4b0d5-113">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="4b0d5-113">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
