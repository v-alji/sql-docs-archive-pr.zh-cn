---
title: 多用户环境 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- users [SQL Server], multiuser environments
- conflict resolution [Visual Database Tools]
- multiple users making database changes
- multiuser environments [Visual Database Tools]
- database modifications [SQL Server]
- version control [Visual Database Tools]
- Visual Database Tools [SQL Server], multiuser environments
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2e219ecda25f477aa459de674a43d9c2360376ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579937"
---
# <a name="multiuser-environments-visual-database-tools"></a><span data-ttu-id="6e202-102">多用户环境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6e202-102">Multiuser Environments (Visual Database Tools)</span></span>
  <span data-ttu-id="6e202-103">多用户环境是指如下环境：在该环境中，其他用户可以连接到您正在使用的同一数据库，并对其进行修改。</span><span class="sxs-lookup"><span data-stu-id="6e202-103">A multiuser environment is one in which other users can connect and make changes to the same database that you are working with.</span></span> <span data-ttu-id="6e202-104">因此，多个用户可能同时对同一数据库对象进行操作。</span><span class="sxs-lookup"><span data-stu-id="6e202-104">As a result, several users might be working with the same database objects at the same time.</span></span> <span data-ttu-id="6e202-105">这样，在多用户环境中，在您进行更改时，数据库可能会受到其他用户所做更改的影响；反之亦然。</span><span class="sxs-lookup"><span data-stu-id="6e202-105">Thus, a multiuser environment introduces the possibility of the database being affected by changes made by other users while you are making changes, and vice versa.</span></span>  
  
 <span data-ttu-id="6e202-106">在多用户环境中使用数据库的关键问题是访问权限。</span><span class="sxs-lookup"><span data-stu-id="6e202-106">A key issue when working with databases in a multiuser environment is access permissions.</span></span> <span data-ttu-id="6e202-107">您所拥有的数据库权限决定了您可以对数据库执行的操作范围。</span><span class="sxs-lookup"><span data-stu-id="6e202-107">The permissions you have for the database determine the extent of the work you can do with the database.</span></span> <span data-ttu-id="6e202-108">例如，若要对数据库中的对象进行更改，您必须对该数据库具有相应的写权限。</span><span class="sxs-lookup"><span data-stu-id="6e202-108">For example, to make changes to objects in a database, you must have the appropriate write permissions for the database.</span></span> <span data-ttu-id="6e202-109">有关数据库中的权限的详细信息，请参阅数据库文档。</span><span class="sxs-lookup"><span data-stu-id="6e202-109">For more information about permissions in your database, see your database documentation.</span></span> <span data-ttu-id="6e202-110">有关详细信息，请参阅[权限和 Visual Database Tools (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="6e202-110">For more information see [Permissions and Visual Database Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="6e202-111">在保存对表所做的更改时，表设计器将验证自您上次保存更改以来该数据库是否已修改。</span><span class="sxs-lookup"><span data-stu-id="6e202-111">When you save changes made to tables, Table Designer verifies that the database has not been modified since you last saved changes.</span></span> <span data-ttu-id="6e202-112">如果另一个用户已进行了更改，则通知您数据库已修改。</span><span class="sxs-lookup"><span data-stu-id="6e202-112">If another user has made changes, you will be notified that the database has been modified.</span></span> <span data-ttu-id="6e202-113">您可能需要协调这些更改。</span><span class="sxs-lookup"><span data-stu-id="6e202-113">You may need to reconcile these changes.</span></span> <span data-ttu-id="6e202-114">有关详细信息，请参阅[协调多个用户所做的更改 (Visual Database Tools)](reconcile-changes-made-by-multiple-users-visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="6e202-114">For more information, see [Reconcile Changes Made by Multiple Users &#40;Visual Database Tools&#41;](reconcile-changes-made-by-multiple-users-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="6e202-115">在多用户环境中，应牢记一些特殊注意事项以避免发生更改冲突。</span><span class="sxs-lookup"><span data-stu-id="6e202-115">In a multiuser environment there are special considerations to keep in mind to avoid conflicting changes.</span></span> <span data-ttu-id="6e202-116">有关详细信息，请参阅[数据库演化问题 (Visual Database Tools)](issues-of-database-evolution-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="6e202-116">For more information, see [Issues of Database Evolution &#40;Visual Database Tools&#41;](issues-of-database-evolution-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="6e202-117">避免问题的一种方法是在进行更改时在数据库的副本（如测试数据库）中工作，然后可以创建一个更改脚本，在脱机解决冲突之后，就可以运行该脚本在原始数据库上执行这些更改。</span><span class="sxs-lookup"><span data-stu-id="6e202-117">One way to avoid problems is to work in a copy of the database, such as a test database, when you make changes, then you can create a change script that you can run to make those changes on the original database after resolving conflicts offline.</span></span> <span data-ttu-id="6e202-118">有关详细信息，请参阅[开发、测试和生产数据库 (Visual Database Tools)](development-test-and-production-databases-visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="6e202-118">For more information see [Development, Test, and Production Databases &#40;Visual Database Tools&#41;](development-test-and-production-databases-visual-database-tools.md).</span></span>  
  
  
