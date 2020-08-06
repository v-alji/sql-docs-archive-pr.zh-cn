---
title: 教程：编写 Transact-SQL 语句 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ac190d6099bca1a38ca2f286e6ce048fe5322e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693589"
---
# <a name="tutorial-writing-transact-sql-statements"></a><span data-ttu-id="61bf8-102">教程：编写 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="61bf8-102">Tutorial: Writing Transact-SQL Statements</span></span>
  <span data-ttu-id="61bf8-103">欢迎学习“编写 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句”教程。</span><span class="sxs-lookup"><span data-stu-id="61bf8-103">Welcome to the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="61bf8-104">本教程适用于对编写 SQL 语句不熟悉的用户。</span><span class="sxs-lookup"><span data-stu-id="61bf8-104">This tutorial is intended for users who are new to writing SQL statements.</span></span> <span data-ttu-id="61bf8-105">本教程通过回顾一些用于创建表和插入数据的基本语句，帮助新用户入门。</span><span class="sxs-lookup"><span data-stu-id="61bf8-105">It will help new users get started by reviewing some basic statements for creating tables and inserting data.</span></span> <span data-ttu-id="61bf8-106">本教程使用 [!INCLUDE[tsql](../includes/tsql-md.md)]，后者是 SQL 标准的 [!INCLUDE[msCoName](../includes/msconame-md.md)] 实现。</span><span class="sxs-lookup"><span data-stu-id="61bf8-106">This tutorial uses [!INCLUDE[tsql](../includes/tsql-md.md)], the [!INCLUDE[msCoName](../includes/msconame-md.md)] implementation of the SQL standard.</span></span> <span data-ttu-id="61bf8-107">本教程旨在简介 [!INCLUDE[tsql](../includes/tsql-md.md)] 语言，但不是要取代 [!INCLUDE[tsql](../includes/tsql-md.md)] 课程。</span><span class="sxs-lookup"><span data-stu-id="61bf8-107">This tutorial is intended as a brief introduction to the [!INCLUDE[tsql](../includes/tsql-md.md)] language and not as a replacement for a [!INCLUDE[tsql](../includes/tsql-md.md)] class.</span></span> <span data-ttu-id="61bf8-108">本教程特意选用了简单的语句，因此它们不能代表标准生产数据库中存在的语句的复杂程度。</span><span class="sxs-lookup"><span data-stu-id="61bf8-108">The statements in this tutorial are intentionally simple, and are not meant to represent the complexity found in a typical production database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61bf8-109">数据库初学者通常会发现，使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 而不是编写 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 语句，能够更容易地使用 [!INCLUDE[tsql](../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="61bf8-109">Novice users of databases will usually find it easier to work with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], instead of writing [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="61bf8-110">查找详细信息</span><span class="sxs-lookup"><span data-stu-id="61bf8-110">Finding More Information</span></span>  
 <span data-ttu-id="61bf8-111">若要查找有关任何特定语句的详细信息，请在 SQL Server 联机丛书中按名称搜索该语句，或使用“目录”浏览在 [Transact-SQL 引用（数据库引擎）](/sql/t-sql/language-reference)下按字母顺序列出的 1,800 个语言元素。</span><span class="sxs-lookup"><span data-stu-id="61bf8-111">To find more information about any specific statement, either search for the statement by name in SQL Server Books Online, or use the Contents to browse the 1,800 language elements listed alphabetically under [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span> <span data-ttu-id="61bf8-112">另一种查找信息的好办法是搜索与您感兴趣的主题相关的关键字。</span><span class="sxs-lookup"><span data-stu-id="61bf8-112">Another good strategy for finding information is to search for key words that are related to the subject matter you are interested in.</span></span> <span data-ttu-id="61bf8-113">例如，如果想要知道如何返回日期的一部分（例如月份），请在索引中搜索 **dates [SQL Server]** ，然后选择 **dateparts**。</span><span class="sxs-lookup"><span data-stu-id="61bf8-113">For example, if you want to know how to return a part of a date (such as the month), search the index for **dates [SQL Server]**, and then select **dateparts**.</span></span> <span data-ttu-id="61bf8-114">这会让你转到主题[日期部分 (Transact-SQL)](/sql/t-sql/functions/datepart-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="61bf8-114">This takes you to the topic [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql).</span></span> <span data-ttu-id="61bf8-115">作为另一个示例，若要了解如何使用字符串，请搜索 **string functions**。</span><span class="sxs-lookup"><span data-stu-id="61bf8-115">As another example, to find out how to work with strings, search for **string functions**.</span></span> <span data-ttu-id="61bf8-116">这会让你转到主题[字符串函数 (Transact-SQL)](/sql/t-sql/functions/string-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="61bf8-116">This takes you to the topic [String Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="61bf8-117">学习内容</span><span class="sxs-lookup"><span data-stu-id="61bf8-117">What You Will Learn</span></span>  
 <span data-ttu-id="61bf8-118">本教程将介绍如何创建数据库、在数据库中创建表、将数据插入到表中、更新数据、读取数据、删除数据，然后删除表。</span><span class="sxs-lookup"><span data-stu-id="61bf8-118">This tutorial shows you how to create a database, create a table in the database, insert data into the table, update the data, read the data, delete the data, and then delete the table.</span></span> <span data-ttu-id="61bf8-119">您将创建视图和存储过程，并为数据库和数据配置用户。</span><span class="sxs-lookup"><span data-stu-id="61bf8-119">You will create views and stored procedures and configure a user to the database and the data.</span></span>  
  
 <span data-ttu-id="61bf8-120">本教程分为三课：</span><span class="sxs-lookup"><span data-stu-id="61bf8-120">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="61bf8-121">第 1 课：创建数据库对象</span><span class="sxs-lookup"><span data-stu-id="61bf8-121">Lesson 1: Creating Database Objects</span></span>](lesson-1-creating-database-objects.md)  
 <span data-ttu-id="61bf8-122">在本课中，将介绍如何创建数据库、在数据库中创建表、将数据插入到表中、更新数据，然后读取数据。</span><span class="sxs-lookup"><span data-stu-id="61bf8-122">In this lesson, you create a database, create a table in the database, insert data into the table, update the data, and read the data.</span></span>  
  
 [<span data-ttu-id="61bf8-123">第 2 课：配置数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="61bf8-123">Lesson 2: Configuring Permissions on Database Objects</span></span>](lesson-2-configuring-permissions-on-database-objects.md)  
 <span data-ttu-id="61bf8-124">在本课中，将介绍如何创建登录名和用户。</span><span class="sxs-lookup"><span data-stu-id="61bf8-124">In this lesson, you create a login and user.</span></span> <span data-ttu-id="61bf8-125">还将创建视图和存储过程，再将用户权限授予存储过程。</span><span class="sxs-lookup"><span data-stu-id="61bf8-125">You will also create a view and a stored procedure, and then grant the user permission to the stored procedure.</span></span>  
  
 [<span data-ttu-id="61bf8-126">第 3 课：删除数据库对象</span><span class="sxs-lookup"><span data-stu-id="61bf8-126">Lesson 3: Deleting Database Objects</span></span>](lesson-3-1-deleting-database-objects.md)  
 <span data-ttu-id="61bf8-127">在本课中，将介绍如何删除对数据的访问权限、从表中删除数据、删除表，然后删除数据库。</span><span class="sxs-lookup"><span data-stu-id="61bf8-127">In this lesson, you remove access to data, delete data from a table, delete the table, and then delete the database.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61bf8-128">要求</span><span class="sxs-lookup"><span data-stu-id="61bf8-128">Requirements</span></span>  
 <span data-ttu-id="61bf8-129">为了完成本教程，您不必知道 SQL 语言，但是应该理解基本的数据库概念，如表。</span><span class="sxs-lookup"><span data-stu-id="61bf8-129">To complete this tutorial, you do not have to know the SQL language, but you should understand basic database concepts such as tables.</span></span> <span data-ttu-id="61bf8-130">在学习本教程的过程中，将创建一个数据库，并创建一个 Windows 用户。</span><span class="sxs-lookup"><span data-stu-id="61bf8-130">During this tutorial, you will create a database and create a Windows user.</span></span> <span data-ttu-id="61bf8-131">这些任务需要高级别的权限；因此，您应该以管理员身份登录到计算机。</span><span class="sxs-lookup"><span data-stu-id="61bf8-131">These tasks require a high level of permissions; therefore, you should log in to the computer as an administrator.</span></span>  
  
 <span data-ttu-id="61bf8-132">您的系统必须安装以下软件：</span><span class="sxs-lookup"><span data-stu-id="61bf8-132">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="61bf8-133">任何版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="61bf8-133">Any edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="61bf8-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 或 Management Studio Express。</span><span class="sxs-lookup"><span data-stu-id="61bf8-134">Either [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or Management Studio Express.</span></span>  
  
-   <span data-ttu-id="61bf8-135">Internet Explorer 6 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="61bf8-135">Internet Explorer 6 or later.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61bf8-136">查看教程时，建议您将 "**下一个**" 和 "**上一个**" 按钮添加到文档查看器工具栏。</span><span class="sxs-lookup"><span data-stu-id="61bf8-136">When you review the tutorials, we recommend that you add the **Next** and **Previous** buttons to the document viewer toolbar.</span></span>  
  
  
