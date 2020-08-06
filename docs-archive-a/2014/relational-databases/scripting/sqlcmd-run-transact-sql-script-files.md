---
title: 使用 sqlcmd 运行 Transact-SQL 脚本文件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: rothja
ms.author: jroth
ms.openlocfilehash: cd34b089fc4e971cac9e5713cbe303192a7a48c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578780"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a><span data-ttu-id="581a1-102">使用 sqlcmd 运行 Transact-SQL 脚本文件</span><span class="sxs-lookup"><span data-stu-id="581a1-102">Run Transact-SQL Script Files Using sqlcmd</span></span>
  <span data-ttu-id="581a1-103">您可以使用 `sqlcmd` 运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="581a1-103">You can use `sqlcmd` to run a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="581a1-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件是一个文本文件，它可以包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、`sqlcmd` 命令以及脚本变量的组合。</span><span class="sxs-lookup"><span data-stu-id="581a1-104">A [!INCLUDE[tsql](../../includes/tsql-md.md)] script file is a text file that can contain a combination of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="581a1-105">若要使用记事本创建一个简单的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="581a1-105">To create a simple [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using Notepad, follow these steps:</span></span>  
  
1.  <span data-ttu-id="581a1-106">单击 **“开始”**，依次指向 **“所有程序”**、 **“附件”**，再单击 **“记事本”**。</span><span class="sxs-lookup"><span data-stu-id="581a1-106">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad**.</span></span>  
  
2.  <span data-ttu-id="581a1-107">复制以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码并将其粘贴到记事本：</span><span class="sxs-lookup"><span data-stu-id="581a1-107">Copy and paste the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code into Notepad:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  <span data-ttu-id="581a1-108">在 C 驱动器中将文件保存为 **myScript.sql** 。</span><span class="sxs-lookup"><span data-stu-id="581a1-108">Save the file as **myScript.sql** in the C drive.</span></span>  
  
### <a name="to-run-the-script-file"></a><span data-ttu-id="581a1-109">运行脚本文件</span><span class="sxs-lookup"><span data-stu-id="581a1-109">To run the script file</span></span>  
  
1.  <span data-ttu-id="581a1-110">打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="581a1-110">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="581a1-111">在命令提示符窗口中，键入：`sqlcmd -S myServer\instanceName -i C:\myScript.sql`</span><span class="sxs-lookup"><span data-stu-id="581a1-111">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`</span></span>  
  
3.  <span data-ttu-id="581a1-112">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="581a1-112">Press ENTER.</span></span>  
  
 <span data-ttu-id="581a1-113">[!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 员工的姓名和地址列表便会输出到命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="581a1-113">A list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] employee names and addresses is written to the command prompt window.</span></span>  
  
### <a name="to-save-this-output-to-a-text-file"></a><span data-ttu-id="581a1-114">将此输出保存到文本文件中</span><span class="sxs-lookup"><span data-stu-id="581a1-114">To save this output to a text file</span></span>  
  
1.  <span data-ttu-id="581a1-115">打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="581a1-115">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="581a1-116">在命令提示符窗口中，键入：`sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`</span><span class="sxs-lookup"><span data-stu-id="581a1-116">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`</span></span>  
  
3.  <span data-ttu-id="581a1-117">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="581a1-117">Press ENTER.</span></span>  
  
 <span data-ttu-id="581a1-118">命令提示符窗口中不会返回任何输出，</span><span class="sxs-lookup"><span data-stu-id="581a1-118">No output is returned in the Command Prompt window.</span></span> <span data-ttu-id="581a1-119">而是将输出发送到 EmpAdds.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="581a1-119">Instead, the output is sent to the EmpAdds.txt file.</span></span> <span data-ttu-id="581a1-120">您可以打开 EmpAdds.txt 文件来查看此输出操作。</span><span class="sxs-lookup"><span data-stu-id="581a1-120">You can verify this output by opening the EmpAdds.txt file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581a1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="581a1-121">See Also</span></span>  
 <span data-ttu-id="581a1-122">[启动 sqlcmd 实用工具](sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="581a1-122">[Start the sqlcmd Utility](sqlcmd-start-the-utility.md) </span></span>  
 [<span data-ttu-id="581a1-123">sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="581a1-123">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
