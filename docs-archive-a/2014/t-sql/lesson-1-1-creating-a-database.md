---
title: 创建数据库（教程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99d5439c289b5d4e71786d4c6734f158f6bba371
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588181"
---
# <a name="creating-a-database-tutorial"></a><span data-ttu-id="fe666-102">创建数据库（教程）</span><span class="sxs-lookup"><span data-stu-id="fe666-102">Creating a Database (Tutorial)</span></span>
  <span data-ttu-id="fe666-103">与许多 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句一样，CREATE DATABASE 语句具有一个必需参数：数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="fe666-103">Like many [!INCLUDE[tsql](../includes/tsql-md.md)] statements, the CREATE DATABASE statement has a required parameter: the name of the database.</span></span> <span data-ttu-id="fe666-104">CREATE DATABASE 还具有许多可选参数，如希望放置数据库文件的磁盘位置。</span><span class="sxs-lookup"><span data-stu-id="fe666-104">CREATE DATABASE also has many optional parameters, such as the disk location where you want to put the database files.</span></span> <span data-ttu-id="fe666-105">在您执行不带可选参数的 CREATE DATABASE 时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用其中许多参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="fe666-105">When you execute CREATE DATABASE without the optional parameters, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses default values for many of these parameters.</span></span> <span data-ttu-id="fe666-106">本教程使用的可选语法参数非常少。</span><span class="sxs-lookup"><span data-stu-id="fe666-106">This tutorial uses very few of the optional syntax parameters.</span></span>  
  
### <a name="to-create-a-database"></a><span data-ttu-id="fe666-107">创建数据库</span><span class="sxs-lookup"><span data-stu-id="fe666-107">To create a database</span></span>  
  
1.  <span data-ttu-id="fe666-108">在查询编辑器窗口中，键入以下代码，但不要执行它：</span><span class="sxs-lookup"><span data-stu-id="fe666-108">In a Query Editor window, type but do not execute the following code:</span></span>  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  <span data-ttu-id="fe666-109">使用指针选择词语 `CREATE DATABASE`，再按 **F1**。</span><span class="sxs-lookup"><span data-stu-id="fe666-109">Use the pointer to select the words `CREATE DATABASE`, and then press **F1**.</span></span> <span data-ttu-id="fe666-110">应该会打开 SQL Server 联机丛书中的 CREATE DATABASE 主题。</span><span class="sxs-lookup"><span data-stu-id="fe666-110">The CREATE DATABASE topic in SQL Server Books Online should open.</span></span> <span data-ttu-id="fe666-111">您可以使用此方法查找 CREATE DATABASE 以及在本教程中使用的其他语句的完整语法。</span><span class="sxs-lookup"><span data-stu-id="fe666-111">You can use this technique to find the complete syntax for CREATE DATABASE and for the other statements that are used in this tutorial.</span></span>  
  
3.  <span data-ttu-id="fe666-112">在查询编辑器中，按 **F5** 以执行语句并创建名为 `TestData`的数据库。</span><span class="sxs-lookup"><span data-stu-id="fe666-112">In Query Editor, press **F5** to execute the statement and create a database named `TestData`.</span></span>  
  
 <span data-ttu-id="fe666-113">创建数据库时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 制作 **model** 数据库的副本，并将该副本重命名为数据库名称。</span><span class="sxs-lookup"><span data-stu-id="fe666-113">When you create a database, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] makes a copy of the **model** database, and renames the copy to the database name.</span></span> <span data-ttu-id="fe666-114">除非您将初始大小很大的数据库指定为可选参数，否则此操作应该只需要几秒钟。</span><span class="sxs-lookup"><span data-stu-id="fe666-114">This operation should only take several seconds, unless you specify a large initial size of the database as an optional parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe666-115">在单个批处理中提交多条语句时，可以用关键字 GO 分隔各语句。</span><span class="sxs-lookup"><span data-stu-id="fe666-115">The keyword GO separates statements when more than one statement is submitted in a single batch.</span></span> <span data-ttu-id="fe666-116">当批处理只包含一条语句时，GO 是可选的。</span><span class="sxs-lookup"><span data-stu-id="fe666-116">GO is optional when the batch contains only one statement.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fe666-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="fe666-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fe666-118">创建表（教程）</span><span class="sxs-lookup"><span data-stu-id="fe666-118">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="fe666-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe666-119">See Also</span></span>  
 [<span data-ttu-id="fe666-120">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fe666-120">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
