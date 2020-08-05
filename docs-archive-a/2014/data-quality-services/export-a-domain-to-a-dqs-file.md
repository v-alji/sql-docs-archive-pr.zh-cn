---
title: 将域导出到 .dqs 文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eba10d3d-b5c4-447b-8a30-fa07996cb28e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5d23e9efa2b3224aab5623201a54d1af56e49e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579048"
---
# <a name="export-a-domain-to-a-dqs-file"></a><span data-ttu-id="74e9f-102">将域导出到 .dqs 文件</span><span class="sxs-lookup"><span data-stu-id="74e9f-102">Export a Domain to a .dqs File</span></span>
  <span data-ttu-id="74e9f-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中将域导出到 .dqs 文件。</span><span class="sxs-lookup"><span data-stu-id="74e9f-103">This topic describes how to export a domain to a .dqs file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="74e9f-104">您可以将域或整个知识库导出到数据文件。</span><span class="sxs-lookup"><span data-stu-id="74e9f-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="74e9f-105">有关导出知识库的信息，请参阅[将知识库导出到 .dqs 文件](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)。</span><span class="sxs-lookup"><span data-stu-id="74e9f-105">For information about exporting a knowledge base, see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="74e9f-106">将域从一个知识库中导出到 .dqs 数据文件，然后将其导入到另一个知识库，可以简化知识生成过程、节省时间并提高效率。</span><span class="sxs-lookup"><span data-stu-id="74e9f-106">Exporting a domain from one knowledge base to a .dqs data file, and then importing it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="74e9f-107">这样，您就可以与他人共享域及其知识。</span><span class="sxs-lookup"><span data-stu-id="74e9f-107">It enables you to share a domain and its knowledge with others.</span></span>  
  
 <span data-ttu-id="74e9f-108">您可以导出单一域或复合域。</span><span class="sxs-lookup"><span data-stu-id="74e9f-108">You can export either a single domain or composite domain.</span></span> <span data-ttu-id="74e9f-109">包含单一域的 .dqs 文件包含所有域数据，其中包括域属性、值和规则，但附加的引用数据信息除外。</span><span class="sxs-lookup"><span data-stu-id="74e9f-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules except for the attached reference data information.</span></span> <span data-ttu-id="74e9f-110">包含复合域的 .dqs 文件包含所有复合域数据，其中包含复合域中包含的各域的所有域数据，以及复合域属性、关系和规则，但引用数据信息除外。</span><span class="sxs-lookup"><span data-stu-id="74e9f-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the domains that are contained in the composite domain, and the composite domain properties, relations, and rules, except for the reference data information.</span></span> <span data-ttu-id="74e9f-111">如果需要，则在导入 .dqs 文件之后，您必须再次将域或复合域附加到相应的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="74e9f-111">You must attach the domain or the composite domain to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="74e9f-112">将同时导出已发布和未发布的数据。</span><span class="sxs-lookup"><span data-stu-id="74e9f-112">Both published and unpublished data is exported.</span></span>  
  
 <span data-ttu-id="74e9f-113">导出过程创建的 .dqs 数据文件已加密，所以无法查看内容。</span><span class="sxs-lookup"><span data-stu-id="74e9f-113">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="74e9f-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="74e9f-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="74e9f-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="74e9f-115">Prerequisites</span></span>  
 <span data-ttu-id="74e9f-116">若要将域导出到 .dqs 数据文件，您必须已创建并选择了一个单一域或包含多个单一域的复合域。</span><span class="sxs-lookup"><span data-stu-id="74e9f-116">To export a domain to a .dqs data file, you must have created and selected a single domain or a composite domain containing multiple single domains.</span></span> <span data-ttu-id="74e9f-117">您无需具有要导出到的 .dqs 文件，系统将为您创建一个。</span><span class="sxs-lookup"><span data-stu-id="74e9f-117">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="74e9f-118">Security</span><span class="sxs-lookup"><span data-stu-id="74e9f-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="74e9f-119">权限</span><span class="sxs-lookup"><span data-stu-id="74e9f-119">Permissions</span></span>  
 <span data-ttu-id="74e9f-120">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能将域导出到 .dqs 数据文件。</span><span class="sxs-lookup"><span data-stu-id="74e9f-120">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a domain to a .dqs data file.</span></span>  
  
##  <a name="export-a-domain-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="74e9f-121">将域导出到 dqs 文件</span><span class="sxs-lookup"><span data-stu-id="74e9f-121">Export a domain to a .dqs file</span></span>  
 <span data-ttu-id="74e9f-122">您可以从任何域管理页进行导出。</span><span class="sxs-lookup"><span data-stu-id="74e9f-122">You can export from any Domain Management page.</span></span> <span data-ttu-id="74e9f-123">导出命令可通过用户界面中的控件和域列表窗格的上下文菜单中的命令来使用。</span><span class="sxs-lookup"><span data-stu-id="74e9f-123">The export command is available from both a control in the user interface and from a command in the context menu of the Domain List pane.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="74e9f-124">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="74e9f-124">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="74e9f-125">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，在域管理活动中打开知识库。</span><span class="sxs-lookup"><span data-stu-id="74e9f-125">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="74e9f-126">在 **“域管理”** 页（任意选项卡处于“选中”状态）中，在 **“域”** 列表中选择单一域或复合域。</span><span class="sxs-lookup"><span data-stu-id="74e9f-126">In the **Domain Management page** (with any tab selected), select a single domain or a composite domain in the **Domain** list.</span></span>  
  
4.  <span data-ttu-id="74e9f-127">单击域列表上方的 **“导出知识库数据”** 图标，然后单击 **“导出域”**。</span><span class="sxs-lookup"><span data-stu-id="74e9f-127">Click the **Export Knowledge Base data** icon above the domain list, and then click **Export Domain**.</span></span> <span data-ttu-id="74e9f-128">或者，还可以在 **“域”** 列表中右键单击域，指向 **“导出”**，然后单击 **“导出域”**。</span><span class="sxs-lookup"><span data-stu-id="74e9f-128">Alternatively, you can right-click the domain in the **Domain** list, point to **Export**, and then click **Export Domain**.</span></span>  
  
5.  <span data-ttu-id="74e9f-129">在“导出到数据文件”对话框中，转到要保存该文件的文件夹，命名该文件或保留默认名称，将“DQS 数据文件 (\*.dqs)”保留为“另存为”类型，然后单击“保存”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74e9f-129">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the default name, keep **DQS Data Files (\*.dqs)** as the **Save as type**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="74e9f-130">在 **“导出域”** 对话框中，验证该对话框中的状态行是否指示导出已完成。</span><span class="sxs-lookup"><span data-stu-id="74e9f-130">In the **Export Domain** dialog box, verify that the status line in the dialog box indicates that the export completed.</span></span> <span data-ttu-id="74e9f-131">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="74e9f-131">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="74e9f-132">跟进：在将域导出到 dqs 文件后</span><span class="sxs-lookup"><span data-stu-id="74e9f-132">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="74e9f-133">将域导出到 .dqs 文件后，您可以将该域导入到另一个知识库。</span><span class="sxs-lookup"><span data-stu-id="74e9f-133">After you export a domain to a .dqs file, you can import the domain into another knowledge base.</span></span>  
  
  
