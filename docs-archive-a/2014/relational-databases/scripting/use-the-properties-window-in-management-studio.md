---
title: 使用 Management Studio 中的“属性”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: rothja
ms.author: jroth
ms.openlocfilehash: 5030bf85fc87482b11e91967ff8fb1baf77a213e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590697"
---
# <a name="use-the-properties-window-in-management-studio"></a><span data-ttu-id="7ae3a-102">使用 Management Studio 中的“属性”窗口</span><span class="sxs-lookup"><span data-stu-id="7ae3a-102">Use the Properties Window in Management Studio</span></span>
  <span data-ttu-id="7ae3a-103">“属性”窗口用于说明 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的项（如连接或 Showplan 运算符）的状态，以及有关数据库对象（如表、视图和设计器等）的信息。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-103">The Properties window describes the state of an item in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as a connection or a Showplan operator, and information about database objects such as tables, views, and designers.</span></span>  
  
 <span data-ttu-id="7ae3a-104">可以使用“属性”窗口查看当前连接的属性。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-104">You can use the Properties window to view the properties of the current connection.</span></span> <span data-ttu-id="7ae3a-105">许多属性在“属性”窗口中是只读的，但可以在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的其他地方更改。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-105">Many properties are read-only in the Properties window but can be changed elsewhere in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="7ae3a-106">例如，查询的数据库属性在“属性”窗口中是只读的，但可在工具栏上更改。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-106">For example, the Database property of a query is read-only in the Properties window, but can be changed on the tool bar.</span></span>  
  
### <a name="to-view-properties-using-the-properties-window"></a><span data-ttu-id="7ae3a-107">使用“属性”窗口查看属性</span><span class="sxs-lookup"><span data-stu-id="7ae3a-107">To view properties using the Properties window</span></span>  
  
1.  <span data-ttu-id="7ae3a-108">如果“属性”窗口不可见，请在 **“查看”** 菜单中单击 **“属性窗口”** ，或者按 F4。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-108">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="7ae3a-109">将要查看的对象设置为焦点。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-109">Set the focus on the object that you want to view.</span></span>  
  
3.  <span data-ttu-id="7ae3a-110">在“属性”窗口中查找特定的属性。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-110">Look for a specific property in the Properties window.</span></span>  
  
### <a name="to-view-connection-properties-of-a-query-window"></a><span data-ttu-id="7ae3a-111">查看查询窗口的连接属性</span><span class="sxs-lookup"><span data-stu-id="7ae3a-111">To view connection properties of a query window</span></span>  
  
1.  <span data-ttu-id="7ae3a-112">如果“属性”窗口不可见，请在 **“查看”** 菜单中单击 **“属性窗口”** ，或者按 F4。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-112">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="7ae3a-113">在“属性”窗口中，可以看到所有连接属性。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-113">In the Properties window, you can see all the connection properties.</span></span>  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a><span data-ttu-id="7ae3a-114">查看 Showplan 运算符的属性</span><span class="sxs-lookup"><span data-stu-id="7ae3a-114">To view the properties of a Showplan operator</span></span>  
  
1.  <span data-ttu-id="7ae3a-115">在 **“查询”** 菜单上，单击 **“包括实际的执行计划”** 。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-115">On the **Query** menu, click **Include Actual Execution Plan**.</span></span>  
  
2.  <span data-ttu-id="7ae3a-116">在 SQL 查询编辑器中，键入并执行一个查询。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-116">In the SQL Query Editor, type and execute a query.</span></span>  
  
3.  <span data-ttu-id="7ae3a-117">如果“属性”窗口不可见，请在 **“查看”** 菜单中单击 **“属性窗口”** ，或者按 F4。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-117">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
4.  <span data-ttu-id="7ae3a-118">在 SQL 查询编辑器的 **“执行计划”** 选项卡中单击运算符的图标，可在“属性”窗口中查看有关这些运算符的信息。</span><span class="sxs-lookup"><span data-stu-id="7ae3a-118">On the **Execution plan** tab of the SQL Query Editor click the icons of the operators to view information about the operators in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae3a-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ae3a-119">See Also</span></span>  
 [<span data-ttu-id="7ae3a-120">属性窗口 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7ae3a-120">Properties Window &#40;Management Studio&#41;</span></span>](../../ssms/properties-window-management-studio.md)  
  
  
