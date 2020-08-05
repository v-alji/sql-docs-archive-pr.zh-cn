---
title: 重命名用户 sys |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3af9d31a54adc5645cab6fcc7104ae7ff27a61b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577233"
---
# <a name="rename-user-sys"></a><span data-ttu-id="f1526-102">重命名 sys 用户</span><span class="sxs-lookup"><span data-stu-id="f1526-102">Rename user sys</span></span>
  <span data-ttu-id="f1526-103">升级顾问检测到数据库中的用户名为**sys** 。</span><span class="sxs-lookup"><span data-stu-id="f1526-103">Upgrade Advisor detected the user name **sys** in a database.</span></span> <span data-ttu-id="f1526-104">该名称为保留名称。</span><span class="sxs-lookup"><span data-stu-id="f1526-104">This name is reserved.</span></span> <span data-ttu-id="f1526-105">在升级之前，请重命名该用户。</span><span class="sxs-lookup"><span data-stu-id="f1526-105">Rename the user before you upgrade.</span></span> <span data-ttu-id="f1526-106">如果未重命名该用户，则数据库在升级过程结束之后将处于可疑状态并且将不可用，直至将数据库联机为止。</span><span class="sxs-lookup"><span data-stu-id="f1526-106">If the user is not renamed, the database will be in a suspect state after the upgrade process and will be unavailable until the database is brought online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="f1526-107">组件</span><span class="sxs-lookup"><span data-stu-id="f1526-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="f1526-108">说明</span><span class="sxs-lookup"><span data-stu-id="f1526-108">Description</span></span>  
 <span data-ttu-id="f1526-109">已保留用户**sys** 。</span><span class="sxs-lookup"><span data-stu-id="f1526-109">User **sys** is reserved.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f1526-110">纠正措施</span><span class="sxs-lookup"><span data-stu-id="f1526-110">Corrective Action</span></span>  
  
### <a name="before-upgrade-procedure"></a><span data-ttu-id="f1526-111">升级前的步骤</span><span class="sxs-lookup"><span data-stu-id="f1526-111">Before Upgrade Procedure</span></span>  
 <span data-ttu-id="f1526-112">升级之前，在包含用户**sys**的每个数据库中，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f1526-112">Before you upgrade, in each database that contains user **sys**, do the following:</span></span>  
  
1.  <span data-ttu-id="f1526-113">创建一个新用户。</span><span class="sxs-lookup"><span data-stu-id="f1526-113">Create a new user.</span></span>  
  
2.  <span data-ttu-id="f1526-114">使用下列语句显示用户**sys**授予的所有权限，并授予用户**sys**权限。</span><span class="sxs-lookup"><span data-stu-id="f1526-114">Use the following statements to display all permissions that are granted by user **sys** and granted to user **sys**.</span></span>  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  <span data-ttu-id="f1526-115">若要将**sys**拥有的所有对象的所有权转移给新用户，请使用**sp_changeobjectowner**。</span><span class="sxs-lookup"><span data-stu-id="f1526-115">To transfer ownership of all objects owned by **sys** to the new user, use **sp_changeobjectowner**.</span></span>  
  
4.  <span data-ttu-id="f1526-116">删除用户**sys**。</span><span class="sxs-lookup"><span data-stu-id="f1526-116">Drop user **sys**.</span></span>  
  
5.  <span data-ttu-id="f1526-117">若要还原在步骤2中捕获的原始权限，请使用 GRANT 语句的 AS *new_user*子句。</span><span class="sxs-lookup"><span data-stu-id="f1526-117">To restore the original permissions captured in step 2, use the AS *new_user* clause of the GRANT statement.</span></span>  
  
6.  <span data-ttu-id="f1526-118">修改脚本以引用新用户。</span><span class="sxs-lookup"><span data-stu-id="f1526-118">Modify scripts to reference the new user.</span></span> <span data-ttu-id="f1526-119">例如，脚本中包含的 `SELECT * FROM sys.my`_`table` 语句必须更改为 `SELECT * FROM new_user.my_table`。</span><span class="sxs-lookup"><span data-stu-id="f1526-119">For example, scripts that contain statements such as `SELECT * FROM sys.my`_`table` must be changed to `SELECT * FROM new_user.my_table`.</span></span>  
  
### <a name="after-upgrade-procedure"></a><span data-ttu-id="f1526-120">升级后的步骤</span><span class="sxs-lookup"><span data-stu-id="f1526-120">After Upgrade Procedure</span></span>  
 <span data-ttu-id="f1526-121">如果在升级之前未重命名用户**sys** ，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f1526-121">If the user **sys** was not renamed prior to upgrading, do the following:</span></span>  
  
1.  <span data-ttu-id="f1526-122">执行语句 `ALTER DATABASE db_name SET ONLINE` 。</span><span class="sxs-lookup"><span data-stu-id="f1526-122">Execute the statement `ALTER DATABASE db_name SET ONLINE`.</span></span> <span data-ttu-id="f1526-123">数据库将处于 SINGLE_USER 模式。</span><span class="sxs-lookup"><span data-stu-id="f1526-123">The database will be in SINGLE_USER mode.</span></span>  
  
2.  <span data-ttu-id="f1526-124">执行“升级前的步骤”部分中的所有步骤。</span><span class="sxs-lookup"><span data-stu-id="f1526-124">Follow all steps in the Before Upgrade Procedure section.</span></span>  
  
3.  <span data-ttu-id="f1526-125">执行语句 `ALTER DATABASE db_name SET MULTI_USER` 。</span><span class="sxs-lookup"><span data-stu-id="f1526-125">Execute the statement `ALTER DATABASE db_name SET MULTI_USER`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1526-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1526-126">See Also</span></span>  
 <span data-ttu-id="f1526-127">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="f1526-127">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="f1526-128">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="f1526-128">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
