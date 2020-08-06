---
title: 运行 Data Quality Client 应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45372ce22fd1b18f0ec13f7a7fd76a369b78dfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694143"
---
# <a name="run-the-data-quality-client-application"></a><span data-ttu-id="29da3-102">运行数据质量客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="29da3-102">Run the Data Quality Client Application</span></span>
  <span data-ttu-id="29da3-103">您可以通过运行[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]并登录到[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]来使用 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (DQS)。</span><span class="sxs-lookup"><span data-stu-id="29da3-103">You can use [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by running [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and logging on to a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="29da3-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="29da3-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="29da3-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="29da3-105">Prerequisites</span></span>  
 <span data-ttu-id="29da3-106">您必须已通过运行 DQSInstaller.exe 文件完成了 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="29da3-106">You must have completed the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="29da3-107">有关详细信息，请参阅 [运行 DQSInstaller.exe 以便完成数据质量服务器安装](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="29da3-107">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="29da3-108">Security</span><span class="sxs-lookup"><span data-stu-id="29da3-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="29da3-109">权限</span><span class="sxs-lookup"><span data-stu-id="29da3-109">Permissions</span></span>  
 <span data-ttu-id="29da3-110">您必须具有对 DQS_MAIN 数据库授予的三种 DQS 角色（dqs_adminstrator、dqs_kb_editor 或 dqs_kb_operator）中的一种，才能登录到 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29da3-110">You must have one of the three DQS roles (dqs_adminstrator, dqs_kb_editor, or dqs_kb_operator) granted on the DQS_MAIN database to be able to log on to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a><span data-ttu-id="29da3-111">运行 Data Quality Client</span><span class="sxs-lookup"><span data-stu-id="29da3-111">Run Data Quality Client</span></span>  
 <span data-ttu-id="29da3-112">若要在装有[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]的计算机上运行它，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="29da3-112">To run [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] on the computer where you have installed it, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="29da3-113">单击 **“开始”**，指向 **“所有程序”**，依次单击 **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**、 **Data Quality Services**和 **“数据质量客户端”**。</span><span class="sxs-lookup"><span data-stu-id="29da3-113">Click **Start**, point to **All Programs**, click **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="29da3-114">在“连接到服务器”对话框中：</span><span class="sxs-lookup"><span data-stu-id="29da3-114">In the **Connect to Server** dialog box:</span></span>  
  
    1.  <span data-ttu-id="29da3-115">指定您要将 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序连接到的服务器。</span><span class="sxs-lookup"><span data-stu-id="29da3-115">Specify the server that you want to connect the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application to.</span></span> <span data-ttu-id="29da3-116">选择 **(LOCAL)** 以便连接到本地计算机上的 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="29da3-116">Select **(LOCAL)** to connect to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] on the local computer.</span></span> <span data-ttu-id="29da3-117">还可以单击向下箭头，选择 **\<Browse network for more servers>** 连接到不同的服务器 (或按名称) 连接到本地服务器。</span><span class="sxs-lookup"><span data-stu-id="29da3-117">You can also click the down arrow and select **\<Browse network for more servers>** to connect to a different server (or to connect to the local server by name).</span></span> <span data-ttu-id="29da3-118">将显示 **“查找服务器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="29da3-118">The **Browse for Servers** dialog box will be displayed.</span></span> <span data-ttu-id="29da3-119">您可以在 **“本地服务器”** 选项卡或 **“网络服务器”** 选项卡中选择某一服务器。</span><span class="sxs-lookup"><span data-stu-id="29da3-119">You can select a server in the **Local Servers** tab or in the **Network Servers** tab.</span></span>  
  
    2.  <span data-ttu-id="29da3-120">如果想要加密在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 和 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 之间传输的数据，请单击“选项”\*\*\*\*，然后选中“加密连接”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="29da3-120">If you want to encrypt data transfer between [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], click **Options**, and then select the **Encrypt Connection** check box.</span></span>  
  
3.  <span data-ttu-id="29da3-121">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="29da3-121">Click **Connect**.</span></span>  
  
 <span data-ttu-id="29da3-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕将出现。</span><span class="sxs-lookup"><span data-stu-id="29da3-122">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen appears.</span></span> <span data-ttu-id="29da3-123">有关详细信息，请参阅[数据质量客户端主屏幕](../../2014/data-quality-services/data-quality-client-home-screen.md)。</span><span class="sxs-lookup"><span data-stu-id="29da3-123">For more information, see [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md).</span></span>  
  
  
