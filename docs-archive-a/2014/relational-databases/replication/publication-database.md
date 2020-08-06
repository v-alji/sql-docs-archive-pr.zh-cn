---
title: 发布数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 511e5f2e2caa934313ba96fb3dbc4cadddace968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577542"
---
# <a name="publication-database"></a><span data-ttu-id="19666-102">发布数据库</span><span class="sxs-lookup"><span data-stu-id="19666-102">Publication Database</span></span>
  <span data-ttu-id="19666-103">发布数据库是发布服务器上的数据库，它是要复制的数据和数据库对象的源。</span><span class="sxs-lookup"><span data-stu-id="19666-103">The publication database is the database on the Publisher that is the source of data and database objects to be replicated.</span></span> <span data-ttu-id="19666-104">必须启用复制操作中使用的每个发布数据库。</span><span class="sxs-lookup"><span data-stu-id="19666-104">Each publication database used in replication must be enabled.</span></span> <span data-ttu-id="19666-105">当 **sysadmin** 固定服务器角色成员执行以下任一操作时，即可启用相应的数据库：</span><span class="sxs-lookup"><span data-stu-id="19666-105">The database is enabled when a member of the **sysadmin** fixed server role:</span></span>  
  
-   <span data-ttu-id="19666-106">使用新建发布向导对该数据库创建发布。</span><span class="sxs-lookup"><span data-stu-id="19666-106">Creates a publication on that database using the New Publication Wizard.</span></span>  
  
-   <span data-ttu-id="19666-107">在 **“发布服务器属性”** 对话框中选择该数据库。</span><span class="sxs-lookup"><span data-stu-id="19666-107">Selects the database in the **Publisher Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="19666-108">执行 **sp_replicationdboption** ，并将 **publish** （对于快照发布或事务发布）或 **merge publish** （对于合并发布）选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="19666-108">Executes **sp_replicationdboption** and sets the option **publish** (for snapshot or transactional publications) or **merge publish** (for merge publications) to **True**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="19666-109">选项</span><span class="sxs-lookup"><span data-stu-id="19666-109">Options</span></span>  
 <span data-ttu-id="19666-110">**数据库**</span><span class="sxs-lookup"><span data-stu-id="19666-110">**Databases**</span></span>  
 <span data-ttu-id="19666-111">选择包含要发布的数据和数据库对象的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="19666-111">Select the name of the database that contains the data and database objects that you want to publish.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19666-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19666-112">See Also</span></span>  
 <span data-ttu-id="19666-113">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="19666-113">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="19666-114">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="19666-114">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="19666-115">[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="19666-115">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="19666-116">sp_replicationdboption (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="19666-116">sp_replicationdboption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
