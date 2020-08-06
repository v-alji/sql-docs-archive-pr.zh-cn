---
title: 在目标服务器上设置加密选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd10d2e05e59015542f41cc123de993e6128f9f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590018"
---
# <a name="set-encryption-options-on-target-servers"></a><span data-ttu-id="02e9e-102">在目标服务器上设置加密选项</span><span class="sxs-lookup"><span data-stu-id="02e9e-102">Set Encryption Options on Target Servers</span></span>
  <span data-ttu-id="02e9e-103">如果您无法在主服务器和某些或所有目标服务器之间的安全套接字层 (SSL) 加密通信中使用证书，但希望对它们之间的通道进行加密，则请将目标服务器配置为使用所需的安全级别。</span><span class="sxs-lookup"><span data-stu-id="02e9e-103">If you cannot use a certificate for Secure Sockets Layer (SSL) encrypted communications between master servers and some or all of your target servers, but you want to encrypt the channel between them, configure the target server to use the level of security required.</span></span>  
  
 <span data-ttu-id="02e9e-104">若要为特定的主服务器/目标服务器通信通道配置所需的适当安全级别，请将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标服务器上的代理注册表子项\*\*\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ \*\* \<*instance_name*> \*\*\SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD) \*\*设置为以下值之一。</span><span class="sxs-lookup"><span data-stu-id="02e9e-104">To configure the appropriate level of security required for a specific master server/target server communication channel, set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** on the target server to one of the following values.</span></span> <span data-ttu-id="02e9e-105">的值 \<*instance_name*> 为**MSSQL。**_n_。</span><span class="sxs-lookup"><span data-stu-id="02e9e-105">The value of \<*instance_name*> is **MSSQL.**_n_.</span></span> <span data-ttu-id="02e9e-106">例如， **MSSQL.1** 或 **MSSQL.3**。</span><span class="sxs-lookup"><span data-stu-id="02e9e-106">For example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
|<span data-ttu-id="02e9e-107">值</span><span class="sxs-lookup"><span data-stu-id="02e9e-107">Value</span></span>|<span data-ttu-id="02e9e-108">说明</span><span class="sxs-lookup"><span data-stu-id="02e9e-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02e9e-109">**0**</span><span class="sxs-lookup"><span data-stu-id="02e9e-109">**0**</span></span>|<span data-ttu-id="02e9e-110">在该目标服务器和主服务器之间禁用加密。</span><span class="sxs-lookup"><span data-stu-id="02e9e-110">Disables encryption between this target server and the master server.</span></span> <span data-ttu-id="02e9e-111">请仅在目标服务器和主服务器之间的通道已使用其他方法进行了保护时才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="02e9e-111">Choose this option only when the channel between the target server and master server is secured by another means.</span></span>|  
|<span data-ttu-id="02e9e-112">**1**</span><span class="sxs-lookup"><span data-stu-id="02e9e-112">**1**</span></span>|<span data-ttu-id="02e9e-113">仅在该目标服务器和主服务器之间启用加密，但不需要证书验证。</span><span class="sxs-lookup"><span data-stu-id="02e9e-113">Enables encryption only between this target server and the master server, but no certificate validation is required.</span></span>|  
|<span data-ttu-id="02e9e-114">**2**</span><span class="sxs-lookup"><span data-stu-id="02e9e-114">**2**</span></span>|<span data-ttu-id="02e9e-115">在该目标服务器和主服务器之间启用完全 SSL 加密和证书验证。</span><span class="sxs-lookup"><span data-stu-id="02e9e-115">Enables full SSL encryption and certificate validation between this target server and the master server.</span></span> <span data-ttu-id="02e9e-116">此设置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="02e9e-116">This setting is the default.</span></span> <span data-ttu-id="02e9e-117">除非出于特定的原因要选择其他值，否则建议不要对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="02e9e-117">Unless you have specific reason to choose a different value, we recommend not changing it.</span></span>|  
  
 <span data-ttu-id="02e9e-118">如果指定了 **1** 或 **2** ，则必须同时在主服务器和目标服务器上启用 SSL。</span><span class="sxs-lookup"><span data-stu-id="02e9e-118">If **1** or **2** is specified, you must have SSL enabled on both the master and target servers.</span></span> <span data-ttu-id="02e9e-119">如果指定了 **2** ，则还必须在主服务器上安装相应的签名证书。</span><span class="sxs-lookup"><span data-stu-id="02e9e-119">If **2** is specified, you must also have a properly signed certificate present on the master server.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="02e9e-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02e9e-120">See Also</span></span>  
 [<span data-ttu-id="02e9e-121">启用数据库引擎的加密连接（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="02e9e-121">Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
