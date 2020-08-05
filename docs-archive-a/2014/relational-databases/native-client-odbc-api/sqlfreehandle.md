---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
ms.openlocfilehash: f51f031bec05715e0345507278113f4f16179a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580709"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  在手动提交模式中，对具有打开的事务的语句句柄调用**SQLFreeHandle**会导致对数据库的挂起的更改回滚。 对语句句柄调用**SQLFreeHandle**将始终关闭任何打开的游标，并放弃挂起的结果，释放与该语句句柄关联的所有资源。  
  
## <a name="see-also"></a>另请参阅  
 [SQLFreeHandle 函数](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC API 实现细节](odbc-api-implementation-details.md)  
  
  
