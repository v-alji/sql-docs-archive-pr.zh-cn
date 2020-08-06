---
title: EKM provider enabled 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b44e7f5e0801bb370a98abe79a6ea449c6f7409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693460"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a><span data-ttu-id="afeb0-102">EKM provider enabled 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="afeb0-102">EKM provider enabled Server Configuration Option</span></span>
  <span data-ttu-id="afeb0-103">`EKM provider enabled` 选项控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的可扩展密钥管理设备支持。</span><span class="sxs-lookup"><span data-stu-id="afeb0-103">The `EKM provider enabled` option controls Extensible Key Management device support in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afeb0-104">默认情况下，此选项处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="afeb0-104">By default this option is off.</span></span>  
  
 <span data-ttu-id="afeb0-105">若要启用或禁用该功能，请执行下列 `sp_configure` 命令之一：</span><span class="sxs-lookup"><span data-stu-id="afeb0-105">To enable or disable the feature, issue one of the following `sp_configure` commands:</span></span>  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  <span data-ttu-id="afeb0-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本均未启用此选项。</span><span class="sxs-lookup"><span data-stu-id="afeb0-106">This option is not enabled in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afeb0-107">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="afeb0-107">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afeb0-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afeb0-108">See Also</span></span>  
 <span data-ttu-id="afeb0-109">[可扩展密钥管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span><span class="sxs-lookup"><span data-stu-id="afeb0-109">[Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span></span>  
 <span data-ttu-id="afeb0-110">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="afeb0-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="afeb0-111">[监视资源使用情况（系统监视器）](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="afeb0-111">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="afeb0-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afeb0-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="afeb0-113">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="afeb0-113">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
