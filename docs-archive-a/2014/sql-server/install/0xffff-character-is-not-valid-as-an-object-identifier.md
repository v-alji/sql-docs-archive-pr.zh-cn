---
title: 0xFFFF 字符对于对象标识符无效 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586248"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a><span data-ttu-id="e1334-102">0xFFFF 字符不能用作对象标识符</span><span class="sxs-lookup"><span data-stu-id="e1334-102">0xFFFF character is not valid as an object identifier</span></span>
  <span data-ttu-id="e1334-103">升级顾问在对象标识符中检测到 0xFFFF 字符。</span><span class="sxs-lookup"><span data-stu-id="e1334-103">Upgrade Advisor has detected the 0xFFFF character in an object identifier.</span></span> <span data-ttu-id="e1334-104">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本中，当数据库兼容模式设置为 90 或更高时，不能引用或重命名标识符中包含该字符的对象（如数据库、表和列）。</span><span class="sxs-lookup"><span data-stu-id="e1334-104">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, objects such as databases, tables, and columns that contain this character in their identifiers cannot be referenced or renamed when the database compatibility mode is set to 90 or later.</span></span> <span data-ttu-id="e1334-105">升级到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 时，用户数据库将保持其兼容模式。</span><span class="sxs-lookup"><span data-stu-id="e1334-105">When you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], user databases maintain their compatibility mode.</span></span> <span data-ttu-id="e1334-106">在将数据库兼容模式更改为 90 或更高之前，请重命名包含 0xFFFF 字符的对象。</span><span class="sxs-lookup"><span data-stu-id="e1334-106">Before you change the database compatibility mode to 90 or later, rename the object that contains the 0xFFFF character.</span></span>  
  
 <span data-ttu-id="e1334-107">有关标识符的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“标识符”。</span><span class="sxs-lookup"><span data-stu-id="e1334-107">For more information about identifiers, see "Identifiers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="e1334-108">有关数据库兼容模式的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“sp_dbcmptlevel”。</span><span class="sxs-lookup"><span data-stu-id="e1334-108">For more information about database compatibility modes, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="e1334-109">组件</span><span class="sxs-lookup"><span data-stu-id="e1334-109">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1334-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1334-110">See Also</span></span>  
 <span data-ttu-id="e1334-111">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e1334-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="e1334-112">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="e1334-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
