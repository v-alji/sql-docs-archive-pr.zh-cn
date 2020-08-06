---
title: SQL Server 数据挖掘外接 () 离群值 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92dddf3338d15e700576a13476ee364696bfd274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694605"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>离群值（SQL Server 数据挖掘外接程序）
  ![“数据挖掘”功能区中的离群值向导](media/dmc-outliers.gif "“数据挖掘”功能区中的离群值向导")  
  
 *离群*值是指由于以下任一原因而出现问题的数据值：  
  
-   值超出预期的范围。  
  
-   数据输入可能有误。  
  
-   缺少值。  
  
-   数据包含空格或其他 Null 字符串。  
  
-   值是准确的，但与分布范围相距甚远，以致无法显著影响模型。  
  
 Excel 数据挖掘客户端能帮助您检测这种数据，然后更新值或取消值。 例如，可将离群值替换为算术平均值，也可删除可能有错的值所在的行。  
  
## <a name="handling-outliers"></a>处理离群值  
 "**删除离群**值" 向导提供了几种适当处理离群值的工具：  
  
-   首先，可以浏览数据以便更好了解值的分布以及离群值与其他数据之间的关系。  
  
     例如，您可以使用 "**浏览数据**" 任务来查看和修复这些值。 "**删除离群**值" 向导还会显示一个图表，该图可以是线条图或条形图，以帮助你了解所有值的分布情况。  
  
-   接下来，可以使用**离群**值向导删除或更改离群值。 使用的方法取决于值是离散的还是连续的。  
  
     该向导在条形图中显示离散值，其中的每个条都表示一个特定的值，条的高度指示每个值的事例数。 对于表示远离分布中心的值组或可能错误的值组的条，可通过滑动条形图上的阈值控件来切断这些条。  
  
-   该向导在条形图或折线图上显示连续值。 在折线图中，值在 X 轴上表示，值的计数在 Y 轴上表示。  
  
     您可以通过更改**最小**值和最大值，或滑动条形，来控制是在图表的低端和**最大**端删除还是保留值。 更改最小值和最大值设置时，要被取消的数据在图表中以阴影显示。  
  
 选择了要处理的离群值之后，可以设置向导如何处理这些离群值。 您可以删除包含离群值的行，或者指定替换值，例如平均值、Null 或其他选择值。  
  
 最后，向导为您提供多种显示新数据的方式。 您可以将原始数据替换为新值，在表中添加包含新值的新列，或者创建包含更新数据的新工作表。  
  
### <a name="using-the-outlier-wizard"></a>使用离群值向导  
  
1.  在 "**数据挖掘**" 功能区中，单击 "**清理数据**"，然后选择**离群**值。  
  
2.  在 "**选择源数据**" 对话框中，选择一个 Excel 数据表或一系列单元格，然后单击 "**下一步**"。  
  
    > [!WARNING]  
    >  不能对外部数据使用**离群**值向导，除非先将该数据复制到 Excel。  
  
3.  在 "**选择列**" 对话框中，选择**单个**列。  
  
     单击“下一步”。  
  
4.  在 "**指定阈值**" 对话框中，查看数据的分布情况。  
  
    -   如果该列含有离散值，则向导显示一个直方图，其中含有每个离散值的数量。  
  
         假设离群值为罕见值，则可以通过更改 "**最小**值" 来筛选它们。  
  
    -   如果列中包含数值数据，则可以在条形图或折线图中，单击 "**以离散形式显示视图**" 或 "**按数值显示视图**"，以在查看条形图或折线图中的值之间进行切换。  
  
5.  在 "**指定阈值**" 对话框中，通过键入最小值和最大值，或者通过拖动滑块来选择想要保留的数据的范围。 单击“下一步”。  
  
6.  在 "**离群处理**" 对话框中，指定是否要删除或替换值，然后单击 "**下一步**"。  
  
7.  在 "**选择目标**" 对话框中，指定要保存新数据的位置。  
  
### <a name="related-options"></a>相关选项  
 该向导提供以下选项：  
  
|**选项**|**注释**|  
|-----------------|-----------------|  
|**选择列**|一次只能处理一列。|  
|**指定阈值处理**|使用 "**最小**值" 设置阈值以排除比阈值更少的行中发现的值。<br /><br /> 最初，**最小**值等于最小行数的值，并且不能使小于该值的最小值。|  
|**离群值处理**|如果决定删除离群值，则可更改当前工作表中的数据，也可在新工作表中创建数据的副本。|  
  
## <a name="see-also"></a>另请参阅  
 [浏览数据挖掘外接 &#40;SQL Server 数据&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  