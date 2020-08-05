---
title: 将知识库导出到 .dqs 文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81dfc8e7f20fae9dacd521595d101be3117a6794
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579043"
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a><span data-ttu-id="30875-102">将知识库导出到 .dqs 文件</span><span class="sxs-lookup"><span data-stu-id="30875-102">Export a Knowledge Base to a .dqs File</span></span>
  <span data-ttu-id="30875-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中将整个知识库导出到 .dqs 数据文件。</span><span class="sxs-lookup"><span data-stu-id="30875-103">This topic describes how to export an entire knowledge base to a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="30875-104">您可以将域或整个知识库导出到数据文件。</span><span class="sxs-lookup"><span data-stu-id="30875-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="30875-105">有关导出域的信息，请参阅[将域导出到 .dqs 文件](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)。</span><span class="sxs-lookup"><span data-stu-id="30875-105">For information about exporting a domain, see [Export a Domain to a .dqs File](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="30875-106">将知识库导出为 .dqs 文件，然后将其作为另一个知识库导入，可以简化知识生成过程、节省时间并提高效率。</span><span class="sxs-lookup"><span data-stu-id="30875-106">Exporting a knowledge base to a .dqs file, and then importing it as another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="30875-107">这样，您就可以与他人共享知识库及其知识。</span><span class="sxs-lookup"><span data-stu-id="30875-107">It enables you to share a knowledge base and its knowledge with others.</span></span> <span data-ttu-id="30875-108">.dqs 文件将包含所有知识库信息，其中包括域和匹配策略，但附加的引用数据信息除外。</span><span class="sxs-lookup"><span data-stu-id="30875-108">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="30875-109">如果需要，则在导入 .dqs 文件之后，您必须再次将所需的域附加到相应的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="30875-109">You must attach the required domains to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="30875-110">此时将同时导出知识库中的已发布和未发布的数据。</span><span class="sxs-lookup"><span data-stu-id="30875-110">Both published and unpublished data in a knowledge base is exported.</span></span>  
  
 <span data-ttu-id="30875-111">导出过程创建的 .dqs 数据文件已加密，所以无法查看内容。</span><span class="sxs-lookup"><span data-stu-id="30875-111">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30875-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="30875-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="30875-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="30875-113">Prerequisites</span></span>  
 <span data-ttu-id="30875-114">若要将知识库导出到 .dqs 数据文件，您必须已创建并打开了知识库。</span><span class="sxs-lookup"><span data-stu-id="30875-114">To export a knowledge base to a .dqs data file, you must have created and opened a knowledge base.</span></span> <span data-ttu-id="30875-115">您无需具有要导出到的 .dqs 文件，系统将为您创建一个。</span><span class="sxs-lookup"><span data-stu-id="30875-115">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30875-116">Security</span><span class="sxs-lookup"><span data-stu-id="30875-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30875-117">权限</span><span class="sxs-lookup"><span data-stu-id="30875-117">Permissions</span></span>  
 <span data-ttu-id="30875-118">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能将知识库导出到 .dqs 数据文件。</span><span class="sxs-lookup"><span data-stu-id="30875-118">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a knowledge base to a .dqs data file.</span></span>  
  
##  <a name="export-a-knowledge-base-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="30875-119">将知识库导出到 dqs 文件</span><span class="sxs-lookup"><span data-stu-id="30875-119">Export a knowledge base to a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="30875-120">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="30875-120">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="30875-121">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，在域管理活动中打开知识库。</span><span class="sxs-lookup"><span data-stu-id="30875-121">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="30875-122">在“域管理”页（选择了任一选项卡）中，单击域列表上方的 **“导出知识库数据”** 图标，然后单击 **“导出知识库”**。</span><span class="sxs-lookup"><span data-stu-id="30875-122">In the Domain Management page (with any tab selected), click the **Export Knowledge Base data** icon above the Domain list, and then click **Export Knowledge Base**.</span></span> <span data-ttu-id="30875-123">或者，您还可以在 **“域”** 列表中右键单击，将鼠标指针悬停在 **“导出”** 之上，然后单击 **“导出知识库”**。</span><span class="sxs-lookup"><span data-stu-id="30875-123">Alternatively, you can also right-click in the **Domain** list, hover over **Export**, and then click **Export Knowledge Base**.</span></span>  
  
4.  <span data-ttu-id="30875-124">在“导出到数据文件”对话框中，转到要保存该文件的文件夹，命名该文件或保留知识库名称，将“DQS 数据文件 (\*.dqs)”保留为“另存为”类型，然后单击“保存”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30875-124">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the knowledge base name, keep **DQS Data Files (\*.dqs)** as the **Save as** type, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="30875-125">在 **“导出知识库”** 对话框中，验证状态行是否指示导出已完成。</span><span class="sxs-lookup"><span data-stu-id="30875-125">In the **Export Knowledge Base** dialog box, verify that the status line indicates that the export completed.</span></span> <span data-ttu-id="30875-126">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="30875-126">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a><span data-ttu-id="30875-127">跟进：在将域导出到 dqs 文件后</span><span class="sxs-lookup"><span data-stu-id="30875-127">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="30875-128">将知识库导出到 .dqs 文件后，您可以将知识库导入到同一个 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] （使用新名称）或导入到另一个 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="30875-128">After you export a knowledge base to a .dqs file, you can import the knowledge base into the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (with a new name) or into a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
  
