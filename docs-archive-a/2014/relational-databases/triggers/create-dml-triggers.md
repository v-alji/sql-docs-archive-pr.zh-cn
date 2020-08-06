---
title: 创建 DML 触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], DML triggers
- deferred name resolution, DML triggers
- WITH ENCRYPTION clause
- IF UPDATE
- SET statement, DML triggers
- DML triggers, programming
- testing column changes
- results [SQL Server], DML triggers
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
author: rothja
ms.author: jroth
ms.openlocfilehash: f843513ba634bcb3479e373eb9ac978ab584588d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590635"
---
# <a name="create-dml-triggers"></a><span data-ttu-id="ea0c6-102">创建 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="ea0c6-102">Create DML Triggers</span></span>
  <span data-ttu-id="ea0c6-103">本主题介绍了如何通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE TRIGGER 语句来创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] DML trigger by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement.</span></span>  
  
##  <a name="before-you-begin"></a><a name="Top"></a> <span data-ttu-id="ea0c6-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="ea0c6-104">Before You Begin</span></span>  
  
### <a name="limitations-and-restrictions"></a><span data-ttu-id="ea0c6-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ea0c6-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ea0c6-106">有关与创建 DML 触发器相关的限制和局限的列表，请参阅 [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-106">For a list of limitations and restrictions related to creating DML triggers, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea0c6-107">权限</span><span class="sxs-lookup"><span data-stu-id="ea0c6-107">Permissions</span></span>  
 <span data-ttu-id="ea0c6-108">需要对要创建触发器的表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-108">Requires ALTER permission on the table or view on which the trigger is being created.</span></span>  
  
##  <a name="how-to-create-a-dml-trigger"></a><a name="Procedures"></a> <span data-ttu-id="ea0c6-109">如何创建 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="ea0c6-109">How to Create a DML Trigger</span></span>  
 <span data-ttu-id="ea0c6-110">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="ea0c6-110">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="ea0c6-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ea0c6-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="ea0c6-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ea0c6-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ea0c6-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ea0c6-113">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="ea0c6-114">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ea0c6-115">展开 **“数据库”** ，展开 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库，展开 **“表”** ，然后展开表 **Purchasing.PurchaseOrderHeader**。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, expand **Tables** and then expand the table **Purchasing.PurchaseOrderHeader**.</span></span>  
  
3.  <span data-ttu-id="ea0c6-116">右键单击“触发器”，然后选择“新建触发器”   。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-116">Right-click **Triggers**, and then select **New Trigger**.</span></span>  
  
4.  <span data-ttu-id="ea0c6-117">在 **“查询”** 菜单上，单击 **“指定模板参数的值”** 。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="ea0c6-118">或者，你可以按下 (Ctrl-Shift-M) 以便打开“指定模板参数的值”  对话框。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-118">Alternatively, you can press (Ctrl-Shift-M) to open the **Specify Values for Template Parameters** dialog box.</span></span>  
  
5.  <span data-ttu-id="ea0c6-119">在 **“指定模板参数的值”** 对话框中，输入下列所示的参数值。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-119">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="ea0c6-120">参数</span><span class="sxs-lookup"><span data-stu-id="ea0c6-120">Parameter</span></span>|<span data-ttu-id="ea0c6-121">值</span><span class="sxs-lookup"><span data-stu-id="ea0c6-121">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="ea0c6-122">作者</span><span class="sxs-lookup"><span data-stu-id="ea0c6-122">Author</span></span>|<span data-ttu-id="ea0c6-123">*您的姓名*</span><span class="sxs-lookup"><span data-stu-id="ea0c6-123">*Your name*</span></span>|  
    |<span data-ttu-id="ea0c6-124">创建日期</span><span class="sxs-lookup"><span data-stu-id="ea0c6-124">Create Date</span></span>|<span data-ttu-id="ea0c6-125">*今天的日期*</span><span class="sxs-lookup"><span data-stu-id="ea0c6-125">*Today's date*</span></span>|  
    |<span data-ttu-id="ea0c6-126">说明</span><span class="sxs-lookup"><span data-stu-id="ea0c6-126">Description</span></span>|<span data-ttu-id="ea0c6-127">在允许插入具有供应商的新采购订单之前，请检查供应商信用等级。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-127">Checks the vendor credit rating before allowing a new purchase order with the vendor to be inserted.</span></span>|  
    |<span data-ttu-id="ea0c6-128">Schema_Name</span><span class="sxs-lookup"><span data-stu-id="ea0c6-128">Schema_Name</span></span>|<span data-ttu-id="ea0c6-129">购买</span><span class="sxs-lookup"><span data-stu-id="ea0c6-129">Purchasing</span></span>|  
    |<span data-ttu-id="ea0c6-130">Trigger_Name</span><span class="sxs-lookup"><span data-stu-id="ea0c6-130">Trigger_Name</span></span>|<span data-ttu-id="ea0c6-131">NewPODetail2</span><span class="sxs-lookup"><span data-stu-id="ea0c6-131">NewPODetail2</span></span>|  
    |<span data-ttu-id="ea0c6-132">Table_Name</span><span class="sxs-lookup"><span data-stu-id="ea0c6-132">Table_Name</span></span>|<span data-ttu-id="ea0c6-133">PurchaseOrderDetail</span><span class="sxs-lookup"><span data-stu-id="ea0c6-133">PurchaseOrderDetail</span></span>|  
    |<span data-ttu-id="ea0c6-134">Data_Modification_Statement</span><span class="sxs-lookup"><span data-stu-id="ea0c6-134">Data_Modification_Statement</span></span>|<span data-ttu-id="ea0c6-135">从列表中删除 UPDATE 和 DELETE。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-135">Remove UPDATE and DELETE from the list.</span></span>|  
  
6.  <span data-ttu-id="ea0c6-136">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="ea0c6-136">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="ea0c6-137">在 **“查询编辑器”** 中，使用以下语句替换注释 `-- Insert statements for trigger here` ：</span><span class="sxs-lookup"><span data-stu-id="ea0c6-137">In the **Query Editor**, replace the comment `-- Insert statements for trigger here` with the following statement:</span></span>  
  
    ```sql  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
8.  <span data-ttu-id="ea0c6-138">若要验证语法是否有效，请在 **“查询”** 菜单上单击 **“分析”** 。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-138">To verify the syntax is valid, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="ea0c6-139">如果返回错误消息，则请将该语句与上述信息进行比较，视需要进行更正并且重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-139">If an error message is returned, compare the statement with the information above and correct as needed and repeat this step.</span></span>  
  
9. <span data-ttu-id="ea0c6-140">若要创建 DML 触发器，请在 **“查询”** 菜单上单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-140">To create the DML trigger, from the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="ea0c6-141">该 DML 触发器作为数据库中的对象创建。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-141">The DML trigger is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="ea0c6-142">若要查看在“对象资源管理器”中列出的 DML 触发器，请右键单击“触发器”，然后选择“刷新”   。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-142">To see the DML trigger listed in Object Explorer, right-click **Triggers** and select **Refresh**.</span></span>  
  
 [<span data-ttu-id="ea0c6-143">开始之前</span><span class="sxs-lookup"><span data-stu-id="ea0c6-143">Before You Begin</span></span>](#Top)  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ea0c6-144">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ea0c6-144">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="ea0c6-145">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ea0c6-146">从 **“文件”** 菜单中，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-146">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ea0c6-147">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ea0c6-148">此示例将创建与上面相同的存储的 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="ea0c6-148">This example creates the same stored DML trigger as above.</span></span>  
  
    ```sql
    -- Trigger valid for multirow and single row inserts  
    -- and optimal for single row inserts.  
    USE AdventureWorks2012;  
    GO  
    CREATE TRIGGER NewPODetail3  
    ON Purchasing.PurchaseOrderDetail  
    FOR INSERT AS  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
