---
title: 用于输入搜索值的规则 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], searches
- date searches
- dates [SQL Server], searches
- embedding apostrophes [SQL Server]
- logical value searches [SQL Server]
- case-sensitive search matches
- search criteria [SQL Server], rules
- text value searches [SQL Server]
- numeric value searches [SQL Server]
ms.assetid: 3c8134b7-83f4-41b4-99c8-e3949a685ff5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 907bcac93863bc5660993e910b37e25e25a129b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577992"
---
# <a name="rules-for-entering-search-values-visual-database-tools"></a><span data-ttu-id="96a13-102">输入搜索值的规则 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="96a13-102">Rules for Entering Search Values (Visual Database Tools)</span></span>
  <span data-ttu-id="96a13-103">本主题讨论当为搜索条件输入以下类型的文本值时必须遵循的约定：</span><span class="sxs-lookup"><span data-stu-id="96a13-103">This topic discusses the conventions you must use when entering the following types of literal values for a search condition:</span></span>  
  
-   <span data-ttu-id="96a13-104">文本值</span><span class="sxs-lookup"><span data-stu-id="96a13-104">Text values</span></span>  
  
-   <span data-ttu-id="96a13-105">数值</span><span class="sxs-lookup"><span data-stu-id="96a13-105">Numeric values</span></span>  
  
-   <span data-ttu-id="96a13-106">日期</span><span class="sxs-lookup"><span data-stu-id="96a13-106">Dates</span></span>  
  
-   <span data-ttu-id="96a13-107">逻辑值</span><span class="sxs-lookup"><span data-stu-id="96a13-107">Logical values</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96a13-108">本主题中的信息派生自标准 SQL-92 的规则。</span><span class="sxs-lookup"><span data-stu-id="96a13-108">The information in this topic is derived from the rules for standard SQL-92.</span></span> <span data-ttu-id="96a13-109">但是，每个数据库能够以自己的方式实现 SQL。</span><span class="sxs-lookup"><span data-stu-id="96a13-109">However, each database can implement SQL in its own way.</span></span> <span data-ttu-id="96a13-110">因此，这里提供的准则不一定适用于每一种情况。</span><span class="sxs-lookup"><span data-stu-id="96a13-110">Therefore, the guidelines provided here might not apply in every case.</span></span> <span data-ttu-id="96a13-111">如果在如何为某个数据库输入搜索值方面有任何疑问，请参阅您所使用的数据库文档。</span><span class="sxs-lookup"><span data-stu-id="96a13-111">If you have questions about how to enter search values for a particular database, refer to the documentation for the database that you are using.</span></span>  
  
## <a name="searching-on-text-values"></a><span data-ttu-id="96a13-112">搜索文本值</span><span class="sxs-lookup"><span data-stu-id="96a13-112">Searching on Text Values</span></span>  
 <span data-ttu-id="96a13-113">以下准则适用于在搜索条件中输入文本值时的情况：</span><span class="sxs-lookup"><span data-stu-id="96a13-113">The following guidelines apply when you enter text values in search conditions:</span></span>  
  
-   <span data-ttu-id="96a13-114">**引号** 将文本值放到单引号内，如下例中的姓氏：</span><span class="sxs-lookup"><span data-stu-id="96a13-114">**Quotation marks** Enclose text values in single quotation marks, as in this example for a last name:</span></span>  
  
    ```  
    'Smith'  
    ```  
  
     <span data-ttu-id="96a13-115">如果在 [条件窗格](visual-database-tools.md)中输入搜索条件，则只需键入文本值，查询和视图设计器将自动为该值括上单引号。</span><span class="sxs-lookup"><span data-stu-id="96a13-115">If you are entering a search condition in the [Criteria Pane](visual-database-tools.md), you can simply type the text value and the Query and View Designer will automatically put single quotation marks around it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96a13-116">在某些数据库中，单引号内的项被解释为文本值，而双引号内的项被解释为数据库对象，如列引用或表引用。</span><span class="sxs-lookup"><span data-stu-id="96a13-116">In some databases, terms in single quotation marks are interpreted as literal values, whereas terms in double quotation marks are interpreted as database objects such as column or table references.</span></span> <span data-ttu-id="96a13-117">因此，尽管查询和视图设计器能够接受双引号中的项，但对其所做的解释有可能与您预期的不同。</span><span class="sxs-lookup"><span data-stu-id="96a13-117">Therefore, even though the Query and View Designer can accept terms in double quotation marks, it might interpret them differently than you expect.</span></span>  
  
-   <span data-ttu-id="96a13-118">**嵌入的撇号** 如果搜索的数据包含一个单引号（撇号），则可以输入两个单引号以指示该单引号是文本值而非分隔符。</span><span class="sxs-lookup"><span data-stu-id="96a13-118">**Embedding apostrophes** If the data you are searching for contains a single quotation mark (an apostrophe), you can enter two single quotation marks to indicate that you mean the single quotation mark as a literal value and not a delimiter.</span></span> <span data-ttu-id="96a13-119">例如，下面的条件将搜索值“Swann's Way”：</span><span class="sxs-lookup"><span data-stu-id="96a13-119">For example, the following condition searches for the value "Swann's Way:"</span></span>  
  
    ```  
    ='Swann''s Way'  
    ```  
  
-   <span data-ttu-id="96a13-120">**长度限制** 当输入长字符串时，不要超过数据库 SQL 语句的最大长度。</span><span class="sxs-lookup"><span data-stu-id="96a13-120">**Length limits** Do not exceed the maximum length of the SQL statement for your database when entering long strings.</span></span>  
  
-   <span data-ttu-id="96a13-121">**区分大小写** 遵循所用数据库大小写区分规则。</span><span class="sxs-lookup"><span data-stu-id="96a13-121">**Case sensitivity** Follow the case sensitivity rules for the database you are using.</span></span> <span data-ttu-id="96a13-122">所使用的数据库决定文本搜索是否区分大小写。</span><span class="sxs-lookup"><span data-stu-id="96a13-122">The database you are using determines whether text searches are case sensitive.</span></span> <span data-ttu-id="96a13-123">例如，某些数据库将运算符“=”解释为精确区分大小写匹配，而有些数据库则允许匹配任意大写和小写字符组合。</span><span class="sxs-lookup"><span data-stu-id="96a13-123">For example, some databases interpret the operator "=" to mean an exact case-sensitive match, but others will allow matches on any combination of uppercase and lowercase characters.</span></span>  
  
     <span data-ttu-id="96a13-124">如果不能确定数据库是否使用区分大小写搜索，可以在搜索条件中使用 UPPER 或 LOWER 函数转换搜索数据的大小写，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="96a13-124">If you are unsure about whether the database uses a case-sensitive search, you can use the UPPER or LOWER functions in the search condition to convert the case of the search data, as illustrated in the following example:</span></span>  
  
    ```  
    WHERE UPPER(lname) = 'SMITH'  
    ```  
  
## <a name="searching-on-numeric-values"></a><span data-ttu-id="96a13-125">搜索数值</span><span class="sxs-lookup"><span data-stu-id="96a13-125">Searching on Numeric Values</span></span>  
 <span data-ttu-id="96a13-126">以下准则适用于在搜索条件中输入数值时的情况：</span><span class="sxs-lookup"><span data-stu-id="96a13-126">The following guidelines apply when you enter numeric values in search conditions:</span></span>  
  
-   <span data-ttu-id="96a13-127">**引号** 不能将数字放在引号内。</span><span class="sxs-lookup"><span data-stu-id="96a13-127">**Quotation marks** Do not enclose numbers in quotation marks.</span></span>  
  
-   <span data-ttu-id="96a13-128">**非数字字符** 除小数点分隔符（在 Windows 控制面板的“区域设置”  对话框中定义）和负号 (-) 之外，不能包含非数字字符。</span><span class="sxs-lookup"><span data-stu-id="96a13-128">**Non-numeric characters** Do not include non-numeric characters except the decimal separator (as defined in the **Regional Settings** dialog box of Windows Control Panel) and negative sign (-).</span></span> <span data-ttu-id="96a13-129">不能包含数字分组符号（如千位间的逗号）或货币符号。</span><span class="sxs-lookup"><span data-stu-id="96a13-129">Do not include digit grouping symbols (such as a comma between thousands) or currency symbols.</span></span>  
  
-   <span data-ttu-id="96a13-130">**小数点标记** 如果输入整数，则可以包含小数点标记，无论所搜索的值是整数还是实数。</span><span class="sxs-lookup"><span data-stu-id="96a13-130">**Decimal marks** If you are entering whole numbers, you can include a decimal mark, whether the value you are searching for is an integer or a real number.</span></span>  
  
-   <span data-ttu-id="96a13-131">**科学记数法** 可以使用科学记数法输入非常大或非常小的数字，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="96a13-131">**Scientific notation** You can enter very large or very small numbers using scientific notation, as in this example:</span></span>  
  
    ```  
    > 1.23456e-9  
    ```  
  
## <a name="searching-on-dates"></a><span data-ttu-id="96a13-132">搜索日期</span><span class="sxs-lookup"><span data-stu-id="96a13-132">Searching on Dates</span></span>  
 <span data-ttu-id="96a13-133">用来输入日期的格式取决于所使用的数据库和在查询和视图设计器的哪个窗格中输入日期。</span><span class="sxs-lookup"><span data-stu-id="96a13-133">The format you use to enter dates depends on the database you are using and in what pane of the Query and View Designer you are entering the date.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96a13-134">如果不知道数据源所使用的格式，请在“条件”窗格的筛选器列中以您所熟悉的任何格式输入日期。</span><span class="sxs-lookup"><span data-stu-id="96a13-134">If you don't know which format your data source uses, type a date into the filter column of the Criteria pane in any format familiar to you.</span></span> <span data-ttu-id="96a13-135">设计器会将大多数这样的输入转换为正确的格式。</span><span class="sxs-lookup"><span data-stu-id="96a13-135">The designer will convert most of such entries into the appropriate format.</span></span>  
  
 <span data-ttu-id="96a13-136">查询和视图设计器可以使用以下日期格式：</span><span class="sxs-lookup"><span data-stu-id="96a13-136">The Query and View Designer can work with the following date formats:</span></span>  
  
-   <span data-ttu-id="96a13-137">**区域设置特定** 在“Windows 区域设置属性”  对话框中指定的日期格式。</span><span class="sxs-lookup"><span data-stu-id="96a13-137">**Locale-specific** The format specified for dates in the **Windows Regional Settings Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="96a13-138">**数据库特定** 数据库可以理解的任何格式。</span><span class="sxs-lookup"><span data-stu-id="96a13-138">**Database-specific** Any format understood by the database.</span></span>  
  
-   <span data-ttu-id="96a13-139">**ANSI 标准日期** 使用大括号、标记“d”指定日期和日期字符串的格式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="96a13-139">**ANSI standard date** A format that uses braces, the marker 'd' to designate the date, and a date string, as in the following example:</span></span>  
  
    ```  
    { d '1990-12-31' }  
    ```  
  
-   <span data-ttu-id="96a13-140">**ANSI 标准日期时间** 与 ANSI 标准日期相似，但用“ts”代替“d”，并在日期中添加小时、分钟和秒（使用 24 小时制），如下例中的 1990 年 12 月 31 日：</span><span class="sxs-lookup"><span data-stu-id="96a13-140">**ANSI standard datetime** Similar to ANSI-standard date, but uses 'ts' instead of 'd' and adds hours, minutes, and seconds to the date (using a 24-hour clock), as in this example for December 31, 1990:</span></span>  
  
    ```  
    { ts '1990-12-31 00:00:00' }  
    ```  
  
     <span data-ttu-id="96a13-141">通常，ANSI 标准日期格式用于那些使用真实日期数据类型表示日期的数据库。</span><span class="sxs-lookup"><span data-stu-id="96a13-141">In general, the ANSI standard date format is used with databases that represent dates using a true date data type.</span></span> <span data-ttu-id="96a13-142">相反，日期时间格式用于支持 datetime 数据类型的数据库。</span><span class="sxs-lookup"><span data-stu-id="96a13-142">In contrast, the datetime format is used with databases that support a datetime data type.</span></span>  
  
 <span data-ttu-id="96a13-143">下表汇总了可在查询和视图设计器的不同窗格中使用的日期格式：</span><span class="sxs-lookup"><span data-stu-id="96a13-143">The following table summarizes the date format that you can use in different panes of the Query and View Designer.</span></span>  
  
|<span data-ttu-id="96a13-144">**窗格**</span><span class="sxs-lookup"><span data-stu-id="96a13-144">**Pane**</span></span>|<span data-ttu-id="96a13-145">**日期格式**</span><span class="sxs-lookup"><span data-stu-id="96a13-145">**Date format**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="96a13-146">条件</span><span class="sxs-lookup"><span data-stu-id="96a13-146">Criteria</span></span>|<span data-ttu-id="96a13-147">区域设置特定、数据库特定、ANSI 标准</span><span class="sxs-lookup"><span data-stu-id="96a13-147">Locale-specific Database-specific ANSI standard</span></span><br /><br /> <span data-ttu-id="96a13-148">在 [条件窗格](visual-database-tools.md) 中输入的日期将在 SQL 窗格中转换成与数据库兼容的格式。</span><span class="sxs-lookup"><span data-stu-id="96a13-148">Dates entered in the [Criteria Pane](visual-database-tools.md) are converted to a database-compatible format in the SQL pane.</span></span>|  
|<span data-ttu-id="96a13-149">SQL</span><span class="sxs-lookup"><span data-stu-id="96a13-149">SQL</span></span>|<span data-ttu-id="96a13-150">数据库特定、ANSI 标准</span><span class="sxs-lookup"><span data-stu-id="96a13-150">Database-specific ANSI standard</span></span>|  
|<span data-ttu-id="96a13-151">结果</span><span class="sxs-lookup"><span data-stu-id="96a13-151">Results</span></span>|<span data-ttu-id="96a13-152">区域设置特定</span><span class="sxs-lookup"><span data-stu-id="96a13-152">Locale-specific</span></span>|  
  
## <a name="searching-on-logical-values"></a><span data-ttu-id="96a13-153">搜索逻辑值</span><span class="sxs-lookup"><span data-stu-id="96a13-153">Searching on Logical Values</span></span>  
 <span data-ttu-id="96a13-154">逻辑数据的格式因数据库而异。</span><span class="sxs-lookup"><span data-stu-id="96a13-154">The format of logical data varies from database to database.</span></span> <span data-ttu-id="96a13-155">False 值通常存储为零 (0)。</span><span class="sxs-lookup"><span data-stu-id="96a13-155">Very frequently, a value of False is stored as zero (0).</span></span> <span data-ttu-id="96a13-156">True 值通常存储为 1，有时存储为 -1。</span><span class="sxs-lookup"><span data-stu-id="96a13-156">A value of True is most frequently stored as 1 and occasionally as -1.</span></span> <span data-ttu-id="96a13-157">以下准则适用于在搜索条件中输入逻辑值时的情况：</span><span class="sxs-lookup"><span data-stu-id="96a13-157">The following guidelines apply when you enter logical values in search conditions:</span></span>  
  
-   <span data-ttu-id="96a13-158">若要搜索 False 值，请使用零，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="96a13-158">To search for a value of False, use a zero, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 0  
    ```  
  
-   <span data-ttu-id="96a13-159">如果在搜索 True 值时不能确定使用什么格式，可尝试使用 1，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="96a13-159">If you are not sure what format to use when searching for a True value, try using 1, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 1  
    ```  
  
-   <span data-ttu-id="96a13-160">或者，也可以通过搜索任何非零值来扩大搜索范围，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="96a13-160">Alternatively, you can broaden the scope of the search by searching for any non-zero value, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract <> 0  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="96a13-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96a13-161">See Also</span></span>  
 [<span data-ttu-id="96a13-162">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="96a13-162">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
