---
title: 快捷查询文件 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe1bdbdadabe0e6448ed3bdc65316104fb26ba43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688968"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a><span data-ttu-id="9c8ad-102">快捷查询文件（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="9c8ad-102">Shortcut Query Files (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="9c8ad-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，使用快捷查询文件可快速连接并加载常用数据。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use shortcut query files to quickly connect and load frequently-used data.</span></span> <span data-ttu-id="9c8ad-104">当您要与他人共享 MDS 数据时，也可以使用这些文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-104">You can also use them when you want to share MDS data with others.</span></span> <span data-ttu-id="9c8ad-105">不需要保存工作表再通过电子邮件发送，而应保存一个快捷查询文件然后通过电子邮件发送该文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-105">Instead of saving the worksheet and emailing it, you should save a shortcut query file and email that instead.</span></span> <span data-ttu-id="9c8ad-106">这将确保您同时连接到 MDS 存储库，以获取最新数据。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-106">This ensures that you are both connecting to the MDS repository to get the latest data.</span></span>  
  
 <span data-ttu-id="9c8ad-107">快捷查询文件是包含以下相关信息的 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="9c8ad-107">Shortcut query files are XML files that contain information about:</span></span>  
  
-   <span data-ttu-id="9c8ad-108">MDS 存储库连接。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-108">The MDS repository connection.</span></span>  
  
-   <span data-ttu-id="9c8ad-109">模型、版本和实体。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-109">The model, version, and entity.</span></span>  
  
-   <span data-ttu-id="9c8ad-110">创建快捷方式时应用的任何筛选器。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-110">Any filters that were applied when the shortcut was created.</span></span>  
  
-   <span data-ttu-id="9c8ad-111">创建快捷方式时从左到右的列顺序。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-111">The left-to-right order of the columns when the shortcut was created.</span></span>  
  
 <span data-ttu-id="9c8ad-112">可以将这些文件保存在一个列表中，然后在打开该外接程序时从中进行选择。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-112">You can save these files in a list and choose from them when you open the Add-in.</span></span> <span data-ttu-id="9c8ad-113">您可以将其导出到您的计算机或某个共享位置，也可以将其发送给其他人。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-113">You can export them to your computer or to a shared location, or you can send them to others.</span></span>  
  
## <a name="queryopener-application"></a><span data-ttu-id="9c8ad-114">QueryOpener 应用程序</span><span class="sxs-lookup"><span data-stu-id="9c8ad-114">QueryOpener Application</span></span>  
 <span data-ttu-id="9c8ad-115">安装了 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 的所有用户都装有名为 QueryOpener 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-115">All users who install the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] have an application called QueryOpener installed.</span></span> <span data-ttu-id="9c8ad-116">此应用程序用于在 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中打开快捷查询文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-116">This application is used to open shortcut query files in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)].</span></span> <span data-ttu-id="9c8ad-117">如果双击快捷查询文件，将自动使用此应用程序在该外接程序中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-117">If you double-click a shortcut query file, this application is automatically used to open the file in the Add-in.</span></span>  
  
 <span data-ttu-id="9c8ad-118">使用此应用程序打开快捷查询文件时，系统会提示将该连接视为“安全”连接，这意味着你信任此位置的内容。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-118">When you open a shortcut query file with this application, you are prompted to make the connection a "safe" connection, which means you trust content from this location.</span></span> <span data-ttu-id="9c8ad-119">每次将某个连接标记为安全连接后，该连接都会添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-119">Each time you mark a connection as safe, it is added to a list.</span></span> <span data-ttu-id="9c8ad-120">如果要清空该列表，请打开 **“设置”** 对话框，然后在 **“添加到安全列表的服务器”** 部分中，单击 **“全部清除”**。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-120">If you want to clear this list, open the **Settings** dialog box and in the **Servers Added to Safe List** section, click **Clear All**.</span></span>  
  
 <span data-ttu-id="9c8ad-121">应用程序的默认位置是*drive*： \PROGRAM Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-121">The default location for the application is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.</span></span>  
  
 <span data-ttu-id="9c8ad-122">有两种方式可以打开快捷查询文件：可以导入这些文件，或通过双击自动打开这些文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-122">There are two ways to open shortcut query files: you can import them or you can double-click them and they are opened automatically.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9c8ad-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9c8ad-123">Related Tasks</span></span>  
  
|<span data-ttu-id="9c8ad-124">任务说明</span><span class="sxs-lookup"><span data-stu-id="9c8ad-124">Task Description</span></span>|<span data-ttu-id="9c8ad-125">主题</span><span class="sxs-lookup"><span data-stu-id="9c8ad-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="9c8ad-126">将活动工作表的内容另存为一个快捷查询文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-126">Save the contents of the active worksheet as a shortcut query file.</span></span>|[<span data-ttu-id="9c8ad-127">保存快捷查询文件（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="9c8ad-127">Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|<span data-ttu-id="9c8ad-128">通过电子邮件发送表示活动工作表内容的快捷查询文件。</span><span class="sxs-lookup"><span data-stu-id="9c8ad-128">Email a shortcut query file that represents the contents of the active worksheet.</span></span>|[<span data-ttu-id="9c8ad-129">以电子邮件形式发送快捷查询文件（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="9c8ad-129">Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="9c8ad-130">相关内容</span><span class="sxs-lookup"><span data-stu-id="9c8ad-130">Related Content</span></span>  
  
-   [<span data-ttu-id="9c8ad-131">连接（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="9c8ad-131">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="9c8ad-132">用于 Microsoft Excel 的 Master Data Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="9c8ad-132">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="9c8ad-133">安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9c8ad-133">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
