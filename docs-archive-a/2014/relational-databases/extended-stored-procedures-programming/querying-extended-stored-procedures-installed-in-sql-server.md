---
title: 查询在 SQL Server 中安装的扩展存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f44db9053ad18c3a6902a30aaab4f81610c5a8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579591"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a><span data-ttu-id="bcfc2-102">查询在 SQL Server 中安装的扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="bcfc2-102">Querying Extended Stored Procedures Installed in SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="bcfc2-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="bcfc2-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="bcfc2-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 经过身份验证的用户可以通过运行**sp_helpextendedproc**系统过程来显示当前定义的扩展存储过程和每个存储过程所属的 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="bcfc2-104">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated user can display the currently defined extended stored procedures and the name of the DLL to which each belongs by running the **sp_helpextendedproc** system procedure.</span></span> <span data-ttu-id="bcfc2-105">例如，下面的示例返回**xp_hello**所属的 DLL：</span><span class="sxs-lookup"><span data-stu-id="bcfc2-105">For example, the following example returns the DLL to which **xp_hello** belongs:</span></span>  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="bcfc2-106">如果在不指定扩展存储过程的情况下执行**sp_helpextendedproc** ，则将显示所有扩展存储过程及其 dll。</span><span class="sxs-lookup"><span data-stu-id="bcfc2-106">If **sp_helpextendedproc** is executed without specifying an extended stored procedure, all the extended stored procedures and their DLLs are displayed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bcfc2-107">将仅为那些登录用户拥有或具有权限的扩展存储过程返回信息。</span><span class="sxs-lookup"><span data-stu-id="bcfc2-107">Information will be returned for only those extended stored procedures that the logged in user owns or has permissions to.</span></span> <span data-ttu-id="bcfc2-108">只有**sysadmin**固定服务器角色的成员和**db_owner**、 **db_securityadmin**和**db_ddladmin**固定数据库角色的成员才能查看所有扩展存储过程的信息。</span><span class="sxs-lookup"><span data-stu-id="bcfc2-108">Only members of the **sysadmin** fixed server role and the **db_owner**, **db_securityadmin**, and the **db_ddladmin** fixed database roles can view information for all extended stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfc2-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bcfc2-109">See Also</span></span>  
 <span data-ttu-id="bcfc2-110">[sp_helpextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bcfc2-110">[sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span></span>  
 <span data-ttu-id="bcfc2-111">[sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bcfc2-111">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="bcfc2-112">sp_dropextendedproc (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bcfc2-112">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
