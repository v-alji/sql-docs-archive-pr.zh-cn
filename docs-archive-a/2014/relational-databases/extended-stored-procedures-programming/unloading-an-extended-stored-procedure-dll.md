---
title: 卸载扩展存储过程 DLL |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd4855390e95d949ab769d6567d6f106959dcde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576760"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a><span data-ttu-id="b4bdc-102">卸载扩展存储过程 DLL</span><span class="sxs-lookup"><span data-stu-id="b4bdc-102">Unloading an Extended Stored Procedure DLL</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="b4bdc-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="b4bdc-103">Use CLR Integration instead.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="b4bdc-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]调用 dll 的一项函数后，立即加载扩展存储过程 DLL。</span><span class="sxs-lookup"><span data-stu-id="b4bdc-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] loads an extended stored procedure DLL as soon as a call is made to one of the functions of the DLL.</span></span> <span data-ttu-id="b4bdc-105">该 DLL 会始终保持加载状态，直到服务器关闭或者系统管理员使用 DBCC 语句将其卸载。</span><span class="sxs-lookup"><span data-stu-id="b4bdc-105">The DLL remains loaded until the server is shut down or until the system administrator uses the DBCC statement to unload it.</span></span> <span data-ttu-id="b4bdc-106">例如，此命令卸载**xp_hello.dll**，允许系统管理员将此文件的较新版本复制到目录而不关闭服务器：</span><span class="sxs-lookup"><span data-stu-id="b4bdc-106">For example, this command unloads the **xp_hello.dll**, allowing the system administrator to copy a newer version of this file to the directory without shutting down the server:</span></span>  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4bdc-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4bdc-107">See Also</span></span>  
 [<span data-ttu-id="b4bdc-108">DBCC dllname &#40;免费&#41; &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="b4bdc-108">DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
