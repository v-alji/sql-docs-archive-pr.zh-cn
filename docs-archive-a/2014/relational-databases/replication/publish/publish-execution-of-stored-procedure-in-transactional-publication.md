---
title: 在事务发布 (SQL Server Management Studio) 中发布存储过程的执行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44310d45a7049701a6aecfa73301b15b0021ac6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578795"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>在事务发布中发布存储过程的执行 (SQL Server Management Studio)
  可在“项目属性 - \<Article>”对话框中指定应发布存储过程执行情况（而不仅仅是其定义）。 “新建发布”向导和“发布属性 - \<Publication>”对话框中提供了该对话框。 有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。  
  
 初始化订阅时，过程定义（CREATE PROCEDURE 语句）将被复制到订阅服务器上；当在发布服务器上执行过程时，复制将在订阅服务器上执行相应的过程。  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>发布存储过程的执行  
  
1.  在“新建发布”向导或“发布属性 - \<Publication>”对话框的“项目”页面上，选择一个存储过程 。  
  
2.  单击 **“项目属性”** ，然后单击 **“设置突出显示的存储过程项目的属性”** 。  
  
3.  在“项目属性 - \<Article>”对话框中，为“复制”选项指定下列值之一 ：  
  
    -   **存储过程的执行**  
  
    -   **SP 的序列化事务中的执行**  
  
         建议选择此选项，因为此选项仅当过程在可序列化事务的上下文中执行时才复制过程的执行。 如果存储过程在可序列化事务的外部执行，则已发布表中的数据更改将复制为一系列数据操作语言 (DML) 语句。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。  
  
## <a name="see-also"></a>另请参阅  
 [在事务复制中发布存储过程执行](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
