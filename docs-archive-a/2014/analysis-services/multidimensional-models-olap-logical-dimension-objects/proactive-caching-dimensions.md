---
title: ) 的主动缓存 (维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50c723d46b6c51fae0ccc227b5e58cf96f72c7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578500"
---
# <a name="proactive-caching-dimensions"></a>主动缓存（维度）
  可以利用主动缓存自动创建 MOLAP 缓存以及管理 OLAP 对象。 多维数据集可利用收自数据库的通知，立即合并对数据库中数据所做的更改。 主动缓存的目标是提供传统 MOLAP 所具有的性能，并同时保持使用 ROLAP 进行管理所具有的方便和快捷。  
  
 简单 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象由计时规范和表通知组成。 计时规范定义收到更改通知后更新缓存的时间范围。 表通知定义数据表和 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象之间的通知架构。  
  
  
