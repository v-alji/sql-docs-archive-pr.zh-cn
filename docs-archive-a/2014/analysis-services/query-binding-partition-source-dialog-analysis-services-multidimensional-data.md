---
title: 查询绑定详细信息 (分区源 "对话框中)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59d2ae1fed9d22366786e21a287a621f08418a5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586991"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>查询绑定详细信息（“分区源”对话框）（Analysis Services - 多维数据）
  可以使用 **“分区源”** 对话框中的 **“查询绑定”** 选项指定为分区提供数据的查询。 通过从 **“分区源”** 对话框中的 **“绑定类型”** 选项中选择 **“查询绑定”** ，可以显示此窗格。  
  
## <a name="options"></a>选项  
 **数据源**  
 选择要对其执行查询的数据源，以便为分区提供事实数据。  
  
 **查询**  
 键入或修改在处理分区过程中检索事实数据时所使用的 SQL 语句。  
  
> [!IMPORTANT]  
>  通过指定 WHERE 子句，可以将记录的子集用于此分区。 当多个分区都基于单一事实数据表时，防止数据重复很重要。 有关详细信息，请参阅 "[分区源" 对话框 &#40;Analysis Services 多维数据&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)。  
  
 **检查**  
 单击此项可以验证“查询”**** 中的语句是否为有效的 SQL 语句。  
  
## <a name="see-also"></a>另请参阅  
 ["分区源" 对话框 &#40;Analysis Services 多维数据&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
