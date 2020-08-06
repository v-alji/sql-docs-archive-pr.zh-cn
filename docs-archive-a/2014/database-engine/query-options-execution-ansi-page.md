---
title: 查询选项执行 (ANSI 页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: rothja
ms.author: jroth
ms.openlocfilehash: 013a7a318ed7f8db9156700f789ae64cf3e4e017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691343"
---
# <a name="query-options-execution-ansi-page"></a><span data-ttu-id="920d1-102">“查询选项”中的“执行”（ANSI 页）</span><span class="sxs-lookup"><span data-stu-id="920d1-102">Query Options Execution (ANSI Page)</span></span>
  <span data-ttu-id="920d1-103">使用此页可以指定 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将使用 ISO (ANSI) 标准中指定的全部或部分设置运行查询。</span><span class="sxs-lookup"><span data-stu-id="920d1-103">Use this page to specify that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will run the queries using all or a portion of the settings specified in the ISO (ANSI) standard.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="920d1-104">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="920d1-104">UI element list</span></span>  
 <span data-ttu-id="920d1-105">**SET ANSI_DEFAULTS**</span><span class="sxs-lookup"><span data-stu-id="920d1-105">**SET ANSI_DEFAULTS**</span></span>  
 <span data-ttu-id="920d1-106">选择所有默认的 ISO 设置。</span><span class="sxs-lookup"><span data-stu-id="920d1-106">Select all of the default ISO settings.</span></span> <span data-ttu-id="920d1-107">默认情况下，此框不可用，因为只配置了部分 ISO 设置。</span><span class="sxs-lookup"><span data-stu-id="920d1-107">This box is unavailable by default, because only some of the ISO settings are configured.</span></span>  
  
 <span data-ttu-id="920d1-108">**SET QUOTED_IDENTIFIER**</span><span class="sxs-lookup"><span data-stu-id="920d1-108">**SET QUOTED_IDENTIFIER**</span></span>  
 <span data-ttu-id="920d1-109">用引号将对象标识符引起来。</span><span class="sxs-lookup"><span data-stu-id="920d1-109">Surround object identifiers with quotation marks.</span></span> <span data-ttu-id="920d1-110">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="920d1-110">This option is selected by default.</span></span>  
  
 <span data-ttu-id="920d1-111">**SET ANSI_NULL_DFLT_ON**</span><span class="sxs-lookup"><span data-stu-id="920d1-111">**SET ANSI_NULL_DFLT_ON**</span></span>  
 <span data-ttu-id="920d1-112">在 CREATE TABLE 或 ALTER TABLE 语句执行过程中，没有显式定义为 NOTNULL 的所有用户定义的数据类型或列都将默认为允许空值。</span><span class="sxs-lookup"><span data-stu-id="920d1-112">Allow null values for all user-defined data types or columns that are not explicitly defined as NOTNULL during a CREATE TABLE or ALTER TABLE statement (the default state).</span></span> <span data-ttu-id="920d1-113">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="920d1-113">This option is selected by default.</span></span>  
  
 <span data-ttu-id="920d1-114">**SET IMPLICIT_TRANSACTIONS**</span><span class="sxs-lookup"><span data-stu-id="920d1-114">**SET IMPLICIT_TRANSACTIONS**</span></span>  
 <span data-ttu-id="920d1-115">默认情况下不选择此选项。</span><span class="sxs-lookup"><span data-stu-id="920d1-115">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="920d1-116">**SET CURSOR_CLOSE_ON_COMMIT**</span><span class="sxs-lookup"><span data-stu-id="920d1-116">**SET CURSOR_CLOSE_ON_COMMIT**</span></span>  
 <span data-ttu-id="920d1-117">在提交事务时，自动关闭所有打开的游标（遵从 ISO 标准）。</span><span class="sxs-lookup"><span data-stu-id="920d1-117">Close any open cursors automatically (in compliance with ISO) when a transaction is committed.</span></span> <span data-ttu-id="920d1-118">如果清除此选项（设置为 OFF），游标将跨越事务边界始终保持打开状态，游标只有在关闭连接或显示关闭它们时才关闭。</span><span class="sxs-lookup"><span data-stu-id="920d1-118">When cleared (set to OFF), cursors remain open across transaction boundaries, closing only when the connection is closed or when they are explicitly closed.</span></span> <span data-ttu-id="920d1-119">默认情况下不选择此选项。</span><span class="sxs-lookup"><span data-stu-id="920d1-119">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="920d1-120">**SET ANSI_PADDING**</span><span class="sxs-lookup"><span data-stu-id="920d1-120">**SET ANSI_PADDING**</span></span>  
 <span data-ttu-id="920d1-121">控制列存储小于列定义大小的值的方式，以及列存储在**char**、 **varchar**、 **binary**和**varbinary**数据中具有尾随空格的值的方式。</span><span class="sxs-lookup"><span data-stu-id="920d1-121">Controls the way the column stores values shorter than the defined size of the column, and the way the column stores values that have trailing blanks in **char**, **varchar**, **binary**, and **varbinary** data.</span></span> <span data-ttu-id="920d1-122">此设置只影响新列的定义。</span><span class="sxs-lookup"><span data-stu-id="920d1-122">This setting affects only the definition of new columns.</span></span> <span data-ttu-id="920d1-123">创建列后， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 会基于创建列时的设置存储这些值。</span><span class="sxs-lookup"><span data-stu-id="920d1-123">After the column is created, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the values based on the setting when the column was created.</span></span> <span data-ttu-id="920d1-124">以后对此设置的更改不会影响现有的列。</span><span class="sxs-lookup"><span data-stu-id="920d1-124">Existing columns are not affected by a later change to this setting.</span></span> <span data-ttu-id="920d1-125">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="920d1-125">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="920d1-126">**SET ANSI_WARNINGS**</span><span class="sxs-lookup"><span data-stu-id="920d1-126">**SET ANSI_WARNINGS**</span></span>  
 <span data-ttu-id="920d1-127">指定对几种错误条件采用 ISO 标准行为：</span><span class="sxs-lookup"><span data-stu-id="920d1-127">Specifies ISO standard behavior for several error conditions:</span></span>  
  
-   <span data-ttu-id="920d1-128">选中此复选框后，如果在聚合函数（如 SUM、AVG、MAX、MIN、STDEV、STDEVP、VAR、VARP 或 COUNT）中出现了空值，则会生成一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="920d1-128">When this check box is selected, if null values appear in aggregate functions (such as SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP, or COUNT), a warning message is generated.</span></span> <span data-ttu-id="920d1-129">当为**OFF**时，不发出警告。</span><span class="sxs-lookup"><span data-stu-id="920d1-129">When **OFF**, no warning is issued.</span></span>  
  
-   <span data-ttu-id="920d1-130">如果清除此复选框，则在发生被零除错误和算术溢出错误时，将导致语句回滚并生成一条错误信息。</span><span class="sxs-lookup"><span data-stu-id="920d1-130">When this check box is cleared, divide-by-zero and arithmetic overflow errors cause the statement to be rolled back and an error message is generated.</span></span> <span data-ttu-id="920d1-131">如果设置为 OFF，则在发生被零除错误和算术溢出错误时，将导致返回空值。</span><span class="sxs-lookup"><span data-stu-id="920d1-131">When OFF, divide-by-zero and arithmetic overflow errors cause null values to be returned.</span></span> <span data-ttu-id="920d1-132">如果尝试对 character、Unicode 或 binary 列执行 INSERT 或 UPDATE 操作，而这些列中的新值长度超出列的最大大小，那么，在发生被零除错误或算术溢出错误时，将导致返回空值。</span><span class="sxs-lookup"><span data-stu-id="920d1-132">The behavior in which a divide-by-zero or arithmetic overflow error causes null values to be returned occurs if an INSERTor UPDATEoperation is attempted on a character, Unicode, or binary column in which the length of a new value exceeds the maximum size of the column.</span></span> <span data-ttu-id="920d1-133">如果**SET ANSI_WARNINGS**为 ON，则根据 ISO 标准的指定取消插入或更新操作。</span><span class="sxs-lookup"><span data-stu-id="920d1-133">If **SET ANSI_WARNINGS** is ON, the INSERT or UPDATE operation is canceled as specified by the ISO standard.</span></span> <span data-ttu-id="920d1-134">字符列的尾随空格和二进制列的尾随零都将被忽略。</span><span class="sxs-lookup"><span data-stu-id="920d1-134">Trailing blanks are ignored for character columns, and trailing nulls are ignored for binary columns.</span></span> <span data-ttu-id="920d1-135">设置为 OFF 时，数据将剪裁为列的大小，并且语句执行成功。</span><span class="sxs-lookup"><span data-stu-id="920d1-135">When OFF, data is truncated to the size of the column and the statement succeeds.</span></span>  
  
 <span data-ttu-id="920d1-136">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="920d1-136">This option is selected by default.</span></span>  
  
 <span data-ttu-id="920d1-137">**SET ANSI_NULLS**</span><span class="sxs-lookup"><span data-stu-id="920d1-137">**SET ANSI_NULLS**</span></span>  
 <span data-ttu-id="920d1-138">指定在与 Null 值一起使用等于 (`=`) 和不等于 (`<>`) 比较运算符时采用符合 ISO 标准的行为。</span><span class="sxs-lookup"><span data-stu-id="920d1-138">Specifies ISO compliant behavior of the Equal (`=`) and Not Equal to (`<>`) comparison operators when used with null values.</span></span> <span data-ttu-id="920d1-139">当选中 **SET ANSI_NULLS** 时，所有与 Null 值进行比较求得的值均为 UNKNOWN，这是符合 ISO 标准的行为。</span><span class="sxs-lookup"><span data-stu-id="920d1-139">When **SET ANSI_NULLS** is selected, all comparisons against a null value evaluate to UNKNOWN, the ISO compliant behavior.</span></span> <span data-ttu-id="920d1-140">如果未选中 **SET ANSI_NULLS** ，则在数据值为 NULL 时，所有数据与空值的比较求得的值为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="920d1-140">When **SET ANSI_NULLS** is not selected, comparisons of all data against a null value evaluate to TRUE if the data value is NULL.</span></span> <span data-ttu-id="920d1-141">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="920d1-141">This option is selected by default.</span></span>  
  
 <span data-ttu-id="920d1-142">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="920d1-142">**Reset to Default**</span></span>  
 <span data-ttu-id="920d1-143">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="920d1-143">Resets all values on this page to the original default values.</span></span>  
  
  
