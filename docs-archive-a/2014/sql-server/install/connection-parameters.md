---
title: 连接参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27eb69dfd2c41710a47861e0992486267f692a3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579977"
---
# <a name="connection-parameters"></a><span data-ttu-id="36b6e-102">连接参数</span><span class="sxs-lookup"><span data-stu-id="36b6e-102">Connection Parameters</span></span>
  <span data-ttu-id="36b6e-103">若要分析某些服务器类型（比如 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]），则必须选择具体的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="36b6e-103">To analyze certain server types, such as the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], you must select a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="36b6e-104">会自动选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="36b6e-104">The default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is automatically selected.</span></span> <span data-ttu-id="36b6e-105">您可以更改此选择，但一次只能选择一个实例供升级顾问分析。</span><span class="sxs-lookup"><span data-stu-id="36b6e-105">You can change this selection, but you can select only one instance at a time for analysis by Upgrade Advisor.</span></span> <span data-ttu-id="36b6e-106">如果包括了要求身份验证的服务器类型，则必须输入身份验证模式和凭据。</span><span class="sxs-lookup"><span data-stu-id="36b6e-106">If you have included a server type that requires authentication, you must enter the authentication mode and credentials.</span></span>  
  
## <a name="options"></a><span data-ttu-id="36b6e-107">选项</span><span class="sxs-lookup"><span data-stu-id="36b6e-107">Options</span></span>  
 <span data-ttu-id="36b6e-108">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="36b6e-108">**Server name**</span></span>  
 <span data-ttu-id="36b6e-109">使用您在“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件”窗格中输入的计算机名进行预填充。</span><span class="sxs-lookup"><span data-stu-id="36b6e-109">Pre-populated with the computer name that you entered in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components pane.</span></span>  
  
 <span data-ttu-id="36b6e-110">**实例名**</span><span class="sxs-lookup"><span data-stu-id="36b6e-110">**Instance name**</span></span>  
 <span data-ttu-id="36b6e-111">从计算机中可用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中进行选择。</span><span class="sxs-lookup"><span data-stu-id="36b6e-111">Select from the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are available on the computer.</span></span> <span data-ttu-id="36b6e-112">如果看不到实例列表，请使用 MSSQLSERVER 扫描默认实例。</span><span class="sxs-lookup"><span data-stu-id="36b6e-112">If you do not see a list of instances, use MSSQLSERVER to scan the default instance.</span></span> <span data-ttu-id="36b6e-113">这对于远程计算机来说尤其重要。</span><span class="sxs-lookup"><span data-stu-id="36b6e-113">This is especially relevant for remote computers.</span></span> <span data-ttu-id="36b6e-114">也可以使用单词“default”来扫描默认实例。</span><span class="sxs-lookup"><span data-stu-id="36b6e-114">You can also use the word "default" to scan the default instance.</span></span>  
  
 <span data-ttu-id="36b6e-115">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="36b6e-115">**Authentication**</span></span>  
 <span data-ttu-id="36b6e-116">从此计算机上可用的身份验证模式列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="36b6e-116">Select from the list of available authentication modes on this computer.</span></span> <span data-ttu-id="36b6e-117">默认情况下，身份验证模式为 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="36b6e-117">By default, the authentication mode is Windows Authentication.</span></span>  
  
 <span data-ttu-id="36b6e-118">**用户名**</span><span class="sxs-lookup"><span data-stu-id="36b6e-118">**User name**</span></span>  
 <span data-ttu-id="36b6e-119">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，请在框中输入用户名。</span><span class="sxs-lookup"><span data-stu-id="36b6e-119">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, enter a user name in the box.</span></span> <span data-ttu-id="36b6e-120">建议该用户名具有计算机上的管理凭据。</span><span class="sxs-lookup"><span data-stu-id="36b6e-120">We recommend that the user name have administrative credentials on the computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36b6e-121">如果选择 "Windows 身份验证"，则将在 "**用户名**" 文本框中填充当前登录用户的用户名。</span><span class="sxs-lookup"><span data-stu-id="36b6e-121">If you select Windows Authentication, the user name of the currently logged-on user is populated in the **User name** text box.</span></span>  
  
 <span data-ttu-id="36b6e-122">**密码**</span><span class="sxs-lookup"><span data-stu-id="36b6e-122">**Password**</span></span>  
 <span data-ttu-id="36b6e-123">输入指定用户的密码。</span><span class="sxs-lookup"><span data-stu-id="36b6e-123">Enter the password for the specified user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b6e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36b6e-124">See Also</span></span>  
 <span data-ttu-id="36b6e-125">[使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="36b6e-125">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="36b6e-126">升级顾问用户界面参考</span><span class="sxs-lookup"><span data-stu-id="36b6e-126">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
