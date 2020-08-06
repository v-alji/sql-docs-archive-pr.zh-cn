---
title: CEILING（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd2f9f455226925d6bf00842e80a8713e6c72771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591487"
---
# <a name="ceiling-ssis-expression"></a>CEILING（SSIS 表达式）
  返回大于或等于数值表达式的最小整数。  
  
## <a name="syntax"></a>语法  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression*  
 有效的数值表达式。  
  
## <a name="result-types"></a>结果类型  
 提交给函数的数值表达式的数据类型。  
  
## <a name="remarks"></a>备注  
 如果参数为空，则 CEILING 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 这些示例对正值、负值和零值应用 CEILING 函数。  
  
```  
CEILING(123.74)  
```  
  
 返回 124.00  
  
```  
CEILING(-124.27)  
```  
  
 返回 -124.00  
  
```  
CEILING(0.00)  
```  
  
 返回 0.00  
  
## <a name="see-also"></a>另请参阅  
 [FLOOR（SSIS 表达式）](floor-ssis-expression.md)   
 [函数（SSIS 表达式）](functions-ssis-expression.md)  
  
  
