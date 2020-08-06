---
title: 全文索引属性 (计划页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.schedule.f1
ms.assetid: a828e284-097e-4854-8c49-931934eb73bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f49fb37295f0b3eb2f1a2dd04d44ab86236f109a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591537"
---
# <a name="full-text-index-properties-schedules-page"></a>全文索引属性（“计划”页）
  使用此页可以查看和创建运行 SQL Server 代理作业的计划，该作业用于启动对全文索引基表的更新的增量填充。 如果基表或视图不包含 `timestamp` 数据类型的列，则执行完全填充。  
  
 **查看或更改全文索引的属性**  
  
-   [管理全文索引](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a>UI 元素列表  
 **计划**  
 列出全文索引的基表上的每个计划增量填充（如果有）。  
  
 **名称**  
 显示每个计划填充的名称。  
  
 **填充类型**  
 显示每个计划填充的类型。  
  
 **已启用**  
 指示当前是启用还是禁用计划填充。  
  
 **说明**  
 显示创建计划时指定的说明。  
  
 **新建**  
 单击此选项可以为填充全文索引创建新计划。  
  
## <a name="see-also"></a>另请参阅  
 [使用全文索引向导](../relational-databases/search/use-the-full-text-indexing-wizard.md)   
 [填充全文索引](../relational-databases/search/populate-full-text-indexes.md)  
  
  
