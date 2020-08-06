---
title: SQL Server 代理属性（“连接”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec9ae575f1ced510d95256d6827435e5b6ad89d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590007"
---
# <a name="sql-server-agent-properties-connection-page"></a><span data-ttu-id="685df-102">SQL Server 代理属性（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="685df-102">SQL Server Agent Properties (Connection Page)</span></span>
  <span data-ttu-id="685df-103">使用此页可以查看和修改代理服务与之间的连接设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="685df-103">Use this page to view and modify the settings for the connection from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="685df-104">选项</span><span class="sxs-lookup"><span data-stu-id="685df-104">Options</span></span>  
 <span data-ttu-id="685df-105">**本地主机服务器别名**</span><span class="sxs-lookup"><span data-stu-id="685df-105">**Alias local host server**</span></span>  
 <span data-ttu-id="685df-106">指定用来连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地实例的别名。</span><span class="sxs-lookup"><span data-stu-id="685df-106">Specifies the alias to use to connect to the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="685df-107">如果无法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的默认连接选项，请为相应的实例定义一个别名，并在此处指定该别名。</span><span class="sxs-lookup"><span data-stu-id="685df-107">If you cannot use the default connection options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, define an alias for the instance and specify the alias here.</span></span>  
  
 <span data-ttu-id="685df-108">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="685df-108">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="685df-109">将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证设置为连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时使用的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="685df-109">Sets [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="685df-110">代理按运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的帐户的身份进行连接。</span><span class="sxs-lookup"><span data-stu-id="685df-110">Agent connects as the account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs as.</span></span>  
  
 <span data-ttu-id="685df-111">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="685df-111">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="685df-112">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证设置为连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时使用的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="685df-112">Sets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="685df-113">提供身份验证是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="685df-113">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="685df-114">为了增强安全性，请使用 Windows 身份验证（如果可能的话）。</span><span class="sxs-lookup"><span data-stu-id="685df-114">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="685df-115">**登录**</span><span class="sxs-lookup"><span data-stu-id="685df-115">**Login**</span></span>  
 <span data-ttu-id="685df-116">指定用于连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的登录名。</span><span class="sxs-lookup"><span data-stu-id="685df-116">Specifies the login name to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="685df-117">**密码**</span><span class="sxs-lookup"><span data-stu-id="685df-117">**Password**</span></span>  
 <span data-ttu-id="685df-118">指定用于连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的密码。</span><span class="sxs-lookup"><span data-stu-id="685df-118">Specifies the password to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
