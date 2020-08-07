---
title: 删除存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 418e68d4bb7c6ba6632767a554aea72e85726840
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590097"
---
# <a name="delete-a-stored-procedure"></a><span data-ttu-id="af845-102">删除存储过程</span><span class="sxs-lookup"><span data-stu-id="af845-102">Delete a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="af845-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除存储过程。</span><span class="sxs-lookup"><span data-stu-id="af845-103">This topic describes how to delete a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="af845-104">**开始之前：** [限制和局限](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="af845-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="af845-105">要删除该过程，请使用：[SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="af845-105">**To delete a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af845-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="af845-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="af845-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="af845-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="af845-108">如果依赖对象和脚本尚未更新以反映过程的删除，则删除过程可能会导致这些对象和脚本失败。</span><span class="sxs-lookup"><span data-stu-id="af845-108">Deleting a procedure can cause dependent objects and scripts to fail when the objects and scripts are not updated to reflect the removal of the procedure.</span></span> <span data-ttu-id="af845-109">但是，如果创建了具有相同名称和参数的新过程来替换已被删除的过程，那么引用该过程的其他对象仍能成功处理。</span><span class="sxs-lookup"><span data-stu-id="af845-109">However, if a new procedure of the same name and the same parameters is created to replace the one that was deleted, other objects that reference it will still process successfully.</span></span> <span data-ttu-id="af845-110">有关详细信息，请参阅 [查看存储过程的依赖关系](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="af845-110">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af845-111">Security</span><span class="sxs-lookup"><span data-stu-id="af845-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af845-112">权限</span><span class="sxs-lookup"><span data-stu-id="af845-112">Permissions</span></span>  
 <span data-ttu-id="af845-113">需要拥有对该过程所属架构的 ALTER 权限，或对该过程的 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="af845-113">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span>  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="af845-114">如何删除存储过程</span><span class="sxs-lookup"><span data-stu-id="af845-114">How to Delete a Stored Procedure</span></span>  
 <span data-ttu-id="af845-115">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="af845-115">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="af845-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af845-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="af845-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af845-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af845-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af845-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="af845-119">**在对象资源管理器中删除过程**</span><span class="sxs-lookup"><span data-stu-id="af845-119">**To delete a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="af845-120">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="af845-120">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="af845-121">展开 **“数据库”** 、过程所属的数据库以及 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="af845-121">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="af845-122">展开“存储过程”，右键单击要删除的过程，再单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="af845-122">Expand **Stored Procedures**, right-click the procedure to remove, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="af845-123">若要查看依赖于过程的对象，请单击 **“显示依赖关系”** 。</span><span class="sxs-lookup"><span data-stu-id="af845-123">To view objects that depend on the procedure, click **Show Dependencies**.</span></span>  
  
5.  <span data-ttu-id="af845-124">确认选择了正确的过程，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="af845-124">Confirm the correct procedure is selected, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="af845-125">从所有依赖对象和脚本中删除对该过程的引用。</span><span class="sxs-lookup"><span data-stu-id="af845-125">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af845-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af845-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="af845-127">**在查询编辑器中删除过程**</span><span class="sxs-lookup"><span data-stu-id="af845-127">**To delete a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="af845-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="af845-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="af845-129">展开 **“数据库”** 、过程所属的数据库，或者从工具栏，从可用数据库列表选择该数据库。</span><span class="sxs-lookup"><span data-stu-id="af845-129">Expand **Databases**, expand the database in which the procedure belongs, or, from the tool bar, select the database from the list of available databases.</span></span>  
  
3.  <span data-ttu-id="af845-130">在“文件”菜单上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="af845-130">On the File menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="af845-131">获取要在当前数据库中删除的存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="af845-131">Obtain the name of stored procedure to remove in the current database.</span></span> <span data-ttu-id="af845-132">从对象资源管理器，展开 **“可编程性”** ，再展开 **“存储过程”** 。</span><span class="sxs-lookup"><span data-stu-id="af845-132">From Object Explorer, expand **Programmability** and then expand **Stored Procedures**.</span></span> <span data-ttu-id="af845-133">或者，在查询编辑器中，运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="af845-133">Alternatively, in the query editor, run the following statement.</span></span>  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  <span data-ttu-id="af845-134">将以下示例复制并粘贴到查询编辑器，然后插入要从当前数据库中删除的存储过程名称。</span><span class="sxs-lookup"><span data-stu-id="af845-134">Copy and paste the following example into the query editor and insert a stored procedure name to delete from the current database.</span></span>  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  <span data-ttu-id="af845-135">从所有依赖对象和脚本中删除对该过程的引用。</span><span class="sxs-lookup"><span data-stu-id="af845-135">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af845-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af845-136">See Also</span></span>  
 <span data-ttu-id="af845-137">[创建存储过程](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="af845-137">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="af845-138">[修改存储过程](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="af845-138">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="af845-139">[重命名存储过程](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="af845-139">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="af845-140">[查看存储过程的定义](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="af845-140">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="af845-141">[查看存储过程的依赖关系](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="af845-141">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="af845-142">DROP PROCEDURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="af845-142">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
