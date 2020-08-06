---
title: 演练：添加和更改数据库关系图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], about database diagrams
- database diagrams [SQL Server], designing
- database diagrams [SQL Server], creating
ms.assetid: 228caa0d-8f24-46ab-86d1-b6d8631322bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: c35eb3674c817e98a25a74cd0309fc7376fe2f58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577990"
---
# <a name="walkthrough-adding-and-changing-a-database-diagram"></a><span data-ttu-id="ac9e1-102">演练：添加和更改数据库关系图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-102">Walkthrough: Adding and Changing a Database Diagram</span></span>
  <span data-ttu-id="ac9e1-103">本演练说明了如何创建和修改数据库关系图以及如何通过数据库关系图组件更改数据库。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-103">This walkthrough illustrates how to create and modify a database diagram and make changes to the database through the database diagrams component.</span></span> <span data-ttu-id="ac9e1-104">您将看到如何向关系图添加表、如何创建表之间的关系、如何对列创建约束和索引以及如何更改每个表的信息级别。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-104">You will see how to add tables to diagrams, create relationships between tables, create constraints and indexes on columns, and change the level of information you see for each table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ac9e1-105">必备条件</span><span class="sxs-lookup"><span data-stu-id="ac9e1-105">Prerequisites</span></span>  
 <span data-ttu-id="ac9e1-106">为了完成本演练，您需要：</span><span class="sxs-lookup"><span data-stu-id="ac9e1-106">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="ac9e1-107">能够访问带有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例数据库的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac9e1-107">Access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database</span></span>  
  
-   <span data-ttu-id="ac9e1-108">一个具有数据库所有者 `dbo` 特权的帐户</span><span class="sxs-lookup"><span data-stu-id="ac9e1-108">An account with database owner `dbo` privileges</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac9e1-109">如果所使用的帐户对要更改的表不具有足够的特权，则在尝试更改表时会出现错误消息。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-109">If you attempt to make changes when using an account without sufficient privileges to make changes to tables, then an error message appears.</span></span>  
  
## <a name="creating-a-diagram"></a><span data-ttu-id="ac9e1-110">创建关系图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-110">Creating a Diagram</span></span>  
  
#### <a name="to-create-a-new-database-diagram"></a><span data-ttu-id="ac9e1-111">创建新的数据库关系图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-111">To create a new database diagram</span></span>  
  
1.  <span data-ttu-id="ac9e1-112">在“视图”  菜单上单击“对象资源管理器”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-112">On the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="ac9e1-113">打开“数据库”节点，再打开 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 节点。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-113">Open the Databases node and then open the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] node.</span></span>  
  
3.  <span data-ttu-id="ac9e1-114">右键单击“数据库关系图”节点并选择“新建数据库关系图”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-114">Right-click the Database Diagrams node and choose **New Database Diagram**.</span></span>  
  
     <span data-ttu-id="ac9e1-115">如果此数据库没有创建关系图所必需的对象，则将显示下列消息： **此数据库没有使用数据库关系图创建功能所需的一个或多个支持对象。要创建它们吗？**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-115">If the database does not have objects necessary to create diagrams, the following message appears: **This database does not have one or more of the support objects required to use database diagramming. Do you wish to create them?**</span></span> <span data-ttu-id="ac9e1-116">选择“是”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-116">Choose **Yes**.</span></span>  
  
     <span data-ttu-id="ac9e1-117">此时将显示“添加表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-117">The **Add Table** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="ac9e1-118">选择“AddressType (Person)”  和“Address (Person)”  并单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-118">Select **AddressType (Person)** and **Address (Person)** and click **Add**.</span></span>  
  
     <span data-ttu-id="ac9e1-119">两个表将添加到关系图中。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-119">Two tables are added to the diagram.</span></span>  
  
5.  <span data-ttu-id="ac9e1-120">关闭“添加表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-120">Close the **Add Table** dialog box.</span></span>  
  
#### <a name="to-view-different-column-data"></a><span data-ttu-id="ac9e1-121">查看不同的列数据</span><span class="sxs-lookup"><span data-stu-id="ac9e1-121">To view different column data</span></span>  
  
1.  <span data-ttu-id="ac9e1-122">右键单击 `Address` 表。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-122">Right-click the `Address` table.</span></span> <span data-ttu-id="ac9e1-123">在快捷菜单上，指向“表视图”  ，再单击“标准”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-123">On the shortcut menu, point to **Table View**, and then click **Standard**.</span></span>  
  
     <span data-ttu-id="ac9e1-124">表的网格将显示三个列：“列名”  、“数据类型”  和“允许 Null 值”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-124">The table grid shows three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
2.  <span data-ttu-id="ac9e1-125">右键单击 `Address` 表，单击“表视图”  并选择“键”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-125">Right-click the `Address` table, click **Table View** and select **Keys**.</span></span>  
  
     <span data-ttu-id="ac9e1-126">表网格将显示一个列，并带有表列名。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-126">The table grid shows one column, with the table-column names.</span></span> <span data-ttu-id="ac9e1-127">仅显示那些参与了索引的列。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-127">Only those columns participating in indexes appear.</span></span>  
  
## <a name="creating-new-tables"></a><span data-ttu-id="ac9e1-128">创建新表</span><span class="sxs-lookup"><span data-stu-id="ac9e1-128">Creating New Tables</span></span>  
  
#### <a name="to-create-tables-within-diagram-designer"></a><span data-ttu-id="ac9e1-129">在关系图设计器中创建表</span><span class="sxs-lookup"><span data-stu-id="ac9e1-129">To create tables within Diagram Designer</span></span>  
  
1.  <span data-ttu-id="ac9e1-130">右键单击现有表外部的关系图设计器并选择“新建表”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-130">Right-click the Diagram Designer outside the existing tables and choose **New Table**.</span></span>  
  
2.  <span data-ttu-id="ac9e1-131">在 "**选择名称**" 对话框中，单击 **"确定"** 以接受默认名称 `Table1` 。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-131">In the **Choose Name** dialog box, click **OK** to accept the default name `Table1`.</span></span>  
  
     <span data-ttu-id="ac9e1-132">将显示具有以下三列的新表网格：“列名”  、“数据类型”  和“允许 Null 值”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-132">A new table grid appears with three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
3.  <span data-ttu-id="ac9e1-133">将以下信息添加到 `Table1` ：</span><span class="sxs-lookup"><span data-stu-id="ac9e1-133">Add the following information to `Table1`:</span></span>  
  
    |<span data-ttu-id="ac9e1-134">**列名称**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-134">**Column Name**</span></span>|<span data-ttu-id="ac9e1-135">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-135">**Data Type**</span></span>|<span data-ttu-id="ac9e1-136">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-136">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T1col1`|`int`|<span data-ttu-id="ac9e1-137">checked</span><span class="sxs-lookup"><span data-stu-id="ac9e1-137">checked</span></span>|  
    |`T1col2`|`varchar(50)`|<span data-ttu-id="ac9e1-138">checked</span><span class="sxs-lookup"><span data-stu-id="ac9e1-138">checked</span></span>|  
    |`T1col3`|`float`|<span data-ttu-id="ac9e1-139">已选中</span><span class="sxs-lookup"><span data-stu-id="ac9e1-139">checked</span></span>|  
  
4.  <span data-ttu-id="ac9e1-140">右键单击 `T1col1` 并选择“设置主键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-140">Right-click `T1col1` and select **Set Primary Key**.</span></span>  
  
     <span data-ttu-id="ac9e1-141">列名旁将显示一个钥匙图标。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-141">A key icon will appear beside the column name.</span></span>  
  
5.  <span data-ttu-id="ac9e1-142">从“文件”\*\*\*\* 菜单，单击“保存 Diagram1”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-142">From the **File** menu, click **Save Diagram1**.</span></span>  
  
6.  <span data-ttu-id="ac9e1-143">在 "**选择名称**" 对话框中，单击 **"确定"** 以接受默认名称 `Diagram1` 。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-143">In the **Choose Name** dialog box, click **OK** to accept the default name `Diagram1`.</span></span>  
  
7.  <span data-ttu-id="ac9e1-144">将显示“保存”\*\*\*\* 对话框和一条指出 `Table1` 将保存到数据库的消息。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-144">The **Save** dialog box appears with a message that `Table1` will be saved to the database.</span></span> <span data-ttu-id="ac9e1-145">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-145">Click **Yes**.</span></span>  
  
## <a name="modifying-table-structure"></a><span data-ttu-id="ac9e1-146">修改表结构</span><span class="sxs-lookup"><span data-stu-id="ac9e1-146">Modifying Table Structure</span></span>  
 <span data-ttu-id="ac9e1-147">您可以添加检查约束，并在关系图设计器中建立表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-147">You can add check constraints and make relationships between tables in Diagram Designer.</span></span>  
  
#### <a name="to-create-check-constraints"></a><span data-ttu-id="ac9e1-148">创建检查约束</span><span class="sxs-lookup"><span data-stu-id="ac9e1-148">To create check constraints</span></span>  
  
1.  <span data-ttu-id="ac9e1-149">在 `Table1` 中，右键单击 `T1col3` 行并选择“CHECK 约束”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-149">In `Table1`, right-click the `T1col3` row and choose **Check Constraints**.</span></span>  
  
     <span data-ttu-id="ac9e1-150">此时将显示“CHECK 约束”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-150">The **Check Constraints** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ac9e1-151">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-151">Click **Add**.</span></span>  
  
     <span data-ttu-id="ac9e1-152">“选定的 CHECK 约束”\*\*\*\* 列表中将出现一个新约束，默认名称为 `CK_Table1`。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-152">A new constraint appears in the **Selected Check Constraint** list, with the default name `CK_Table1`.</span></span>  
  
3.  <span data-ttu-id="ac9e1-153">在网格中选择“表达式”\*\*\*\* 行并单击省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-153">Select the **Expression** row in the grid and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="ac9e1-154">此时将显示“CHECK 约束表达式”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-154">The **Check Constraint Expression** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="ac9e1-155">键入 `T1col3 > 5` ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-155">Type `T1col3 > 5` and click **OK**.</span></span>  
  
     <span data-ttu-id="ac9e1-156">`Table1` 现在有了一个约束，即输入到 `T1col3` 中的所有值都必须大于 5。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-156">`Table1` now has a constraint that all values entered into `T1col3` must be greater than 5.</span></span>  
  
5.  <span data-ttu-id="ac9e1-157">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-157">Click **Close**.</span></span>  
  
#### <a name="to-create-relationships-between-tables"></a><span data-ttu-id="ac9e1-158">在表之间创建关系</span><span class="sxs-lookup"><span data-stu-id="ac9e1-158">To create relationships between tables</span></span>  
  
1.  <span data-ttu-id="ac9e1-159">在关系图设计器中创建名为 `Table2` 的新表，该表具有以下列：</span><span class="sxs-lookup"><span data-stu-id="ac9e1-159">Create a new table in Diagram designer named `Table2` with the following columns:</span></span>  
  
    |<span data-ttu-id="ac9e1-160">**列名**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-160">**Column Name**</span></span>|<span data-ttu-id="ac9e1-161">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-161">**Data Type**</span></span>|<span data-ttu-id="ac9e1-162">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="ac9e1-162">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T2col1`|`int`|<span data-ttu-id="ac9e1-163">未选中</span><span class="sxs-lookup"><span data-stu-id="ac9e1-163">not checked</span></span>|  
    |`T2col2`|`varchar(50)`|<span data-ttu-id="ac9e1-164">checked</span><span class="sxs-lookup"><span data-stu-id="ac9e1-164">checked</span></span>|  
    |`T2col3`|`xml`|<span data-ttu-id="ac9e1-165">checked</span><span class="sxs-lookup"><span data-stu-id="ac9e1-165">checked</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac9e1-166">外键关系的主键方上的列必须参与主键或唯一约束。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-166">The columns on the primary key side of a foreign key relationship must participate in either a Primary Key or a Unique Constraint.</span></span>  
  
2.  <span data-ttu-id="ac9e1-167">将 `T2col1` 拖动到 `T1col1`。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-167">Drag `T2col1` to `T1col1`.</span></span>  
  
     <span data-ttu-id="ac9e1-168">将显示两个对话框：背景中的“外键关系”\*\*\*\* 对话框和前景中的“表和列”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-168">Two dialog boxes appear: **Foreign Key Relationship** in the background and **Tables and Columns** in the foreground.</span></span>  
  
3.  <span data-ttu-id="ac9e1-169">单击“确定”\*\*\*\* 保存新的关系。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-169">Click **OK** to save the new relationship.</span></span>  
  
4.  <span data-ttu-id="ac9e1-170">再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-170">Click **OK** again.</span></span>  
  
## <a name="creating-indexes"></a><span data-ttu-id="ac9e1-171">创建索引</span><span class="sxs-lookup"><span data-stu-id="ac9e1-171">Creating Indexes</span></span>  
 <span data-ttu-id="ac9e1-172">您可以对大多数数据类型（包括 XML）创建索引。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-172">You can create indexes on most types of data, including XML.</span></span>  
  
#### <a name="to-create-a-standard-index"></a><span data-ttu-id="ac9e1-173">创建标准索引</span><span class="sxs-lookup"><span data-stu-id="ac9e1-173">To create a standard index</span></span>  
  
1.  <span data-ttu-id="ac9e1-174">右键单击 `Table1` 并选择“索引/键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-174">Right-click `Table1` and choose **Indexes/Keys**.</span></span>  
  
     <span data-ttu-id="ac9e1-175">此时将显示“索引/键”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-175">The **Indexes/Keys** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ac9e1-176">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-176">Click **Add**.</span></span>  
  
     <span data-ttu-id="ac9e1-177">“选定的主/唯一键或索引”\*\*\*\* 列表中将出现一个新索引，并使用类似 `IX_Table1` 的默认名称。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-177">A new index appears in the **Selected Primary/Unique Key or Index** list, with a default name similar to `IX_Table1`.</span></span>  
  
3.  <span data-ttu-id="ac9e1-178">选择“列”\*\*\*\* 行并单击省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-178">Select the **Columns** row and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="ac9e1-179">此时将显示“索引列”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-179">The **Index Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="ac9e1-180">单击“列名”\*\*\*\* 下方的下拉箭头并选择 `T1col2`。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-180">Click the drop-down arrow under **Column Name** and select `T1col2`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac9e1-181">您可以通过选择 `T1col2` 下的单元并选择其他列名来向此索引添加其他列。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-181">You may add additional columns to this index by selecting the cell below `T1col2` and choosing another column name.</span></span>  
  
5.  <span data-ttu-id="ac9e1-182">单击“确定”\*\*\*\* 保存此索引。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-182">Click **OK** to save this index.</span></span>  
  
6.  <span data-ttu-id="ac9e1-183">在“索引/键”\*\*\*\* 对话框中单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-183">Click **Close** in the **Indexes/Keys** dialog box.</span></span>  
  
#### <a name="to-create-an-xml-index"></a><span data-ttu-id="ac9e1-184">创建 XML 索引</span><span class="sxs-lookup"><span data-stu-id="ac9e1-184">To create an XML index</span></span>  
  
1.  <span data-ttu-id="ac9e1-185">右键单击 `T2col1` 并选择“设置主键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-185">Right-click `T2col1` and choose **Set Primary Key**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac9e1-186">添加 XML 索引要求将表中的另一列设置为聚集主键。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-186">Adding an XML index requires that another column in the table be set as a clustered primary key.</span></span>  
  
2.  <span data-ttu-id="ac9e1-187">在 `T2col3` 中右键单击 `Table2` 行，并选择“XML 索引”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-187">Right-click the `T2col3` row in `Table2` and select **XML Indexes**.</span></span>  
  
     <span data-ttu-id="ac9e1-188">此时将显示“XML 索引”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-188">The **XML Indexes** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="ac9e1-189">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-189">Click **Add**.</span></span>  
  
     <span data-ttu-id="ac9e1-190">将向“选定的 XML 索引”\*\*\*\* 列表中添加一个具有默认值的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-190">An XML index with default values will be added to the **Selected XML Index** list.</span></span>  
  
4.  <span data-ttu-id="ac9e1-191">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-191">Click **Close**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac9e1-192">XML 索引是按列创建的。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-192">XML indexes are created per-column.</span></span> <span data-ttu-id="ac9e1-193">第一个 XML 索引是主索引，所有其他索引都是辅助索引。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-193">The first XML index is primary; any additional indexes are secondary.</span></span>  
  
## <a name="saving-the-diagram"></a><span data-ttu-id="ac9e1-194">保存关系图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-194">Saving the Diagram</span></span>  
 <span data-ttu-id="ac9e1-195">对关系图所做的全部更改在保存后才会发布到数据库。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-195">All of the changes you make to a diagram are not posted to the database until you save it.</span></span> <span data-ttu-id="ac9e1-196">如果存在问题或冲突，则会出现一个带有详细信息的对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-196">If there are problems or conflicts, a dialog box appears with more information.</span></span>  
  
#### <a name="to-save-a-database-diagram"></a><span data-ttu-id="ac9e1-197">保存数据库关系图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-197">To save a database diagram</span></span>  
  
1.  <span data-ttu-id="ac9e1-198">在“文件”\*\*\*\* 菜单上，选择“保存 Diagram1”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-198">On the **File** menu, select **Save Diagram1**.</span></span>  
  
     <span data-ttu-id="ac9e1-199">此时将显示“保存”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-199">The **Save** dialog box appears.</span></span> <span data-ttu-id="ac9e1-200">如果选中了“表受到影响时警告”\*\*\*\*，则会列出有关新表或更改的表的信息。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-200">If **Warn about Tables Affected** is selected, information about new or changed tables is listed.</span></span>  
  
2.  <span data-ttu-id="ac9e1-201">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-201">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="ac9e1-202">如果发生了任何错误，则会出现“保存后的通知”\*\*\*\* 对话框，显示错误及其原因。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-202">If any errors occurred, the **Post-Save Notifications** dialog box appears with the errors and their causes.</span></span> <span data-ttu-id="ac9e1-203">修复错误并再次保存关系图。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-203">Fix the errors and save the diagram again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ac9e1-204">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ac9e1-204">Next Steps</span></span>  
 <span data-ttu-id="ac9e1-205">虽然这是一个仅包含两个现有表和两个新表的简单关系图，但是它展示了创建现有数据库的关系图或直观地创建新架构的潜力。</span><span class="sxs-lookup"><span data-stu-id="ac9e1-205">This is a basic diagram with just two existing and two new tables, but it illustrates the potential for diagramming an existing database or creating a new schema visually.</span></span> <span data-ttu-id="ac9e1-206">建议了解的其他内容包括：</span><span class="sxs-lookup"><span data-stu-id="ac9e1-206">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="ac9e1-207">创建包含多组相关表的新关系图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-207">Create new diagrams containing groups of related tables</span></span>  
  
-   <span data-ttu-id="ac9e1-208">自定义各表中显示的信息量</span><span class="sxs-lookup"><span data-stu-id="ac9e1-208">Customize the amount of information shown for each table</span></span>  
  
-   <span data-ttu-id="ac9e1-209">更改布局和添加批注</span><span class="sxs-lookup"><span data-stu-id="ac9e1-209">Change the layout and add annotations</span></span>  
  
-   <span data-ttu-id="ac9e1-210">将关系图复制到位图</span><span class="sxs-lookup"><span data-stu-id="ac9e1-210">Copy the diagram to a bitmap</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac9e1-211">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac9e1-211">See Also</span></span>  
 <span data-ttu-id="ac9e1-212">[自定义关系图中显示的信息量 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ac9e1-212">[Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="ac9e1-213">[&#40;Visual Database Tools 设置数据库关系图设计器&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ac9e1-213">[Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ac9e1-214">[在 Visual Database Tools &#40;向关系图中添加表&#41;](add-tables-to-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ac9e1-214">[Add Tables to Diagrams &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ac9e1-215">[在 Visual Database Tools&#41;的关系图上创建表之间的关系 &#40;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ac9e1-215">[Create Relationships Between Tables on a Diagram &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ac9e1-216">[创建 XML 索引](../../relational-databases/xml/create-xml-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="ac9e1-216">[Create XML Indexes](../../relational-databases/xml/create-xml-indexes.md) </span></span>  
 <span data-ttu-id="ac9e1-217">[将数据库关系图的图像复制到剪贴板 &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ac9e1-217">[Copy an Image of a Database Diagram to the Clipboard &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ac9e1-218">使用关系图布局 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ac9e1-218">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
