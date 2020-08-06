---
title: 高级 Integration Services 表达式的示例 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb1e8dc6f9bffd22c917414f80f6ba9f257b25b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585915"
---
# <a name="examples-of-advanced-integration-services-expressions"></a><span data-ttu-id="1d152-102">高级 Integration Services 表达式的示例</span><span class="sxs-lookup"><span data-stu-id="1d152-102">Examples of Advanced Integration Services Expressions</span></span>
  <span data-ttu-id="1d152-103">本节提供合并多个运算符和函数的高级表达式示例。</span><span class="sxs-lookup"><span data-stu-id="1d152-103">This section provides examples of advanced expressions that combine multiple operators and functions.</span></span> <span data-ttu-id="1d152-104">如果表达式用于优先约束或有条件拆分转换中，则其计算结果必须为布尔值。</span><span class="sxs-lookup"><span data-stu-id="1d152-104">If an expression is used in a precedence constraint or the Conditional Split transformation, it must evaluate to a Boolean.</span></span> <span data-ttu-id="1d152-105">但是，这一限制并不适用于属性表达式、变量、派生列转换或 For 循环容器中使用的表达式。</span><span class="sxs-lookup"><span data-stu-id="1d152-105">That restriction, however, does not apply to expressions used in property expressions, variables, the Derived Column transformation, or the For Loop container.</span></span>  
  
 <span data-ttu-id="1d152-106">下列示例使用 AdventureWorks 和  [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 数据库[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d152-106">The following examples use the **AdventureWorks** and the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="1d152-107">每个示例都标识了其使用的表。</span><span class="sxs-lookup"><span data-stu-id="1d152-107">Each example identifies the tables it uses.</span></span>  
  
## <a name="boolean-expressions"></a><span data-ttu-id="1d152-108">布尔表达式</span><span class="sxs-lookup"><span data-stu-id="1d152-108">Boolean Expressions</span></span>  
  
-   <span data-ttu-id="1d152-109">此示例使用 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-109">This example uses the **Product** table.</span></span> <span data-ttu-id="1d152-110">表达式计算 **SellStartDate** 列中的月份项，如果月份为六月或更晚，则返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="1d152-110">The expression evaluates the month entry in the **SellStartDate** column and returns TRUE if the month is June or later.</span></span>  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   <span data-ttu-id="1d152-111">此示例使用 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-111">This example uses the **Product** table.</span></span> <span data-ttu-id="1d152-112">表达式计算 **ListPrice** 列被 **StandardCost** 列除后的舍入结果，如果结果大于 1.5，则返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="1d152-112">The expression evaluates the rounded result of dividing the **ListPrice** column by the **StandardCost** column, and returns TRUE if the result is greater than 1.5.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   <span data-ttu-id="1d152-113">此示例使用 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-113">This example uses the **Product** table.</span></span> <span data-ttu-id="1d152-114">如果三个运算的计算结果都为 TRUE，则表达式返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="1d152-114">The expression returns TRUE if all three operations evaluate to TRUE.</span></span> <span data-ttu-id="1d152-115">如果 **Size** 列和 **BikeSize** 变量具有不兼容的数据类型，则表达式就需要进行显式转换，如第二个示例所示。</span><span class="sxs-lookup"><span data-stu-id="1d152-115">If the **Size** column and the **BikeSize** variable have incompatible data types, the expression requires an explicit cast as shown the second example.</span></span> <span data-ttu-id="1d152-116">到 DT_WSTR 的转换包括字符串的长度。</span><span class="sxs-lookup"><span data-stu-id="1d152-116">The cast to DT_WSTR includes the length of the string.</span></span>  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   <span data-ttu-id="1d152-117">此示例使用 **CurrencyRate** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-117">This example uses the **CurrencyRate** table.</span></span> <span data-ttu-id="1d152-118">表达式比较表和变量中的值。</span><span class="sxs-lookup"><span data-stu-id="1d152-118">The expression compares values in tables and variables.</span></span> <span data-ttu-id="1d152-119">如果 **FromCurrencyCode** 或 **ToCurrencyCode** 列中的项等于变量值，且 **AverageRate** 中的值大于 **EndOfDayRate**中的值，则返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="1d152-119">It returns TRUE if entries in the **FromCurrencyCode** or **ToCurrencyCode** columns are equal to variable values and if the value in **AverageRate** is greater that the value in **EndOfDayRate**.</span></span>  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   <span data-ttu-id="1d152-120">此示例使用 **Currency** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-120">This example uses the **Currency** table.</span></span> <span data-ttu-id="1d152-121">如果 **Name** 列的第一个字符不是 a 或 A，则表达式返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="1d152-121">The expression returns TRUE if the first character in the **Name** column is not a or A.</span></span>  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     <span data-ttu-id="1d152-122">下列表达式提供相同的结果，但效率更高（因为只有一个字符被转换为大写）。</span><span class="sxs-lookup"><span data-stu-id="1d152-122">The following expression provides the same results, but it is more efficient because only one character is converted to uppercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a><span data-ttu-id="1d152-123">非布尔表达式</span><span class="sxs-lookup"><span data-stu-id="1d152-123">Non-Boolean Expressions</span></span>  
 <span data-ttu-id="1d152-124">非布尔表达式用于派生列转换、属性表达式和 For 循环容器中。</span><span class="sxs-lookup"><span data-stu-id="1d152-124">Non-Boolean expressions are used in the Derived Column transformation, property expressions, and the For Loop container.</span></span>  
  
-   <span data-ttu-id="1d152-125">此示例使用 **Contact** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-125">This example uses the **Contact** table.</span></span> <span data-ttu-id="1d152-126">表达式删除 **FirstName**、 **MiddleName**和 **LastName** 列中的前导空格和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="1d152-126">The expression removes leading and trailing spaces from the **FirstName**, **MiddleName**, and **LastName** columns.</span></span> <span data-ttu-id="1d152-127">如果 **MiddleName** 列不为空，则提取其第一个字母，将该中间名首字母与 **FirstName** 和 **LastName**中的值连接，并在值之间插入适当的空格。</span><span class="sxs-lookup"><span data-stu-id="1d152-127">It extracts the first letter of the **MiddleName** column if it is not null, concatenates the middle initial and the values in **FirstName** and **LastName**, and inserts appropriate spaces between values.</span></span>  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   <span data-ttu-id="1d152-128">此示例使用 **Contact** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-128">This example uses the **Contact** table.</span></span> <span data-ttu-id="1d152-129">表达式验证 **Salutation** 列中的项。</span><span class="sxs-lookup"><span data-stu-id="1d152-129">The expression validates entries in the **Salutation** column.</span></span> <span data-ttu-id="1d152-130">它返回 **Salutation** 项或空字符串。</span><span class="sxs-lookup"><span data-stu-id="1d152-130">It returns a **Salutation** entry or an empty string.</span></span>  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   <span data-ttu-id="1d152-131">此示例使用 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-131">This example uses the **Product** table.</span></span> <span data-ttu-id="1d152-132">表达式将 **Color** 列中的第一个字符转换为大写，并将其余字符转换为小写。</span><span class="sxs-lookup"><span data-stu-id="1d152-132">The expression converts the first character in the **Color** column to uppercase and converts remaining characters to lowercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   <span data-ttu-id="1d152-133">此示例使用 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-133">This example uses the **Product** table.</span></span> <span data-ttu-id="1d152-134">表达式计算产品的销售月份数，并在 **SellStartDate** 或 **SellEndDate** 列包含 NULL 时，返回字符串“Unknown”。</span><span class="sxs-lookup"><span data-stu-id="1d152-134">The expression calculates the number of months a product has been sold and returns the string "Unknown" if either the **SellStartDate** or the **SellEndDate** column contains NULL.</span></span>  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   <span data-ttu-id="1d152-135">此示例使用 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="1d152-135">This example uses the **Product** table.</span></span> <span data-ttu-id="1d152-136">表达式计算 **StandardCost** 列上的加成，并将结果舍入到小数点后两位。</span><span class="sxs-lookup"><span data-stu-id="1d152-136">The expression calculates the markup on the **StandardCost** column and rounds the result to a precision of two.</span></span> <span data-ttu-id="1d152-137">结果以百分比表示。</span><span class="sxs-lookup"><span data-stu-id="1d152-137">The result is presented as a percentage.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a><span data-ttu-id="1d152-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1d152-138">Related Tasks</span></span>  
 [<span data-ttu-id="1d152-139">在数据流组件中使用表达式</span><span class="sxs-lookup"><span data-stu-id="1d152-139">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="1d152-140">相关内容</span><span class="sxs-lookup"><span data-stu-id="1d152-140">Related Content</span></span>  
 <span data-ttu-id="1d152-141">pragmaticworks.com 上的技术文章 [SSIS 表达式小抄表](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)。</span><span class="sxs-lookup"><span data-stu-id="1d152-141">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
