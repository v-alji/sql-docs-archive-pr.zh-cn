---
title: 使用通配符搜索文本
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: rothja
ms.author: jroth
ms.openlocfilehash: cc4e24c3dce73e46350b0c106429c42ab5f0edb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591219"
---
# <a name="search-text-with-wildcards"></a><span data-ttu-id="13123-102">使用通配符搜索文本</span><span class="sxs-lookup"><span data-stu-id="13123-102">Search Text with Wildcards</span></span>
  <span data-ttu-id="13123-103">以下表达式可以替换 **“查找和替换”对话框的“查找内容”字段中的字符或数字**[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  。</span><span class="sxs-lookup"><span data-stu-id="13123-103">The following expressions can replace characters or digits in the **Find what** field of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.</span></span>  
  
#### <a name="to-search-using-wildcards"></a><span data-ttu-id="13123-104">使用通配符进行搜索</span><span class="sxs-lookup"><span data-stu-id="13123-104">To search using wildcards</span></span>  
  
1.  <span data-ttu-id="13123-105">若要在“快速查找”、 **“在文件中查找”** 、 **“快速替换”** 或 **“在文件中替换”** 操作过程中在 **“查找内容”** 字段中使用通配符，请选择 **“查找选项”** 下的 **“使用”** 选项，然后选择 **“通配符”** 。</span><span class="sxs-lookup"><span data-stu-id="13123-105">To enable the use of wildcards in the **Find what** field during Quick Find, **Find in Files**, **Quick Replace**, or **Replace in Files** operations, select the **Use** option under **Find Options** and then choose **Wildcards**.</span></span>  
  
2.  <span data-ttu-id="13123-106">**“查找内容”** 字段旁边的 **“引用列表”** 三角形按钮将变为可用状态。</span><span class="sxs-lookup"><span data-stu-id="13123-106">The triangular **Reference List** button next to the **Find what** field then becomes available.</span></span> <span data-ttu-id="13123-107">单击此按钮以显示可用通配符列表。</span><span class="sxs-lookup"><span data-stu-id="13123-107">Click this button to display a list of the available wildcards.</span></span> <span data-ttu-id="13123-108">从 **“引用列表”** 中选择任意项后，便会将该项插入到 **“查找内容”** 字符串中。</span><span class="sxs-lookup"><span data-stu-id="13123-108">When you choose any item from the **Reference List**, it is inserted into the **Find what** string.</span></span>  
  
 <span data-ttu-id="13123-109">下表介绍了 **“引用列表”** 中可用的通配符。</span><span class="sxs-lookup"><span data-stu-id="13123-109">The following table describes the wildcards available in the **Reference List**.</span></span>  
  
|<span data-ttu-id="13123-110">表达式</span><span class="sxs-lookup"><span data-stu-id="13123-110">Expression</span></span>|<span data-ttu-id="13123-111">语法</span><span class="sxs-lookup"><span data-stu-id="13123-111">Syntax</span></span>|<span data-ttu-id="13123-112">说明</span><span class="sxs-lookup"><span data-stu-id="13123-112">Description</span></span>|  
|----------------|------------|-----------------|  
|<span data-ttu-id="13123-113">任何单个字符</span><span class="sxs-lookup"><span data-stu-id="13123-113">Any single character</span></span>|<span data-ttu-id="13123-114">?</span><span class="sxs-lookup"><span data-stu-id="13123-114">?</span></span>|<span data-ttu-id="13123-115">与任何单个字符匹配。</span><span class="sxs-lookup"><span data-stu-id="13123-115">Matches any single character.</span></span>|  
|<span data-ttu-id="13123-116">任何单个数字</span><span class="sxs-lookup"><span data-stu-id="13123-116">Any single digit</span></span>|#|<span data-ttu-id="13123-117">与任何单个数字匹配。</span><span class="sxs-lookup"><span data-stu-id="13123-117">Matches any single digit.</span></span> <span data-ttu-id="13123-118">例如，7# 与包括 7 且其后跟随另一数字的数字匹配，例如 71，但不能是 17。</span><span class="sxs-lookup"><span data-stu-id="13123-118">For example, 7# matches numbers that include 7 followed by another number, such as 71, but not 17.</span></span>|  
|<span data-ttu-id="13123-119">集合中没有的字符</span><span class="sxs-lookup"><span data-stu-id="13123-119">Characters not in set</span></span>|<span data-ttu-id="13123-120">[!</span><span class="sxs-lookup"><span data-stu-id="13123-120">[!</span></span> <span data-ttu-id="13123-121">]</span><span class="sxs-lookup"><span data-stu-id="13123-121">]</span></span>|<span data-ttu-id="13123-122">与未在集合中指定的任一字符匹配。</span><span class="sxs-lookup"><span data-stu-id="13123-122">Matches any one character that is not specified in the set.</span></span>|  
|<span data-ttu-id="13123-123">一个或多个字符</span><span class="sxs-lookup"><span data-stu-id="13123-123">One or more characters</span></span>|*|<span data-ttu-id="13123-124">与任何一个或多个字符匹配。</span><span class="sxs-lookup"><span data-stu-id="13123-124">Matches any one or more characters.</span></span> <span data-ttu-id="13123-125">例如，new\* 与任何包括“new”的文本匹配，例如 newfile.txt。</span><span class="sxs-lookup"><span data-stu-id="13123-125">For example, new\* matches any text that includes "new", such as newfile.txt.</span></span>|  
|<span data-ttu-id="13123-126">字符集</span><span class="sxs-lookup"><span data-stu-id="13123-126">Set of characters</span></span>|<span data-ttu-id="13123-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="13123-127">[ ]</span></span>|<span data-ttu-id="13123-128">与在集合中指定的任一字符匹配。</span><span class="sxs-lookup"><span data-stu-id="13123-128">Matches any one of the characters specified in the set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13123-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13123-129">See Also</span></span>  
 <span data-ttu-id="13123-130">[搜索和替换](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="13123-130">[Search and Replace](search-and-replace.md) </span></span>  
 [<span data-ttu-id="13123-131">使用正则表达式搜索文本</span><span class="sxs-lookup"><span data-stu-id="13123-131">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
