---
title: 分发服务器密码 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 63e635903793bfa63d12b8a4cd2985178f9c4837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578114"
---
# <a name="distributor-password"></a><span data-ttu-id="ffcac-102">分发服务器密码</span><span class="sxs-lookup"><span data-stu-id="ffcac-102">Distributor Password</span></span>
  <span data-ttu-id="ffcac-103">在此向导的 **“发布服务器”** 页上，如果允许一个或多个发布服务器将此服务器作为远程分发服务器，则必须为复制使用 **distributor_admin** 登录名在发布服务器和远程分发服务器之间建立的连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="ffcac-103">If, on the **Publishers** page of this wizard, you enabled one or more Publishers to use this server as a remote Distributor, you must specify a password for the connection replication makes between the Publisher and the remote Distributor using the **distributor_admin** login.</span></span> <span data-ttu-id="ffcac-104">在新建发布向导或配置分发向导的 **“管理密码”** 页上，必须为每个使用此远程分发服务器的发布服务器输入相同的密码。</span><span class="sxs-lookup"><span data-stu-id="ffcac-104">The same password must be entered for each Publisher that uses this remote Distributor on the **Administrative Password** page of the New Publication Wizard or the Configure Distribution Wizard.</span></span> <span data-ttu-id="ffcac-105">有关分发服务器的安全性的详细信息，请参阅[保护分发服务器](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="ffcac-105">For more information on security for Distributors, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ffcac-106">选项</span><span class="sxs-lookup"><span data-stu-id="ffcac-106">Options</span></span>  
 <span data-ttu-id="ffcac-107">**密码**</span><span class="sxs-lookup"><span data-stu-id="ffcac-107">**Password**</span></span>  
 <span data-ttu-id="ffcac-108">为发布服务器和远程分发服务器之间的连接输入强密码。</span><span class="sxs-lookup"><span data-stu-id="ffcac-108">Enter a strong password for the connection between the Publisher and the remote Distributor.</span></span>  
  
 <span data-ttu-id="ffcac-109">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="ffcac-109">**Confirm Password**</span></span>  
 <span data-ttu-id="ffcac-110">重新输入密码以确认密码输入正确。</span><span class="sxs-lookup"><span data-stu-id="ffcac-110">Re-enter the password to confirm it was entered correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcac-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffcac-111">See Also</span></span>  
 <span data-ttu-id="ffcac-112">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="ffcac-112">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="ffcac-113">配置发布和分发</span><span class="sxs-lookup"><span data-stu-id="ffcac-113">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
  
