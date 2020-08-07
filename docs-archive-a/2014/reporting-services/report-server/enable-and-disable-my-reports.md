---
title: 启用和禁用“我的报表”| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deactivated My Reports folder
- folders [Reporting Services], My Reports
- activated My Reports folder
- My Reports folder [Reporting Services]
- disabling My Reports folder
ms.assetid: 16c76e82-9fd4-417c-9ed3-a7d5bcd1dba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef9b48744365b981d11b0e5ae20dc654f2d131d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588280"
---
# <a name="enable-and-disable-my-reports"></a><span data-ttu-id="41a1e-102">启用和禁用“我的报表”</span><span class="sxs-lookup"><span data-stu-id="41a1e-102">Enable and Disable My Reports</span></span>
  <span data-ttu-id="41a1e-103">使用“我的报表”功能可以在报表服务器数据库内分配个人存储区，便于用户在私人文件夹中保存自己的报表。</span><span class="sxs-lookup"><span data-stu-id="41a1e-103">The My Reports feature allocates personal storage in the report server database so that users can save reports that they own in a private folder.</span></span> <span data-ttu-id="41a1e-104">报表服务器管理员可以启用或禁用此功能，或通过修改控制用户如何使用此工作区的安全设置，来更改该功能的工作方式。</span><span class="sxs-lookup"><span data-stu-id="41a1e-104">As a report server administrator, you can enable or disable this feature or change how the feature works by modifying the security settings that control what users can do with this workspace.</span></span>  
  
 <span data-ttu-id="41a1e-105">默认情况下，将禁用“我的报表”功能。</span><span class="sxs-lookup"><span data-stu-id="41a1e-105">The My Reports feature is disabled by default.</span></span> <span data-ttu-id="41a1e-106">您可以对所有用户启用或禁用该功能，但不能对一部分用户启用该功能。</span><span class="sxs-lookup"><span data-stu-id="41a1e-106">You can either enable or disable the feature for all users, but you cannot enable it for a subset of users.</span></span> <span data-ttu-id="41a1e-107">大多数用户和单位都认为这项功能颇有价值；请权衡本主题下文列出的优缺点，确定该功能是否适用于您的单位。</span><span class="sxs-lookup"><span data-stu-id="41a1e-107">Most users and organizations find this feature valuable; study the advantages and disadvantages presented later in this topic to determine whether it is a good fit for your organization.</span></span>  
  
## <a name="how-to-enable-and-disable-my-reports"></a><span data-ttu-id="41a1e-108">如何启用和禁用“我的报表”功能</span><span class="sxs-lookup"><span data-stu-id="41a1e-108">How to Enable and Disable My Reports</span></span>  
 <span data-ttu-id="41a1e-109">若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]启用“我的报表”功能，请连接到报表服务器实例，打开 **“服务器属性”** 页。</span><span class="sxs-lookup"><span data-stu-id="41a1e-109">To enable My Reports by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the report server instance and open the **Server Properties** page.</span></span> <span data-ttu-id="41a1e-110">然后在 **“常规”** 选项卡上选中 **“为每个用户启用‘我的报表’文件夹”** 选项。</span><span class="sxs-lookup"><span data-stu-id="41a1e-110">Then on the **General** tab, select the **Enable a My Reports folder for each user** option.</span></span>  
  
 <span data-ttu-id="41a1e-111">用于“我的报表”功能的角色定义可确定在“我的报表”工作区中支持哪些操作。</span><span class="sxs-lookup"><span data-stu-id="41a1e-111">The role definition used for My Reports determines what actions are supported in the My Reports workspace.</span></span> <span data-ttu-id="41a1e-112">例如，如果“我的报表”角色不包括“创建链接报表”任务，用户将无法在“我的报表”文件夹中创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="41a1e-112">For example, if the My Reports role excludes "Create linked reports," users cannot create linked reports in the My Reports folders.</span></span> <span data-ttu-id="41a1e-113">有关详细信息，请参阅 [保护我的报表](../security/secure-my-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="41a1e-113">For more information, see [Secure My Reports](../security/secure-my-reports.md).</span></span>  
  
 <span data-ttu-id="41a1e-114">若要停用“我的报表”功能，请清除 **“为每个用户启用‘我的报表’文件夹。”** 。</span><span class="sxs-lookup"><span data-stu-id="41a1e-114">To deactivate My Reports, clear **Enable a My Reports folder for each user**.</span></span> <span data-ttu-id="41a1e-115">停用“我的报表”功能将为用户移除“我的报表”文件夹的所有可见的指示形式。</span><span class="sxs-lookup"><span data-stu-id="41a1e-115">Deactivating My Reports removes for users all visible indications of the My Reports folder.</span></span> <span data-ttu-id="41a1e-116">一旦禁用该功能，您必须手动删除提供实际存储位置的文件夹（即“用户文件夹”中的子文件夹）。</span><span class="sxs-lookup"><span data-stu-id="41a1e-116">The folders that provide actual storage (that is, the subfolders in Users Folders) must be deleted manually once the feature is disabled.</span></span>  
  
### <a name="when-my-reports-is-activated"></a><span data-ttu-id="41a1e-117">激活“我的报表”功能之后</span><span class="sxs-lookup"><span data-stu-id="41a1e-117">When My Reports Is Activated</span></span>  
 <span data-ttu-id="41a1e-118">一旦激活该功能，用户将在根文件夹（即“主文件夹”）之下看到“我的报表”文件夹。</span><span class="sxs-lookup"><span data-stu-id="41a1e-118">Once the feature is activated, users see a My Reports folder located under the root folder, Home.</span></span> <span data-ttu-id="41a1e-119">除了“我的报表”文件夹外，报表服务器管理员还会在“用户文件夹”文件夹中看到对应每个用户的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="41a1e-119">In addition to a My Reports folder, report server administrators also see a Users Folders folder that contains the subfolder for each user.</span></span>  
  
 <span data-ttu-id="41a1e-120">激活该功能后，将无法删除“用户文件夹”及其子文件夹。</span><span class="sxs-lookup"><span data-stu-id="41a1e-120">While the feature is activated, Users Folders and its subfolders cannot be deleted.</span></span> <span data-ttu-id="41a1e-121">此外，名称“我的报表”将成为根节点（主文件夹）下创建的文件夹的保留名称。</span><span class="sxs-lookup"><span data-stu-id="41a1e-121">Furthermore, the name "My Reports" becomes a reserved name for folders created under the root node (Home).</span></span>  
  
 <span data-ttu-id="41a1e-122">如果在停用“我的报表”功能后激活它，报表服务器将创建新的“用户文件夹”文件夹（如果尚不存在）。</span><span class="sxs-lookup"><span data-stu-id="41a1e-122">If you activate My Reports after it has been deactivated, the report server creates a new Users Folders folder if one does not already exist.</span></span> <span data-ttu-id="41a1e-123">如果“用户文件夹”已存在，报表服务器将在用户登录到各自的“我的报表”文件夹时添加新的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="41a1e-123">If Users Folders exists, the report server adds new subfolders as users log on to their My Reports folders.</span></span>  
  
### <a name="when-my-reports-is-deactivated"></a><span data-ttu-id="41a1e-124">停用“我的报表”功能之后</span><span class="sxs-lookup"><span data-stu-id="41a1e-124">When My Reports Is Deactivated</span></span>  
 <span data-ttu-id="41a1e-125">一旦停用该功能，名称“我的报表”将不再保留；这时用户可以在主文件夹下创建名为“我的报表”的个人文件夹。</span><span class="sxs-lookup"><span data-stu-id="41a1e-125">Once the feature is deactivated, the name "My Reports" is no longer reserved; users can create a personal folder named My Reports under the Home folder.</span></span> <span data-ttu-id="41a1e-126">此外，不再执行从“我的报表”到用户特定的“我的报表”子文件夹的重定向。</span><span class="sxs-lookup"><span data-stu-id="41a1e-126">In addition, redirection from My Reports to user-specific My Reports subfolders is no longer performed.</span></span> <span data-ttu-id="41a1e-127">最后，在 URL 地址中包括用户特定“我的报表”文件夹的任何报表链接都将不再有效。</span><span class="sxs-lookup"><span data-stu-id="41a1e-127">Lastly, any report links that include a user-specific My Reports folder in the URL address will no longer work.</span></span>  
  
## <a name="choosing-to-use-my-reports"></a><span data-ttu-id="41a1e-128">选用“我的报表”功能</span><span class="sxs-lookup"><span data-stu-id="41a1e-128">Choosing to Use My Reports</span></span>  
 <span data-ttu-id="41a1e-129">是否使用“我的报表”功能取决于您是否希望将一些服务器资源专门用于支持用户工作区。</span><span class="sxs-lookup"><span data-stu-id="41a1e-129">Deciding whether to use My Reports depends on whether you want to dedicate server resources to support a user workspace.</span></span> <span data-ttu-id="41a1e-130">“我的报表”是一项强大的功能，用户可以使用该功能控制协助他们完成工作的信息资源。</span><span class="sxs-lookup"><span data-stu-id="41a1e-130">My Reports is a powerful feature that allows users to have control over information resources that help them do their jobs.</span></span> <span data-ttu-id="41a1e-131">通过该功能，用户还可以处理不常用的报表。</span><span class="sxs-lookup"><span data-stu-id="41a1e-131">It also provides a way for users to work with reports that are not intended for general use.</span></span> <span data-ttu-id="41a1e-132">使用“我的报表”的一个最主要的原因在于：它为需要编制和查看报表的用户提供了安全、易管理的支持功能。</span><span class="sxs-lookup"><span data-stu-id="41a1e-132">One of the most compelling reasons to use My Reports is that it provides secure, manageable support for the segment of users who need to author and review reports.</span></span> <span data-ttu-id="41a1e-133">如果没有此功能，您会发现自己需要专门为各个用户创建文件夹和安全策略。</span><span class="sxs-lookup"><span data-stu-id="41a1e-133">Without this feature, you may find yourself creating folders and security policies for various users on an ad hoc basis.</span></span> <span data-ttu-id="41a1e-134">随着用户和用户需求的变化，这种方式势必造成文件夹和策略的数量不断增加，时间越久越不易维护。</span><span class="sxs-lookup"><span data-stu-id="41a1e-134">As users and user needs change, this approach results in ever-increasing numbers of folders and policies that are difficult to maintain over time.</span></span>  
  
 <span data-ttu-id="41a1e-135">请注意，如果确实激活了“我的报表”功能，对于单击“我的报表”链接并且具有域帐户的每个用户，即使用户并不希望或不需要“我的报表”文件夹，报表服务器也会为这些用户创建该文件夹。</span><span class="sxs-lookup"><span data-stu-id="41a1e-135">Note that if you do activate My Reports, the report server creates a My Reports folder for every user with a domain account who clicks the My Reports link, even if the user does not want or need a My Reports folder.</span></span> <span data-ttu-id="41a1e-136">无法通过系统确定哪些文件夹正在使用。</span><span class="sxs-lookup"><span data-stu-id="41a1e-136">There is no systematic way to determine which folders are being used.</span></span> <span data-ttu-id="41a1e-137">您必须手动检查各文件夹，确定其中是否包含内容。</span><span class="sxs-lookup"><span data-stu-id="41a1e-137">You must review the folders manually to see whether they contain anything.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a1e-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41a1e-138">See Also</span></span>  
 <span data-ttu-id="41a1e-139">[保护我的报表](../security/secure-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="41a1e-139">[Secure My Reports](../security/secure-my-reports.md) </span></span>  
 [<span data-ttu-id="41a1e-140">报表服务器内容管理（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="41a1e-140">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](report-server-content-management-ssrs-native-mode.md)  
  
  
