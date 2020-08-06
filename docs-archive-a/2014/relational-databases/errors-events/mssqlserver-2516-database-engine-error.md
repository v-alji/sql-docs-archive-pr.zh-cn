---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be0809b3560d94bb883cf3a4acfa3d2c484b8b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687919"
---
# <a name="mssqlserver_2516"></a>MSSQLSERVER_2516
    
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2516|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|消息正文|修复操作已经使数据库 NAME 的差异位图无效。 差异备份链断开。 必须首先执行完全数据库备份，才能执行差异备份。|  
  
## <a name="explanation"></a>说明  
 在修复错误 MSSQLEngine_2515 时返回了此信息性消息。  
  
## <a name="user-action"></a>用户操作  
 执行一次完整数据库备份。  
  
## <a name="see-also"></a>另请参阅  
 [创建完整数据库备份 (SQL Server)](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
