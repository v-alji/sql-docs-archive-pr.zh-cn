---
title: 连接到服务器（“登录”页）(Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 285518f4a1f3d9180d2c3c07a41bf75a00ea3593
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693067"
---
# <a name="connect-to-server-login-page-integration-services"></a><span data-ttu-id="2a06a-102">连接到服务器（“登录”页）(Integration Services)</span><span class="sxs-lookup"><span data-stu-id="2a06a-102">Connect to Server (Login Page) Integration Services</span></span>
  <span data-ttu-id="2a06a-103">在连接到时，使用此选项卡可以查看或指定以下选项 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2a06a-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a06a-104">选项</span><span class="sxs-lookup"><span data-stu-id="2a06a-104">Options</span></span>  
 <span data-ttu-id="2a06a-105">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="2a06a-105">**Server type**</span></span>  
 <span data-ttu-id="2a06a-106">从对象资源管理器进行服务器注册时，请选择要连接到何种类型的服务器： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="2a06a-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="2a06a-107">对话框的其余部分只显示适用于所选服务器类型的选项。</span><span class="sxs-lookup"><span data-stu-id="2a06a-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="2a06a-108">从“已注册的服务器”注册某服务器时，“服务器类型”  框是只读的，并且与“已注册的服务器”组件中显示的服务器类型匹配。</span><span class="sxs-lookup"><span data-stu-id="2a06a-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="2a06a-109">若要注册其他类型的服务器，请在开始注册新服务器之前，从“已注册的服务器”工具栏中选择[!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="2a06a-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="2a06a-110">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="2a06a-110">**Server name**</span></span>  
 <span data-ttu-id="2a06a-111">选择要连接到的服务器。</span><span class="sxs-lookup"><span data-stu-id="2a06a-111">Select the server to connect to.</span></span> <span data-ttu-id="2a06a-112">默认情况下，显示上次连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="2a06a-112">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a06a-113">不要使用 *\<servername>* \\ *\<instancename>* ，因为不 [!INCLUDE[ssIS](../includes/ssis-md.md)] 支持计算机上的多个实例。</span><span class="sxs-lookup"><span data-stu-id="2a06a-113">Do not use *\<servername>*\\*\<instancename>*, because [!INCLUDE[ssIS](../includes/ssis-md.md)] does not support multiple instances on a computer.</span></span>  
  
 <span data-ttu-id="2a06a-114">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="2a06a-114">**Authentication**</span></span>  
 <span data-ttu-id="2a06a-115">只有 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 身份验证可用于 [!INCLUDE[ssIS](../includes/ssis-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a06a-115">Only [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span> <span data-ttu-id="2a06a-116">Windows 身份验证模式允许用户通过 Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="2a06a-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="2a06a-117">**用户名**</span><span class="sxs-lookup"><span data-stu-id="2a06a-117">**User name**</span></span>  
 <span data-ttu-id="2a06a-118">由于只有 Windows 身份验证可用于 [!INCLUDE[ssIS](../includes/ssis-md.md)]，因此此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="2a06a-118">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="2a06a-119">**密码**</span><span class="sxs-lookup"><span data-stu-id="2a06a-119">**Password**</span></span>  
 <span data-ttu-id="2a06a-120">由于只有 Windows 身份验证可用于 [!INCLUDE[ssIS](../includes/ssis-md.md)]，因此此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="2a06a-120">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="2a06a-121">**记住密码**</span><span class="sxs-lookup"><span data-stu-id="2a06a-121">**Remember password**</span></span>  
 <span data-ttu-id="2a06a-122">由于只有 Windows 身份验证可用于 [!INCLUDE[ssIS](../includes/ssis-md.md)]，因此此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="2a06a-122">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="2a06a-123">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="2a06a-123">**Connect**</span></span>  
 <span data-ttu-id="2a06a-124">连接到在上面选择的服务器。</span><span class="sxs-lookup"><span data-stu-id="2a06a-124">Connect to the server selected above.</span></span>  
  
 <span data-ttu-id="2a06a-125">**选项**</span><span class="sxs-lookup"><span data-stu-id="2a06a-125">**Options**</span></span>  
 <span data-ttu-id="2a06a-126">单击此项可更改对话框并隐藏其他服务器连接选项，例如记住密码。</span><span class="sxs-lookup"><span data-stu-id="2a06a-126">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
