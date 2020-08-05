---
title: GETDATE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580796"
---
# <a name="getdate-ssis-expression"></a>GETDATE（SSIS 表达式）
  以 DT_DBTIMESTAMP 格式返回系统的当前日期。 GETDATE 函数不使用参数。  
  
> [!NOTE]  
>  GETDATE 函数的返回结果的长度为 29 个字符。  
  
## <a name="syntax"></a>语法  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>参数  
 无  
  
## <a name="result-types"></a>结果类型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>表达式示例  
 此示例返回当前日期的年份。  
  
```  
DATEPART("year",GETDATE())  
```  
  
 此示例返回 **ModifiedDate** 列中的日期和当前日期之间的天数。  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 此示例将三个月加到当前日期。  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>另请参阅  
 [GETUTCDATE（SSIS 表达式）](getutcdate-ssis-expression.md)   
 [函数（SSIS 表达式）](functions-ssis-expression.md)  
  
  
