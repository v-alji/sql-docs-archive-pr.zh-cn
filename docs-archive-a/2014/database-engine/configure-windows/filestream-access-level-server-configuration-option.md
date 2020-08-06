---
title: “文件流访问级别”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dfa43b8e6e1762e87dd9c2abbdf7a583963e196e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590945"
---
# <a name="filestream-access-level-server-configuration-option"></a><span data-ttu-id="45799-102">filestream access level 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="45799-102">filestream access level Server Configuration Option</span></span>
  <span data-ttu-id="45799-103">可以使用 filestream_access_level 选项来更改此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的 FILESTREAM 访问级别。</span><span class="sxs-lookup"><span data-stu-id="45799-103">Use the filestream_access_level option to change the FILESTREAM access level for this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45799-104">必须先启用 Windows FILESTREAM 管理设置，然后此选项才会生效。</span><span class="sxs-lookup"><span data-stu-id="45799-104">Before this option has any effect, the Windows administration settings for FILESTREAM must be enabled.</span></span> <span data-ttu-id="45799-105">可以在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时启用这些设置，也可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器进行启用。</span><span class="sxs-lookup"><span data-stu-id="45799-105">You can enable these settings when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
|<span data-ttu-id="45799-106">值</span><span class="sxs-lookup"><span data-stu-id="45799-106">Value</span></span>|<span data-ttu-id="45799-107">定义</span><span class="sxs-lookup"><span data-stu-id="45799-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="45799-108">0</span><span class="sxs-lookup"><span data-stu-id="45799-108">0</span></span>|<span data-ttu-id="45799-109">为此实例禁用 FILESTREAM 支持。</span><span class="sxs-lookup"><span data-stu-id="45799-109">Disables FILESTREAM support for this instance.</span></span>|  
|<span data-ttu-id="45799-110">1</span><span class="sxs-lookup"><span data-stu-id="45799-110">1</span></span>|<span data-ttu-id="45799-111">针对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="45799-111">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span>|  
|<span data-ttu-id="45799-112">2</span><span class="sxs-lookup"><span data-stu-id="45799-112">2</span></span>|<span data-ttu-id="45799-113">针对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和 Win32 流访问启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="45799-113">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] and Win32 streaming access.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45799-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45799-114">See Also</span></span>  
 <span data-ttu-id="45799-115">[数据库引擎配置 - 文件流](../../sql-server/install/database-engine-configuration-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="45799-115">[Database Engine Configuration - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span></span>  
 [<span data-ttu-id="45799-116">启用和配置 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="45799-116">Enable and Configure FILESTREAM</span></span>](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
