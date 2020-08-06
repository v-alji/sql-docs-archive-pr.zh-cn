---
title: 参数信息 (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: rothja
ms.author: jroth
ms.openlocfilehash: b7e5e7496753006808f75378182db0d3cb606d4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590157"
---
# <a name="parameter-info-intellisense"></a><span data-ttu-id="8ae52-102">参数信息 (IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="8ae52-102">Parameter Info (IntelliSense)</span></span>
  <span data-ttu-id="8ae52-103">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense 的 **“参数信息”** 选项可打开一个参数列表，其中提供了有关函数或存储过程所需的参数数目、参数名称和参数类型的信息。</span><span class="sxs-lookup"><span data-stu-id="8ae52-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Parameter Info** option opens a parameters list that provides information about the number, names, and types of the parameters that are required by a function or stored procedure.</span></span> <span data-ttu-id="8ae52-104">以粗体显示的参数指示键入某个函数或存储过程时所需的下一个参数。</span><span class="sxs-lookup"><span data-stu-id="8ae52-104">The parameter in bold indicates the next parameter that is required as you type a function or stored procedure.</span></span>  
  
 <span data-ttu-id="8ae52-105">对于嵌套函数，也会显示这一参数列表。</span><span class="sxs-lookup"><span data-stu-id="8ae52-105">The parameter list is also displayed for nested functions.</span></span> <span data-ttu-id="8ae52-106">如果将一个函数键入为另一个函数的参数，则参数列表将显示内部函数的参数。</span><span class="sxs-lookup"><span data-stu-id="8ae52-106">If you type a function as a parameter to another function, the parameter list displays the parameters for the inner function.</span></span> <span data-ttu-id="8ae52-107">内部函数参数列表完成后，参数列表会还原为显示外部函数参数。</span><span class="sxs-lookup"><span data-stu-id="8ae52-107">Then, when the inner function parameter list is complete, the parameter list reverts to displaying the outer function parameters.</span></span>  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a><span data-ttu-id="8ae52-108">查看函数或存储过程的参数信息</span><span class="sxs-lookup"><span data-stu-id="8ae52-108">To view Parameter Info for functions or stored procedures</span></span>  
  
1.  <span data-ttu-id="8ae52-109">在函数名称后面，以常用方式键入左括号，以打开参数列表。</span><span class="sxs-lookup"><span data-stu-id="8ae52-109">After the name of a function, type an open parenthesis as you usually type to open the parameters list.</span></span> <span data-ttu-id="8ae52-110">键入存储过程的名称后，照常键入空格以获取有关该过程参数的信息。</span><span class="sxs-lookup"><span data-stu-id="8ae52-110">After you type the name of a stored procedure, type a space as you usually type to obtain information about the procedure parameters.</span></span>  
  
     <span data-ttu-id="8ae52-111">IntelliSense 将在插入点下方的弹出窗口中显示存储过程的函数或参数的完整声明。</span><span class="sxs-lookup"><span data-stu-id="8ae52-111">IntelliSense displays the complete declaration for the function or the parameters for a stored procedure in a pop-up window just under the insertion point.</span></span> <span data-ttu-id="8ae52-112">列表中的第一个参数以粗体显示。</span><span class="sxs-lookup"><span data-stu-id="8ae52-112">The first parameter in the list appears in bold.</span></span>  
  
2.  <span data-ttu-id="8ae52-113">键入参数时，粗体会更改以反映您要输入的下一个参数。</span><span class="sxs-lookup"><span data-stu-id="8ae52-113">As you type the parameters, the bold font changes to reflect the next parameter that you need to enter.</span></span>  
  
3.  <span data-ttu-id="8ae52-114">按 ESC 随时关闭列表，或继续键入直到函数键入完成。</span><span class="sxs-lookup"><span data-stu-id="8ae52-114">Press ESC at any time to close the list, or continue typing until you have completed the function.</span></span>  
  
     <span data-ttu-id="8ae52-115">对于函数，如果键入右括号，还会关闭参数列表。</span><span class="sxs-lookup"><span data-stu-id="8ae52-115">For a function, if you type the closing parenthesis you also close the parameter list.</span></span>  
  
#### <a name="to-manually-start-parameter-info"></a><span data-ttu-id="8ae52-116">手动引导参数信息</span><span class="sxs-lookup"><span data-stu-id="8ae52-116">To manually start Parameter Info</span></span>  
  
1.  <span data-ttu-id="8ae52-117">在 **“编辑”** 菜单上，选择 **IntelliSense** ，再选择 **“参数信息”** 。</span><span class="sxs-lookup"><span data-stu-id="8ae52-117">On the **Edit** menu, select **IntelliSense** and then select **Parameter Info**.</span></span>  
  
2.  <span data-ttu-id="8ae52-118">按键盘快捷键 Ctrl+Shift+空格键。</span><span class="sxs-lookup"><span data-stu-id="8ae52-118">Press the CTRL+SHIFT+SPACE keyboard shortcut.</span></span>  
  
 <span data-ttu-id="8ae52-119">有关详细信息，请参阅[配置 IntelliSense (SQL Server Management Studio)](configure-intellisense-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="8ae52-119">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ae52-120">“参数信息”  选项仅可用于 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器和 XML 查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="8ae52-120">The **Parameter Info** option is available only for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the XML Query Editor.</span></span>  
  
  
