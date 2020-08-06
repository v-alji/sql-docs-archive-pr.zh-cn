---
title: 授予访问数据库的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45b6d6c8dcd9c04d18489807271802aafee785b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590478"
---
# <a name="granting-access-to-a-database"></a><span data-ttu-id="4ab24-102">授予访问数据库的权限</span><span class="sxs-lookup"><span data-stu-id="4ab24-102">Granting Access to a Database</span></span>
  <span data-ttu-id="4ab24-103">现在 Mary 具有访问此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的权限，但是不具有访问数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="4ab24-103">Mary now has access to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but does not have permission to access the databases.</span></span> <span data-ttu-id="4ab24-104">在授权她作为数据库用户之前，她甚至无权访问其默认数据库 **TestData** 。</span><span class="sxs-lookup"><span data-stu-id="4ab24-104">She does not even have access to her default database **TestData** until you authorize her as a database user.</span></span>  
  
 <span data-ttu-id="4ab24-105">若要授予 Mary 访问权限，请切换到 **TestData** 数据库，再使用 CREATE USER 语句将她的登录名映射到名为 Mary 的用户。</span><span class="sxs-lookup"><span data-stu-id="4ab24-105">To grant Mary access, switch to the **TestData** database, and then use the CREATE USER statement to map her login to a user named Mary.</span></span>  
  
### <a name="to-create-a-user-in-a-database"></a><span data-ttu-id="4ab24-106">在数据库中创建用户</span><span class="sxs-lookup"><span data-stu-id="4ab24-106">To create a user in a database</span></span>  
  
1.  <span data-ttu-id="4ab24-107">键入并执行下列语句（将 `computer_name` 替换为您计算机的名称），以授予 `Mary` 访问 `TestData` 数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="4ab24-107">Type and execute the following statements (replacing `computer_name` with the name of your computer) to grant `Mary` access to the `TestData` database.</span></span>  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     <span data-ttu-id="4ab24-108">现在，对于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 和 `TestData` 数据库，Mary 都具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="4ab24-108">Now, Mary has access to both [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the `TestData` database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4ab24-109">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="4ab24-109">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4ab24-110">创建视图和存储过程</span><span class="sxs-lookup"><span data-stu-id="4ab24-110">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
