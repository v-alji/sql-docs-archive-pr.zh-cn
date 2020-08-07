---
title: SQL Server 代理服务无法使用 SQL Server 身份验证 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588253"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a><span data-ttu-id="16755-102">SQL Server Agent 服务不能使用 SQL Server 身份验证</span><span class="sxs-lookup"><span data-stu-id="16755-102">SQL Server Agent Service cannot use SQL Server Authentication</span></span>
  <span data-ttu-id="16755-103">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理仅支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="16755-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent only supports Windows Authentication when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="16755-104">组件</span><span class="sxs-lookup"><span data-stu-id="16755-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="16755-105">代理</span><span class="sxs-lookup"><span data-stu-id="16755-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="16755-106">说明</span><span class="sxs-lookup"><span data-stu-id="16755-106">Description</span></span>  
 <span data-ttu-id="16755-107">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务只能通过使用 Windows 身份验证登录到数据库。</span><span class="sxs-lookup"><span data-stu-id="16755-107">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can only log on to the database using Windows Authentication.</span></span> <span data-ttu-id="16755-108">也就是说，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户必须为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户。</span><span class="sxs-lookup"><span data-stu-id="16755-108">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="16755-109">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“自动管理的安全性”和“实现 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理安全性”主题。</span><span class="sxs-lookup"><span data-stu-id="16755-109">For more information, see the topics "Security for Automatic Administration" and "Implementing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Security" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16755-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16755-110">See Also</span></span>  
 [<span data-ttu-id="16755-111">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="16755-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
