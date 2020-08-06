---
title: 列属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.columnproperties.general.f1
ms.assetid: a745890b-994e-4c23-8028-5c83751e60c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29a82df217eef719b4f0efffb3fc0c24b36a27aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591843"
---
# <a name="column-properties-general-page"></a><span data-ttu-id="d8b09-102">列属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="d8b09-102">Column Properties (General Page)</span></span>
  <span data-ttu-id="d8b09-103">使用此页可以查看所选列的属性。</span><span class="sxs-lookup"><span data-stu-id="d8b09-103">Use this page to view properties for the selected column.</span></span>  
  
 <span data-ttu-id="d8b09-104">此页上的信息为只读信息。</span><span class="sxs-lookup"><span data-stu-id="d8b09-104">Information on this page is read-only.</span></span> <span data-ttu-id="d8b09-105">若要修改列，请关闭“列属性”  对话框，然后在对象资源管理器中展开表和列，右键单击该列，再单击“设计”  。</span><span class="sxs-lookup"><span data-stu-id="d8b09-105">To modify the column, close the **Column Properties** dialog box, expand the table and columns in Object Explorer, right-click the column, and then click **Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8b09-106">选项</span><span class="sxs-lookup"><span data-stu-id="d8b09-106">Options</span></span>  
 <span data-ttu-id="d8b09-107">**名称**</span><span class="sxs-lookup"><span data-stu-id="d8b09-107">**Name**</span></span>  
 <span data-ttu-id="d8b09-108">列的名称。</span><span class="sxs-lookup"><span data-stu-id="d8b09-108">The name of the column.</span></span>  
  
 <span data-ttu-id="d8b09-109">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="d8b09-109">**Data Type**</span></span>  
 <span data-ttu-id="d8b09-110">此列所能包含的数据类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-110">The type of data that the column can hold.</span></span> <span data-ttu-id="d8b09-111">如果数据类型为用户定义数据类型，则显示用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-111">If the data type is a user-defined data type, the user-defined data type is displayed.</span></span> <span data-ttu-id="d8b09-112">如果数据类型不是用户定义数据类型，则显示系统数据类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-112">If the data type is not a user-defined data type, then the system data type is displayed.</span></span> <span data-ttu-id="d8b09-113">有关详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d8b09-113">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="d8b09-114">**系统类型**</span><span class="sxs-lookup"><span data-stu-id="d8b09-114">**System Type**</span></span>  
 <span data-ttu-id="d8b09-115">此列所能包含的数据类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-115">The type of data that the column can hold.</span></span> <span data-ttu-id="d8b09-116">如果数据类型为系统数据类型，则显示系统数据类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-116">If the data type is a system data type, then the system data type is displayed.</span></span> <span data-ttu-id="d8b09-117">如果数据类型为用户定义数据类型，则显示组成用户定义数据类型的系统数据类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-117">If the data type is a user-defined data type, the system data type that makes up the user-defined data type is displayed.</span></span>  
  
 <span data-ttu-id="d8b09-118">**主键**</span><span class="sxs-lookup"><span data-stu-id="d8b09-118">**Primary Key**</span></span>  
 <span data-ttu-id="d8b09-119">指示该列是否为主键。</span><span class="sxs-lookup"><span data-stu-id="d8b09-119">Indicates whether the column is a primary key.</span></span> <span data-ttu-id="d8b09-120">可能的值包括 **True**和 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8b09-120">Possible values are **True**and **False**.</span></span>  
  
 <span data-ttu-id="d8b09-121">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="d8b09-121">**Allow Nulls**</span></span>  
 <span data-ttu-id="d8b09-122">指示列是否接受空值。</span><span class="sxs-lookup"><span data-stu-id="d8b09-122">Indicates whether the column accepts null values.</span></span> <span data-ttu-id="d8b09-123">可能的值包括 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8b09-123">Possible values are **True** and **False**.</span></span>  
  
 <span data-ttu-id="d8b09-124">**是计算**</span><span class="sxs-lookup"><span data-stu-id="d8b09-124">**Is Computed**</span></span>  
 <span data-ttu-id="d8b09-125">指示该列的值是否为计算表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="d8b09-125">Indicates whether the column value is the result of a computed expression.</span></span>  
  
 <span data-ttu-id="d8b09-126">**计算文本**</span><span class="sxs-lookup"><span data-stu-id="d8b09-126">**Computed text**</span></span>  
 <span data-ttu-id="d8b09-127">指示用于计算列文本的语句。</span><span class="sxs-lookup"><span data-stu-id="d8b09-127">Indicates the statement used to compute the column text.</span></span> <span data-ttu-id="d8b09-128">有关详细信息，请参阅 [Specify Computed Columns in a Table](specify-computed-columns-in-a-table.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b09-128">For more information, [Specify Computed Columns in a Table](specify-computed-columns-in-a-table.md).</span></span>  
  
 <span data-ttu-id="d8b09-129">**标识**</span><span class="sxs-lookup"><span data-stu-id="d8b09-129">**Identity**</span></span>  
 <span data-ttu-id="d8b09-130">指示列是否为表的标识列。</span><span class="sxs-lookup"><span data-stu-id="d8b09-130">Indicates whether the column is the identity column for the table.</span></span> <span data-ttu-id="d8b09-131">可能的值包括 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8b09-131">Possible values are **True** and **False**.</span></span>  
  
 <span data-ttu-id="d8b09-132">**标识种子**</span><span class="sxs-lookup"><span data-stu-id="d8b09-132">**Identity Seed**</span></span>  
 <span data-ttu-id="d8b09-133">指示标识列的初始行值。</span><span class="sxs-lookup"><span data-stu-id="d8b09-133">Indicates the initial row value for an identity column.</span></span>  
  
 <span data-ttu-id="d8b09-134">**标识增量**</span><span class="sxs-lookup"><span data-stu-id="d8b09-134">**Identity Increment**</span></span>  
 <span data-ttu-id="d8b09-135">“标识增量”属性指定在   为插入的行生成标识值时，在现有的最大行标识值基础上所加的值[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8b09-135">The **Identity Increment** property specifies the value [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adds to the greatest existing row identity value as it generates an identity value for a row being inserted.</span></span>  
  
 <span data-ttu-id="d8b09-136">**默认值绑定**</span><span class="sxs-lookup"><span data-stu-id="d8b09-136">**Default Binding**</span></span>  
 <span data-ttu-id="d8b09-137">绑定到该列的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认值。</span><span class="sxs-lookup"><span data-stu-id="d8b09-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default bound to the column.</span></span> <span data-ttu-id="d8b09-138">如果未绑定默认值，此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="d8b09-138">This option is blank if no default is bound.</span></span>  
  
 <span data-ttu-id="d8b09-139">**默认架构**</span><span class="sxs-lookup"><span data-stu-id="d8b09-139">**Default Schema**</span></span>  
 <span data-ttu-id="d8b09-140">标识拥有绑定到被引用列的默认值的数据库架构。</span><span class="sxs-lookup"><span data-stu-id="d8b09-140">Identifies the database schema owning the default bound to the referenced column.</span></span> <span data-ttu-id="d8b09-141">如果未绑定默认值，此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="d8b09-141">This option is blank if no default is bound.</span></span>  
  
 <span data-ttu-id="d8b09-142">**规则**</span><span class="sxs-lookup"><span data-stu-id="d8b09-142">**Rule**</span></span>  
 <span data-ttu-id="d8b09-143">标识绑定到该列的数据完整性约束。</span><span class="sxs-lookup"><span data-stu-id="d8b09-143">Identifies the data integrity constraint that is bound to the column.</span></span> <span data-ttu-id="d8b09-144">如果未绑定规则，此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="d8b09-144">This option is blank if no rule is bound.</span></span>  
  
 <span data-ttu-id="d8b09-145">**规则架构**</span><span class="sxs-lookup"><span data-stu-id="d8b09-145">**Rule Schema**</span></span>  
 <span data-ttu-id="d8b09-146">显示拥有绑定到被引用列的规则的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库架构。</span><span class="sxs-lookup"><span data-stu-id="d8b09-146">Displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database schema that owns the rule bound to the referenced column.</span></span> <span data-ttu-id="d8b09-147">如果未绑定规则，此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="d8b09-147">This option is blank if no rule is bound.</span></span>  
  
 <span data-ttu-id="d8b09-148">**长度**</span><span class="sxs-lookup"><span data-stu-id="d8b09-148">**Length**</span></span>  
 <span data-ttu-id="d8b09-149">指示该列可接受的最大字符数或字节数。</span><span class="sxs-lookup"><span data-stu-id="d8b09-149">Indicates the maximum number of characters or bytes accepted by the column.</span></span>  
  
 <span data-ttu-id="d8b09-150">**排序规则**</span><span class="sxs-lookup"><span data-stu-id="d8b09-150">**Collation**</span></span>  
 <span data-ttu-id="d8b09-151">显示该列当前的排序规则。</span><span class="sxs-lookup"><span data-stu-id="d8b09-151">Displays the current collation for the column.</span></span> <span data-ttu-id="d8b09-152">如果为空，则从对象继承排序规则属性。</span><span class="sxs-lookup"><span data-stu-id="d8b09-152">If blank, the collation property is inherited from the object.</span></span>  
  
 <span data-ttu-id="d8b09-153">**数值精度**</span><span class="sxs-lookup"><span data-stu-id="d8b09-153">**Numeric Precision**</span></span>  
 <span data-ttu-id="d8b09-154">指定固定精度数值数据类型中的最大位数。</span><span class="sxs-lookup"><span data-stu-id="d8b09-154">Indicates the maximum number of digits in a fixed-precision, numeric data type.</span></span>  
  
 <span data-ttu-id="d8b09-155">**小数位数**</span><span class="sxs-lookup"><span data-stu-id="d8b09-155">**Numeric Scale**</span></span>  
 <span data-ttu-id="d8b09-156">指示固定精度数值数据类型中小数点后的位数。</span><span class="sxs-lookup"><span data-stu-id="d8b09-156">Indicates the number of digits to the right of the decimal point in a fixed-precision, numeric data type.</span></span>  
  
 <span data-ttu-id="d8b09-157">**XML 架构命名空间**</span><span class="sxs-lookup"><span data-stu-id="d8b09-157">**XML Schema Namespace**</span></span>  
 <span data-ttu-id="d8b09-158">通过 XML 架构定义 (XSD) 语言验证定义 XML 列的类型。</span><span class="sxs-lookup"><span data-stu-id="d8b09-158">Defines the type of the XML column by way of XML Schema Definition (XSD) Language validation.</span></span>  
  
 <span data-ttu-id="d8b09-159">**XML 架构命名空间架构**</span><span class="sxs-lookup"><span data-stu-id="d8b09-159">**XML Schema Namespace schema**</span></span>  
 <span data-ttu-id="d8b09-160">拥有 XML 架构命名空间的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 架构。</span><span class="sxs-lookup"><span data-stu-id="d8b09-160">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schema that owns the XML Schema Namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8b09-161">架构一词具有多种不同的常用含义。</span><span class="sxs-lookup"><span data-stu-id="d8b09-161">There are several common but different meanings of the word schema.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d8b09-162">使用架构来组织数据库对象。</span><span class="sxs-lookup"><span data-stu-id="d8b09-162">uses schema to organize database objects.</span></span> <span data-ttu-id="d8b09-163">其含义类似于所有权。</span><span class="sxs-lookup"><span data-stu-id="d8b09-163">It is similar to ownership.</span></span> <span data-ttu-id="d8b09-164">XML 使用架构来定义 XML 信息在一系列命名空间内的结构。</span><span class="sxs-lookup"><span data-stu-id="d8b09-164">XML uses the schema to define the organization of XML information into a series of namespaces.</span></span> <span data-ttu-id="d8b09-165">架构是一种组织相关 XML 代码的方式。</span><span class="sxs-lookup"><span data-stu-id="d8b09-165">It is a way to group related XML code together.</span></span>  
  
 <span data-ttu-id="d8b09-166">**稀疏**</span><span class="sxs-lookup"><span data-stu-id="d8b09-166">**Is Sparse**</span></span>  
 <span data-ttu-id="d8b09-167">指示列是否为稀疏列。</span><span class="sxs-lookup"><span data-stu-id="d8b09-167">Indicates whether the column is a sparse column.</span></span> <span data-ttu-id="d8b09-168">可能的值包括 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8b09-168">Possible values are **True** and **False**.</span></span> <span data-ttu-id="d8b09-169">有关详细信息，请参阅 [使用稀疏列](use-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b09-169">For more information, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
 <span data-ttu-id="d8b09-170">**是列集**</span><span class="sxs-lookup"><span data-stu-id="d8b09-170">**Is Column Set**</span></span>  
 <span data-ttu-id="d8b09-171">指示列是否为列集。</span><span class="sxs-lookup"><span data-stu-id="d8b09-171">Indicates whether the column is a column set.</span></span> <span data-ttu-id="d8b09-172">可能的值包括 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8b09-172">Possible values are **True** and **False**.</span></span> <span data-ttu-id="d8b09-173">有关详细信息，请参阅 [使用列集](use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b09-173">For more information, see [Use Column Sets](use-column-sets.md).</span></span>  
  
 <span data-ttu-id="d8b09-174">**ANSI 填充状态**</span><span class="sxs-lookup"><span data-stu-id="d8b09-174">**ANSI Padding Status**</span></span>  
 <span data-ttu-id="d8b09-175">指示 ANSI 填充是启用还是禁用。</span><span class="sxs-lookup"><span data-stu-id="d8b09-175">Indicates whether ANSI padding is on or off.</span></span> <span data-ttu-id="d8b09-176">有关详细信息，请参阅 [SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d8b09-176">For more information, see [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span></span>  
  
 <span data-ttu-id="d8b09-177">**全文**</span><span class="sxs-lookup"><span data-stu-id="d8b09-177">**Full Text**</span></span>  
 <span data-ttu-id="d8b09-178">显示该列是否参与全文查询。</span><span class="sxs-lookup"><span data-stu-id="d8b09-178">Displays whether the column participates in full-text queries.</span></span>  
  
 <span data-ttu-id="d8b09-179">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="d8b09-179">**Statistical Semantics**</span></span>  
 <span data-ttu-id="d8b09-180">指示是否为列启用了统计语义搜索。</span><span class="sxs-lookup"><span data-stu-id="d8b09-180">Indicates whether statistical semantic search is enabled for the column.</span></span> <span data-ttu-id="d8b09-181">有关详细信息，请参阅[语义搜索 (SQL Server)](../search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b09-181">For more information, see [Semantic Search &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="d8b09-182">**不用于复制**</span><span class="sxs-lookup"><span data-stu-id="d8b09-182">**Not For Replication**</span></span>  
 <span data-ttu-id="d8b09-183">指示该列是否可用于复制。</span><span class="sxs-lookup"><span data-stu-id="d8b09-183">Indicates whether the column is available for replication.</span></span> <span data-ttu-id="d8b09-184">可能的值包括 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="d8b09-184">Possible values are **True** and **False**.</span></span>  
  
  
