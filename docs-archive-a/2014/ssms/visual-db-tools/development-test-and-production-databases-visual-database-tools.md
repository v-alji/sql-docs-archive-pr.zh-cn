---
title: 开发、测试和生产数据库 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98ac88aec42b53012e0f57233a089bddbd3c8cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688408"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a><span data-ttu-id="a0c4e-102">开发、测试和生产数据库 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a0c4e-102">Development, Test, and Production Databases (Visual Database Tools)</span></span>
  <span data-ttu-id="a0c4e-103">如果您有结构相同的两个数据库，则可以在一个数据库中进行更改，再将更改传播到另一个数据库。</span><span class="sxs-lookup"><span data-stu-id="a0c4e-103">If you have two databases with identical structure, you can make changes in one database and propagate those changes to the other.</span></span> <span data-ttu-id="a0c4e-104">例如，如果您有一个个人开发数据库和一个工作组范围的测试数据库，则可以修改开发数据库，再将更改传播到测试数据库。</span><span class="sxs-lookup"><span data-stu-id="a0c4e-104">For example, if you have a personal development database and a group-wide test database, you can modify the development database, then propagate those changes to the test database.</span></span>  
  
 <span data-ttu-id="a0c4e-105">为此，需要在单个会话中完成对开发数据库的所有修改，并创建该会话的更改脚本，在以后对测试数据库运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="a0c4e-105">To accomplish this, perform all the modifications in a single session with the development database, create a Change Script of your session and later run the script on the test database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c4e-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0c4e-106">See Also</span></span>  
 [<span data-ttu-id="a0c4e-107">多用户环境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a0c4e-107">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
