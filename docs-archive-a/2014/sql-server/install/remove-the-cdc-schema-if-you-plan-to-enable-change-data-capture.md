---
title: 如果计划启用变更数据捕获，则删除 cdc 架构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abdb33fa3d1ff022a65ed569f19d48bcf4468501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588844"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a><span data-ttu-id="d60ad-102">如果计划启用变更数据捕获则删除 cdc 架构</span><span class="sxs-lookup"><span data-stu-id="d60ad-102">Remove the cdc schema if you plan to enable change data capture</span></span>
  <span data-ttu-id="d60ad-103">数据库已经包含一个 cdc 架构。</span><span class="sxs-lookup"><span data-stu-id="d60ad-103">A database already contains a cdc schema.</span></span> <span data-ttu-id="d60ad-104">如果计划在升级后启用变更数据捕获，则必须先删除此 cdc 架构。</span><span class="sxs-lookup"><span data-stu-id="d60ad-104">If you plan to enable change data capture after upgrade, you must first drop this cdc schema.</span></span> <span data-ttu-id="d60ad-105">当对数据库启用变更数据捕获时，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]将创建一个名为 cdc 的新架构。</span><span class="sxs-lookup"><span data-stu-id="d60ad-105">When you enable a database for change data capture, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create a new schema named cdc.</span></span>  
  
  
