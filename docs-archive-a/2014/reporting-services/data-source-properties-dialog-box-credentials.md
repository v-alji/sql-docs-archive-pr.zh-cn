---
title: "\"数据源属性\" 对话框-\"凭据\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.credentials.f1
- "10100"
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 491da16e6cd38db54c4d27bd8497ca7fdfaae5b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587245"
---
# <a name="data-source-properties-dialog-box-credentials"></a><span data-ttu-id="69207-102">“数据源属性”对话框 ->“凭据”</span><span class="sxs-lookup"><span data-stu-id="69207-102">Data Source Properties Dialog Box, Credentials</span></span>
  <span data-ttu-id="69207-103">在 **“数据源属性”** 对话框中选择 **“凭据”** ，可以显示和修改凭据以便连接到报表中的数据源。</span><span class="sxs-lookup"><span data-stu-id="69207-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to a data source in the report.</span></span> <span data-ttu-id="69207-104">您所提供的凭据用于访问数据源和缓存数据副本以便进行报表预览。</span><span class="sxs-lookup"><span data-stu-id="69207-104">The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports.</span></span> <span data-ttu-id="69207-105">有关如何缓存预览数据的详细信息，请参阅 [预览报表](reports/previewing-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="69207-105">For more information about how preview data is cached, see [Previewing Reports](reports/previewing-reports.md).</span></span> <span data-ttu-id="69207-106">有关凭据的详细信息，请参阅 [指定报表数据源的凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="69207-106">For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="69207-107">选项</span><span class="sxs-lookup"><span data-stu-id="69207-107">Options</span></span>  
 <span data-ttu-id="69207-108">**使用 Windows 身份验证(集成安全性)**</span><span class="sxs-lookup"><span data-stu-id="69207-108">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="69207-109">选择此选项可以使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="69207-109">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="69207-110">**使用此用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="69207-110">**Use this user name and password**</span></span>  
 <span data-ttu-id="69207-111">选择此选项可以提供特定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="69207-111">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="69207-112">对于共享数据源，当您将报表服务器项目发布到目标服务器时，用户名和密码将作为数据库的存储凭据保存。</span><span class="sxs-lookup"><span data-stu-id="69207-112">For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="69207-113">如果要将用户名和密码用作 Windows 凭据，则可以在目标服务器上编辑已发布共享数据源的属性。</span><span class="sxs-lookup"><span data-stu-id="69207-113">If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="69207-114">有关详细信息，请参阅[创建、删除或修改共享数据源（报表管理器）](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="69207-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).</span></span>  
  
 <span data-ttu-id="69207-115">**用户名**</span><span class="sxs-lookup"><span data-stu-id="69207-115">**User name**</span></span>  
 <span data-ttu-id="69207-116">键入登录数据源时要使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="69207-116">Type a user name to log in to the data source.</span></span>  
  
 <span data-ttu-id="69207-117">**密码**</span><span class="sxs-lookup"><span data-stu-id="69207-117">**Password**</span></span>  
 <span data-ttu-id="69207-118">键入登录数据源时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="69207-118">Type a password to log in to the data source.</span></span>  
  
 <span data-ttu-id="69207-119"> 提示凭据</span><span class="sxs-lookup"><span data-stu-id="69207-119">**Prompt for credentials**</span></span>  
 <span data-ttu-id="69207-120">选择此选项可以在运行报表时提示输入凭据。</span><span class="sxs-lookup"><span data-stu-id="69207-120">Select this option to prompt for credentials when the report is run.</span></span>  
  
 <span data-ttu-id="69207-121">**输入提示字符串**</span><span class="sxs-lookup"><span data-stu-id="69207-121">**Enter prompt string**</span></span>  
 <span data-ttu-id="69207-122">键入用于指示用户提供数据源登录凭据的语句。</span><span class="sxs-lookup"><span data-stu-id="69207-122">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="69207-123">**无凭据**</span><span class="sxs-lookup"><span data-stu-id="69207-123">**No credentials**</span></span>  
 <span data-ttu-id="69207-124">选择此选项可指定不向数据源提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="69207-124">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="69207-125">仅当数据源不接受凭据，或者要通过其他方式传递凭据时，才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="69207-125">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69207-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69207-126">See Also</span></span>  
 <span data-ttu-id="69207-127">["数据源属性" 对话框-"常规"](../../2014/reporting-services/data-source-properties-dialog-box-general.md) </span><span class="sxs-lookup"><span data-stu-id="69207-127">[Data Source Properties Dialog Box, General](../../2014/reporting-services/data-source-properties-dialog-box-general.md) </span></span>  
 <span data-ttu-id="69207-128">[为报表数据源指定凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="69207-128">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 [<span data-ttu-id="69207-129">Data Connections, Data Sources, and Connection Strings in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="69207-129">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
