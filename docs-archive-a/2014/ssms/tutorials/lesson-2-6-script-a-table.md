---
title: 编写表脚本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 247c839d83768756c57297d47f952401a1c8fd46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580493"
---
# <a name="script-a-table"></a><span data-ttu-id="de968-102">编写表脚本</span><span class="sxs-lookup"><span data-stu-id="de968-102">Script a Table</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="de968-103">可以创建脚本，用于选择、插入、更新和删除表，以及用于创建、更改、删除或执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="de968-103">can create scripts to select, insert, update, and delete tables, and to create, alter, drop, or execute stored procedures.</span></span>  
  
 <span data-ttu-id="de968-104">有时您可能需要使用具有多个选项的脚本，如删除一个过程后再创建一个过程，或者创建一个表后再更改一个表。</span><span class="sxs-lookup"><span data-stu-id="de968-104">Sometimes you want a script with multiple options, such as drop a procedure and then create a procedure, or create a table then alter a table.</span></span> <span data-ttu-id="de968-105">若要创建组合的脚本，请将第一个脚本保存到“查询编辑器”窗口中，并将第二个脚本保存到剪贴板上，这样就可以在窗口中将第二个脚本粘贴到第一个脚本之后。</span><span class="sxs-lookup"><span data-stu-id="de968-105">To create combined scripts, save the first script to a Query Editor window and the second to the clipboard so you can paste it into the window after the first script.</span></span>  
  
## <a name="creating-an-update-script"></a><span data-ttu-id="de968-106">创建更新脚本</span><span class="sxs-lookup"><span data-stu-id="de968-106">Creating an Update Script</span></span>  
  
#### <a name="to-create-the-insert-script-for-a-table"></a><span data-ttu-id="de968-107">若要创建表的插入脚本，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="de968-107">To create the insert script for a table</span></span>  
  
1.  <span data-ttu-id="de968-108">在“对象资源管理器”中，依次展开服务器、“数据库”\*\*\*\*、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]、“表”\*\*\*\*，再右键单击“HumanResources.Employee”\*\*\*\*，然后指向“编写表脚本为”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de968-108">In Object Explorer, expand your server, expand **Databases**, expand [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], expand **Tables**, right-click **HumanResources.Employee**, and then point to **Script Table As**.</span></span>  
  
2.  <span data-ttu-id="de968-109">快捷菜单有七个可用脚本选项：“CREATE To”\*\*\*\*、“DROP To”\*\*\*\*、“DROP and CREATE To”\*\*\*\*、“SELECT To”\*\*\*\*、“INSERT To”\*\*\*\*、“UPDATE To”\*\*\*\* 和“DELETE To”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de968-109">The shortcut menu has seven available scripting options: **CREATE To**, **DROP To**, **DROP and CREATE To**, **SELECT To**, **INSERT To**, **UPDATE To**, and **DELETE To**.</span></span> <span data-ttu-id="de968-110">指向“UPDATE To”\*\*\*\*，再单击“新查询编辑器窗口”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de968-110">Point to **UPDATE To**, and then click **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="de968-111">系统将打开一个新查询编辑器窗口，执行连接并显示完整的更新语句。</span><span class="sxs-lookup"><span data-stu-id="de968-111">A new Query Editor window opens, makes a connection, and presents the entire update statement.</span></span>  
  
     <span data-ttu-id="de968-112">本练习阐释了除编写脚本创建表或存储过程外，脚本编写功能如何实现其他功能。</span><span class="sxs-lookup"><span data-stu-id="de968-112">This exercise demonstrates how the scripting feature can do more than just script the creation of a table or stored procedure.</span></span> <span data-ttu-id="de968-113">使用这项新功能可以将数据操作脚本快速添加到项目中，并可轻松编写执行存储过程的脚本。</span><span class="sxs-lookup"><span data-stu-id="de968-113">This new feature can help you quickly add data manipulation scripts to your project and easily script execution of stored procedures.</span></span> <span data-ttu-id="de968-114">这可以大量节省多字段的表和过程的执行时间。</span><span class="sxs-lookup"><span data-stu-id="de968-114">This can be a big timesaver for tables and procedures with many fields.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="de968-115">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="de968-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="de968-116">摘要：编写 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="de968-116">Summary: Writing Transact-SQL</span></span>](../../tutorials/summary-writing-transact-sql.md)  
  
  
