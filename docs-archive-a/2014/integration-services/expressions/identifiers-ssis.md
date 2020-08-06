---
title: 标识符 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- regular identifiers [Integration Services]
- variables [Integration Services], expressions
- identifiers [Integration Services]
- expressions [Integration Services], variables
- lineage identifiers
- columns [Integration Services], identifiers
- names [Integration Services]
- expressions [Integration Services], identifiers
- qualified identifiers [Integration Services]
ms.assetid: 56af984d-88b4-4db8-b6a2-6b07315a699e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 751830d30f26e9b182b3b926549760d1df517914
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689997"
---
# <a name="identifiers-ssis"></a><span data-ttu-id="8a301-102">标识符 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="8a301-102">Identifiers (SSIS)</span></span>
  <span data-ttu-id="8a301-103">在表达式中，标识符是可供运算使用的列和变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-103">In expressions, identifiers are columns and variables that are available to the operation.</span></span> <span data-ttu-id="8a301-104">表达式可以使用常规标识符和限定标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-104">Expressions can use regular and qualified identifiers.</span></span>  
  
## <a name="regular-identifiers"></a><span data-ttu-id="8a301-105">常规标识符</span><span class="sxs-lookup"><span data-stu-id="8a301-105">Regular Identifiers</span></span>  
 <span data-ttu-id="8a301-106">常规标识符是不需要其他限定符的标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-106">A regular identifier is an identifier that needs no additional qualifiers.</span></span> <span data-ttu-id="8a301-107">例如， **MiddleName**（ **AdventureWorks** 数据库的 **Contacts** 表中的列）是常规标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-107">For example, **MiddleName**, a column in the **Contacts** table of the **AdventureWorks** database, is a regular identifier.</span></span>  
  
 <span data-ttu-id="8a301-108">常规标识符的命名必须遵循以下这些规则：</span><span class="sxs-lookup"><span data-stu-id="8a301-108">The naming of regular identifiers must follow these rules:</span></span>  
  
-   <span data-ttu-id="8a301-109">按照 Unicode 标准 2.0 的规定，名称的第一个字符必须是字母，或者是下划线“_”。</span><span class="sxs-lookup"><span data-stu-id="8a301-109">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="8a301-110">后面的字符可以是在 Unicode 标准 2.0 中定义的字母或数字、下划线 (_) 以及字符 \@、$ 和 #。</span><span class="sxs-lookup"><span data-stu-id="8a301-110">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8a301-111">常规标识符中不能包含空格和特殊字符（上述特殊字符除外）。</span><span class="sxs-lookup"><span data-stu-id="8a301-111">Embedded spaces and special characters, other than the ones listed, are not valid in regular identifiers.</span></span> <span data-ttu-id="8a301-112">若要使用空格和特殊字符，必须使用限定标识符而不是常规标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-112">In order to use spaces and special characters, you must use a qualified identifier instead of a regular identifier.</span></span>  
  
## <a name="qualified-identifiers"></a><span data-ttu-id="8a301-113">限定标识符</span><span class="sxs-lookup"><span data-stu-id="8a301-113">Qualified Identifiers</span></span>  
 <span data-ttu-id="8a301-114">限定标识符是由方括号分隔的标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-114">A qualified identifier is an identifier that is delimited by brackets.</span></span> <span data-ttu-id="8a301-115">标识符可能需要分隔符，因为标识符名称包括空格，或标识符名称不以字母或下划线字符开头。</span><span class="sxs-lookup"><span data-stu-id="8a301-115">An identifier may require a delimiter because the name of the identifier includes spaces, or because the identifier name does not begin with either a letter or the underscore character.</span></span> <span data-ttu-id="8a301-116">例如，列名 **Middle Name** 必须由方括号限定，在表达式中书写为 [Middle Name]。</span><span class="sxs-lookup"><span data-stu-id="8a301-116">For example, the column name **Middle Name** must be qualified by brackets and written as [Middle Name] in an expression.</span></span>  
  
 <span data-ttu-id="8a301-117">如果标识符的名称包含空格或名称不是有效的常规标识符名称，则必须对该标识符进行限定。</span><span class="sxs-lookup"><span data-stu-id="8a301-117">If the name of the identifier includes spaces, or if the name is not a valid regular identifier name, the identifier must be qualified.</span></span> <span data-ttu-id="8a301-118">表达式计算器使用左右方括号 ([]) 来限定标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-118">The expression evaluator uses the opening and closing ([]) brackets to qualify identifiers.</span></span> <span data-ttu-id="8a301-119">方括号置于字符串的开头和末尾。</span><span class="sxs-lookup"><span data-stu-id="8a301-119">The brackets are put in the first and the last position of the string.</span></span> <span data-ttu-id="8a301-120">例如，标识符 5$> 将变为 [5$>]。</span><span class="sxs-lookup"><span data-stu-id="8a301-120">For example, the identifier 5$> becomes [5$>].</span></span> <span data-ttu-id="8a301-121">方括号可与列名、变量名和函数名一起使用。</span><span class="sxs-lookup"><span data-stu-id="8a301-121">Brackets can be used with column names, variable names, and function names.</span></span>  
  
 <span data-ttu-id="8a301-122">如果使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器对话框生成表达式，则常规标识符将自动包含在方括号中。</span><span class="sxs-lookup"><span data-stu-id="8a301-122">If you build expressions using the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer dialog boxes, regular identifiers are automatically enclosed in brackets.</span></span> <span data-ttu-id="8a301-123">但是，只有当名称包括无效字符时，才需要括号。</span><span class="sxs-lookup"><span data-stu-id="8a301-123">However, brackets are required only if the name include invalid characters.</span></span> <span data-ttu-id="8a301-124">例如，名为 **MiddleName** 的列不带方括号也是有效的。</span><span class="sxs-lookup"><span data-stu-id="8a301-124">For example, the column named **MiddleName** is valid without brackets.</span></span>  
  
 <span data-ttu-id="8a301-125">不能在表达式中引用包含方括号的列名。</span><span class="sxs-lookup"><span data-stu-id="8a301-125">You cannot reference column names that include brackets in expressions.</span></span> <span data-ttu-id="8a301-126">例如，不能在表达式中使用列名 **Column[1]** 。</span><span class="sxs-lookup"><span data-stu-id="8a301-126">For example, the column name **Column[1]** cannot be used in an expression.</span></span> <span data-ttu-id="8a301-127">若要在表达式中使用此列，必须将其重命名为不带方括号的名称。</span><span class="sxs-lookup"><span data-stu-id="8a301-127">To use the column in an expression it must be renamed to a name without brackets.</span></span>  
  
## <a name="lineage-identifiers"></a><span data-ttu-id="8a301-128">沿袭标识符</span><span class="sxs-lookup"><span data-stu-id="8a301-128">Lineage Identifiers</span></span>  
 <span data-ttu-id="8a301-129">表达式可以使用沿袭标识符来引用列。</span><span class="sxs-lookup"><span data-stu-id="8a301-129">Expressions can use lineage identifiers to refer to columns.</span></span> <span data-ttu-id="8a301-130">沿袭标识符是在首次创建包时自动分配的。</span><span class="sxs-lookup"><span data-stu-id="8a301-130">The lineage identifiers are assigned automatically when you first create the package.</span></span> <span data-ttu-id="8a301-131">可以在 **设计器中** “高级编辑器” **对话框的** “列属性” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡上查看列的沿袭标识符。</span><span class="sxs-lookup"><span data-stu-id="8a301-131">You can view the lineage identifier for a column on the **Column Properties** tab of the **Advanced Editor** dialog box in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="8a301-132">如果使用列的沿袭标识符引用列，则标识符必须包含井号 (#) 字符前缀。</span><span class="sxs-lookup"><span data-stu-id="8a301-132">If you refer to a column using its lineage identifier, the identifier must include the pound (#) character prefix.</span></span> <span data-ttu-id="8a301-133">例如，必须将沿袭标识符为 147 的列引用为 #147。</span><span class="sxs-lookup"><span data-stu-id="8a301-133">For example, a column with the lineage identifier 147 must be referenced as #147.</span></span>  
  
 <span data-ttu-id="8a301-134">如果表达式分析成功，则表达式计算器会将沿袭标识符替换为对话框中的列名。</span><span class="sxs-lookup"><span data-stu-id="8a301-134">If an expression parses successfully, the expression evaluator replaces the lineage identifiers with column names in the dialog box.</span></span>  
  
## <a name="unique-column-names"></a><span data-ttu-id="8a301-135">唯一列名</span><span class="sxs-lookup"><span data-stu-id="8a301-135">Unique Column Names</span></span>  
 <span data-ttu-id="8a301-136">包中使用的多个组件可能以相同的名称显示列。</span><span class="sxs-lookup"><span data-stu-id="8a301-136">Multiple components used in a package can expose columns with the same name.</span></span> <span data-ttu-id="8a301-137">如果在表达式中使用这些列，则必须消除它们的歧义后才能成功分析表达式。</span><span class="sxs-lookup"><span data-stu-id="8a301-137">If these columns are used in expressions, they must be disambiguated before the expressions can be parsed successfully.</span></span> <span data-ttu-id="8a301-138">表达式计算器支持用点分表示法标识列的源。</span><span class="sxs-lookup"><span data-stu-id="8a301-138">The expression evaluator supports the dotted notation for identifying the source of the column.</span></span> <span data-ttu-id="8a301-139">例如，两个名为 **Age** 的列可以成为 **FlatFileSource.Age** 和 **OLEDBSource.Age**，这表示它们的源分别是 FlatFileSource 和 OLEDBSource。</span><span class="sxs-lookup"><span data-stu-id="8a301-139">For example, two columns named **Age** become **FlatFileSource.Age** and **OLEDBSource.Age**, which indicates that their sources are FlatFileSource or OLEDBSource.</span></span> <span data-ttu-id="8a301-140">分析器将完全限定名视为单个列名。</span><span class="sxs-lookup"><span data-stu-id="8a301-140">The parser treats the fully qualified name as a single column name.</span></span>  
  
 <span data-ttu-id="8a301-141">源组件名和列名是分别限定的。</span><span class="sxs-lookup"><span data-stu-id="8a301-141">Source component names and column names are qualified separately.</span></span> <span data-ttu-id="8a301-142">下列示例说明了点分表示法中方括号的有效用法：</span><span class="sxs-lookup"><span data-stu-id="8a301-142">The following examples show valid use of brackets in a dotted notation:</span></span>  
  
-   <span data-ttu-id="8a301-143">源组件名包含空格。</span><span class="sxs-lookup"><span data-stu-id="8a301-143">The source component name includes spaces.</span></span>  
  
    ```  
    [MySo urce].Age  
    ```  
  
-   <span data-ttu-id="8a301-144">列名的第一个字符无效。</span><span class="sxs-lookup"><span data-stu-id="8a301-144">The first character in the column name is not valid.</span></span>  
  
    ```  
    MySource.[#Age]  
    ```  
  
-   <span data-ttu-id="8a301-145">源组件名和列名包含无效字符。</span><span class="sxs-lookup"><span data-stu-id="8a301-145">The source component and the column names contain invalid characters.</span></span>  
  
    ```  
    [MySource?].[#Age]  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8a301-146">如果点分表示法中的两个元素括在一对方括号中，则表达式计算器会将此元素对解释为单个标识符，而不是源-列组合。</span><span class="sxs-lookup"><span data-stu-id="8a301-146">If both elements in dotted notation are enclosed in one pair of brackets, the expression evaluator interprets the pair as a single identifier, not a source-column combination.</span></span>  
  
## <a name="variables-in-expressions"></a><span data-ttu-id="8a301-147">表达式中的变量</span><span class="sxs-lookup"><span data-stu-id="8a301-147">Variables in Expressions</span></span>  
 <span data-ttu-id="8a301-148">表达式中引用的变量必须包含 \@ 前缀。</span><span class="sxs-lookup"><span data-stu-id="8a301-148">Variables, when referenced in expressions, must include the \@ prefix.</span></span> <span data-ttu-id="8a301-149">例如，使用 \@Counter 引用 Counter 变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-149">For example, the **Counter** variable is referenced by using \@Counter.</span></span> <span data-ttu-id="8a301-150">\@ 字符不属于变量名，仅向表达式计算器指明标识符是变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-150">The \@ character is not part of the variable name; it only identifies the variable to the expression evaluator.</span></span> <span data-ttu-id="8a301-151">如果使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器提供的对话框生成表达式，\@ 字符会自动添加到变量名中。</span><span class="sxs-lookup"><span data-stu-id="8a301-151">If you build expressions by using the dialog boxes that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, the \@ character is automatically added to the variable name.</span></span> <span data-ttu-id="8a301-152">在 \@ 字符和变量名之间添加的空格无效。</span><span class="sxs-lookup"><span data-stu-id="8a301-152">It is not valid to include spaces between the \@ character and the variable name.</span></span>  
  
 <span data-ttu-id="8a301-153">变量名和其他常规标识符遵循同样的规则：</span><span class="sxs-lookup"><span data-stu-id="8a301-153">Variable names follow the same rules as those for other regular identifiers:</span></span>  
  
-   <span data-ttu-id="8a301-154">按照 Unicode 标准 2.0 的规定，名称的第一个字符必须是字母，或者是下划线“_”。</span><span class="sxs-lookup"><span data-stu-id="8a301-154">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="8a301-155">后面的字符可以是在 Unicode 标准 2.0 中定义的字母或数字、下划线 (_) 以及字符 \@、$ 和 #。</span><span class="sxs-lookup"><span data-stu-id="8a301-155">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
 <span data-ttu-id="8a301-156">如果变量名中包含以上所列之外的字符，则必须将变量用方括号括起来。</span><span class="sxs-lookup"><span data-stu-id="8a301-156">If a variable name contains characters other than those listed, the variable must be enclosed in brackets.</span></span> <span data-ttu-id="8a301-157">例如，带有空格的变量名必须括在方括号内。</span><span class="sxs-lookup"><span data-stu-id="8a301-157">For example, variable names with spaces must be enclosed in brackets.</span></span> <span data-ttu-id="8a301-158">\@ 字符后面紧跟左括号。</span><span class="sxs-lookup"><span data-stu-id="8a301-158">The opening bracket follows the \@ character.</span></span> <span data-ttu-id="8a301-159">例如，My Name  变量被引用为 \@[My Name]。</span><span class="sxs-lookup"><span data-stu-id="8a301-159">For example, the **My Name** variable is referenced as \@[My Name].</span></span> <span data-ttu-id="8a301-160">如果变量名和方括号间包含空格，则无效。</span><span class="sxs-lookup"><span data-stu-id="8a301-160">It is not valid to include spaces between the variable name and the brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a301-161">用户定义的变量名和系统变量名区分大小写。</span><span class="sxs-lookup"><span data-stu-id="8a301-161">The names of user-defined and system variables are case-sensitive.</span></span>  
  
## <a name="unique-variable-names"></a><span data-ttu-id="8a301-162">唯一变量名</span><span class="sxs-lookup"><span data-stu-id="8a301-162">Unique Variable Names</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="8a301-163">支持自定义变量并提供一组系统变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-163">supports custom variables and provides a set of system variables.</span></span> <span data-ttu-id="8a301-164">默认情况下，自定义变量属于 **User** 命名空间，而系统变量属于 **System** 命名空间。</span><span class="sxs-lookup"><span data-stu-id="8a301-164">By default, custom variables belong to the **User** namespace, and system variables belong to the **System** namespace.</span></span> <span data-ttu-id="8a301-165">可以为自定义变量创建其他命名空间并更新命名空间名称来满足应用程序要求。</span><span class="sxs-lookup"><span data-stu-id="8a301-165">You can create additional namespaces for custom variables and update the namespace names to suit the needs of your application.</span></span> <span data-ttu-id="8a301-166">表达式生成器列出了所有命名空间中的作用域内变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-166">The expression builder lists in-scope variables in all namespaces.</span></span>  
  
 <span data-ttu-id="8a301-167">所有变量都有作用域并属于某个命名空间。</span><span class="sxs-lookup"><span data-stu-id="8a301-167">All variables have scope and belong to a namespace.</span></span> <span data-ttu-id="8a301-168">变量的作用域可以是包或者包中的容器或任务。</span><span class="sxs-lookup"><span data-stu-id="8a301-168">A variable has package scope or the scope of a container or task in the package.</span></span> <span data-ttu-id="8a301-169">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中的表达式生成器仅列出作用域内变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-169">The expression builder in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists only the in-scope variables.</span></span> <span data-ttu-id="8a301-170">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="8a301-170">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
 <span data-ttu-id="8a301-171">表达式中使用的变量必须具有唯一的名称，表达式计算器才能正确地计算表达式。</span><span class="sxs-lookup"><span data-stu-id="8a301-171">Variables used in expressions must have unique names for the expression evaluator to evaluate the expression correctly.</span></span> <span data-ttu-id="8a301-172">如果包使用多个同名变量，则它们的命名空间必须不同。</span><span class="sxs-lookup"><span data-stu-id="8a301-172">If a package uses multiple variables with the same name, their namespaces must be different.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="8a301-173">提供了命名空间解析运算符，该运算符由两个冒号 (::) 组成，用于以命名空间限定变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-173">provides a namespace resolution operator, consisting of two colons (::), for qualifying a variable with its namespace.</span></span> <span data-ttu-id="8a301-174">例如，下面的表达式使用两个名为 **Count**的变量；一个属于 **User** 命名空间，另一个属于 **MyNamespace** 命名空间。</span><span class="sxs-lookup"><span data-stu-id="8a301-174">For example, the following expression uses two variables named **Count**; one belongs to the **User** namespace and one to the **MyNamespace** namespace.</span></span>  
  
```  
@[User::Count] > @[MyNamespace::Count]  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8a301-175">必须将命名空间与限定的变量名二者的组合放在方括号中，表达式计算器才能识别该变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-175">You must enclose the combination of namespace and qualified variable name in brackets for the expression evaluator to recognize the variable.</span></span>  
  
 <span data-ttu-id="8a301-176">如果**用户**命名空间中的**计数**值为10，并且**MyNamespace**中的**count**值为2，则表达式的计算结果为， `true` 因为表达式计算器识别了两个不同的变量。</span><span class="sxs-lookup"><span data-stu-id="8a301-176">If the value of **Count** in the **User** namespace is 10 and the value of **Count** in **MyNamespace** is 2, the expression evaluates to `true` because the expression evaluator recognizes two different variables.</span></span>  
  
 <span data-ttu-id="8a301-177">如果变量名不唯一，将不会发生错误。</span><span class="sxs-lookup"><span data-stu-id="8a301-177">If variable names are not unique, no error occurs.</span></span> <span data-ttu-id="8a301-178">相反，表达式计算器将仅使用变量的一个实例来计算表达式并返回错误的结果。</span><span class="sxs-lookup"><span data-stu-id="8a301-178">Instead, the expression evaluator uses only one instance of the variable to evaluate the expression and returns an incorrect result.</span></span> <span data-ttu-id="8a301-179">例如，下面的表达式用于比较两个单独**Count**变量的值 (10 和 2) ，但表达式的计算结果为， `false` 因为表达式计算器两次使用同一个**Count**变量实例。</span><span class="sxs-lookup"><span data-stu-id="8a301-179">For example, the following expression was intended to compare the values (10 and 2) for two separate **Count** variables but the expression evaluates to `false` because the expression evaluator uses the same instance of the **Count** variable two times.</span></span>  
  
```  
@Count > @Count  
```  
  
## <a name="related-content"></a><span data-ttu-id="8a301-180">相关内容</span><span class="sxs-lookup"><span data-stu-id="8a301-180">Related Content</span></span>  
 <span data-ttu-id="8a301-181">pragmaticworks.com 上的技术文章 [SSIS 表达式小抄表](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)。</span><span class="sxs-lookup"><span data-stu-id="8a301-181">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
