---
title: 从 SQL Server 中删除扩展存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.openlocfilehash: 284da815de073248669da032c06ddeeb68c697a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694466"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a><span data-ttu-id="74eac-102">从 SQL Server 中删除扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="74eac-102">Removing an Extended Stored Procedure from SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="74eac-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="74eac-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="74eac-104">若要删除用户定义的扩展存储过程 DLL 中的每个扩展存储过程函数， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员必须运行**sp_dropextendedproc**系统存储过程，并指定函数的名称和该函数所驻留的 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="74eac-104">To drop each extended stored procedure function in a user-defined extended stored procedure DLL, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must run the **sp_dropextendedproc** system stored procedure, specifying the name of the function and the name of the DLL in which that function resides.</span></span> <span data-ttu-id="74eac-105">例如，此命令将从中删除名为 xp_hello.dll 的 DLL 中的函数**xp_hello** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="74eac-105">For example, this command removes the function **xp_hello**, located in a DLL named xp_hello.dll, from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="74eac-106">从开始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ， **sp_dropextendedproc**不删除系统扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="74eac-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** does not drop system extended stored procedures.</span></span> <span data-ttu-id="74eac-107">相反，系统管理员应对**公共**角色拒绝对扩展存储过程的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="74eac-107">Instead, the system administrator should deny EXECUTE permission on the extended stored procedure to the **public** role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74eac-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74eac-108">See Also</span></span>  
 [<span data-ttu-id="74eac-109">sp_dropextendedproc (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="74eac-109">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
