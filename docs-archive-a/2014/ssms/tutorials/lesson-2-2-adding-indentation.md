---
title: 添加缩进 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d0b7ee8819f98df5e5658321a3d950ca31083b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588202"
---
# <a name="adding-indentation"></a><span data-ttu-id="53069-102">添加缩进</span><span class="sxs-lookup"><span data-stu-id="53069-102">Adding Indentation</span></span>
  <span data-ttu-id="53069-103">查询编辑器允许您通过一个步骤缩进大段代码，并允许您更改缩进量。</span><span class="sxs-lookup"><span data-stu-id="53069-103">Query Editor allows you to indent large sections of code with a single step, and you can change the amount of the indentation.</span></span>  
  
## <a name="indenting-code"></a><span data-ttu-id="53069-104">缩进代码</span><span class="sxs-lookup"><span data-stu-id="53069-104">Indenting Code</span></span>  
  
#### <a name="to-indent-multiple-lines-of-code"></a><span data-ttu-id="53069-105">缩进多行代码</span><span class="sxs-lookup"><span data-stu-id="53069-105">To indent multiple lines of code</span></span>  
  
1.  <span data-ttu-id="53069-106">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="53069-106">On the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="53069-107">创建第二个查询，该查询会从 **Person**架构的 **Person**表中选择 **BusinessEntityID** 、FirstName、 **MiddleName** 和 **LastName** 列。</span><span class="sxs-lookup"><span data-stu-id="53069-107">Create a second query that selects the **BusinessEntityID**, FirstName, **MiddleName**, and **LastName** columns from the **Person** table of the **Person** schema.</span></span> <span data-ttu-id="53069-108">将每个列放在单独的行上，使代码显示如下：</span><span class="sxs-lookup"><span data-stu-id="53069-108">Place each column on a separate line so the code looks like this:</span></span>  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  <span data-ttu-id="53069-109">选择从 `BusinessEntityID` 到 `LastName` 的所有文本。</span><span class="sxs-lookup"><span data-stu-id="53069-109">Select all text from `BusinessEntityID` to `LastName`.</span></span>  
  
4.  <span data-ttu-id="53069-110">在“SQL 编辑器”\*\*\*\* 工具栏中，单击“增加缩进”\*\*\*\* 以同时缩进所有的行。</span><span class="sxs-lookup"><span data-stu-id="53069-110">On the **SQL Editor** toolbar, click **Increase Indent** to indent all the lines at once.</span></span>  
  
#### <a name="to-change-the-default-indentation"></a><span data-ttu-id="53069-111">更改默认缩进</span><span class="sxs-lookup"><span data-stu-id="53069-111">To change the default indentation</span></span>  
  
1.  <span data-ttu-id="53069-112">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="53069-112">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="53069-113">依次展开“文本编辑器”\*\*\*\*、“所有语言”\*\*\*\*，再单击“制表符”\*\*\*\* 并设置适当的缩进值。</span><span class="sxs-lookup"><span data-stu-id="53069-113">Expand **Text Editor**, expand **All Languages**, and click **Tabs** , and set indentation values as appropriate.</span></span> <span data-ttu-id="53069-114">请注意，您可以更改缩进的大小和制表符的大小，还可更改是否将制表符转换为空格。</span><span class="sxs-lookup"><span data-stu-id="53069-114">Note that you can change the size of the indent as well as the size of tabs, and whether tabs are converted to spaces.</span></span>  
  
     <span data-ttu-id="53069-115">![“选项卡”对话框的外观](media/tabsdialog.gif "“选项卡”对话框的外观")</span><span class="sxs-lookup"><span data-stu-id="53069-115">![Appearance of the Tabs dialog box](media/tabsdialog.gif "Appearance of the Tabs dialog box")</span></span>  
  
3.  <span data-ttu-id="53069-116">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="53069-116">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="53069-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="53069-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="53069-118">最大化查询编辑器</span><span class="sxs-lookup"><span data-stu-id="53069-118">Maximizing Query Editor</span></span>](lesson-2-3-maximizing-query-editor.md)  
  
  
