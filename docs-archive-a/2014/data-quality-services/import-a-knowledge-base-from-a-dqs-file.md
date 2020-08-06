---
title: 从 .dqs 文件导入知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9b9786fe-9e80-429a-afcb-dc3b3dd6f0b0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 522c5f6d8f962cef77e215c21133927e8da4d04f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690175"
---
# <a name="import-a-knowledge-base-from-a-dqs-file"></a><span data-ttu-id="6c6d8-102">从 .dqs 文件导入知识库</span><span class="sxs-lookup"><span data-stu-id="6c6d8-102">Import a Knowledge Base from a .dqs File</span></span>
  <span data-ttu-id="6c6d8-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中从 .dqs 数据文件导入整个知识库。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-103">This topic describes how to import an entire knowledge base from a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="6c6d8-104">您可以通过从 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序内导出现有知识库来创建数据文件（请参阅 [将知识库导出到.dqs 文件](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)）。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-104">You create the data file by exporting an existing knowledge base from within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application (see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)).</span></span>  
  
 <span data-ttu-id="6c6d8-105">使用 .dqs 数据文件导出知识库的内容，然后将内容导入到同一个 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 或不同 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 中的另一个知识库，可以简化知识生成过程、节省时间并提高效率。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-105">Using a .dqs data file to export the contents of a knowledge base and then import the contents into another knowledge base on the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] or a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="6c6d8-106">这样，您就可以与他人共享知识库及其知识，同时节省时间。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-106">It enables you to share a knowledge base and its knowledge with others, saving them time.</span></span> <span data-ttu-id="6c6d8-107">.dqs 文件将包含所有知识库信息，其中包括域和匹配策略，但附加的引用数据信息除外。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-107">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="6c6d8-108">将导入已发布和未发布的数据。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-108">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="6c6d8-109">.dqs 数据文件已加密，因此无法查看。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-109">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="6c6d8-110">在导入知识库时，您可以使用相同的名称，除非客户端应用程序中已存在该知识库名称，在这种情况下，您必须重新命名知识库。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-110">When you import a knowledge base, you can use the same name, unless the knowledge base name already exists in the client application, in which case you must rename it.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c6d8-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="6c6d8-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="6c6d8-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="6c6d8-112">Prerequisites</span></span>  
 <span data-ttu-id="6c6d8-113">若要从 .dqs 文件中导入知识库，您必须已将该知识库导出到 .dqs 文件。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-113">To import a knowledge base from a .dqs file, you must have already exported the knowledge base into the .dqs file.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c6d8-114">Security</span><span class="sxs-lookup"><span data-stu-id="6c6d8-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c6d8-115">权限</span><span class="sxs-lookup"><span data-stu-id="6c6d8-115">Permissions</span></span>  
 <span data-ttu-id="6c6d8-116">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能从 .dqs 数据文件导入知识库。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-116">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a knowledge base from a .dqs data file.</span></span>  
  
##  <a name="import-a-knowledge-base-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="6c6d8-117">从 dqs 文件导入知识库</span><span class="sxs-lookup"><span data-stu-id="6c6d8-117">Import a knowledge base from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="6c6d8-118">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-118">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="6c6d8-119">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“新建知识库”**。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-119">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="6c6d8-120">输入该知识库的名称。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-120">Enter a name for the knowledge base.</span></span>  
  
4.  <span data-ttu-id="6c6d8-121">单击 **“知识库创建自”** 的向下箭头，然后选择 **“自 DQS 文件导入”**。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-121">Click the down arrow for **Create knowledge base from**, and then select **Import from DQS file**.</span></span>  
  
5.  <span data-ttu-id="6c6d8-122">对于 **“选择数据文件”**，单击 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-122">For **Select data file**, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="6c6d8-123">在 **“从数据文件导入”** 对话框中，转到包含要导入的 .dqs 文件的文件夹，然后单击该文件的名称。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-123">In the **Import from Data File** dialog box, move to the folder that contains the .dqs file that you want to import, and then click the name of the file.</span></span> <span data-ttu-id="6c6d8-124">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-124">Click **Open**.</span></span>  
  
7.  <span data-ttu-id="6c6d8-125">验证 **“域”** 列表中显示正确的知识库和域。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-125">Verify that the correct knowledge base and domains are displayed in the **Domain** list.</span></span>  
  
8.  <span data-ttu-id="6c6d8-126">选择要执行的活动，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-126">Select the activity that you want to perform, and then click **Create**.</span></span>  
  
9. <span data-ttu-id="6c6d8-127">在 **“导入知识库”** 对话框中，验证状态行是否指示导入已完成。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-127">In the **Import Knowledge Base** dialog box, verify that the status line indicates that the import completed.</span></span> <span data-ttu-id="6c6d8-128">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-128">Click **OK**.</span></span>  
  
10. <span data-ttu-id="6c6d8-129">完成知识发现、域管理或需要执行的匹配策略任务，然后单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-129">Complete the knowledge discovery, domain management, or matching policy tasks that you need to perform, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="6c6d8-130">单击 **“发布”** 发布知识库中的知识，或单击 **“否”** 不发布知识。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-130">Click **Publish** to publish the knowledge in the knowledge base, or **No** not to.</span></span>  
  
12. <span data-ttu-id="6c6d8-131">如果您发布知识库，则单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-131">If you published the knowledge base, click **OK**.</span></span>  
  
13. <span data-ttu-id="6c6d8-132">在 Data Quality Services 主页中，验证该知识库是否列在 **“最近的知识库”** 下。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-132">In the Data Quality Services home page, verify that the knowledge base is listed under **Recent knowledge bases**.</span></span>  
  
##  <a name="follow-up-after-importing-a-knowledge-base-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="6c6d8-133">跟进：从 .dqs 文件导入知识库后</span><span class="sxs-lookup"><span data-stu-id="6c6d8-133">Follow Up: After Importing a Knowledge Base from a .dqs File</span></span>  
 <span data-ttu-id="6c6d8-134">在从 .dqs 文件导入知识库之后，您可以将知识添加到知识库，或在清理或匹配项目中使用此知识库，具体取决于知识库的内容。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-134">After you import a knowledge base from a .dqs file, you can add knowledge to the knowledge base or use the knowledge base in a cleansing or matching project, depending on the contents of the knowledge base.</span></span> <span data-ttu-id="6c6d8-135">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)、[管理复合域](../../2014/data-quality-services/managing-a-composite-domain.md)、[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)、[数据清理](../../2014/data-quality-services/data-cleansing.md)或[数据匹配](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="6c6d8-135">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
