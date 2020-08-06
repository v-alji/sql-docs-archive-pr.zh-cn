---
title: 任务1：创建知识库和域 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce1b22e3d677e831a1d518dacc1267ad0e6be236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689197"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a><span data-ttu-id="a272d-102">任务 1：创建知识库和域</span><span class="sxs-lookup"><span data-stu-id="a272d-102">Task 1: Creating a Knowledge Base and Domains</span></span>
  <span data-ttu-id="a272d-103">在此任务中，您将创建**供应商**知识库并创建用于清理数据和匹配数据的域以删除重复项。</span><span class="sxs-lookup"><span data-stu-id="a272d-103">In this task, you create the **Suppliers** knowledge base and create domains that is used for cleansing data and matching data to remove duplicates.</span></span>  
  
1.  <span data-ttu-id="a272d-104">启动**Data Quality Client**。</span><span class="sxs-lookup"><span data-stu-id="a272d-104">Launch **Data Quality Client**.</span></span> <span data-ttu-id="a272d-105">单击 "**开始**"，依次指向 "**所有程序**"、 **Microsoft SQL Server 2012**、" **Data Quality Services**"，然后单击 " **Data Quality Client**"。</span><span class="sxs-lookup"><span data-stu-id="a272d-105">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2012**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="a272d-106">在 "**连接到服务器**" 对话框中，选择安装 DQS 的数据库服务器实例，然后单击 "**连接**"。</span><span class="sxs-lookup"><span data-stu-id="a272d-106">In the **Connect to Server** dialog box, select the database server instance on which the DQS is installed, and click **Connect**.</span></span>  
  
     <span data-ttu-id="a272d-107">!["连接到服务器" 对话框](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "“连接到服务器”对话框")</span><span class="sxs-lookup"><span data-stu-id="a272d-107">![Connect to Server Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Connect to Server Dialog Box")</span></span>  
  
3.  <span data-ttu-id="a272d-108">在 Data Quality Client 主页的 "**知识库管理**" 窗格中，单击 "**新建知识库**"。</span><span class="sxs-lookup"><span data-stu-id="a272d-108">In the Data Quality Client home page, in the **Knowledge Base Management** pane, click **New Knowledge Base**.</span></span>  
  
     <span data-ttu-id="a272d-109">![知识库管理 - 新建知识库](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "知识库管理 - 新建知识库")</span><span class="sxs-lookup"><span data-stu-id="a272d-109">![Knowledge Base Management - New KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Knowledge Base Management - New KB")</span></span>  
  
4.  <span data-ttu-id="a272d-110">输入该知识库的**名称**的**供应商**。</span><span class="sxs-lookup"><span data-stu-id="a272d-110">Enter **Suppliers** for **Name** of the knowledge base.</span></span>  
  
     <span data-ttu-id="a272d-111">![新建知识库 - 域管理](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "新建知识库 - 域管理")</span><span class="sxs-lookup"><span data-stu-id="a272d-111">![New Knowledge Base - Domain Management](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "New Knowledge Base - Domain Management")</span></span>  
  
5.  <span data-ttu-id="a272d-112">请确认将 "**创建知识库**" 字段设置为 "**无**"，因为您是从头开始创建**供应商**知识库的。</span><span class="sxs-lookup"><span data-stu-id="a272d-112">Confirm that **Create Knowledge Base from** field is set to **None** since you are creating the **Suppliers** knowledge base from scratch.</span></span>  
  
6.  <span data-ttu-id="a272d-113">确认为**活动**选择了 "**域管理**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="a272d-113">Confirm that **Domain Management** is selected for the **Activity** and click **Next**.</span></span> <span data-ttu-id="a272d-114">通过域管理活动，您可以在知识库中创建和管理域。</span><span class="sxs-lookup"><span data-stu-id="a272d-114">The Domain Management activity lets you create and manage domains in the knowledge base.</span></span>  
  
7.  <span data-ttu-id="a272d-115">在 "**域管理**" 窗口中，单击 "**创建域**" 工具栏按钮以创建域。</span><span class="sxs-lookup"><span data-stu-id="a272d-115">In the **Domain Management** window, click **Create a domain** toolbar button to create a domain.</span></span>  
  
     <span data-ttu-id="a272d-116">![“创建域”工具栏按钮](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "“创建域”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="a272d-116">![Create Domain Toolbar Button](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Create Domain Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="a272d-117">在 "**创建域**" 对话框中，键入**域名**的 "**供应商 ID** "，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="a272d-117">In the **Create Domain** dialog box, type **Supplier ID** for the **Domain Name**, and click **OK**.</span></span>  
  
     <span data-ttu-id="a272d-118">![“创建域”对话框](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "“创建域”对话框")</span><span class="sxs-lookup"><span data-stu-id="a272d-118">![Create Domain Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "Create Domain Dialog Box")</span></span>  
  
9. <span data-ttu-id="a272d-119">重复执行前一步以便创建具有所有默认设置的以下域。</span><span class="sxs-lookup"><span data-stu-id="a272d-119">Repeat previous step to create the following domains with all the default settings.</span></span> <span data-ttu-id="a272d-120">为简化本教程，请将所有域的**数据类型**设置为**String**。</span><span class="sxs-lookup"><span data-stu-id="a272d-120">To keep the tutorial simple, you set the **Data Type** of all the domains as **String**.</span></span> <span data-ttu-id="a272d-121">其他允许的数据类型是：Integer、Decimal 和 Date。</span><span class="sxs-lookup"><span data-stu-id="a272d-121">The other allowed data types are: Integer, Decimal, and Date.</span></span> <span data-ttu-id="a272d-122">如果选择了 "**使用前导值**" 选项 (默认值) ，则会将所有同义词替换为输出中的同义词组的前导值。</span><span class="sxs-lookup"><span data-stu-id="a272d-122">When the **Use Leading Values** option is selected (default), all synonyms are replaced with the leading value of the synonym group in the output.</span></span> <span data-ttu-id="a272d-123"> (默认) 设置**正常化字符串**选项会删除域值中的任何特殊字符。</span><span class="sxs-lookup"><span data-stu-id="a272d-123">Setting **Normalize String** option (default) removes any special characters in the domain values.</span></span> <span data-ttu-id="a272d-124">利用 "将**输出格式设置为**" 选项，您可以选择在输出域中的数据值时要应用的格式设置。</span><span class="sxs-lookup"><span data-stu-id="a272d-124">The **Format Output to** option lets you select the formatting that is applied when the data values in the domain are output.</span></span> <span data-ttu-id="a272d-125">选择 "**启用拼写检查**器" (默认) 在填充域时对所有字符串值运行拼写检查器。</span><span class="sxs-lookup"><span data-stu-id="a272d-125">Select **Enable Speller** (default) to run Speller on all string values when populating the domain.</span></span> <span data-ttu-id="a272d-126">**语言**设置指定要应用的**拼写检查**器的语言版本。</span><span class="sxs-lookup"><span data-stu-id="a272d-126">The **Language** setting specifies which language version of the **Speller** you want to apply.</span></span> <span data-ttu-id="a272d-127">选择 "**禁用语法错误算法**" 可填充域而不检查字符串值是否存在语法错误。</span><span class="sxs-lookup"><span data-stu-id="a272d-127">Select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span> <span data-ttu-id="a272d-128">有关更多详细信息，请参阅 MSDN library 中的[创建域](https://msdn.microsoft.com/library/hh510401.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="a272d-128">See [Create a Domain](https://msdn.microsoft.com/library/hh510401.aspx) topic in the MSDN library for more details.</span></span>  
  
    -   <span data-ttu-id="a272d-129">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="a272d-129">Supplier Name</span></span>  
  
    -   <span data-ttu-id="a272d-130">联系人电子邮件</span><span class="sxs-lookup"><span data-stu-id="a272d-130">Contact Email</span></span>  
  
    -   <span data-ttu-id="a272d-131">Address Line</span><span class="sxs-lookup"><span data-stu-id="a272d-131">Address Line</span></span>  
  
    -   <span data-ttu-id="a272d-132">城市</span><span class="sxs-lookup"><span data-stu-id="a272d-132">City</span></span>  
  
    -   <span data-ttu-id="a272d-133">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="a272d-133">State</span></span>  
  
    -   <span data-ttu-id="a272d-134">国家/地区</span><span class="sxs-lookup"><span data-stu-id="a272d-134">Country</span></span>  
  
    -   <span data-ttu-id="a272d-135">Zip</span><span class="sxs-lookup"><span data-stu-id="a272d-135">Zip</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a272d-136">下一步</span><span class="sxs-lookup"><span data-stu-id="a272d-136">Next Step</span></span>  
 [<span data-ttu-id="a272d-137">任务 2：手动添加域值</span><span class="sxs-lookup"><span data-stu-id="a272d-137">Task 2: Adding Domain Values Manually</span></span>](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
