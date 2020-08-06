---
title: 第 2 课：配置数据库对象的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fcc6ee3ddf9be072b51bd568fd3e72eb6c871785
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693164"
---
# <a name="lesson-2-configuring-permissions-on-database-objects"></a><span data-ttu-id="2e067-102">第 2 课：配置数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="2e067-102">Lesson 2: Configuring Permissions on Database Objects</span></span>
  <span data-ttu-id="2e067-103">授予用户访问数据库的权限涉及三个步骤。</span><span class="sxs-lookup"><span data-stu-id="2e067-103">Granting a user access to a database involves three steps.</span></span> <span data-ttu-id="2e067-104">首先，创建登录名。</span><span class="sxs-lookup"><span data-stu-id="2e067-104">First, you create a login.</span></span> <span data-ttu-id="2e067-105">使用登录名，用户可以连接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e067-105">The login lets the user connect to the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="2e067-106">然后将登录名配置为指定数据库中的用户。</span><span class="sxs-lookup"><span data-stu-id="2e067-106">Then you configure the login as a user in the specified database.</span></span> <span data-ttu-id="2e067-107">最后，授予该用户访问数据库对象的权限。</span><span class="sxs-lookup"><span data-stu-id="2e067-107">And finally, you grant that user permission to database objects.</span></span> <span data-ttu-id="2e067-108">本课介绍了这三个步骤，并介绍了如何将视图和存储过程创建为对象。</span><span class="sxs-lookup"><span data-stu-id="2e067-108">This lesson shows you these three steps, and shows you how to create a view and a stored procedure as the object.</span></span>  
  
 <span data-ttu-id="2e067-109">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="2e067-109">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="2e067-110">创建登录名</span><span class="sxs-lookup"><span data-stu-id="2e067-110">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
-   [<span data-ttu-id="2e067-111">授予访问数据库的权限</span><span class="sxs-lookup"><span data-stu-id="2e067-111">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
-   [<span data-ttu-id="2e067-112">创建视图和存储过程</span><span class="sxs-lookup"><span data-stu-id="2e067-112">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
-   [<span data-ttu-id="2e067-113">授予访问数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="2e067-113">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
-   [<span data-ttu-id="2e067-114">摘要：配置数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="2e067-114">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2e067-115">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="2e067-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2e067-116">创建登录名</span><span class="sxs-lookup"><span data-stu-id="2e067-116">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
  
