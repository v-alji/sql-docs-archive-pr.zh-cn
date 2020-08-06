---
title: “允许更新”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7e3ede317509a2044be90635db46e30a932af66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588045"
---
# <a name="allow-updates-server-configuration-option"></a><span data-ttu-id="b3a1e-102">allow updates 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="b3a1e-102">allow updates Server Configuration Option</span></span>
  <span data-ttu-id="b3a1e-103">此选项仍然存在于 **sp_configure** 存储过程中，但是其功能在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中不可用。</span><span class="sxs-lookup"><span data-stu-id="b3a1e-103">This option is still present in the **sp_configure** stored procedure, although its functionality is unavailable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b3a1e-104">其设置不起作用。</span><span class="sxs-lookup"><span data-stu-id="b3a1e-104">The setting has no effect.</span></span> <span data-ttu-id="b3a1e-105">不支持直接更新系统表。</span><span class="sxs-lookup"><span data-stu-id="b3a1e-105">Direct updates to the system tables are not supported.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="b3a1e-106">更改 **allow updates** 选项将导致 RECONFIGURE 语句失败。</span><span class="sxs-lookup"><span data-stu-id="b3a1e-106">Changing the **allow updates** option will cause the RECONFIGURE statement to fail.</span></span> <span data-ttu-id="b3a1e-107">应当从所有脚本中删除对 **allow updates** 选项的更改。</span><span class="sxs-lookup"><span data-stu-id="b3a1e-107">Changes to the **allow updates** option should be removed from all scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a1e-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3a1e-108">See Also</span></span>  
 [<span data-ttu-id="b3a1e-109">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b3a1e-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
