---
title: "\"共享数据源属性\" 对话框-\"凭据\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shareddatasource.credentials.f1
ms.assetid: c08d1a5f-206b-4d53-ab1a-368b651ee5bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8594c6627c033d31937b2aa8691869cdbba213b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689762"
---
# <a name="shared-data-source-properties-dialog-box-credentials"></a><span data-ttu-id="f7562-102">“共享数据源属性”对话框 -&gt;“凭据”</span><span class="sxs-lookup"><span data-stu-id="f7562-102">Shared Data Source Properties Dialog Box, Credentials</span></span>
  <span data-ttu-id="f7562-103">在 **“共享数据源属性”** 对话框中选择 **“凭据”** 可以显示和修改凭据以便连接到报表中的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="f7562-103">Select **Credentials** on the **Shared Data Source Properties** dialog box to display and modify credentials to connect to a shared data source in the report.</span></span> <span data-ttu-id="f7562-104">您所提供的凭据用于访问数据源和缓存数据副本以便进行报表预览。</span><span class="sxs-lookup"><span data-stu-id="f7562-104">The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports.</span></span> <span data-ttu-id="f7562-105">有关如何缓存预览数据的详细信息，请参阅 [预览报表](reports/previewing-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="f7562-105">For more information about how preview data is cached, see [Previewing Reports](reports/previewing-reports.md).</span></span> <span data-ttu-id="f7562-106">有关凭据的详细信息，请参阅 [指定报表数据源的凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="f7562-106">For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f7562-107">选项</span><span class="sxs-lookup"><span data-stu-id="f7562-107">Options</span></span>  
 <span data-ttu-id="f7562-108">**使用 Windows 身份验证(集成安全性)**</span><span class="sxs-lookup"><span data-stu-id="f7562-108">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="f7562-109">选择此选项可以使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f7562-109">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="f7562-110">**使用此用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="f7562-110">**Use this user name and password**</span></span>  
 <span data-ttu-id="f7562-111">选择此选项可以提供特定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="f7562-111">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="f7562-112">对于共享数据源，当您将报表服务器项目发布到目标服务器时，用户名和密码将作为数据库的存储凭据保存。</span><span class="sxs-lookup"><span data-stu-id="f7562-112">For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="f7562-113">如果要将用户名和密码用作 Windows 凭据，则可以在目标服务器上编辑已发布共享数据源的属性。</span><span class="sxs-lookup"><span data-stu-id="f7562-113">If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="f7562-114">有关详细信息，请参阅[创建、删除或修改共享数据源（报表管理器）](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="f7562-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).</span></span>  
  
 <span data-ttu-id="f7562-115">**用户名**</span><span class="sxs-lookup"><span data-stu-id="f7562-115">**User name**</span></span>  
 <span data-ttu-id="f7562-116">键入登录数据源时要使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="f7562-116">Type a user name to log in to the data source.</span></span>  
  
 <span data-ttu-id="f7562-117">**密码**</span><span class="sxs-lookup"><span data-stu-id="f7562-117">**Password**</span></span>  
 <span data-ttu-id="f7562-118">键入登录数据源时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="f7562-118">Type a password to log in to the data source.</span></span>  
  
 <span data-ttu-id="f7562-119"> 提示凭据</span><span class="sxs-lookup"><span data-stu-id="f7562-119">**Prompt for credentials**</span></span>  
 <span data-ttu-id="f7562-120">选择此选项可以在运行报表时提示输入凭据。</span><span class="sxs-lookup"><span data-stu-id="f7562-120">Select this option to prompt for credentials when the report is run.</span></span>  
  
 <span data-ttu-id="f7562-121">**输入提示字符串**</span><span class="sxs-lookup"><span data-stu-id="f7562-121">**Enter prompt string**</span></span>  
 <span data-ttu-id="f7562-122">键入用于指示用户提供数据源登录凭据的语句。</span><span class="sxs-lookup"><span data-stu-id="f7562-122">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="f7562-123">**无凭据**</span><span class="sxs-lookup"><span data-stu-id="f7562-123">**No credentials**</span></span>  
 <span data-ttu-id="f7562-124">选择此选项可指定不向数据源提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="f7562-124">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="f7562-125">仅当数据源不接受凭据，或者要通过其他方式传递凭据时，才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f7562-125">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7562-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7562-126">See Also</span></span>  
 <span data-ttu-id="f7562-127">[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f7562-127">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="f7562-128">[为报表数据源指定凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="f7562-128">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 [<span data-ttu-id="f7562-129">“共享数据源属性”对话框 -&amp;gt;“常规”</span><span class="sxs-lookup"><span data-stu-id="f7562-129">Shared Data Source Properties Dialog Box, General</span></span>](../../2014/reporting-services/shared-data-source-properties-dialog-box-general.md)  
  
  
