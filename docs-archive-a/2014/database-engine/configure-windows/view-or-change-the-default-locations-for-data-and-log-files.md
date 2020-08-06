---
title: 查看或更改数据和日志文件 (SQL Server Management Studio) 的默认位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: def6be137aecbab7f2730fa4c2bf210b374a3a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688191"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a><span data-ttu-id="2161f-102">查看或更改数据文件和日志文件的默认位置 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2161f-102">View or Change the Default Locations for Data and Log Files (SQL Server Management Studio)</span></span>
  <span data-ttu-id="2161f-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看和更改新的数据文件和日志文件的默认位置。</span><span class="sxs-lookup"><span data-stu-id="2161f-103">This topic describes how to view and change the default locations of new data and log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2161f-104">默认路径从注册表中获得。</span><span class="sxs-lookup"><span data-stu-id="2161f-104">The default path is obtained from the registry.</span></span> <span data-ttu-id="2161f-105">在更改位置后，如果未指定其他位置，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中创建的所有新数据库将使用该位置。</span><span class="sxs-lookup"><span data-stu-id="2161f-105">After you change the location all new databases created in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will use that location if a different location is not specified.</span></span>  
  
 <span data-ttu-id="2161f-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2161f-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2161f-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2161f-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2161f-108">建议</span><span class="sxs-lookup"><span data-stu-id="2161f-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2161f-109">**查看或更改数据文件和日志文件的默认位置，使用：**</span><span class="sxs-lookup"><span data-stu-id="2161f-109">**To view or change the data and log file default locations, using:**</span></span>  
  
     [<span data-ttu-id="2161f-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2161f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="2161f-111">**跟进：**  [更改默认位置](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2161f-111">**Follow Up:**  [Changing the Default Locations](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2161f-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="2161f-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2161f-113">建议</span><span class="sxs-lookup"><span data-stu-id="2161f-113">Recommendations</span></span>  
 <span data-ttu-id="2161f-114">保护数据文件和日志文件的最佳做法是确保它们受访问控制列表 (ACL) 保护。</span><span class="sxs-lookup"><span data-stu-id="2161f-114">The best practice for protecting your data files and log files is to ensure that they are protected by access control lists (ACLs).</span></span> <span data-ttu-id="2161f-115">ACL 应设置在创建这些文件的根目录下。</span><span class="sxs-lookup"><span data-stu-id="2161f-115">The ACLs should be set on the directory root under which the files are created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2161f-116">Security</span><span class="sxs-lookup"><span data-stu-id="2161f-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2161f-117">权限</span><span class="sxs-lookup"><span data-stu-id="2161f-117">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2161f-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2161f-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a><span data-ttu-id="2161f-119">查看或更改数据库文件的默认位置</span><span class="sxs-lookup"><span data-stu-id="2161f-119">To view or change the default locations for database files</span></span>  
  
1.  <span data-ttu-id="2161f-120">在对象资源浏览器中，右键单击某个服务器，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2161f-120">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2161f-121">在左窗格中，单击 **“数据库设置”** 页。</span><span class="sxs-lookup"><span data-stu-id="2161f-121">In the left panel, click the **Database settings** page.</span></span>  
  
3.  <span data-ttu-id="2161f-122">在 **“数据库默认位置”** 中，查看新的数据文件和日志文件的当前默认位置。</span><span class="sxs-lookup"><span data-stu-id="2161f-122">In **Database default locations**, view the current default locations for new data files and new log files.</span></span> <span data-ttu-id="2161f-123">若要更改默认位置，请在 **“数据”** 或 **“日志”** 字段中输入新的默认路径名，或者单击浏览按钮找到并选择路径名。</span><span class="sxs-lookup"><span data-stu-id="2161f-123">To change a default location, enter a new default pathname in the **Data** or **Log** field, or click the browse button to find and select a pathname.</span></span>  
  
##  <a name="follow-up-after-changing-the-default-locations"></a><a name="FollowUp"></a><span data-ttu-id="2161f-124">跟进：在更改默认位置之后</span><span class="sxs-lookup"><span data-stu-id="2161f-124">Follow Up: After Changing the Default Locations</span></span>  
 <span data-ttu-id="2161f-125">必须停止并重新启动 SQL Server 服务以完成更改。</span><span class="sxs-lookup"><span data-stu-id="2161f-125">You must stop and start the SQL Server service to complete the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2161f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2161f-126">See Also</span></span>  
 <span data-ttu-id="2161f-127">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2161f-127">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="2161f-128">创建数据库</span><span class="sxs-lookup"><span data-stu-id="2161f-128">Create a Database</span></span>](../../relational-databases/databases/create-a-database.md)  
  
  
