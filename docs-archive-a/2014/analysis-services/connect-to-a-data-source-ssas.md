---
title: " (SSAS) 连接到数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4fe7f7d5b31118369b8ce2a855b955e44f661dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579222"
---
# <a name="connect-to-a-data-source-ssas"></a><span data-ttu-id="f4e8c-102">连接到数据源 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="f4e8c-102">Connect to a Data Source (SSAS)</span></span>
  <span data-ttu-id="f4e8c-103">**“表导入向导”** 的这一页可用于创建与各种数据源（例如关系数据库、数据馈送和文件）的新数据源连接。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-103">This page of the **Table Import Wizard** enables you to create a new data source connection to a variety of data sources, such as relational databases, data feeds, and files.</span></span> <span data-ttu-id="f4e8c-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="f4e8c-105">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-105">To connect to a data source, you must have the appropriate provider installed on your machine.</span></span> <span data-ttu-id="f4e8c-106">您还必须在工作区数据库服务器上安装有适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-106">You must also have the appropriate provider installed on the workspace database server.</span></span> <span data-ttu-id="f4e8c-107">对于 32 位 (x86) 服务器，必须安装 32 位访问接口。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-107">For 32-bit (x86) servers, 32-bit providers must be installed.</span></span> <span data-ttu-id="f4e8c-108">对于 64 位 (x64) 服务器，必须安装 64 位访问接口。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-108">For 64-bit (x64) servers, 64-bit providers must be installed.</span></span>  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] <span data-ttu-id="f4e8c-109">始终在 32 位进程中运行，而与体系结构无关。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-109">always runs in a 32-bit process, regardless of architecture.</span></span> <span data-ttu-id="f4e8c-110">在 64 位计算机上运行 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 时，如果安装数据访问接口，您应该知道以下事项：</span><span class="sxs-lookup"><span data-stu-id="f4e8c-110">When running [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] on a 64-bit machine, you should be aware of the following when installing data providers:</span></span>  
  
-   <span data-ttu-id="f4e8c-111">对于支持 32 位和 64 位访问接口的并行安装的访问接口，您应该安装这两个访问接口。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-111">For providers that support side-by-side installation of 32-bit and 64-bit providers, you should install both providers.</span></span>  
  
-   <span data-ttu-id="f4e8c-112">对于 ACE 访问接口，您必须安装该访问接口的 64 位版本。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-112">For the ACE provider, you must install the 64-bit version of the provider.</span></span> <span data-ttu-id="f4e8c-113">因为 Office 自动安装 ACE 访问接口，所以您不应在承载工作区数据库服务器的 64 位计算机上安装 Microsoft Office 的 32 位版本。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-113">Because Office automatically installs the ACE provider, you should not run a 32-bit version of Microsoft Office on a 64-bit machine hosting the workspace database server.</span></span>  
  
     <span data-ttu-id="f4e8c-114">该 ACE 访问接口用于从文本文件、Excel 文件和 Access 文件导入。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-114">The ACE provider is used to import from Text, Excel, and Access files.</span></span> <span data-ttu-id="f4e8c-115">如果不需要对这些数据源的支持，则您可以在运行 64 位工作区数据库服务器的计算机上运行 Microsoft Office 的 32 位版本。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-115">If support for these data sources is not needed, you can then run a 32-bit version of Microsoft Office on a machine running a 64-bit workspace database server.</span></span>  
  
-   <span data-ttu-id="f4e8c-116">对于不支持 32 位和 64 位访问接口的并行安装的其他访问接口，您必须安装 32 位访问接口。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-116">For other providers that do not support side-by-side installation of 32-bit and 64-bit providers, you must install the 32-bit provider.</span></span> <span data-ttu-id="f4e8c-117">如果只有 64 位计算机可用，则您必须将安装有 64 位访问接口的远程计算机用作工作区数据库服务器。</span><span class="sxs-lookup"><span data-stu-id="f4e8c-117">If only 64-bit machines are available, you must use a remote machine with a 64-bit provider installed as the workspace database server.</span></span>  
  
  
