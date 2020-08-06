---
title: 从 .dqs 文件导入域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2e08837fd0b160732b506af77a6cf4a1cbe1966f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689598"
---
# <a name="import-a-domain-from-a-dqs-file"></a><span data-ttu-id="a0379-102">从 .dqs 文件导入域</span><span class="sxs-lookup"><span data-stu-id="a0379-102">Import a Domain from a .dqs File</span></span>
  <span data-ttu-id="a0379-103">本主题说明如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中将域从 .dqs 文件导入到现有知识库。</span><span class="sxs-lookup"><span data-stu-id="a0379-103">This topic describes how to import a domain from a .dqs file into an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="a0379-104">通过从 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序导出域或知识库可创建 .dqs 数据文件。</span><span class="sxs-lookup"><span data-stu-id="a0379-104">A .dqs data file is created by exporting a domain or knowledge base from the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="a0379-105">.dqs 数据文件已加密，因此无法查看。</span><span class="sxs-lookup"><span data-stu-id="a0379-105">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="a0379-106">通过使用 .dqs 数据文件从一个知识库中导出域，然后将域导入到另一个知识库，可以简化知识生成过程、节省时间并提高效率。</span><span class="sxs-lookup"><span data-stu-id="a0379-106">Using a .dqs data file to export a domain from one knowledge base and then import it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="a0379-107">这样，您就可以与他人共享域及其知识，同时节省时间。</span><span class="sxs-lookup"><span data-stu-id="a0379-107">It enables you to share a domain and its knowledge with others, saving them time.</span></span> <span data-ttu-id="a0379-108">您可以导入一个单一域或一个复合域（包含多个单一域）。</span><span class="sxs-lookup"><span data-stu-id="a0379-108">You can import either one single domain or one composite domain (containing multiple single domains).</span></span> <span data-ttu-id="a0379-109">包含单一域的 .dqs 文件包含所有域数据，其中包括域属性、值和规则数据，但映射的引用数据信息除外。</span><span class="sxs-lookup"><span data-stu-id="a0379-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules data, except for the mapped reference data information.</span></span> <span data-ttu-id="a0379-110">包含复合域的 .dqs 文件包含所有复合域数据，其中包含复合域中包含的各单一域的所有域数据，以及复合域属性、值关系和 CD 规则，但映射的引用数据除外。</span><span class="sxs-lookup"><span data-stu-id="a0379-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the singles domains that are contained within the composite domain, and the composite domain properties, value relations, and CD rules, except for the mapped reference data.</span></span> <span data-ttu-id="a0379-111">将导入已发布和未发布的数据。</span><span class="sxs-lookup"><span data-stu-id="a0379-111">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="a0379-112">在导入域时，域名称仍保持与最初导出的域的名称相同，除非域名称已经存在，在此情况下 DQS 将在此名称之后追加“_1”。</span><span class="sxs-lookup"><span data-stu-id="a0379-112">When you import a domain, the name of the domain remains the same as the name of the domain that was originally exported, unless the domain name already exists, in which case DQS will append "_1" to the name.</span></span> <span data-ttu-id="a0379-113">如果导入的复合域包含与现有域同名的单个域，则上述命名规则也适用。</span><span class="sxs-lookup"><span data-stu-id="a0379-113">This is also true if you import a composite domain that contains an individual domain with the same name as an existing domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a0379-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="a0379-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="a0379-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="a0379-115">Prerequisites</span></span>  
 <span data-ttu-id="a0379-116">若要从 .dqs 文件导入域，必须已将一个单一域或一个复合域（包含多个单一域）导出到 .dqs 文件。</span><span class="sxs-lookup"><span data-stu-id="a0379-116">To import a domain from a .dqs file, you must have already exported one single domain or one composite domain (containing multiple single domains) into the .dqs file.</span></span> <span data-ttu-id="a0379-117">.dqs 文件必须只包含一个域。</span><span class="sxs-lookup"><span data-stu-id="a0379-117">The .dqs file must only contain one domain.</span></span> <span data-ttu-id="a0379-118">您还必须已创建并打开了要将域导入到其中的知识库。</span><span class="sxs-lookup"><span data-stu-id="a0379-118">You must also have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a0379-119">Security</span><span class="sxs-lookup"><span data-stu-id="a0379-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a0379-120">权限</span><span class="sxs-lookup"><span data-stu-id="a0379-120">Permissions</span></span>  
 <span data-ttu-id="a0379-121">您必须具有 DQS_MAIN 数据库的 dqs_kb_editor 或 dqs_administrator 角色，才能从 .dqs 数据文件导入域。</span><span class="sxs-lookup"><span data-stu-id="a0379-121">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a domain from a .dqs data file.</span></span>  
  
##  <a name="import-a-domain-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="a0379-122">从 dqs 文件导入域</span><span class="sxs-lookup"><span data-stu-id="a0379-122">Import a domain from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="a0379-123">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a0379-123">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="a0379-124">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，在域管理活动中打开知识库。</span><span class="sxs-lookup"><span data-stu-id="a0379-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="a0379-125">单击 **“从数据文件导入域”** 图标。</span><span class="sxs-lookup"><span data-stu-id="a0379-125">Click the **Import Domain from data file** icon.</span></span>  
  
4.  <span data-ttu-id="a0379-126">在 **“从数据文件导入”** 对话框中，转到要从中导入文件的文件夹，选中该文件（DQS 文件类型），然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="a0379-126">In the **Import from Data File** dialog box, move to the folder that you want to import the file from, select the file (of type DQS File), and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="a0379-127">在 **“导入域”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a0379-127">In the **Import Domain** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0379-128">仅当您要从中导入的 .dqs 文件仅包含一个单一域或一个复合域（包含多个单个域）时，导入操作才会成功。</span><span class="sxs-lookup"><span data-stu-id="a0379-128">The import operation will succeed only if the .dqs file that you are importing from contains only one single domain or one composite domain (containing multiple single domains).</span></span>  
  
6.  <span data-ttu-id="a0379-129">确认您导入的域显示在 **“域”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="a0379-129">Verify that the domain that you imported is displayed in the **Domain** list.</span></span> <span data-ttu-id="a0379-130">如果您导入复合域，请验证此复合域以及复合域中包含的单一域均出现在 **“域”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="a0379-130">If you imported a composite domain, verify that the composite domain and the single domains contained in it are all in the **Domain** list.</span></span>  
  
##  <a name="follow-up-after-importing-a-domain-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="a0379-131">跟进：从 .dqs 文件导入域后</span><span class="sxs-lookup"><span data-stu-id="a0379-131">Follow Up: After Importing a Domain from a .dqs File</span></span>  
 <span data-ttu-id="a0379-132">在从 .dqs 文件导入域之后，可以将知识添加到域中或在清理或匹配项目中使用域，具体取决于域的内容。</span><span class="sxs-lookup"><span data-stu-id="a0379-132">After you import a domain from a .dqs file, you can add knowledge to the domain or use the domain in a cleansing or matching project, depending on the contents of the domain.</span></span> <span data-ttu-id="a0379-133">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)、[管理复合域](../../2014/data-quality-services/managing-a-composite-domain.md)、[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)、[数据清理](../../2014/data-quality-services/data-cleansing.md)或[数据匹配](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="a0379-133">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
