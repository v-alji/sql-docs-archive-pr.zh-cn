---
title: “查询参数”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 76052876ad2899fc959aa7fc49f4299e08bac713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688404"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a><span data-ttu-id="f0a43-102">“查询参数”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0a43-102">Query Parameters Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="f0a43-103">使用此对话框可为查询中定义的参数输入值。</span><span class="sxs-lookup"><span data-stu-id="f0a43-103">This dialog allows you to enter values for the parameters defined in the query.</span></span> <span data-ttu-id="f0a43-104">在执行包含需要最终用户在运行时输入的参数的查询时，将显示此对话框。</span><span class="sxs-lookup"><span data-stu-id="f0a43-104">This dialog box appears when you execute a query that contains parameters that require end-user input at run time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0a43-105">选项</span><span class="sxs-lookup"><span data-stu-id="f0a43-105">Options</span></span>  
 <span data-ttu-id="f0a43-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="f0a43-106">**Name**</span></span>  
 <span data-ttu-id="f0a43-107">列出为正在执行的查询定义的参数。</span><span class="sxs-lookup"><span data-stu-id="f0a43-107">Lists the parameters defined for the query being executed.</span></span> <span data-ttu-id="f0a43-108">如果该查询包含命名参数，则这些名称将显示在该列表中。</span><span class="sxs-lookup"><span data-stu-id="f0a43-108">If the query contains named parameters, the names appear in the list.</span></span> <span data-ttu-id="f0a43-109">如果该查询包含未命名参数，则会为该查询中的每个参数列出系统定义的参数名称。</span><span class="sxs-lookup"><span data-stu-id="f0a43-109">If the query contains unnamed parameters, system-defined parameter names are listed for each parameter in the query.</span></span>  
  
 <span data-ttu-id="f0a43-110">**值**</span><span class="sxs-lookup"><span data-stu-id="f0a43-110">**Value**</span></span>  
 <span data-ttu-id="f0a43-111">为“名称”  下列出的每个参数输入值。</span><span class="sxs-lookup"><span data-stu-id="f0a43-111">Enter the value for each parameter listed under **Name**.</span></span> <span data-ttu-id="f0a43-112">最近所用的值将显示为默认的参数值。</span><span class="sxs-lookup"><span data-stu-id="f0a43-112">The value used most recently appears as the default parameter value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0a43-113">示例</span><span class="sxs-lookup"><span data-stu-id="f0a43-113">Example</span></span>  
 <span data-ttu-id="f0a43-114">SQL 窗格中的以下查询在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中执行时将打开“查询参数”对话框。</span><span class="sxs-lookup"><span data-stu-id="f0a43-114">The following query in the SQL Pane, opens the Query Parameters dialog box when executed in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0a43-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0a43-115">See Also</span></span>  
 [<span data-ttu-id="f0a43-116">使用参数进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0a43-116">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
