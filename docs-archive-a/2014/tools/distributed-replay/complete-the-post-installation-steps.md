---
title: 完成安装后步骤 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1e9aae3dccaa409bcebc473213286f3edf19e7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587655"
---
# <a name="complete-the-post-installation-steps"></a><span data-ttu-id="77b54-102">完成安装后步骤</span><span class="sxs-lookup"><span data-stu-id="77b54-102">Complete the Post-Installation Steps</span></span>
  <span data-ttu-id="77b54-103">安装 Distributed Replay 后，您必须修改 Distributed Replay 控制器和客户端服务帐户。</span><span class="sxs-lookup"><span data-stu-id="77b54-103">After you install Distributed Replay you must modify the Distributed Replay controller and client services accounts.</span></span>  
  
### <a name="to-complete-the-post-installation-steps"></a><span data-ttu-id="77b54-104">完成安装后步骤</span><span class="sxs-lookup"><span data-stu-id="77b54-104">To complete the post-installation steps</span></span>  
  
1.  <span data-ttu-id="77b54-105">**创建防火墙规则**：在控制器和客户端计算机上，必须允许相应服务的入站流量通过防火墙。</span><span class="sxs-lookup"><span data-stu-id="77b54-105">**Create firewall rules**: On the controller and client computers, you must allow inbound traffic through the firewall for the corresponding service.</span></span> <span data-ttu-id="77b54-106">指定位于安装文件夹中的服务可执行文件的防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="77b54-106">Specify the firewall rules for the service executables, located in the installation folders.</span></span>  
  
    1.  <span data-ttu-id="77b54-107">对于控制器服务，请为位于安装文件夹中的 **DReplayController.exe**创建规则。</span><span class="sxs-lookup"><span data-stu-id="77b54-107">For the controller service, create a rule for **DReplayController.exe**, located in the installation folder.</span></span> <span data-ttu-id="77b54-108">例如，下面的命令会启用该规则，其中 `%InstallPath%` 是服务的安装文件夹：</span><span class="sxs-lookup"><span data-stu-id="77b54-108">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  <span data-ttu-id="77b54-109">对于客户端服务，请在每台客户端计算机上为位于安装文件夹中的 **DReplayClient.exe**创建规则。</span><span class="sxs-lookup"><span data-stu-id="77b54-109">For the client service, on each client computer, create a rule for **DReplayClient.exe**, located in the installation folder.</span></span> <span data-ttu-id="77b54-110">例如，下面的命令会启用该规则，其中 `%InstallPath%` 是服务的安装文件夹：</span><span class="sxs-lookup"><span data-stu-id="77b54-110">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  <span data-ttu-id="77b54-111">**在目标服务器上授予每个客户端权限**：在客户端计算机上安装完客户端服务后，必须手动将客户端服务帐户添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标实例上的 sysadmin 角色中。</span><span class="sxs-lookup"><span data-stu-id="77b54-111">**Grant each client permissions on the target server**: After you have completed installing the client service on the client computers, you must manually add the client service accounts to the sysadmin role on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="77b54-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="77b54-112">.NET Framework Security</span></span>  
 <span data-ttu-id="77b54-113">您必须具有管理权限才能安装任何 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="77b54-113">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="77b54-114">只有拥有 sysadmin 权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名才可以将客户端服务帐户添加到测试服务器的 sysadmin 服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="77b54-114">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="77b54-115">有关分布式重播的安全注意事项的详细信息，请参阅 [Distributed Replay Security](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="77b54-115">For more information about Distributed Replay security considerations, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
  
