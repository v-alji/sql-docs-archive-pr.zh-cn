---
title: 导入和导出知识 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6bd5c4f1acde5d25068ac19a7416069704793345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682384"
---
# <a name="importing-and-exporting-knowledge"></a><span data-ttu-id="c1898-102">导入和导出知识</span><span class="sxs-lookup"><span data-stu-id="c1898-102">Importing and Exporting Knowledge</span></span>
  <span data-ttu-id="c1898-103">您可以在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序中直接创建知识库和域，也可以将知识导入到知识库中或从知识库中导出知识。</span><span class="sxs-lookup"><span data-stu-id="c1898-103">You can create knowledge bases and domains directly in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, or you can import knowledge into, or export it from, a knowledge base.</span></span> <span data-ttu-id="c1898-104">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序中，您可以使用某一数据文件执行导入和导出操作，也可以使用 Excel 文件执行导入操作。</span><span class="sxs-lookup"><span data-stu-id="c1898-104">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, you can use a data file for import and export operations, or an Excel file for import operations.</span></span> <span data-ttu-id="c1898-105">使用的数据文件是由 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 创建的扩展名为 .dqs 的加密文件。</span><span class="sxs-lookup"><span data-stu-id="c1898-105">The data file used is an encrypted file that is created by [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) with a .dqs extension.</span></span> <span data-ttu-id="c1898-106">由 Microsoft Excel 创建的文件可以具有 .xlsx、.xls 或 .csv 扩展名。</span><span class="sxs-lookup"><span data-stu-id="c1898-106">The files created by Microsoft Excel can have an extension of .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="c1898-107">这些操作使您可以更灵活地生成和共享用于执行数据清理和匹配的知识。</span><span class="sxs-lookup"><span data-stu-id="c1898-107">These operations give you more flexibility in building and sharing the knowledge that you use to perform data cleansing and matching.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1898-108">您可以通过从命令提示符处运行 DQSInstaller.exe 文件，一次将 *中的*[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] “所有”知识库导出到某一 DQS 备份文件 (.dqsb)。</span><span class="sxs-lookup"><span data-stu-id="c1898-108">You can export *all* the knowledge bases in your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="c1898-109">同样，您可以通过从命令提示符处运行 DQSInstaller.exe 文件，一次将某一 DQS 备份文件 (.dqsb) 中的 \*\* “所有”知识库导入到 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="c1898-109">Similarly, you can import *all* the knowledge bases from a DQS backup file (.dqsb) to your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="c1898-110">有关此操作的信息，请参阅 DQS 安装指南中的 [使用 DQSInstaller.exe 导出和导入 DQS 知识库](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) 。</span><span class="sxs-lookup"><span data-stu-id="c1898-110">For information about doing so, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) in the DQS installation guide.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1898-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="c1898-111">In This Section</span></span>  
 <span data-ttu-id="c1898-112">您可以执行下列导入和导出操作：</span><span class="sxs-lookup"><span data-stu-id="c1898-112">You can perform the following import and export operations:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1898-113">将知识库中的域导出到 .dqs 数据文件中</span><span class="sxs-lookup"><span data-stu-id="c1898-113">Export a domain in a knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="c1898-114">将域导出到 .dqs 文件</span><span class="sxs-lookup"><span data-stu-id="c1898-114">Export a Domain to a .dqs File</span></span>](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|<span data-ttu-id="c1898-115">将域从 .dqs 数据文件导入到现有知识库中</span><span class="sxs-lookup"><span data-stu-id="c1898-115">Import a domain from a .dqs data file into an existing knowledge base</span></span>|[<span data-ttu-id="c1898-116">从 .dqs 文件导入域</span><span class="sxs-lookup"><span data-stu-id="c1898-116">Import a Domain from a .dqs File</span></span>](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|<span data-ttu-id="c1898-117">将整个知识库导出到 .dqs 数据文件中</span><span class="sxs-lookup"><span data-stu-id="c1898-117">Export an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="c1898-118">将知识库导出到 .dqs 文件</span><span class="sxs-lookup"><span data-stu-id="c1898-118">Export a Knowledge Base to a .dqs File</span></span>](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|<span data-ttu-id="c1898-119">将整个知识库导入到 .dqs 数据文件中</span><span class="sxs-lookup"><span data-stu-id="c1898-119">Import an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="c1898-120">从 .dqs 文件导入知识库</span><span class="sxs-lookup"><span data-stu-id="c1898-120">Import a Knowledge Base from a .dqs File</span></span>](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|<span data-ttu-id="c1898-121">将值从 Excel 文件导入到域</span><span class="sxs-lookup"><span data-stu-id="c1898-121">Import values from an Excel file into a domain</span></span>|[<span data-ttu-id="c1898-122">将值从 Excel 文件导入到域</span><span class="sxs-lookup"><span data-stu-id="c1898-122">Import Values from an Excel File into a Domain</span></span>](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|<span data-ttu-id="c1898-123">将域从 Excel 文件中导入到知识库中</span><span class="sxs-lookup"><span data-stu-id="c1898-123">Import domains from an Excel file into a knowledge base</span></span>|[<span data-ttu-id="c1898-124">在知识发现中从 Excel 文件中导入域</span><span class="sxs-lookup"><span data-stu-id="c1898-124">Import Domains from an Excel File in Knowledge Discovery</span></span>](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|<span data-ttu-id="c1898-125">将在清理过程中收集的知识导入到知识库中</span><span class="sxs-lookup"><span data-stu-id="c1898-125">Import knowledge gathered during cleansing into a knowledge base</span></span>|[<span data-ttu-id="c1898-126">将清理项目值导入到域中</span><span class="sxs-lookup"><span data-stu-id="c1898-126">Import Cleansing Project Values into a Domain</span></span>](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="c1898-127">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c1898-127">Related Tasks</span></span>  
  
|<span data-ttu-id="c1898-128">任务说明</span><span class="sxs-lookup"><span data-stu-id="c1898-128">Task Description</span></span>|<span data-ttu-id="c1898-129">主题</span><span class="sxs-lookup"><span data-stu-id="c1898-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c1898-130">通过运行知识发现并以交互方式管理知识来生成知识库</span><span class="sxs-lookup"><span data-stu-id="c1898-130">Building a knowledge base by running knowledge discovery and interactively managing knowledge</span></span>|[<span data-ttu-id="c1898-131">生成知识库</span><span class="sxs-lookup"><span data-stu-id="c1898-131">Building a Knowledge Base</span></span>](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|<span data-ttu-id="c1898-132">创建单一域，并将知识添加到该域中。</span><span class="sxs-lookup"><span data-stu-id="c1898-132">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="c1898-133">管理域</span><span class="sxs-lookup"><span data-stu-id="c1898-133">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="c1898-134">创建一个复合域，并将知识添加到该域中。</span><span class="sxs-lookup"><span data-stu-id="c1898-134">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="c1898-135">管理复合域</span><span class="sxs-lookup"><span data-stu-id="c1898-135">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
