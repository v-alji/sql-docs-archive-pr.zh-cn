---
title: “排序规则”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.definecolumncollation
- vdtsql.chm:65561
ms.assetid: e4020f79-7abf-4839-b9b2-984ef7049817
author: stevestein
ms.author: sstein
ms.openlocfilehash: d551b2ae7ca27250c144afedf13038efd78ad6ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591689"
---
# <a name="collation-dialog-box-visual-database-tools"></a><span data-ttu-id="71281-102">“排序规则”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="71281-102">Collation Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="71281-103">使用此对话框可为列指定排序规则顺序。</span><span class="sxs-lookup"><span data-stu-id="71281-103">This dialog box lets you specify a collation sequence for the column.</span></span> <span data-ttu-id="71281-104">列的排序规则顺序可用在将列值与其他列的值或常量值进行比较的各项操作中。</span><span class="sxs-lookup"><span data-stu-id="71281-104">A column's collation sequence is used in any operation that compares values of the column to another column or to constant values.</span></span> <span data-ttu-id="71281-105">它还会影响一些字符串函数（如 SUBSTRING 和 CHARINDEX）的行为。</span><span class="sxs-lookup"><span data-stu-id="71281-105">It also affects the behavior of some string functions, such as SUBSTRING and CHARINDEX.</span></span> <span data-ttu-id="71281-106">有关列排序规则设置的效果的完整列表，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="71281-106">For a complete list of the effects of a column's collation setting, see the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="71281-107">在以下情况下将显示此对话框：</span><span class="sxs-lookup"><span data-stu-id="71281-107">This dialog box appears:</span></span>  
  
-   <span data-ttu-id="71281-108">在“列属性”  选项卡的“排序规则”  字段中输入无效的排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="71281-108">If you enter an invalid collation name in the **Collation** field on the **Column Properties** tab.</span></span>  
  
-   <span data-ttu-id="71281-109">在“列属性”选项卡的“排序规则”字段中单击，再单击该字段右侧的省略号按钮 (…)    。</span><span class="sxs-lookup"><span data-stu-id="71281-109">If you click in the **Collation** field on the **Column Properties** tab, and then click the ellipsis button (**...**) to the right of the field.</span></span>  
  
## <a name="options"></a><span data-ttu-id="71281-110">选项</span><span class="sxs-lookup"><span data-stu-id="71281-110">Options</span></span>  
 <span data-ttu-id="71281-111">**SQL 排序规则**</span><span class="sxs-lookup"><span data-stu-id="71281-111">**SQL Collation**</span></span>  
 <span data-ttu-id="71281-112">在下拉列表中由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定义的排序规则顺序之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="71281-112">Choose among the collation sequences defined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the drop-down list.</span></span>  
  
 <span data-ttu-id="71281-113">**Windows 排序规则**</span><span class="sxs-lookup"><span data-stu-id="71281-113">**Windows Collation**</span></span>  
 <span data-ttu-id="71281-114">在下拉列表中由 Windows 定义的排序规则顺序之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="71281-114">Choose among the collation sequences defined by Windows from the drop-down list.</span></span>  
  
 <span data-ttu-id="71281-115">**二进制排序**</span><span class="sxs-lookup"><span data-stu-id="71281-115">**Binary Sort**</span></span>  
 <span data-ttu-id="71281-116">使用字符值的二进制代码进行比较。</span><span class="sxs-lookup"><span data-stu-id="71281-116">Use the binary codes of character values for comparisons.</span></span> <span data-ttu-id="71281-117">如果选择此选项，某些字母比较选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="71281-117">If you select this option, certain alphabetic comparison options become unavailable.</span></span> <span data-ttu-id="71281-118">例如，不区分大小写的比较选项将不可用，因为大写字母和小写字母具有不同的二进制编码。</span><span class="sxs-lookup"><span data-stu-id="71281-118">For example, case-insensitive comparisons become unavailable because uppercase letters and lowercase letters have different binary encodings.</span></span> <span data-ttu-id="71281-119">只有在选择了“Windows 排序规则”  后才适用。</span><span class="sxs-lookup"><span data-stu-id="71281-119">Applies only if you select **Windows collation**.</span></span>  
  
 <span data-ttu-id="71281-120">**字典排序**</span><span class="sxs-lookup"><span data-stu-id="71281-120">**Dictionary Sort**</span></span>  
 <span data-ttu-id="71281-121">使用字母比较选项。</span><span class="sxs-lookup"><span data-stu-id="71281-121">Use alphabetic comparison options.</span></span> <span data-ttu-id="71281-122">只有在选择了“Windows 排序规则”  后才适用。</span><span class="sxs-lookup"><span data-stu-id="71281-122">Applies only if you select **Windows collation**.</span></span> <span data-ttu-id="71281-123">字母比较选项包括：</span><span class="sxs-lookup"><span data-stu-id="71281-123">The alphabetic comparisons options are:</span></span>  
  
-   <span data-ttu-id="71281-124">**区分大小写** 如果希望在比较中将大写字母和小写字母视为不相同，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="71281-124">**Case Sensitive** Select this if you want comparisons to consider uppercase and lowercase letters to be unequal.</span></span>  
  
-   <span data-ttu-id="71281-125">**区分重音** 如果希望在比较中将重音字母和非重音字母视为不相同，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="71281-125">**Accent Sensitive** Select this if you want comparisons to consider accented and unaccented letters to be unequal.</span></span> <span data-ttu-id="71281-126">如果选择此选项，在比较中还会将重音位于不同字母的情况视为不相同。</span><span class="sxs-lookup"><span data-stu-id="71281-126">If you select this, comparisons will also consider differently accented letters to be unequal.</span></span>  
  
-   <span data-ttu-id="71281-127">**区分假名** 如果希望在比较中将片假名和平假名日语音节视为不相同，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="71281-127">**Kana Sensitive** Select this if you want comparisons to consider katakana and hiragana Japanese syllables to be unequal.</span></span>  
  
-   <span data-ttu-id="71281-128">**区分全半角** 如果希望在比较中将半角字符和全角字符视为不相同，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="71281-128">**Width Sensitive** Select this if you want comparisons to consider half-width and full-width characters to be unequal.</span></span>  
  
 <span data-ttu-id="71281-129">**“恢复默认值”按钮**</span><span class="sxs-lookup"><span data-stu-id="71281-129">**Restore Default Button**</span></span>  
 <span data-ttu-id="71281-130">向列应用数据库的默认排序规则顺序。</span><span class="sxs-lookup"><span data-stu-id="71281-130">Apply the default collation sequence for the database to the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71281-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71281-131">See Also</span></span>  
 [<span data-ttu-id="71281-132">在聚合查询中使用列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="71281-132">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
