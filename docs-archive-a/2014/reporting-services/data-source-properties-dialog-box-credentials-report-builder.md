---
title: "\"数据源属性\" 对话框-\"凭据 (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e47ba571e2b0adf2738499c1d027a4edde86e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588335"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a><span data-ttu-id="b18b1-102">“数据源属性”对话框 -&gt;“凭据”（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="b18b1-102">Data Source Properties Dialog Box, Credentials (Report Builder)</span></span>
  <span data-ttu-id="b18b1-103">在 **“数据源属性”** 对话框中选择 **“凭据”** 可以显示和修改用于连接到报表中的嵌入数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="b18b1-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to an embedded data source in the report.</span></span> <span data-ttu-id="b18b1-104">您所提供的凭据用于访问数据源以便预览报表。</span><span class="sxs-lookup"><span data-stu-id="b18b1-104">The credentials that you provide are used to access the data source for previewing reports.</span></span> <span data-ttu-id="b18b1-105">有关凭据的详细信息，请参阅 [在报表生成器中指定凭据](../../2014/reporting-services/specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b18b1-105">For more information about credentials, see [Specify Credentials in Report Builder](../../2014/reporting-services/specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b18b1-106">选项</span><span class="sxs-lookup"><span data-stu-id="b18b1-106">Options</span></span>  
 <span data-ttu-id="b18b1-107">**使用 Windows 身份验证(集成安全性)**</span><span class="sxs-lookup"><span data-stu-id="b18b1-107">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="b18b1-108">选择此选项可以使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b18b1-108">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b18b1-109">**使用此用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="b18b1-109">**Use this user name and password**</span></span>  
 <span data-ttu-id="b18b1-110">选择此选项可以提供特定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b18b1-110">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="b18b1-111">对于嵌入数据源，在将报表服务器项目发布到目标服务器时，用户名和密码将保存为数据库的存储凭据。</span><span class="sxs-lookup"><span data-stu-id="b18b1-111">For embedded data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="b18b1-112">如果要将用户名和密码用作 Windows 凭据，则可以在目标服务器上更改已发布共享数据源的属性。</span><span class="sxs-lookup"><span data-stu-id="b18b1-112">If you want to use the user name and password as Windows credentials, you can change the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="b18b1-113">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]文档中的[创建、删除或修改共享数据源（报表管理器）](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b18b1-113">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="b18b1-114">**用户名**</span><span class="sxs-lookup"><span data-stu-id="b18b1-114">**User name**</span></span>  
 <span data-ttu-id="b18b1-115">键入用于登录数据源的用户名。</span><span class="sxs-lookup"><span data-stu-id="b18b1-115">Type a user name to log on to the data source.</span></span>  
  
 <span data-ttu-id="b18b1-116">**密码**</span><span class="sxs-lookup"><span data-stu-id="b18b1-116">**Password**</span></span>  
 <span data-ttu-id="b18b1-117">键入用于登录数据源的密码。</span><span class="sxs-lookup"><span data-stu-id="b18b1-117">Type a password to log on to the data source.</span></span>  
  
 <span data-ttu-id="b18b1-118"> 提示凭据</span><span class="sxs-lookup"><span data-stu-id="b18b1-118">**Prompt for credentials**</span></span>  
 <span data-ttu-id="b18b1-119">选择此选项可以在报表运行时提示输入凭据。</span><span class="sxs-lookup"><span data-stu-id="b18b1-119">Select this option to prompt for credentials when the report runs.</span></span>  
  
 <span data-ttu-id="b18b1-120">**输入提示字符串**</span><span class="sxs-lookup"><span data-stu-id="b18b1-120">**Enter prompt string**</span></span>  
 <span data-ttu-id="b18b1-121">键入用于指示用户提供数据源登录凭据的语句。</span><span class="sxs-lookup"><span data-stu-id="b18b1-121">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="b18b1-122">**无凭据**</span><span class="sxs-lookup"><span data-stu-id="b18b1-122">**No credentials**</span></span>  
 <span data-ttu-id="b18b1-123">选择此选项可指定不向数据源提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="b18b1-123">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="b18b1-124">仅当数据源不接受凭据，或者要通过其他方式传递凭据时，才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="b18b1-124">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
 <span data-ttu-id="b18b1-125">对于某些数据扩展插件，必须在报表服务器上配置无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="b18b1-125">From some data extensions, the unattended execution account must be configured on the report server.</span></span>  
  
 <span data-ttu-id="b18b1-126">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 文档中的[从外部数据源中添加数据(SSRS)](report-data/add-data-from-external-data-sources-ssrs.md)和 [配置无人参与的执行帐户（SSRS 配置管理器）](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)中相应数据源类型的主题。</span><span class="sxs-lookup"><span data-stu-id="b18b1-126">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18b1-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b18b1-127">See Also</span></span>  
 <span data-ttu-id="b18b1-128">[报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="b18b1-128">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="b18b1-129">["数据源属性" 对话框-"常规" &#40;报表生成器&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="b18b1-129">[Data Source Properties Dialog Box, General &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span></span>  
 <span data-ttu-id="b18b1-130">[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b18b1-130">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b18b1-131">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b18b1-131">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
