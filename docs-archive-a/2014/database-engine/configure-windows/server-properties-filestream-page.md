---
title: SQL Server 属性（“文件流”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.filestream.f1
helpviewer_keywords:
- FILESTREAM [SQL Server], properties page
ms.assetid: 8a8d38d3-e97a-4b09-a40b-659b2e3a5c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ca13877a195a0f829c3fd0a628c446626819e14a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692512"
---
# <a name="sql-server-properties-filestream-page"></a><span data-ttu-id="098d5-102">SQL Server 属性（FILESTREAM 页）</span><span class="sxs-lookup"><span data-stu-id="098d5-102">SQL Server Properties (FILESTREAM Page)</span></span>
  <span data-ttu-id="098d5-103">使用此页可针对此 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]安装启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="098d5-103">Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="098d5-104">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="098d5-104">UI element list</span></span>  
 <span data-ttu-id="098d5-105">**针对 Transact-SQL 访问启用 FILESTREAM**</span><span class="sxs-lookup"><span data-stu-id="098d5-105">**Enable FILESTREAM for Transact-SQL access**</span></span>  
 <span data-ttu-id="098d5-106">选中此项可针对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="098d5-106">Select to enable FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="098d5-107">必须选中此控制选项，才能使用其他控制选项。</span><span class="sxs-lookup"><span data-stu-id="098d5-107">This control must be checked before the other control options will be available.</span></span>  
  
 <span data-ttu-id="098d5-108">**针对文件 I/O 流访问启用 FILESTREAM**</span><span class="sxs-lookup"><span data-stu-id="098d5-108">**Enable FILESTREAM for file I/O streaming access**</span></span>  
 <span data-ttu-id="098d5-109">选中此项可针对 FILESTREAM 启用 Win32 流访问。</span><span class="sxs-lookup"><span data-stu-id="098d5-109">Select to enable Win32 streaming access for FILESTREAM.</span></span>  
  
 <span data-ttu-id="098d5-110">**Windows 共享名**</span><span class="sxs-lookup"><span data-stu-id="098d5-110">**Windows share name**</span></span>  
 <span data-ttu-id="098d5-111">使用此控制选项可输入将用来存储 FILESTREAM 数据的 Windows 共享的名称。</span><span class="sxs-lookup"><span data-stu-id="098d5-111">Use this control to enter the name of the Windows share in which the FILESTREAM data will be stored.</span></span>  
  
 <span data-ttu-id="098d5-112">**允许远程客户端针对 FILESTREAM 数据启用流访问**</span><span class="sxs-lookup"><span data-stu-id="098d5-112">**Allow remote clients to have streaming access to FILESTREAM data**</span></span>  
 <span data-ttu-id="098d5-113">选中此控制选项可允许远程客户端访问此服务器上的此 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="098d5-113">Select this control to allow remote clients to access this FILESTREAM data on this server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098d5-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="098d5-114">See Also</span></span>  
 <span data-ttu-id="098d5-115">[FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="098d5-115">[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md) </span></span>  
 [<span data-ttu-id="098d5-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="098d5-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
