---
title: 选择数据源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 641aa04f7fe658123aa21cc1bd21264ec0ee28ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688476"
---
# <a name="select-the-data-source"></a><span data-ttu-id="70117-102">选择数据源</span><span class="sxs-lookup"><span data-stu-id="70117-102">Select the Data Source</span></span>
  <span data-ttu-id="70117-103">使用报表向导的此页可为报表定义数据源。</span><span class="sxs-lookup"><span data-stu-id="70117-103">Use this page of the Report Wizard to define a data source for the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70117-104">选项</span><span class="sxs-lookup"><span data-stu-id="70117-104">Options</span></span>  
 <span data-ttu-id="70117-105">**共享数据源**</span><span class="sxs-lookup"><span data-stu-id="70117-105">**Shared data source**</span></span>  
 <span data-ttu-id="70117-106">选择“共享数据源”可使用已具有所需的数据源连接信息的预定义共享数据源。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70117-106">Select **Shared Data Source** to use a predefined shared data source that already has the data source connection information you want to use.</span></span> <span data-ttu-id="70117-107">该列表包含了项目中包括的所有共享数据源。</span><span class="sxs-lookup"><span data-stu-id="70117-107">The list contains all shared data sources that are included in the project.</span></span>  
  
 <span data-ttu-id="70117-108">**新建数据源**</span><span class="sxs-lookup"><span data-stu-id="70117-108">**New data source**</span></span>  
 <span data-ttu-id="70117-109">选择“新建数据源”可定义新的数据源。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70117-109">Select **New data source** to define a new data source.</span></span> <span data-ttu-id="70117-110">该数据源信息将仅用于当前报表。</span><span class="sxs-lookup"><span data-stu-id="70117-110">The data source information will be used only with the current report.</span></span>  
  
 <span data-ttu-id="70117-111">**名称**</span><span class="sxs-lookup"><span data-stu-id="70117-111">**Name**</span></span>  
 <span data-ttu-id="70117-112">键入用于连接到数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="70117-112">Type a name for the connection to the data source.</span></span> <span data-ttu-id="70117-113">数据源名称在报表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="70117-113">The data source name must be unique within the report.</span></span>  
  
 <span data-ttu-id="70117-114">**Type**</span><span class="sxs-lookup"><span data-stu-id="70117-114">**Type**</span></span>  
 <span data-ttu-id="70117-115">选择要使用的数据源的类型 (例如，如果使用的是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库，请选择 " [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]) "。</span><span class="sxs-lookup"><span data-stu-id="70117-115">Select the type of data source you are using (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, choose [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).</span></span>  
  
 <span data-ttu-id="70117-116">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="70117-116">**Connection string**</span></span>  
 <span data-ttu-id="70117-117">为数据源键入连接字符串。</span><span class="sxs-lookup"><span data-stu-id="70117-117">Type a connection string for the data source.</span></span> <span data-ttu-id="70117-118">有关连接字符串的详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70117-118">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="70117-119">单击 **“编辑”** ，在 **“连接属性”** 对话框中指定数据源服务器。</span><span class="sxs-lookup"><span data-stu-id="70117-119">Click **Edit** to specify the data source server in the **Connection Properties** dialog box.</span></span> <span data-ttu-id="70117-120">您可以指定本地或远程数据源。</span><span class="sxs-lookup"><span data-stu-id="70117-120">You can specify a local or remote data source.</span></span>  
  
 <span data-ttu-id="70117-121">单击 **“凭据”** 可提供数据库凭据。</span><span class="sxs-lookup"><span data-stu-id="70117-121">Click **Credentials** to supply database credentials.</span></span> <span data-ttu-id="70117-122">指定的凭据至少要满足您连接到数据源以进行报表设计的要求。</span><span class="sxs-lookup"><span data-stu-id="70117-122">At a minimum, the credentials you specify must be sufficient for you to connect to the data source for report design purposes.</span></span> <span data-ttu-id="70117-123">在报表服务器上部署报表时，数据库凭据必须适应报表的所有用户的要求。</span><span class="sxs-lookup"><span data-stu-id="70117-123">When the report is deployed on a report server, the database credentials must accommodate all users of the report.</span></span> <span data-ttu-id="70117-124">例如，如果你希望所有报表用户都使用凭据连接数据源，请选择“使用 Windows 身份验证（集成安全性）”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70117-124">For example, if you want all report users to connect to the data source using their credentials, choose **Use Windows Authentication (Integrated Security)**.</span></span> <span data-ttu-id="70117-125">您指定的凭据必须对数据源有效，因此如果您选择 Windows 身份验证，则请确保数据源可接受来自要运行报表的所有用户帐户的连接。</span><span class="sxs-lookup"><span data-stu-id="70117-125">The credentials you specify must be valid for the data source, so if you choose Windows Authentication, be sure that the data source accepts connections from all user accounts that will be running the report.</span></span> <span data-ttu-id="70117-126">数据库凭据和报表可以分开管理。</span><span class="sxs-lookup"><span data-stu-id="70117-126">Database credentials can be managed separately from the report.</span></span> <span data-ttu-id="70117-127">有关详细信息，请参阅 [管理报表数据源](report-data/manage-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="70117-127">For more information, see [Manage Report Data Sources](report-data/manage-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="70117-128">**使其成为共享数据源**</span><span class="sxs-lookup"><span data-stu-id="70117-128">**Make this a shared data source**</span></span>  
 <span data-ttu-id="70117-129">选择此选项可将数据源以共享数据源形式存储在项目中，而不是存储在报表中。</span><span class="sxs-lookup"><span data-stu-id="70117-129">Select this option to store the data source in the project as a shared data source, instead of in the report.</span></span> <span data-ttu-id="70117-130">这样，即可将其用作项目中其他报表的数据源。</span><span class="sxs-lookup"><span data-stu-id="70117-130">That way, you can use it as the data source for other reports in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70117-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70117-131">See Also</span></span>  
 <span data-ttu-id="70117-132">[嵌入和共享的数据连接或数据源 &#40;报表生成器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70117-132">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="70117-133">[为报表数据源指定凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="70117-133">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 <span data-ttu-id="70117-134">[Reporting Services 报表服务器](../../2014/reporting-services/reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="70117-134">[Reporting Services Report Server](../../2014/reporting-services/reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="70117-135">[Rsreportdesigner.config 配置文件](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="70117-135">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="70117-136">[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="70117-136">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="70117-137">报表向导帮助</span><span class="sxs-lookup"><span data-stu-id="70117-137">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
