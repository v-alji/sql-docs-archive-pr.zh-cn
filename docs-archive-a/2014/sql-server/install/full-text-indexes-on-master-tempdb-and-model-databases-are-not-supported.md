---
title: 不支持对 master、tempdb 和 model 数据库建立全文索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591742"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>不支持对 master、tempdb 和 model 数据库建立全文检索
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许对任何系统数据库建立全文检索。  
  
## <a name="description"></a>说明  
 在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，支持对 master、tempdb 和 model 数据库建立全文索引。  
  
 在升级过程中，将删除 master、tempdb 和 model 数据库中的所有全文目录。  
  
## <a name="see-also"></a>另请参阅  
 [使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
