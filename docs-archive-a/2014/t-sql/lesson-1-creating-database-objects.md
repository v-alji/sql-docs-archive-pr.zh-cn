---
title: 第 1 课：创建数据库对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 172fdbcaedc10f9c359befd48ed09ec825aea9bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691456"
---
# <a name="lesson-1-creating-database-objects"></a><span data-ttu-id="8d3bf-102">第 1 课：创建数据库对象</span><span class="sxs-lookup"><span data-stu-id="8d3bf-102">Lesson 1: Creating Database Objects</span></span>
  <span data-ttu-id="8d3bf-103">本课将介绍如何创建数据库，在数据库中创建表，然后访问表中的数据并对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-103">This lesson shows you how to create a database, create a table in the database, and then access and change the data in the table.</span></span> <span data-ttu-id="8d3bf-104">由于本课是对使用 [!INCLUDE[tsql](../includes/tsql-md.md)]的简介，因此它未使用或说明为这些语句提供的许多选项。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-104">Because this lesson is an introduction to using [!INCLUDE[tsql](../includes/tsql-md.md)], it does not use or describe the many options that are available for these statements.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="8d3bf-105">语句可以使用下列方法进行编写并提交到 [!INCLUDE[ssDE](../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="8d3bf-105">statements can be written and submitted to the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="8d3bf-106">通过使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-106">By using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="8d3bf-107">本教程假定使用的是 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，但是也可以使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express（可以从 [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=14630)免费下载）。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-107">This tutorial assumes that you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], but you can also use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express, which is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630).</span></span>  
  
-   <span data-ttu-id="8d3bf-108">通过使用 [sqlcmd 实用工具](../tools/sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-108">By using the [sqlcmd utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="8d3bf-109">通过从您创建的应用程序进行连接。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-109">By connecting from an application that you create.</span></span>  
  
 <span data-ttu-id="8d3bf-110">代码以相同方式和相同权限在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 上执行，而不管您如何提交代码语句。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-110">The code executes on the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the same way and with the same permissions, regardless of how you submit the code statements.</span></span>  
  
 <span data-ttu-id="8d3bf-111">若要在 [!INCLUDE[tsql](../includes/tsql-md.md)] 中运行 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]语句，请打开 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 并连接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="8d3bf-111">To run [!INCLUDE[tsql](../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], open [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8d3bf-112">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="8d3bf-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="8d3bf-113">创建数据库（教程）</span><span class="sxs-lookup"><span data-stu-id="8d3bf-113">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
-   [<span data-ttu-id="8d3bf-114">创建表（教程）</span><span class="sxs-lookup"><span data-stu-id="8d3bf-114">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
-   [<span data-ttu-id="8d3bf-115">插入和更新表中的数据（教程）</span><span class="sxs-lookup"><span data-stu-id="8d3bf-115">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
-   [<span data-ttu-id="8d3bf-116">读取表中的数据（教程）</span><span class="sxs-lookup"><span data-stu-id="8d3bf-116">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
-   [<span data-ttu-id="8d3bf-117">摘要：创建数据库对象</span><span class="sxs-lookup"><span data-stu-id="8d3bf-117">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8d3bf-118">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="8d3bf-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8d3bf-119">创建数据库（教程）</span><span class="sxs-lookup"><span data-stu-id="8d3bf-119">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
  
