---
title: 连接到服务器 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3530f38534e09ef19e77293880129274dfc211b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682381"
---
# <a name="connect-to-server-analysis-services"></a><span data-ttu-id="b5947-102">连接到服务器 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b5947-102">Connect to Server (Analysis Services)</span></span>
  <span data-ttu-id="b5947-103">连接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 时，可以使用此对话框查看或指定选项。</span><span class="sxs-lookup"><span data-stu-id="b5947-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="b5947-104">选项</span><span class="sxs-lookup"><span data-stu-id="b5947-104">Options</span></span>  
 <span data-ttu-id="b5947-105">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="b5947-105">**Server type**</span></span>  
 <span data-ttu-id="b5947-106">从对象资源管理器进行服务器注册时，请选择要连接到何种类型的服务器： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="b5947-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="b5947-107">对话框的其余部分只显示适用于所选服务器类型的选项。</span><span class="sxs-lookup"><span data-stu-id="b5947-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="b5947-108">从“已注册的服务器”注册某服务器时，“服务器类型”  框是只读的，并且与“已注册的服务器”组件中显示的服务器类型匹配。</span><span class="sxs-lookup"><span data-stu-id="b5947-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="b5947-109">若要注册其他类型的服务器，请在开始注册新服务器之前，从“已注册的服务器”工具栏中选择[!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="b5947-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="b5947-110">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="b5947-110">**Server name**</span></span>  
 <span data-ttu-id="b5947-111">选择要连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b5947-111">Select the server instance to connect to.</span></span> <span data-ttu-id="b5947-112">默认情况下，显示上次连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b5947-112">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="b5947-113">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="b5947-113">**Authentication**</span></span>  
 <span data-ttu-id="b5947-114">在连接到 Analysis Services 的实例时，支持下列身份验证模式： [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b5947-114">The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="b5947-115">**Windows 身份验证模式（Windows 身份验证）**</span><span class="sxs-lookup"><span data-stu-id="b5947-115">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="b5947-116">**Windows 身份验证**模式允许用户通过 windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="b5947-116">**Windows Authentication** mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="b5947-117">**用户名**</span><span class="sxs-lookup"><span data-stu-id="b5947-117">**User name**</span></span>  
 <span data-ttu-id="b5947-118">此选项在此版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="b5947-118">This option is not available in this release.</span></span> <span data-ttu-id="b5947-119">输入连接所使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="b5947-119">Enter the user name to connect with.</span></span> <span data-ttu-id="b5947-120">仅当已选择使用**Windows 身份验证**进行连接时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b5947-120">This option is only available if you have selected to connect using **Windows Authentication**.</span></span>  
  
 <span data-ttu-id="b5947-121">**密码**</span><span class="sxs-lookup"><span data-stu-id="b5947-121">**Password**</span></span>  
 <span data-ttu-id="b5947-122">此选项在此版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="b5947-122">This option is not available in this release.</span></span> <span data-ttu-id="b5947-123">输入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="b5947-123">Enter the password for the login.</span></span> <span data-ttu-id="b5947-124">只有在已选择使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b5947-124">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="b5947-125">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="b5947-125">**Connect**</span></span>  
 <span data-ttu-id="b5947-126">单击此项可连接到在上面选择的服务器。</span><span class="sxs-lookup"><span data-stu-id="b5947-126">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="b5947-127">**选项**</span><span class="sxs-lookup"><span data-stu-id="b5947-127">**Options**</span></span>  
 <span data-ttu-id="b5947-128">单击此项可显示其他服务器连接选项，如注册服务器和记住密码。</span><span class="sxs-lookup"><span data-stu-id="b5947-128">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
