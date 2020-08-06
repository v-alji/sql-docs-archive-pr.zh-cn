---
title: 系统数据库中的对称密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 28e25ae3-d3dc-45ec-b316-f219512a1a47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 81c657ededc694ed87df99e0739ff74b1eb9e39b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590735"
---
# <a name="symmetric-keys-on-system-databases"></a>系统数据库中的对称密钥
  此规则检查 master、msdb、model 和 tempdb 数据库中是否存在用户创建的对称密钥。  
  
## <a name="best-practices-recommendations"></a>最佳做法建议  
 请勿在系统数据库中创建对称密钥。  
  
## <a name="for-more-information"></a>有关详细信息  
 [选择加密算法](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>另请参阅  
 [使用基于策略的管理来监视和强制执行最佳做法](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
