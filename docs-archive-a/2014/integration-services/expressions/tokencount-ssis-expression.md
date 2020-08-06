---
title: TOKENCOUNT（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9068e4958570a0222bc8e1a4c90d34acc5bdf3dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689956"
---
# <a name="tokencount-ssis-expression"></a><span data-ttu-id="39db6-102">TOKENCOUNT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="39db6-102">TOKENCOUNT (SSIS Expression)</span></span>
  <span data-ttu-id="39db6-103">返回包含指定分隔符分隔的标记的字符串中的标记数目。</span><span class="sxs-lookup"><span data-stu-id="39db6-103">Returns the number of tokens in a string that contains tokens separated by the specified delimiters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39db6-104">语法</span><span class="sxs-lookup"><span data-stu-id="39db6-104">Syntax</span></span>  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a><span data-ttu-id="39db6-105">参数</span><span class="sxs-lookup"><span data-stu-id="39db6-105">Arguments</span></span>  
 <span data-ttu-id="39db6-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="39db6-106">*character_expression*</span></span>  
 <span data-ttu-id="39db6-107">包含分隔符分隔的标记的字符串。</span><span class="sxs-lookup"><span data-stu-id="39db6-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="39db6-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="39db6-108">*delimiter_string*</span></span>  
 <span data-ttu-id="39db6-109">包含分隔符字符的字符串。</span><span class="sxs-lookup"><span data-stu-id="39db6-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="39db6-110">例如，”; ,”包含三个分隔符字符，即一个分号、一个空白空间和一个逗号。</span><span class="sxs-lookup"><span data-stu-id="39db6-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="39db6-111">结果类型</span><span class="sxs-lookup"><span data-stu-id="39db6-111">Result Types</span></span>  
 <span data-ttu-id="39db6-112">DT_I4</span><span class="sxs-lookup"><span data-stu-id="39db6-112">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39db6-113">备注</span><span class="sxs-lookup"><span data-stu-id="39db6-113">Remarks</span></span>  
 <span data-ttu-id="39db6-114">下面的备注适用于 TOKEN 函数：</span><span class="sxs-lookup"><span data-stu-id="39db6-114">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="39db6-115">分隔符字符串可以包含一个或多个分隔符字符。</span><span class="sxs-lookup"><span data-stu-id="39db6-115">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="39db6-116">前导分隔符将被跳过。</span><span class="sxs-lookup"><span data-stu-id="39db6-116">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="39db6-117">TOKENCOUNT 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="39db6-117">TOKENCOUNT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="39db6-118">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 TOKEN 执行操作前将隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="39db6-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="39db6-119">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="39db6-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="39db6-120">如果 character_expression 为 Null，TOKENCOUNT 将返回 0（零）。</span><span class="sxs-lookup"><span data-stu-id="39db6-120">TOKENCOUNT returns 0 (zero) if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="39db6-121">您可以使用变量和列作为此表达式的参数。</span><span class="sxs-lookup"><span data-stu-id="39db6-121">You can use variables and columns as arguments for this expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="39db6-122">表达式示例</span><span class="sxs-lookup"><span data-stu-id="39db6-122">Expression Examples</span></span>  
 <span data-ttu-id="39db6-123">在下面的示例中，TOKENCOUNT 函数返回 3，因为该字符串包含三个标记：“01”、“12”、“2011”。</span><span class="sxs-lookup"><span data-stu-id="39db6-123">In the following example, the TOKENCOUNT function returns 3 because the string contains three tokens: "01", "12", "2011".</span></span>  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 <span data-ttu-id="39db6-124">在下面的示例中，TOKENCOUNT 函数返回 4，因为存在四个标记（“a”、“little”、“white”、“dog”）。</span><span class="sxs-lookup"><span data-stu-id="39db6-124">In the following example, the TOKENCOUNT function returns 4 because there are four tokens ("a", "little", "white", "dog").</span></span>  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 <span data-ttu-id="39db6-125">在下面的示例中，TOKENCOUNT 函数返回 1。</span><span class="sxs-lookup"><span data-stu-id="39db6-125">In the following example, the TOKENCOUNT function returns 1.</span></span> <span data-ttu-id="39db6-126">该函数对分隔符的输入字符串进行分析，因为该字符串中没有任何内容，所以它只是将整个字符串作为第一个标记添加。</span><span class="sxs-lookup"><span data-stu-id="39db6-126">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 <span data-ttu-id="39db6-127">在下面的示例中，TOKENCOUNT 函数返回 4。</span><span class="sxs-lookup"><span data-stu-id="39db6-127">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="39db6-128">此示例中的分隔符字符串包含 5 个分隔符。</span><span class="sxs-lookup"><span data-stu-id="39db6-128">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="39db6-129">输入字符串包含 4 个标记：“a”、“little”、“white”、“dog”。</span><span class="sxs-lookup"><span data-stu-id="39db6-129">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 <span data-ttu-id="39db6-130">在下面的示例中，TOKENCOUNT 函数返回 4。</span><span class="sxs-lookup"><span data-stu-id="39db6-130">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="39db6-131">它将忽略所有前导空格字符。</span><span class="sxs-lookup"><span data-stu-id="39db6-131">It ignores all the leading space characters.</span></span>  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="39db6-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39db6-132">See Also</span></span>  
 [<span data-ttu-id="39db6-133">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="39db6-133">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
