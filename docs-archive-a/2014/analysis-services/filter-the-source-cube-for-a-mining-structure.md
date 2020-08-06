---
title: 筛选挖掘结构的源多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61409b4803f43d3ff2634daaba65a92bc343db36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579180"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>筛选挖掘结构的源多维数据集
  在创建基于多维模型中的数据 (OLAP 多维数据集) 的挖掘结构时，您可以对该挖掘结构所基于的多维数据集进行*切片*。 通过切片操作可创建数据子集，作为用于给挖掘模型定型的数据的一种筛选器。  
  
### <a name="to-slice-a-cube"></a>对多维数据集进行切片  
  
1.  在的数据挖掘设计器中 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，选择 "**挖掘结构**" 选项卡或 "**挖掘模型**" 选项卡。  
  
2.  在 "**挖掘模型**" 菜单上，选择 "**定义挖掘结构多维数据集切片**"。  
  
     此时将打开 "**切片多维数据集**" 对话框。  
  
3.  在 "**切片多维数据集**" 对话框的 "**维度**" 列中，选择要筛选的维度。  
  
4.  使用 "**层次结构**" 列中的列表选择层次结构的级别。  
  
5.  从 "**运算符**" 列的列表中选择一个运算符，以便在生成筛选条件时使用。  
  
6.  单击 "**筛选器**" 列中的框。  
  
     此时将打开包含层次结构指定级别中的所有成员的对话框。  
  
7.  选择您要进行筛选的成员。  
  
8.  在 "成员" 对话框中单击 **"确定"** 。  
  
9. 在 "**切片多维数据集**" 对话框中单击 **"确定"** 。  
  
     现在根据多维数据集切片的定义对源多维数据集进行筛选。  
  
## <a name="see-also"></a>另请参阅  
 [挖掘结构任务和操作指南](data-mining/mining-structure-tasks-and-how-tos.md)   
 [创建新的 OLAP 挖掘结构](data-mining/create-a-new-olap-mining-structure.md)  
  
  
