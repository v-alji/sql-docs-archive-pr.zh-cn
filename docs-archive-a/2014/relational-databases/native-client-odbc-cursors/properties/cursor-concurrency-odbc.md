---
title: ODBC)  (游标并发 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: rothja
ms.author: jroth
ms.openlocfilehash: c47f24152978fedf8f2c3d49ec3b721969712814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589041"
---
# <a name="cursor-concurrency-odbc"></a>游标并发 (ODBC)
  和游标类型一样，游标操作也受应用程序设置的并发选项的影响。 并发选项是使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_CONCURRENCY 选项设置的。 并发类型包括：  
  
-   只读 (SQL_CONCUR_READONLY)  
  
-   值 (SQL_CONCUR_VALUES)  
  
-   行版本 (SQL_CONCUR_ROWVER)  
  
-   锁 (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>另请参阅  
 [游标属性](cursor-properties.md)  
  
  
