---
title: 为复制启用数据库 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 307d52e24187e35c1c30f609facd13bfad569216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578102"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a><span data-ttu-id="c65ea-102">为复制启用数据库 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c65ea-102">Enable a Database for Replication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="c65ea-103">当 **sysadmin** 固定服务器角色的成员使用新建发布向导创建发布时，将为复制隐式启用数据库。</span><span class="sxs-lookup"><span data-stu-id="c65ea-103">A database is implicitly enabled for replication when a member of the **sysadmin** fixed server role creates a publication with the New Publication Wizard.</span></span> <span data-ttu-id="c65ea-104">**sysadmin** 固定服务器角色的成员还可以为复制显式启用数据库，使 **db_owner** 固定数据库角色的成员可以在该数据库中创建一个或多个发布。</span><span class="sxs-lookup"><span data-stu-id="c65ea-104">A member of the **sysadmin** fixed server role can also enable a database for replication explicitly, so that a member of the **db_owner** fixed database role can create one or more publications in that database.</span></span> <span data-ttu-id="c65ea-105">若要显式启用数据库，请使用“发布服务器属性 - \<Publisher>”对话框的“发布数据库”页。</span><span class="sxs-lookup"><span data-stu-id="c65ea-105">To enable a database explicitly, use the **Publication Databases** page of the **Publisher Properties - \<Publisher>** dialog box.</span></span> <span data-ttu-id="c65ea-106">有关访问此对话框的详细信息，请参阅 [Create a Publication](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="c65ea-106">For more information about accessing this dialog box, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
### <a name="to-enable-a-database-for-replication"></a><span data-ttu-id="c65ea-107">为复制启用数据库</span><span class="sxs-lookup"><span data-stu-id="c65ea-107">To enable a database for replication</span></span>  
  
1.  <span data-ttu-id="c65ea-108">在“发布服务器属性 - \<Publisher>”对话框的“发布数据库”页上，选择每个要复制的数据库所对应的“事务”和/或“合并”复选框。</span><span class="sxs-lookup"><span data-stu-id="c65ea-108">On the **Publication Databases** page of the **Publisher Properties - \<Publisher>** dialog box, select the **Transactional** and/or **Merge** check box for each database you want to replicate.</span></span> <span data-ttu-id="c65ea-109">选择 **“事务”** 将为快照复制启用数据库。</span><span class="sxs-lookup"><span data-stu-id="c65ea-109">Select **Transactional** to enable the database for snapshot replication.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
