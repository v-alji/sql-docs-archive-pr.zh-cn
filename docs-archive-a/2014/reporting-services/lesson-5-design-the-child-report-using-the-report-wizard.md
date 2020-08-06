---
title: 第 5 课：使用报表向导设计子报表 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f188a914fc2a2bb8370843191a31474a54c02aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578707"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>第 5 课：使用报表向导设计子报表
  创建用于子报表的数据连接和数据表后，接下来要使用报表设计器中的报表向导设计子报表。 有关报表设计器的详细信息，请参阅[使用报表设计器设计报表 (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)。  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>使用报表向导设计子报表  
  
1.  确保在“解决方案资源管理器”中选择顶级网站  。  
  
2.  右键单击该网站，然后选择“添加新项”  。  
  
3.  在 "**添加新项**" 对话框中，单击 "**报表向导**"，输入报表文件的名称，然后单击 "**添加**"。  
  
     随后将启动报表向导。  
  
4.  在 "数据**集属性**" 页的 "**数据源**" 框中，单击**DataSet2**。  
  
     随后将自动使用创建的 DataTable 更新“可用数据集”框  。  
  
5.  单击“下一步”。  
  
6.  在“排列字段”页中，执行以下操作  ：  
  
    1.  将 ProductID、PurchaseOrderID、PurchaseOrderDetailID、OrderQty、ReceivedQty、RejectedQty 和 StockedQty 从“可用字段”拖到“值”框中          。  
  
    2.  依次单击**sum (ProductID) **、Sum ** (PurchaseOrderID) **、 **sum (PurchaseOrderDetailID) **、 **Sum (OrderQty) **、 **sum (ReceivedQty) **、 **Sum (RejectedQty) **和**sum (StockedQty) **并清除**sum**选项旁边的箭头。  
  
7.  单击 "**下一步**" 两次，然后单击 "**完成**" 关闭**报表向导**。  
  
     现已创建 .rdlc 文件。 随后将在报表设计器中打开该文件。 设计图面中现在显示由您设计的 tablix。  
  
8.  打开 .rdlc 文件后，通过执行以下操作添加参数：  
  
    1.  在 "**报表数据**" 窗格中单击 "**参数**"，然后单击 "**添加参数**"。  
  
    2.  在“名称”框中输入“productid”   。  
  
    3.  确认在“数据类型”列表框中选择了“整数”   。  
  
    4.  单击“确定”。   
  
9. 保存 .rdlc 文件。  
  
## <a name="next-task"></a>下一个任务  
 您已成功地使用报表向导设计了子报表。 接下来，将向网站应用程序添加 ReportViewer 控件。  
  
  
