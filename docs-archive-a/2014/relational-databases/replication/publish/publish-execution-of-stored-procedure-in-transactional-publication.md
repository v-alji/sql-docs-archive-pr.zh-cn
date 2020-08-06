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
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a><span data-ttu-id="17864-102">在事务发布中发布存储过程的执行 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="17864-102">Publish the Execution of a Stored Procedure in a Transactional Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="17864-103">可在“项目属性 - \<Article>”对话框中指定应发布存储过程执行情况（而不仅仅是其定义）。</span><span class="sxs-lookup"><span data-stu-id="17864-103">Specify that the execution of a stored procedure (rather than just its definition) should be published in the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="17864-104">“新建发布”向导和“发布属性 - \<Publication>”对话框中提供了该对话框。</span><span class="sxs-lookup"><span data-stu-id="17864-104">This dialog box is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="17864-105">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="17864-105">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="17864-106">初始化订阅时，过程定义（CREATE PROCEDURE 语句）将被复制到订阅服务器上；当在发布服务器上执行过程时，复制将在订阅服务器上执行相应的过程。</span><span class="sxs-lookup"><span data-stu-id="17864-106">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span>  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a><span data-ttu-id="17864-107">发布存储过程的执行</span><span class="sxs-lookup"><span data-stu-id="17864-107">To publish the execution of a stored procedure</span></span>  
  
1.  <span data-ttu-id="17864-108">在“新建发布”向导或“发布属性 - \<Publication>”对话框的“项目”页面上，选择一个存储过程 。</span><span class="sxs-lookup"><span data-stu-id="17864-108">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a stored procedure.</span></span>  
  
2.  <span data-ttu-id="17864-109">单击 **“项目属性”** ，然后单击 **“设置突出显示的存储过程项目的属性”** 。</span><span class="sxs-lookup"><span data-stu-id="17864-109">Click **Article Properties**, and then click **Set Properties of Highlighted Stored Procedure**.</span></span>  
  
3.  <span data-ttu-id="17864-110">在“项目属性 - \<Article>”对话框中，为“复制”选项指定下列值之一 ：</span><span class="sxs-lookup"><span data-stu-id="17864-110">In the **Article Properties - \<Article>** dialog box, specify one of the following values for the **Replicate** option:</span></span>  
  
    -   <span data-ttu-id="17864-111">**存储过程的执行**</span><span class="sxs-lookup"><span data-stu-id="17864-111">**Execution of the stored procedure**</span></span>  
  
    -   <span data-ttu-id="17864-112">**SP 的序列化事务中的执行**</span><span class="sxs-lookup"><span data-stu-id="17864-112">**Execution in a serialized transaction of the SP**</span></span>  
  
         <span data-ttu-id="17864-113">建议选择此选项，因为此选项仅当过程在可序列化事务的上下文中执行时才复制过程的执行。</span><span class="sxs-lookup"><span data-stu-id="17864-113">This is the recommended option, because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="17864-114">如果存储过程在可序列化事务的外部执行，则已发布表中的数据更改将复制为一系列数据操作语言 (DML) 语句。</span><span class="sxs-lookup"><span data-stu-id="17864-114">If the stored procedure is executed outside of a serializable transaction, changes to data in published tables are replicated as a series of data manipulation language (DML) statements.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="17864-115">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="17864-115">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17864-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17864-116">See Also</span></span>  
 [<span data-ttu-id="17864-117">在事务复制中发布存储过程执行</span><span class="sxs-lookup"><span data-stu-id="17864-117">Publishing Stored Procedure Execution in Transactional Replication</span></span>](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
