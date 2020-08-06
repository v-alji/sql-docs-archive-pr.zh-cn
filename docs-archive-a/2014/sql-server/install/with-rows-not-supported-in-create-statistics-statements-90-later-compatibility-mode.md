---
title: 在90或更高版本的兼容模式下，CREATE STATISTICS 语句中不支持 WITH ROWS |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d28a05e7cd025e213e2cebdce9d582a9df446fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586082"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>在 90 或更高的兼容模式下，CREATE STATISTICS 语句中不支持 WITH ROWS
  当运行兼容模式设置为 90 或更高的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，不支持在 CREATE STATISTICS 语句中指定 WITH ROWS。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>纠正措施  
 通过指定带有示例*号*行或指定符合记录语法的其他选项，修改包含行的 CREATE STATISTICS 语句。 有关详细信息，请参阅 SQL Server 联机丛书中的 "CREATE STATISTICS (Transact-sql) 。  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 升级顾问 &#91;新&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
