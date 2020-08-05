---
title: 语法对的自动匹配
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], delimiter highlighting
- IntelliSense [SQL Server], syntax pair matching
ms.assetid: bfc54cda-bfd6-4545-a5b9-f9db2ae13769
author: rothja
ms.author: jroth
ms.openlocfilehash: d1237eeb9aaec39e3210b00c880c0005ef3d95bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580656"
---
# <a name="automatic-matching-of-syntax-pairs"></a><span data-ttu-id="ec9b9-102">语法对的自动匹配</span><span class="sxs-lookup"><span data-stu-id="ec9b9-102">Automatic Matching of Syntax Pairs</span></span>
  <span data-ttu-id="ec9b9-103">使用自动匹配语法对功能，可获得有关必须以成对方式进行编码的语法元素是否正确配对的即时反馈。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-103">Automatic matching of syntax pairs gives you immediate feedback on whether syntax elements that must be coded in pairs are correctly paired.</span></span> <span data-ttu-id="ec9b9-104">这种匹配在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中被称为分隔符匹配，在 Analysis Services XMLA 查询编辑器中被称为大括号匹配，而在 MDX 和 DMX 编辑器中则被称为圆括号匹配。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-104">This is known as delimiter matching in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, brace matching in the Analysis Services XMLA Query Editor, and parenthesis matching in the MDX and DMX editors.</span></span>  
  
## <a name="database-engine-query-editor-delimiter-matching"></a><span data-ttu-id="ec9b9-105">数据库引擎查询编辑器的分隔符匹配</span><span class="sxs-lookup"><span data-stu-id="ec9b9-105">Database Engine Query Editor Delimiter Matching</span></span>  
 <span data-ttu-id="ec9b9-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器与标识代码块边界的分隔符相匹配。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor matches the delimiters that identify the boundaries of code blocks.</span></span> <span data-ttu-id="ec9b9-107">有两种匹配方式：</span><span class="sxs-lookup"><span data-stu-id="ec9b9-107">The matching is done in two ways:</span></span>  
  
-   <span data-ttu-id="ec9b9-108">键入成对分隔符中的第二个分隔符后，该编辑器将突出显示此对分隔符中的两个分隔符。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-108">The editor highlights both delimiters in a pair when you finish typing the second delimiter in the pair.</span></span>  
  
-   <span data-ttu-id="ec9b9-109">只要光标位于一对分隔符中的其中一个分隔符中，就可使用 Ctrl+] 键盘快捷键跳转到与之相匹配的分隔符。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-109">Anytime the cursor is in one of the delimiters in a pair, you can use the CTRL+] keyboard shortcut to jump to the matching delimiter.</span></span>  
  
### <a name="delimiter-pairs"></a><span data-ttu-id="ec9b9-110">成对分隔符</span><span class="sxs-lookup"><span data-stu-id="ec9b9-110">Delimiter Pairs</span></span>  
 <span data-ttu-id="ec9b9-111">自动分隔符匹配可识别以下几组分隔符：</span><span class="sxs-lookup"><span data-stu-id="ec9b9-111">Automatic delimiter matching recognizes the following sets of delimiters:</span></span>  
  
|<span data-ttu-id="ec9b9-112">前导分隔符</span><span class="sxs-lookup"><span data-stu-id="ec9b9-112">Lead Delimiter</span></span>|<span data-ttu-id="ec9b9-113">结尾分隔符</span><span class="sxs-lookup"><span data-stu-id="ec9b9-113">Closing Delimiter</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="ec9b9-114">**(**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-114">**(**</span></span>|<span data-ttu-id="ec9b9-115">**)**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-115">**)**</span></span>|  
|<span data-ttu-id="ec9b9-116">**BEGIN**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-116">**BEGIN**</span></span>|<span data-ttu-id="ec9b9-117">**END**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-117">**END**</span></span>|  
|<span data-ttu-id="ec9b9-118">**BEGIN TRY**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-118">**BEGIN TRY**</span></span>|<span data-ttu-id="ec9b9-119">**END TRY**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-119">**END TRY**</span></span>|  
|<span data-ttu-id="ec9b9-120">**BEGIN CATCH**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-120">**BEGIN CATCH**</span></span>|<span data-ttu-id="ec9b9-121">**END CATCH**</span><span class="sxs-lookup"><span data-stu-id="ec9b9-121">**END CATCH**</span></span>|  
  
 <span data-ttu-id="ec9b9-122">自动分隔符匹配不识别中括号标识符 ([ObjectName]) 或引号标识符 ("ObjectName") 之类的分隔符。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-122">Automatic delimiter matching does not recognize the delimiters for bracketed identifiers ([ObjectName]), or quoted identifiers ("ObjectName").</span></span> <span data-ttu-id="ec9b9-123">由于颜色编码已形象地指示出字符串是否已进行分隔，因此成对分隔符匹配功能与字符串文字 ('string') 的单引号分隔符不匹配。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-123">Pair matching does not match the single quotation delimiters for string literals ('string') because color coding already gives a visual indication of whether the string has been delimited.</span></span>  
  
### <a name="delimiter-highlighting"></a><span data-ttu-id="ec9b9-124">分隔符的突出显示</span><span class="sxs-lookup"><span data-stu-id="ec9b9-124">Delimiter Highlighting</span></span>  
 <span data-ttu-id="ec9b9-125">匹配突出显示一对分隔符的前导和结尾元素，</span><span class="sxs-lookup"><span data-stu-id="ec9b9-125">Matching highlights both the lead and closing element of a pair of delimiters.</span></span> <span data-ttu-id="ec9b9-126">从而便于您直观地识别代码块并检查不匹配的分隔符对。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-126">This lets you visually identify code blocks and check for mismatched pairs of delimiters.</span></span>  
  
 <span data-ttu-id="ec9b9-127">键入结束成对分隔符的最后一个字母后，分隔符将突出显示出来。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-127">Delimiters are highlighted when you type the final letter that completes the pair.</span></span> <span data-ttu-id="ec9b9-128">例如，对于一对 BEGIN END 分隔符，首先键入 BEGIN，然后键入 END，在键入 END 的最后一个字母 D 时，将打开突出显示。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-128">For example, for a BEGIN END pair where you type BEGIN first followed by END, highlighting turns on when you type the final letter in END.</span></span> <span data-ttu-id="ec9b9-129">但不必通过先键入前导分隔符，再键入结尾分隔符的方式来启动突出显示。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-129">You do not have to type the lead delimiter followed by the closing delimiter to turn on highlighting.</span></span> <span data-ttu-id="ec9b9-130">如果先键入 END，然后向上回滚脚本并键入 BEGIN，则在键入 BEGIN 的最后一个字母 N 时，将启用突出显示。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-130">If you type END first, then scroll back up the script and type BEGIN, highlighting is turned on when you type the final letter in BEGIN.</span></span> <span data-ttu-id="ec9b9-131">但最后键入的字母不一定是分隔符的结尾字母。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-131">The final letter typed does not have to be the end letter in the delimiter.</span></span> <span data-ttu-id="ec9b9-132">例如，有可能将 BEGIN 错拼成 BEIN，则在插入最后一个字母 G 时，将突出显示该 BEGIN END 对。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-132">For example, you could misspell BEGIN as BEIN, when you insert the final G the BEGIN END pair is highlighted.</span></span>  
  
 <span data-ttu-id="ec9b9-133">移动光标之前，该对分隔符将保持突出显示状态。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-133">The delimiter pair remains highlighted until you move the cursor.</span></span> <span data-ttu-id="ec9b9-134">移动光标后，将关闭突出显示，即使新光标位置仍在同一分隔符中时也是如此。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-134">The highlighting is turned off when the cursor is moved, even if the new cursor position remains in the same delimiter.</span></span> <span data-ttu-id="ec9b9-135">删除并重新键入该对分隔符任一成员中的任一字母即可重新启用突出显示。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-135">You can turn the highlighting back on by deleting and retyping any letter in either member of the pair.</span></span>  
  
## <a name="analysis-services-xmla-query-editor-brace-matching"></a><span data-ttu-id="ec9b9-136">Analysis Services XMLA 查询编辑器的大括号匹配</span><span class="sxs-lookup"><span data-stu-id="ec9b9-136">Analysis Services XMLA Query Editor Brace Matching</span></span>  
 <span data-ttu-id="ec9b9-137">XMLA 查询编辑器的大括号匹配通过突出显示左右大括号来显示是否存在闭合的元素。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-137">The XMLA Query Editor brace matching shows if you have closed elements by highlighting opening and closing braces.</span></span> <span data-ttu-id="ec9b9-138">还可使用 Ctrl+] 键盘快捷键从一个大括号跳转到与其匹配的大括号。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-138">You can also use the CTRL+] keyboard shortcut to jump from one brace to the matching brace.</span></span>  
  
 <span data-ttu-id="ec9b9-139">XMLA 查询编辑器对以下项进行大括号匹配：</span><span class="sxs-lookup"><span data-stu-id="ec9b9-139">The XMLA Query Editor does brace matching for the following terms:</span></span>  
  
-   <span data-ttu-id="ec9b9-140">匹配的开始和结束标记。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-140">Matching start and end tags.</span></span>  
  
-   <span data-ttu-id="ec9b9-141">任何 " \<" and "> " 尖括号对。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-141">Any pair of "\<" and ">" angle brackets.</span></span>  
  
-   <span data-ttu-id="ec9b9-142">注释的开头和结尾。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-142">Start and end of comments.</span></span>  
  
-   <span data-ttu-id="ec9b9-143">处理指令的开头和结尾。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-143">Start and end of processing instructions.</span></span>  
  
-   <span data-ttu-id="ec9b9-144">CDATA 块的开头和结尾。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-144">Start and end of CDATA blocks.</span></span>  
  
-   <span data-ttu-id="ec9b9-145">DTD 声明的开头和结尾。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-145">Start and end of DTD declarations.</span></span>  
  
-   <span data-ttu-id="ec9b9-146">属性的左右引号。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-146">Opening and closing quotes on attributes.</span></span>  
  
## <a name="mdx-and-dmx-editor-parenthesis-matching"></a><span data-ttu-id="ec9b9-147">MDX 和 DMX 编辑器的圆括号匹配</span><span class="sxs-lookup"><span data-stu-id="ec9b9-147">MDX and DMX Editor Parenthesis Matching</span></span>  
 <span data-ttu-id="ec9b9-148">多维表达式 (MDX) 和数据挖掘表达式 (DMX) 编辑器自动匹配函数中的成对圆括号。</span><span class="sxs-lookup"><span data-stu-id="ec9b9-148">The Multi-Dimensional Expressions (MDX) and Data Mining Expressions (DMX) Editors automatically match parenthesis pairs in functions.</span></span>  
  
  
