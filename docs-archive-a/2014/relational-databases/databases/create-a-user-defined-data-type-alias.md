---
title: 创建用户定义的数据类型别名 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.userdefineddatatype.general.f1
- sql12.swb.new.datatype.properties.general.f1
helpviewer_keywords:
- alias data types [SQL Server], creating
ms.assetid: b1dd8413-0cd0-411b-a79b-1bb043ccc62d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35db332c23e2df5a8e67c3677cd2411768816765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576816"
---
# <a name="create-a-user-defined-data-type-alias"></a><span data-ttu-id="aa6d5-102">创建用户定义的数据类型别名</span><span class="sxs-lookup"><span data-stu-id="aa6d5-102">Create a User-Defined Data Type Alias</span></span>
  <span data-ttu-id="aa6d5-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建新的用户定义数据类型别名。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-103">This topic describes how to create a new user-defined data type alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="aa6d5-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="aa6d5-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="aa6d5-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa6d5-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="aa6d5-107">安全性</span><span class="sxs-lookup"><span data-stu-id="aa6d5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="aa6d5-108">**创建用户定义的数据类型别名，使用：**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-108">**To create a user-defined data type alias, using:**</span></span>  
  
     [<span data-ttu-id="aa6d5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa6d5-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="aa6d5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aa6d5-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa6d5-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="aa6d5-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="aa6d5-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa6d5-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="aa6d5-113">用户定义的数据类型别名必须符合标识符的规则。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-113">The name of a user-defined data type alias must comply with the rules for identifiers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="aa6d5-114">Security</span><span class="sxs-lookup"><span data-stu-id="aa6d5-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="aa6d5-115">权限</span><span class="sxs-lookup"><span data-stu-id="aa6d5-115">Permissions</span></span>  
 <span data-ttu-id="aa6d5-116">要求在当前数据库中具有 CREATE TYPE 权限，以及具有对 *schema_name*的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-116">Requires CREATE TYPE permission in the current database and ALTER permission on *schema_name*.</span></span> <span data-ttu-id="aa6d5-117">如果未指定 *schema_name* ，则将应用用于确定当前用户的架构的默认名称解析规则。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-117">If *schema_name* is not specified, the default name resolution rules for determining the schema for the current user apply.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aa6d5-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa6d5-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-user-defined-data-type"></a><span data-ttu-id="aa6d5-119">创建用户定义数据类型</span><span class="sxs-lookup"><span data-stu-id="aa6d5-119">To create a user-defined data type</span></span>  
  
1.  <span data-ttu-id="aa6d5-120">在“对象资源管理器”中，依次展开“数据库”、一个数据库、“可编程性”和“类型”，右键单击“用户定义数据类型”，然后单击“新建用户定义数据类型”    。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-120">In Object Explorer, expand **Databases**, expand a database, expand **Programmability**, expand **Types**, right-click **User-Defined Data Types**, and then click **New User-Defined Data Type**.</span></span>  
  
     <span data-ttu-id="aa6d5-121">**允许 Null**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-121">**Allow NULLs**</span></span>  
     <span data-ttu-id="aa6d5-122">指定用户定义数据类型是否可以接受 Null 值。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-122">Specify whether the user-defined data type can accept NULL values.</span></span> <span data-ttu-id="aa6d5-123">不能编辑现有的用户定义数据类型的为 NULL 性。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-123">The nullability of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="aa6d5-124">**Data type**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-124">**Data type**</span></span>  
     <span data-ttu-id="aa6d5-125">从列表框中选择基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-125">Select the base data type from the list box.</span></span> <span data-ttu-id="aa6d5-126">该列表框显示除 `geography`、`geometry`、`hierarchyid`、`sysname`、`timestamp` 和 `xml` 数据类型之外的所有数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-126">The list box displays all data types except for the `geography`, `geometry`, `hierarchyid`, `sysname`, `timestamp` , and `xml` data types.</span></span> <span data-ttu-id="aa6d5-127">不能编辑现有的用户定义数据类型的数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-127">The data type of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="aa6d5-128">**Default**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-128">**Default**</span></span>  
     <span data-ttu-id="aa6d5-129">（可选）选择要绑定到用户定义数据类型别名的规则或默认值。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-129">Optionally select a rule or a default to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="aa6d5-130">**长度/精度**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-130">**Length/Precision**</span></span>  
     <span data-ttu-id="aa6d5-131">相应地显示数据类型的长度或精度。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-131">Displays the length or precision of the data type as applicable.</span></span> <span data-ttu-id="aa6d5-132">**长度** 适用于基于字符的用户定义数据类型； **精度** 仅适用于基于数字的用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-132">**Length** applies to character-based user-defined data types; **Precision** applies only to numeric-based user-defined data types.</span></span> <span data-ttu-id="aa6d5-133">该标签会根据先前所选的数据类型而相应地改变。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-133">The label changes depending on the data type selected earlier.</span></span> <span data-ttu-id="aa6d5-134">如果所选数据类型的长度或精度是固定的，则不能编辑此框。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-134">This box is not editable if the length or precision of the selected data type is fixed.</span></span>  
  
     <span data-ttu-id="aa6d5-135">不为 `nvarchar(max)`、`varchar(max)` 或 `varbinary(max)` 数据类型显示长度。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-135">Length is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
     <span data-ttu-id="aa6d5-136">**名称**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-136">**Name**</span></span>  
     <span data-ttu-id="aa6d5-137">如果创建新的用户定义数据类型别名，请键入用于在整个数据库中表示用户定义数据类型的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-137">If you are creating a new user-defined data type alias, type a unique name to be used across the database to represent the user-defined data type.</span></span> <span data-ttu-id="aa6d5-138">最大字符数必须与系统 `sysname` 数据类型匹配。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-138">The maximum number of characters must match the system `sysname` data type.</span></span> <span data-ttu-id="aa6d5-139">不能编辑现有的用户定义数据类型别名的名称。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-139">The name of an existing user-defined data type alias is not editable.</span></span>  
  
     <span data-ttu-id="aa6d5-140">**规则**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-140">**Rule**</span></span>  
     <span data-ttu-id="aa6d5-141">（可选）选择要绑定到用户定义数据类型别名的规则。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-141">Optionally select a rule to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="aa6d5-142">**缩放**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-142">**Scale**</span></span>  
     <span data-ttu-id="aa6d5-143">指定可以在小数点右存储的十进制数字的最大位数。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-143">Specify the maximum number of decimal digits that can be stored to the right of the decimal point.</span></span>  
  
     <span data-ttu-id="aa6d5-144">**架构**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-144">**Schema**</span></span>  
     <span data-ttu-id="aa6d5-145">从包含当前用户的所有可用架构的列表中选择架构。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-145">Select a schema from a list of all schemas available to the current user.</span></span> <span data-ttu-id="aa6d5-146">默认选择是当前用户的默认架构。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-146">The default selection is the default schema for the current user.</span></span>  
  
     <span data-ttu-id="aa6d5-147">**存储**</span><span class="sxs-lookup"><span data-stu-id="aa6d5-147">**Storage**</span></span>  
     <span data-ttu-id="aa6d5-148">显示用户定义数据类型别名的最大存储大小。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-148">Displays the maximum storage size for the user-defined data type alias.</span></span> <span data-ttu-id="aa6d5-149">最大存储大小会根据精度的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-149">Maximum storage sizes vary, based on precision.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="aa6d5-150">1 - 9</span><span class="sxs-lookup"><span data-stu-id="aa6d5-150">1 - 9</span></span>|<span data-ttu-id="aa6d5-151">5</span><span class="sxs-lookup"><span data-stu-id="aa6d5-151">5</span></span>|  
    |<span data-ttu-id="aa6d5-152">10 - 19</span><span class="sxs-lookup"><span data-stu-id="aa6d5-152">10 - 19</span></span>|<span data-ttu-id="aa6d5-153">9</span><span class="sxs-lookup"><span data-stu-id="aa6d5-153">9</span></span>|  
    |<span data-ttu-id="aa6d5-154">20 - 28</span><span class="sxs-lookup"><span data-stu-id="aa6d5-154">20 - 28</span></span>|<span data-ttu-id="aa6d5-155">13</span><span class="sxs-lookup"><span data-stu-id="aa6d5-155">13</span></span>|  
    |<span data-ttu-id="aa6d5-156">29 - 38</span><span class="sxs-lookup"><span data-stu-id="aa6d5-156">29 - 38</span></span>|<span data-ttu-id="aa6d5-157">17</span><span class="sxs-lookup"><span data-stu-id="aa6d5-157">17</span></span>|  
  
     <span data-ttu-id="aa6d5-158">对于 `nchar` 和 `nvarchar` 数据类型，存储值始终是值**的**两倍。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-158">For `nchar` and `nvarchar` data types, the storage value is always two times the value in **Length**.</span></span>  
  
     <span data-ttu-id="aa6d5-159">不为 `nvarchar(max)`、`varchar(max)` 或 `varbinary(max)` 数据类型显示存储。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-159">Storage is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
2.  <span data-ttu-id="aa6d5-160">在“新建用户定义数据类型”对话框的“架构”框中，键入此数据类型别名所属的架构，或使用浏览按钮选择架构 。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-160">In the **New User-defined Data Type** dialog box, in the **Schema** box, type the schema to own this data type alias, or use the browse button to select the schema.</span></span>  
  
3.  <span data-ttu-id="aa6d5-161">在 **“名称”** 框中，键入新数据类型别名的名称。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-161">In the **Name** box, type a name for the new data type alias.</span></span>  
  
4.  <span data-ttu-id="aa6d5-162">在 **“数据类型”** 框中，选择新数据类型别名所基于的数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-162">In the **Data type** box, select the data type that the new data type alias will be based on.</span></span>  
  
5.  <span data-ttu-id="aa6d5-163">如果该数据类型适用，请填写 **“长度”** 框、 **“精度”** 框和 **“小数位数”** 框。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-163">Complete the **Length**, **Precision**, and **Scale** boxes if appropriate for that data type.</span></span>  
  
6.  <span data-ttu-id="aa6d5-164">如果新数据类型别名允许 Null 值，请选中 **“允许 NULL”** 。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-164">Check **Allow NULLs** if the new data type alias can permit NULL values.</span></span>  
  
7.  <span data-ttu-id="aa6d5-165">如果希望为新数据类型别名绑定默认值或规则，请在 **“绑定”** 区域中，填写 **“默认值”** 框或 **“规则”** 框。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-165">In the **Binding** area, complete the **Default** or **Rule** boxes if you want to bind a default or rule to the new data type alias.</span></span> <span data-ttu-id="aa6d5-166">默认值和规则不能在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中创建。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-166">Defaults and rules cannot be created in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="aa6d5-167">改用 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa6d5-167">Use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="aa6d5-168">模板资源管理器中提供了创建默认值和规则的示例代码。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-168">Example code for creating defaults and rules are available in Template Explorer.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="aa6d5-169">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aa6d5-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-user-defined-data-type-alias"></a><span data-ttu-id="aa6d5-170">创建用户定义的数据类型别名</span><span class="sxs-lookup"><span data-stu-id="aa6d5-170">To create a user-defined data type alias</span></span>  
  
1.  <span data-ttu-id="aa6d5-171">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-171">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="aa6d5-172">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-172">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="aa6d5-173">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-173">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="aa6d5-174">此示例基于系统提供的 `varchar` 数据类型创建一个数据类型别名。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-174">This example creates a data type alias based on the system-supplied `varchar` data type.</span></span> <span data-ttu-id="aa6d5-175">`ssn` 数据类型别名用于那些保存 11 位数字的社会保障号 (999-99-9999) 的列。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-175">The `ssn` data type alias is used for columns holding 11-digit social security numbers (999-99-9999).</span></span> <span data-ttu-id="aa6d5-176">该列不能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="aa6d5-176">The column cannot be NULL.</span></span>  
  
```sql  
CREATE TYPE ssn  
FROM varchar(11) NOT NULL ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa6d5-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa6d5-177">See Also</span></span>  
 <span data-ttu-id="aa6d5-178">[数据库标识符](database-identifiers.md) </span><span class="sxs-lookup"><span data-stu-id="aa6d5-178">[Database Identifiers](database-identifiers.md) </span></span>  
 [<span data-ttu-id="aa6d5-179">CREATE TYPE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aa6d5-179">CREATE TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-type-transact-sql)  
  
  
