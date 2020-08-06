---
title: 将防火墙配置为允许 FILESTREAM 访问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8b787403fefdd336dd82bf7ccb93cdf21fe5a90d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589723"
---
# <a name="configure-a-firewall-for-filestream-access"></a><span data-ttu-id="3085e-102">将防火墙配置为进行 FILESTREAM 访问</span><span class="sxs-lookup"><span data-stu-id="3085e-102">Configure a Firewall for FILESTREAM Access</span></span>
  <span data-ttu-id="3085e-103">若要在防火墙保护的环境中使用 FILESTREAM，客户端和服务器都必须能够将 DNS 名称解析为包含 FILESTREAM 文件的服务器。</span><span class="sxs-lookup"><span data-stu-id="3085e-103">To use FILESTREAM in a firewall-protected environment, both the client and server must be able to resolve DNS names to the server that contains the FILESTREAM files.</span></span> <span data-ttu-id="3085e-104">FILESTREAM 要求 Windows 文件共享端口 139 和 445 处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="3085e-104">FILESTREAM requires the Windows file-sharing ports 139 and 445 to be open.</span></span>  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a><span data-ttu-id="3085e-105">在运行 Windows 7 的计算机上打开 Windows 文件共享端口</span><span class="sxs-lookup"><span data-stu-id="3085e-105">To open the Windows file-sharing ports on a computer that is running Windows 7</span></span>  
  
1.  <span data-ttu-id="3085e-106">在“控制面板”中，打开 **“Windows 防火墙”** 。</span><span class="sxs-lookup"><span data-stu-id="3085e-106">In Control Panel, open **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="3085e-107">在左窗格中，单击 **“高级设置”** 。</span><span class="sxs-lookup"><span data-stu-id="3085e-107">In the left pane, click **Advanced settings**.</span></span> <span data-ttu-id="3085e-108">如果系统提示需要管理员密码或确认，请键入密码或进行确认。</span><span class="sxs-lookup"><span data-stu-id="3085e-108">If you're prompted for an administrator password or confirmation, type the password or provide confirmation.</span></span>  
  
3.  <span data-ttu-id="3085e-109">在 **“高级安全 Windows 防火墙”** 对话框的左窗格中，单击 **“入站规则”** ，然后在右窗格中单击 **“新建规则”** 。</span><span class="sxs-lookup"><span data-stu-id="3085e-109">In the **Windows Firewall with Advanced Security** dialog box, in the left pane, click **Inbound Rules**, and then, in the right pane, click **New Rule**.</span></span>  
  
4.  <span data-ttu-id="3085e-110">按照“新建入站规则”向导中的说明添加 TCP 端口 139。</span><span class="sxs-lookup"><span data-stu-id="3085e-110">Follow the instructions in the New Inbound Rule wizard to add TCP port 139.</span></span>  
  
5.  <span data-ttu-id="3085e-111">重复上述步骤添加 TCP 端口 445。</span><span class="sxs-lookup"><span data-stu-id="3085e-111">Repeat the previous step to add TCP port 445.</span></span>  
  
6.  <span data-ttu-id="3085e-112">关闭 **“高级安全 Windows 防火墙”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3085e-112">Close the **Windows Firewall with Advanced Security** dialog box.</span></span>  
  
  
