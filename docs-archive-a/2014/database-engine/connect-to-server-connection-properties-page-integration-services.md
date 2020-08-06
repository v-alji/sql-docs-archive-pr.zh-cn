---
title: 连接到服务器 (连接属性页) Integration Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodts.connectionproperties.f1
- sql12.ssiseditserverregistration.connectionproperties.f1
ms.assetid: c2513dab-8415-4e0c-9475-6d4ab97fea7c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 05f3d370a3f3a299bb90df53538b3fa3e90e28c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693071"
---
# <a name="connect-to-server-connection-properties-page-integration-services"></a><span data-ttu-id="f4cf5-102">连接到服务器（“连接属性”页）(Integration Services)</span><span class="sxs-lookup"><span data-stu-id="f4cf5-102">Connect to Server (Connection Properties Page) Integration Services</span></span>
  <span data-ttu-id="f4cf5-103">当连接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 或在“已注册的服务器”\*\*\*\* 中注册 [!INCLUDE[ssIS](../includes/ssis-md.md)] 时，使用此选项卡可以查看或指定选项。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] or registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="f4cf5-104">进行连接时，此对话框中仅显示“连接”\*\*\*\* 和“选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="f4cf5-105">注册 [!INCLUDE[ssIS](../includes/ssis-md.md)] 时，此对话框中仅显示“测试”\*\*\*\* 和“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4cf5-106">选项</span><span class="sxs-lookup"><span data-stu-id="f4cf5-106">Options</span></span>  
 <span data-ttu-id="f4cf5-107">**端口号**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-107">**Port number**</span></span>  
 <span data-ttu-id="f4cf5-108">输入 [!INCLUDE[ssIS](../includes/ssis-md.md)]使用的端口号。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-108">Enter the port number used by [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="f4cf5-109">**连接超时**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-109">**Connection time-out**</span></span>  
 <span data-ttu-id="f4cf5-110">输入在超时之前等待建立连接的秒数。默认值为15秒。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-110">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="f4cf5-111">**执行超时值**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-111">**Execution time-out**</span></span>  
 <span data-ttu-id="f4cf5-112">输入在服务器上完成任务执行之前等待的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-112">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="f4cf5-113">默认值为零秒，指示无超时。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-113">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="f4cf5-114">**全部重置**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-114">**Reset All**</span></span>  
 <span data-ttu-id="f4cf5-115">将所有手动输入的连接属性值替换为默认值。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-115">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="f4cf5-116">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-116">**Connect**</span></span>  
 <span data-ttu-id="f4cf5-117">使用列出的值尝试连接。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-117">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="f4cf5-118">**选项**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-118">**Options**</span></span>  
 <span data-ttu-id="f4cf5-119">单击此项可更改对话框并隐藏其他服务器连接选项，例如记住密码。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-119">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="f4cf5-120">**Test**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-120">**Test**</span></span>  
 <span data-ttu-id="f4cf5-121">在“已注册的服务器”\*\*\*\* 中注册 [!INCLUDE[ssIS](../includes/ssis-md.md)] 时，单击此选项可以测试连接。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-121">When registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="f4cf5-122">**保存**</span><span class="sxs-lookup"><span data-stu-id="f4cf5-122">**Save**</span></span>  
 <span data-ttu-id="f4cf5-123">保存“已注册的服务器”\*\*\*\* 中的设置。</span><span class="sxs-lookup"><span data-stu-id="f4cf5-123">Saves the settings in **Registered Servers**.</span></span>  
  
  
