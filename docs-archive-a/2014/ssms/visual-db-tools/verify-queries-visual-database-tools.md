---
title: 验证查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bf24de9bdc0e8b7b7ceb33bb881812b180ce112
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587661"
---
# <a name="verify-queries-visual-database-tools"></a><span data-ttu-id="4b0da-102">验证查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4b0da-102">Verify Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="4b0da-103">为了避免问题，可以对所生成的查询进行检查以确保其语法正确。</span><span class="sxs-lookup"><span data-stu-id="4b0da-103">To avoid problems, you can check the query you have built to ensure its syntax is correct.</span></span> <span data-ttu-id="4b0da-104">在 [SQL 窗格](visual-database-tools.md)中输入语句时，此选项尤其有用。</span><span class="sxs-lookup"><span data-stu-id="4b0da-104">This option is especially useful when you enter statements in the [SQL pane](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4b0da-105">在验证查询时应谨记以下几点：</span><span class="sxs-lookup"><span data-stu-id="4b0da-105">Some notes to keep in mind about verifying queries:</span></span>  
  
-   <span data-ttu-id="4b0da-106">即使无法在“关系图”  窗格和“条件”  窗格中表示某个语句，该语句也可能是有效的，因此可以通过验证。</span><span class="sxs-lookup"><span data-stu-id="4b0da-106">A statement can be valid, and therefore be verified successfully, even if it cannot be represented in the **Diagram Pane** and **Criteria Pane**.</span></span>  
  
-   <span data-ttu-id="4b0da-107">SQL 验证可检测某些 SQL 错误，但不能检测所有 SQL 错误。</span><span class="sxs-lookup"><span data-stu-id="4b0da-107">SQL Verification can detect some, but not all SQL errors.</span></span> <span data-ttu-id="4b0da-108">如果查询包含在 SQL 验证过程中未检测到的错误，则在运行该查询时，数据库将检测到该错误。</span><span class="sxs-lookup"><span data-stu-id="4b0da-108">If a query contains an error not detected during SQL verification, the database will detect the error when you run the query.</span></span>  
  
-   <span data-ttu-id="4b0da-109">无法对包含参数的查询进行验证。</span><span class="sxs-lookup"><span data-stu-id="4b0da-109">Queries that contain parameters cannot be verified.</span></span>  
  
### <a name="to-verify-an-sql-statement"></a><span data-ttu-id="4b0da-110">验证 SQL 语句</span><span class="sxs-lookup"><span data-stu-id="4b0da-110">To verify an SQL statement</span></span>  
  
-   <span data-ttu-id="4b0da-111">右键单击“SQL 窗格”  ，然后从快捷菜单中选择“验证 SQL 语法”  。</span><span class="sxs-lookup"><span data-stu-id="4b0da-111">Right-click in the **SQL Pane**, and select **Verify SQL Syntax** from the shortcut menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0da-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b0da-112">See Also</span></span>  
 <span data-ttu-id="4b0da-113">[&#40;Visual Database Tools 运行查询&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4b0da-113">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4b0da-114">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4b0da-114">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
