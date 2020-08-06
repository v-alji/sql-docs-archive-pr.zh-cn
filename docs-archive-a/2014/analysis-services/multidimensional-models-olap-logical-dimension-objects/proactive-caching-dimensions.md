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
# <a name="proactive-caching-dimensions"></a><span data-ttu-id="9256b-102">主动缓存（维度）</span><span class="sxs-lookup"><span data-stu-id="9256b-102">Proactive Caching (Dimensions)</span></span>
  <span data-ttu-id="9256b-103">可以利用主动缓存自动创建 MOLAP 缓存以及管理 OLAP 对象。</span><span class="sxs-lookup"><span data-stu-id="9256b-103">Proactive caching provides automatic MOLAP cache creation and management for OLAP objects.</span></span> <span data-ttu-id="9256b-104">多维数据集可利用收自数据库的通知，立即合并对数据库中数据所做的更改。</span><span class="sxs-lookup"><span data-stu-id="9256b-104">The cubes immediately incorporate changes that are made to the data in the database, based upon notifications received from the database.</span></span> <span data-ttu-id="9256b-105">主动缓存的目标是提供传统 MOLAP 所具有的性能，并同时保持使用 ROLAP 进行管理所具有的方便和快捷。</span><span class="sxs-lookup"><span data-stu-id="9256b-105">The goal of proactive caching is to provide the performance of traditional MOLAP, while retaining the immediacy and ease of management offered by ROLAP.</span></span>  
  
 <span data-ttu-id="9256b-106">简单 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象由计时规范和表通知组成。</span><span class="sxs-lookup"><span data-stu-id="9256b-106">A simple <xref:Microsoft.AnalysisServices.ProactiveCaching> object is composed of: timing specification, and table notification.</span></span> <span data-ttu-id="9256b-107">计时规范定义收到更改通知后更新缓存的时间范围。</span><span class="sxs-lookup"><span data-stu-id="9256b-107">The timing specification defines the timeframe for updating the cache after a change notification has been received.</span></span> <span data-ttu-id="9256b-108">表通知定义数据表和 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象之间的通知架构。</span><span class="sxs-lookup"><span data-stu-id="9256b-108">The table notification defines the notification schema between the data table and the <xref:Microsoft.AnalysisServices.ProactiveCaching> object.</span></span>  
  
  
