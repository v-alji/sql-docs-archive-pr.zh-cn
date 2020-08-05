---
title: 完成 Transact-SQL 代码段
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: rothja
ms.author: jroth
ms.openlocfilehash: d90c77f72ba8ce80d26503645d9b04d795f5e503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580640"
---
# <a name="complete-transact-sql-snippets"></a><span data-ttu-id="d9df7-102">完成 Transact-SQL 代码段</span><span class="sxs-lookup"><span data-stu-id="d9df7-102">Complete Transact-SQL Snippets</span></span>
  <span data-ttu-id="d9df7-103">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码段插入脚本后，可以编辑代码段的内容以生成完整的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="d9df7-103">Once a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet has been inserted into a script, you edit the contents of the snippet to build a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="completing-snippets"></a><span data-ttu-id="d9df7-104">完成代码段</span><span class="sxs-lookup"><span data-stu-id="d9df7-104">Completing Snippets</span></span>  
 <span data-ttu-id="d9df7-105">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码段添加到脚本时，插入的代码段语句具有一个或多个替换点，这些替换点会突出显示。</span><span class="sxs-lookup"><span data-stu-id="d9df7-105">When you add a [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet to your script, the inserted snippet statement has one or more replacement points, which are highlighted.</span></span> <span data-ttu-id="d9df7-106">如果您将鼠标指针放在替换点上，会出现一个工具提示，其中包含您可以指定的语法元素的说明。</span><span class="sxs-lookup"><span data-stu-id="d9df7-106">If you rest your mouse pointer on a replacement point, a tooltip appears with a description of the syntax element you can specify.</span></span> <span data-ttu-id="d9df7-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器会将代码段与周围的脚本区分开，直到您关闭源文件。</span><span class="sxs-lookup"><span data-stu-id="d9df7-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor recognizes the snippet as separate from the surrounding script until you close the source file.</span></span> <span data-ttu-id="d9df7-108">替换点将保持活动状态，直到您关闭源文件。</span><span class="sxs-lookup"><span data-stu-id="d9df7-108">The replacement points remain active until you close the source file.</span></span>  
  
 <span data-ttu-id="d9df7-109">您还可以向代码段所插入的模板代码中添加其他语法元素。</span><span class="sxs-lookup"><span data-stu-id="d9df7-109">You can also add additional syntax elements to the template code inserted by a snippet.</span></span> <span data-ttu-id="d9df7-110">例如，创建表代码段模板生成两个列定义；您必须添加其他列定义才能创建具有两个以上列的表格。</span><span class="sxs-lookup"><span data-stu-id="d9df7-110">For example, the Create Table snippet template generates two column definitions; you must add additional column definitions to create a table with more than two columns.</span></span>  
  
#### <a name="completing-the-snippet-statement"></a><span data-ttu-id="d9df7-111">完成代码段语句</span><span class="sxs-lookup"><span data-stu-id="d9df7-111">Completing the Snippet Statement</span></span>  
  
1.  <span data-ttu-id="d9df7-112">使用 Tab 键从一个替换点移到下一个替换点。</span><span class="sxs-lookup"><span data-stu-id="d9df7-112">Use the TAB key to move from one replacement point to the next.</span></span> <span data-ttu-id="d9df7-113">使用 Shift+Tab 移到前一个替换点。</span><span class="sxs-lookup"><span data-stu-id="d9df7-113">Use SHIFT+TAB to move to the previous replacement point.</span></span>  
  
2.  <span data-ttu-id="d9df7-114">按 Ctrl+空格键以调用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="d9df7-114">Click CTRL+SPACE to invoke IntelliSense.</span></span>  
  
3.  <span data-ttu-id="d9df7-115">从列表中选择一个项目，或键入您选择的替换内容。</span><span class="sxs-lookup"><span data-stu-id="d9df7-115">Select an item from the list, or type a replacement of your choice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9df7-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9df7-116">See Also</span></span>  
 <span data-ttu-id="d9df7-117">[插入 Transact-SQL 代码段](insert-transact-sql-snippets.md) </span><span class="sxs-lookup"><span data-stu-id="d9df7-117">[Insert Transact-SQL Snippets](insert-transact-sql-snippets.md) </span></span>  
 [<span data-ttu-id="d9df7-118">插入外侧 Transact-SQL 代码片段</span><span class="sxs-lookup"><span data-stu-id="d9df7-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
