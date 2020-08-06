---
title: TOKEN（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9fdd06bf-5bc9-445c-95bf-709e0ca5989b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0598c3832e4bf6f838087be4fee541663c8bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689960"
---
# <a name="token--ssis-expression"></a><span data-ttu-id="3dbf3-102">TOKEN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="3dbf3-102">TOKEN  (SSIS Expression)</span></span>
  <span data-ttu-id="3dbf3-103">基于分隔字符串中的标记的指定分隔符以及表示要返回的标记的标记数目，从字符串返回标记（子字符串）。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-103">Returns a token (substring) from a string based on the specified delimiters that separate tokens in the string and the number of the token that denotes which token to be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dbf3-104">语法</span><span class="sxs-lookup"><span data-stu-id="3dbf3-104">Syntax</span></span>  
  
```  
TOKEN(character_expression, delimiter_string, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="3dbf3-105">参数</span><span class="sxs-lookup"><span data-stu-id="3dbf3-105">Arguments</span></span>  
 <span data-ttu-id="3dbf3-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="3dbf3-106">*character_expression*</span></span>  
 <span data-ttu-id="3dbf3-107">包含分隔符分隔的标记的字符串。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="3dbf3-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="3dbf3-108">*delimiter_string*</span></span>  
 <span data-ttu-id="3dbf3-109">包含分隔符字符的字符串。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="3dbf3-110">例如，”; ,”包含三个分隔符字符，即一个分号、一个空白空间和一个逗号。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
 <span data-ttu-id="3dbf3-111">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="3dbf3-111">*occurrence*</span></span>  
 <span data-ttu-id="3dbf3-112">指定要返回的标记的有符号或无符号整数。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-112">A signed or unsigned integer that specifies the token to be returned.</span></span> <span data-ttu-id="3dbf3-113">例如，如果您指定 3 作为此参数的值，则返回字符串中的第三个标记。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-113">For example, if you specify 3 as a value for this parameter, the third token in the string is returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3dbf3-114">结果类型</span><span class="sxs-lookup"><span data-stu-id="3dbf3-114">Result Types</span></span>  
 <span data-ttu-id="3dbf3-115">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="3dbf3-115">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dbf3-116">备注</span><span class="sxs-lookup"><span data-stu-id="3dbf3-116">Remarks</span></span>  
 <span data-ttu-id="3dbf3-117">此函数将 <character_expression> 字符串拆分为一组由 <delimiter_string> 中指定的分隔符分隔的标记，然后返回第 N 个标记，其中 N 是 \<occurrence> 参数指定的标记出现的次数。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-117">This function splits up the <character_expression> string into a set of tokens separated by the delimiters specified in the <delimiter_string> and then returns the Nth token where N is the number of occurrence of the token specified by the \<occurrence> parameter.</span></span> <span data-ttu-id="3dbf3-118">有关此函数的用法示例，请参阅“示例”部分。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-118">See Examples section for sample usages of this function.</span></span>  
  
 <span data-ttu-id="3dbf3-119">下面的备注适用于 TOKEN 函数：</span><span class="sxs-lookup"><span data-stu-id="3dbf3-119">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="3dbf3-120">分隔符字符串可以包含一个或多个分隔符字符。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-120">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="3dbf3-121">如果 \<occurrence> 参数的值大于字符串中标记的总数，则该函数返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-121">If the value of \<occurrence> parameter is higher than the total number of tokens in the string, the function returns NULL.</span></span>  
  
-   <span data-ttu-id="3dbf3-122">前导分隔符将被跳过。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-122">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="3dbf3-123">TOKEN 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-123">TOKEN works only with the DT_WSTR data type.</span></span> <span data-ttu-id="3dbf3-124">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 TOKEN 执行操作前将隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-124">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="3dbf3-125">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-125">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="3dbf3-126">如果 character_expression 为 Null，则 TOKEN 将返回 Null 结果。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-126">TOKEN returns a null result if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="3dbf3-127">您可以使用变量和列作为表达式中所有参数的值。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-127">You can use variables and columns as values of all arguments in the expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="3dbf3-128">表达式示例</span><span class="sxs-lookup"><span data-stu-id="3dbf3-128">Expression Examples</span></span>  
 <span data-ttu-id="3dbf3-129">在下面的示例中，TOKEN 函数返回“a”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-129">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="3dbf3-130">字符串“a little white dog”具有由分隔符“ ”（空格字符）分隔的 4 个标记“a”、“little”、“white”、“dog”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-130">The string "a little white dog" has 4 tokens "a", "little", "white", "dog" separated by the delimiter " " (space character).</span></span> <span data-ttu-id="3dbf3-131">第二个参数（分隔符字符串）仅指定要将输入字符串拆分为多个标记的一个分隔符，即空格字符。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-131">The second argument, a delimiter string, specifies only one delimiter, the space character, to be used in splitting the input string into tokens.</span></span> <span data-ttu-id="3dbf3-132">最后一个参数 1 指定要返回的第一个标记。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-132">The last argument, 1, specifies that the first token to be returned.</span></span> <span data-ttu-id="3dbf3-133">在此示例字符串中，第一个标记是“a”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-133">The first token is "a" in this sample string.</span></span>  
  
```  
TOKEN("a little white dog"," ",1)  
```  
  
 <span data-ttu-id="3dbf3-134">在下面的示例中，TOKEN 函数返回“dog”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-134">In the following example, the TOKEN function returns "dog".</span></span> <span data-ttu-id="3dbf3-135">此示例中的分隔符字符串包含 5 个分隔符。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-135">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="3dbf3-136">输入字符串包含 4 个标记：“a”、“little”、“white”、“dog”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-136">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKEN("a:little|white dog","| ,.:",4)  
```  
  
 <span data-ttu-id="3dbf3-137">在下面的示例中，TOKEN 函数返回 ""（空字符串），因为在字符串中有没有 99 个标记。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-137">In the following example, the TOKEN function returns "" (an empty string) because there are no 99 tokens in the string.</span></span>  
  
```  
TOKEN("a little white dog"," ",99)  
```  
  
 <span data-ttu-id="3dbf3-138">在下面的示例中，TOKEN 函数返回整个字符串。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-138">In the following example, the TOKEN function returns the full string.</span></span> <span data-ttu-id="3dbf3-139">该函数对分隔符的输入字符串进行分析，因为该字符串中没有任何内容，所以它只是将整个字符串作为第一个标记添加。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-139">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKEN("a little white dog","|",1)  
```  
  
 <span data-ttu-id="3dbf3-140">在下面的示例中，TOKEN 函数返回“a”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-140">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="3dbf3-141">它将忽略所有前导空格字符。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-141">It ignores all the leading space characters.</span></span>  
  
```  
TOKEN("        a little white dog", " ", 1)  
```  
  
 <span data-ttu-id="3dbf3-142">在下面的示例中，TOKEN 函数从日期字符串中返回年份。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-142">In the following example, the TOKEN function returns the year from a date string.</span></span>  
  
```  
TOKEN("2009/01/01", "/"), 1  
```  
  
 <span data-ttu-id="3dbf3-143">在下面的示例中，TOKEN 函数从指定路径中返回文件名。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-143">In the following example, the TOKEN function returns the file name from the specified path.</span></span> <span data-ttu-id="3dbf3-144">例如，如果 User::Path 的值为“c:\program files\data\myfile.txt”，则 TOKEN 函数返回“myfile.txt”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-144">For example, if the value of User::Path is "c:\program files\data\myfile.txt", the TOKEN function returns "myfile.txt".</span></span> <span data-ttu-id="3dbf3-145">TOKENCOUNT 函数返回 4，TOKEN 函数第 4 个标记“myfile.txt”。</span><span class="sxs-lookup"><span data-stu-id="3dbf3-145">The TOKENCOUNT function returns 4 and the TOKEN function return the 4th token, "myfile.txt".</span></span>  
  
```  
TOKEN(@[User::Path], "\\", TOKENCOUNT(@[User::Path], "\\"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="3dbf3-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3dbf3-146">See Also</span></span>  
 [<span data-ttu-id="3dbf3-147">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="3dbf3-147">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
