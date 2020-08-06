---
title: 连接到服务器（“连接属性”页）Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoas.connectionproperties.f1
ms.assetid: 26cf53e3-3bcb-4697-8a88-53e93bc68b56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 04706671ea8b0a50f2bf72cd7b73db88dce34d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682379"
---
# <a name="connect-to-server-connection-properties-page-analysis-services"></a><span data-ttu-id="0ba65-102">连接到服务器（“连接属性”页）(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="0ba65-102">Connect to Server (Connection Properties Page) Analysis Services</span></span>
  <span data-ttu-id="0ba65-103">当连接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 或在“已注册的服务器”\*\*\*\* 中注册 [!INCLUDE[ssAS](../includes/ssas-md.md)] 时，使用此选项卡可以查看或指定选项。</span><span class="sxs-lookup"><span data-stu-id="0ba65-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] or registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="0ba65-104">进行连接时，此对话框中仅显示“连接”\*\*\*\* 和“选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ba65-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="0ba65-105">注册 [!INCLUDE[ssAS](../includes/ssas-md.md)] 时，此对话框中仅显示“测试”\*\*\*\* 和“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ba65-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssAS](../includes/ssas-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ba65-106">选项</span><span class="sxs-lookup"><span data-stu-id="0ba65-106">Options</span></span>  
 <span data-ttu-id="0ba65-107">**连接到数据库**</span><span class="sxs-lookup"><span data-stu-id="0ba65-107">**Connect to database**</span></span>  
 <span data-ttu-id="0ba65-108">从列表中选择要连接到的数据库。</span><span class="sxs-lookup"><span data-stu-id="0ba65-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="0ba65-109">如果选择 **\<default>** ，则将连接到服务器的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="0ba65-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="0ba65-110">如果选择 **\<Browse server>** ，则可以浏览服务器以查找要连接到的数据库。</span><span class="sxs-lookup"><span data-stu-id="0ba65-110">If you select **\<Browse server>**, you can browse the server for the database you would like to connect to.</span></span>  
  
 <span data-ttu-id="0ba65-111">**连接超时**</span><span class="sxs-lookup"><span data-stu-id="0ba65-111">**Connection timeout**</span></span>  
 <span data-ttu-id="0ba65-112">输入在超时之前等待建立连接的秒数。默认值为15秒。</span><span class="sxs-lookup"><span data-stu-id="0ba65-112">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="0ba65-113">**执行超时**</span><span class="sxs-lookup"><span data-stu-id="0ba65-113">**Execution timeout**</span></span>  
 <span data-ttu-id="0ba65-114">输入在服务器上完成任务执行之前等待的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="0ba65-114">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="0ba65-115">默认值为零秒，指示无超时。</span><span class="sxs-lookup"><span data-stu-id="0ba65-115">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="0ba65-116">**加密连接**</span><span class="sxs-lookup"><span data-stu-id="0ba65-116">**Encrypt connection**</span></span>  
 <span data-ttu-id="0ba65-117">强制对连接进行加密。</span><span class="sxs-lookup"><span data-stu-id="0ba65-117">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="0ba65-118">**全部重置**</span><span class="sxs-lookup"><span data-stu-id="0ba65-118">**Reset All**</span></span>  
 <span data-ttu-id="0ba65-119">将所有手动输入的连接属性值替换为默认值。</span><span class="sxs-lookup"><span data-stu-id="0ba65-119">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="0ba65-120">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="0ba65-120">**Connect**</span></span>  
 <span data-ttu-id="0ba65-121">使用列出的值尝试连接。</span><span class="sxs-lookup"><span data-stu-id="0ba65-121">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="0ba65-122">**选项**</span><span class="sxs-lookup"><span data-stu-id="0ba65-122">**Options**</span></span>  
 <span data-ttu-id="0ba65-123">单击此项可更改对话框并隐藏其他服务器连接选项，例如记住密码。</span><span class="sxs-lookup"><span data-stu-id="0ba65-123">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="0ba65-124">**Test**</span><span class="sxs-lookup"><span data-stu-id="0ba65-124">**Test**</span></span>  
 <span data-ttu-id="0ba65-125">在“已注册的服务器”\*\*\*\* 中注册 [!INCLUDE[ssAS](../includes/ssas-md.md)] 时，单击此选项可以测试连接。</span><span class="sxs-lookup"><span data-stu-id="0ba65-125">When registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="0ba65-126">**保存**</span><span class="sxs-lookup"><span data-stu-id="0ba65-126">**Save**</span></span>  
 <span data-ttu-id="0ba65-127">保存“已注册的服务器”\*\*\*\* 中的设置。</span><span class="sxs-lookup"><span data-stu-id="0ba65-127">Saves the settings in **Registered Servers**.</span></span>  
  
  
