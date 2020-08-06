---
title: SQLTablePrivileges |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: rothja
ms.author: jroth
ms.openlocfilehash: 63298330d3f0ebf707dbb42c337553c1f363deab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586656"
---
# <a name="sqltableprivileges"></a><span data-ttu-id="24040-102">SQLTablePrivileges</span><span class="sxs-lookup"><span data-stu-id="24040-102">SQLTablePrivileges</span></span>
  <span data-ttu-id="24040-103">可以对静态游标执行**SQLTablePrivileges** 。</span><span class="sxs-lookup"><span data-stu-id="24040-103">**SQLTablePrivileges** can be executed on a static cursor.</span></span> <span data-ttu-id="24040-104">尝试在可更新 (键集驱动或动态) 上执行**SQLTablePrivileges**会返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="24040-104">An attempt to execute **SQLTablePrivileges** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="24040-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过接受由两部分组成的*CatalogName*参数的名称来支持链接服务器上表的报告信息： *Linked_Server_Name。 Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="24040-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24040-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24040-106">See Also</span></span>  
 <span data-ttu-id="24040-107">[SQLTablePrivileges 函数] (https://go.microsoft.com/fwlink/?LinkId=59373\)</span><span class="sxs-lookup"><span data-stu-id="24040-107">[SQLTablePrivileges Function](https://go.microsoft.com/fwlink/?LinkId=59373\)</span></span>   
 [<span data-ttu-id="24040-108">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="24040-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
