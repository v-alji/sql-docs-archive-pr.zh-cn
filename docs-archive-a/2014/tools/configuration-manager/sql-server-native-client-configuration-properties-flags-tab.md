---
title: SQL Server Native Client 配置属性（“标志”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3ca7b87963fc3848bbb933a5c21f9d608d37d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590451"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a><span data-ttu-id="127a8-102">SQL Server Native Client 配置属性（“标志”选项卡）</span><span class="sxs-lookup"><span data-stu-id="127a8-102">SQL Server Native Client Configuration Properties (Flags Tab)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="127a8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 库文件中提供的协议与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务器进行通信。</span><span class="sxs-lookup"><span data-stu-id="127a8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this machine, communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers using the protocols provided in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client library file.</span></span> <span data-ttu-id="127a8-104">使用本页可将客户端计算机配置为使用安全套接字层 (SSL) 请求加密的连接。</span><span class="sxs-lookup"><span data-stu-id="127a8-104">This page provides configures the client computer to request an encrypted connection using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="127a8-105">如果无法建立加密的连接，则连接将失败。</span><span class="sxs-lookup"><span data-stu-id="127a8-105">If an encrypted connection cannot be established, the connection will fail.</span></span>  
  
 <span data-ttu-id="127a8-106">登录过程始终是加密的。</span><span class="sxs-lookup"><span data-stu-id="127a8-106">The login process is always encrypted.</span></span> <span data-ttu-id="127a8-107">以下选项仅适用于加密数据。</span><span class="sxs-lookup"><span data-stu-id="127a8-107">The options below apply only to encrypting data.</span></span> <span data-ttu-id="127a8-108">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何加密通信的详细信息，以及如何将客户端配置为信任服务器证书的根颁发机构的说明，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]联机丛书中的“加密与 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的连接”和“如何启用与[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的加密连接（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器）”。</span><span class="sxs-lookup"><span data-stu-id="127a8-108">For more information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypts communication and for instructions on how to configure the client to trust the root authority of the server certificate, see "Encrypting Connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" and "How to: Enable Encrypted Connections to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="127a8-109">选项</span><span class="sxs-lookup"><span data-stu-id="127a8-109">Options</span></span>  
 <span data-ttu-id="127a8-110">**强制协议加密**</span><span class="sxs-lookup"><span data-stu-id="127a8-110">**Force protocol encryption**</span></span>  
 <span data-ttu-id="127a8-111">使用 SSL 请求连接。</span><span class="sxs-lookup"><span data-stu-id="127a8-111">Request a connection using SSL.</span></span>  
  
 <span data-ttu-id="127a8-112">**信任服务器证书**</span><span class="sxs-lookup"><span data-stu-id="127a8-112">**Trust Server Certificate**</span></span>  
 <span data-ttu-id="127a8-113">当设置为  “否”时，客户端进程将尝试验证服务器证书。</span><span class="sxs-lookup"><span data-stu-id="127a8-113">When set to **No**, the client process attempts to validate the server certificate.</span></span> <span data-ttu-id="127a8-114">客户端和服务器均必须拥有公共证书颁发机构颁发的证书。</span><span class="sxs-lookup"><span data-stu-id="127a8-114">The client and server must have each have a certificate issues from a public certification authority.</span></span> <span data-ttu-id="127a8-115">如果客户端计算机上没有证书，或如果验证证书失败，则连接将终止。</span><span class="sxs-lookup"><span data-stu-id="127a8-115">If the certificate is not present on the client computer, or if the validation of the certificate fails, the connection is terminated.</span></span>  
  
 <span data-ttu-id="127a8-116">当设置为  “是”时，客户端不会验证服务器证书，而是使用自签名证书。</span><span class="sxs-lookup"><span data-stu-id="127a8-116">When set to **Yes**, the client does not validate the server certificate, thereby enabling the use of a self-signed certificate.</span></span>  
  
 <span data-ttu-id="127a8-117">仅在“强制协议加密”  设置为“是”  时，才可使用“信任服务器证书”  。</span><span class="sxs-lookup"><span data-stu-id="127a8-117">**Trust Server Certificate** is only available if **Force protocol encryption** is set to **Yes**.</span></span>  
  
  
