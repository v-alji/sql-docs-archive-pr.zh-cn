---
title: 获取数据连接的备选方法（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2be693469318172b2a55fbcb17b33e1deaaed3df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578737"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a><span data-ttu-id="e6ffb-102">获取数据连接的备选方法（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="e6ffb-102">Alternative Ways to Get a Data Connection (Report Builder)</span></span>
  <span data-ttu-id="e6ffb-103">数据连接包含要连接到外部数据源（如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库）的信息。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-103">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="e6ffb-104">通常会从数据源所有者处获取连接信息以及要使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-104">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span>  
  
 <span data-ttu-id="e6ffb-105">若要指定数据连接，可以从报表服务器使用共享数据源或创建仅在某个特定报表中使用的嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-105">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in a specific report.</span></span>  
  
 <span data-ttu-id="e6ffb-106">在大多数教程中，您使用嵌入数据源，但如果您有权访问共享数据源，则可以改为使用共享数据源。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-106">In most tutorials you use embedded data sources, but if you have access to shared data sources, then you can use them instead.</span></span>  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a><span data-ttu-id="e6ffb-107">从共享数据源获取数据连接</span><span class="sxs-lookup"><span data-stu-id="e6ffb-107">Getting a Data Connection From a Shared Data Source</span></span>  
 <span data-ttu-id="e6ffb-108">如果报表服务器具有您有权使用的可用共享数据源，则您可以使用这些数据源来代替嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-108">If the report server has available shared data source that you have permissions to use, you can use them instead of an embedded data source.</span></span> <span data-ttu-id="e6ffb-109">以下过程说明如何找到共享数据源并提供使用这些数据源所需的任何凭据。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-109">The following procedures tell how to locate the shared data sources and provide any credentials needed to use them.</span></span>  
  
 <span data-ttu-id="e6ffb-110">若要使用共享数据源，则必须浏览到报表服务器并选择一个共享数据源。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-110">To use a shared data source, you must browse to a report server and select one.</span></span> <span data-ttu-id="e6ffb-111">通常会从报表服务器管理员处获取报表服务器 URL。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-111">Usually, you get the report server URL from the report server administrator.</span></span>  
  
#### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a><span data-ttu-id="e6ffb-112">从共享数据源列表指定数据连接</span><span class="sxs-lookup"><span data-stu-id="e6ffb-112">To specify a data connection from a list of shared data sources</span></span>  
  
1.  <span data-ttu-id="e6ffb-113">在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-113">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="e6ffb-114">将打开“选择数据源的连接”  页面。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-114">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="e6ffb-115">从数据源列表中选择有权访问的数据源。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-115">From the list of data sources, select a data source that you have permission to access.</span></span>  
  
3.  <span data-ttu-id="e6ffb-116">若要验证是否能连接到数据源，请单击“测试连接”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-116">To verify that you can connect to the data source, click **Test Connection**.</span></span> <span data-ttu-id="e6ffb-117">将显示消息“已成功地创建连接”。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-117">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="e6ffb-118">单击“下一步”。 </span><span class="sxs-lookup"><span data-stu-id="e6ffb-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="e6ffb-119">如果需要，请输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-119">If necessary, enter your credentials.</span></span> <span data-ttu-id="e6ffb-120">要本地保存凭据，请选择“保存连接的密码”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-120">To save the credentials locally, select **Save password with connection**.</span></span> <span data-ttu-id="e6ffb-121">如果不选择此选项，则每当您运行该报表时系统将提示您输入凭据。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-121">If you not select this option, you will be prompted for credentials every time that you run the report</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a><span data-ttu-id="e6ffb-122">通过浏览到报表服务器上的共享数据源来指定数据连接</span><span class="sxs-lookup"><span data-stu-id="e6ffb-122">To specify a data connection by browsing to a shared data source on a report server</span></span>  
  
1.  <span data-ttu-id="e6ffb-123">在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-123">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="e6ffb-124">将打开“选择数据源的连接”  页面。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-124">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="e6ffb-125">单击“浏览”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-125">Click **Browse**.</span></span> <span data-ttu-id="e6ffb-126">“选择数据源”对话框随即打开  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-126">The **Select Data Source** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e6ffb-127">从“查找范围”下拉列表中选择“最近使用的站点和服务器”   。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-127">From the **Look in** drop-down list, select **Recent Sites and Servers**.</span></span> <span data-ttu-id="e6ffb-128">在数据源窗格中，单击服务器的 URL，然后单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-128">In the data source pane, click the URL for your server, and then click **Open**.</span></span>  
  
     <span data-ttu-id="e6ffb-129">将显示数据源或模型的列表。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-129">The list of data sources or models appears.</span></span>  
  
4.  <span data-ttu-id="e6ffb-130">或者，在“名称”中，键入报表服务器的 URL  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-130">Alternatively, in **Name**, type the URL to the report server.</span></span> <span data-ttu-id="e6ffb-131">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-131">Click **Open**.</span></span>  
  
     <span data-ttu-id="e6ffb-132">报表生成器将连接到报表服务器，并加载根文件夹中可用的数据源。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-132">Report Builder connects to the report server and loads the data sources that are available at the root folder.</span></span>  
  
5.  <span data-ttu-id="e6ffb-133">导航到包含一个数据源（你有足够的权限，可以连接到该数据源）的文件夹，选择该数据源，然后单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-133">Navigate to a folder that contains a data source that you have sufficient permissions to connect to, select the data source, and then click **Open**.</span></span>  
  
     <span data-ttu-id="e6ffb-134">返回至“选择数据源的连接”页  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-134">You are back on the **Choose a connection to a data source** page.</span></span>  
  
6.  <span data-ttu-id="e6ffb-135">若要验证是否能连接到数据源，请单击“测试连接”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-135">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="e6ffb-136">将显示消息“已成功地创建连接”。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-136">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="e6ffb-137">单击“下一步”。 </span><span class="sxs-lookup"><span data-stu-id="e6ffb-137">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="e6ffb-138">如果系统提示您输入用户名和密码，请输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-138">If you are prompted for a user name and password, enter your credentials.</span></span> <span data-ttu-id="e6ffb-139">要本地保存凭据，请选择“保存连接的密码”  。</span><span class="sxs-lookup"><span data-stu-id="e6ffb-139">To save the credentials locally, select **Save password with connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6ffb-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6ffb-140">See Also</span></span>  
 <span data-ttu-id="e6ffb-141">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e6ffb-141">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="e6ffb-142">教程 &#40;报表生成器&#41;</span><span class="sxs-lookup"><span data-stu-id="e6ffb-142">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
