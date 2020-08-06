---
title: 删除以保留 ORDPATH 数据类型命名的 UDT&#39;Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694239"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>删除以保留 ORDPATH 数据类型命名的 UDT&#39;
  升级顾问检测到根据为 `ORDPATH` 数据类型保留的术语命名的用户定义类型 (UDT)。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>说明  
 用于内置数据类型的术语不应用作公共语言运行时 (CLR) 或别名 UDT 的名称。  
  
## <a name="corrective-action"></a>纠正措施  
 删除根据数据类型命名的 UDT，并使用非保留名称重新创建 UDT。  
  
## <a name="external-resources"></a>外部资源  
 [创建用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
