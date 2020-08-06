---
title: open objects 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6d22a3d6dd358afe9cf921376664c2d25705a6a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683047"
---
# <a name="open-objects-server-configuration-option"></a><span data-ttu-id="cb90c-102">open objects 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="cb90c-102">open objects Server Configuration Option</span></span>
  <span data-ttu-id="cb90c-103">尽管在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中已禁用此选项的功能，但此选项仍然存在于 sp_configure 中。</span><span class="sxs-lookup"><span data-stu-id="cb90c-103">This option is still present in **sp_configure**, although its functionality has been disabled in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cb90c-104">（其设置不起作用。）在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，打开的数据库对象的数量是动态管理的，该数量只受可用内存的限制。</span><span class="sxs-lookup"><span data-stu-id="cb90c-104">(The setting has no effect.) In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the number of open database objects is managed dynamically and is limited only by the available memory.</span></span> <span data-ttu-id="cb90c-105">**sp_configure** 中可用的 **open objects** 选项用于现有脚本的后向兼容性。</span><span class="sxs-lookup"><span data-stu-id="cb90c-105">The **open objects** option available in **sp_configure** for backward compatibility with existing scripts.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb90c-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb90c-106">See Also</span></span>  
 [<span data-ttu-id="cb90c-107">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cb90c-107">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
