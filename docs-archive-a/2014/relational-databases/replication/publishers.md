---
title: 发布服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 879fa3cc2ecadf56914928c6ae83600f513f6ddb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576630"
---
# <a name="publishers"></a><span data-ttu-id="4de89-102">发布者</span><span class="sxs-lookup"><span data-stu-id="4de89-102">Publishers</span></span>
  <span data-ttu-id="4de89-103">您可以为其他发布服务器授予使用分发服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="4de89-103">You can give permission for other Publishers to use this Distributor.</span></span> <span data-ttu-id="4de89-104">请注意，允许发布服务器将此服务器用作其远程分发服务器的同时，并不会使该服务器成为发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4de89-104">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="4de89-105">必须连接到发布服务器，对其进行配置以用于发布，并选择此服务器作为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="4de89-105">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="4de89-106">您可以通过新建发布向导配置发布服务器并选择分发服务器。</span><span class="sxs-lookup"><span data-stu-id="4de89-106">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
 <span data-ttu-id="4de89-107">被选作发布服务器的服务器将使用此向导的 **“分发数据库”** 页上指定的分发数据库。</span><span class="sxs-lookup"><span data-stu-id="4de89-107">The servers you select as Publishers will use the distribution database specified on the **Distribution Database** page of this wizard.</span></span> <span data-ttu-id="4de89-108">若要使用其他分发数据库，此时请不要启用发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4de89-108">If you want to use a different distribution database, do not enable the Publisher at this time.</span></span> <span data-ttu-id="4de89-109">相反，在完成配置分发向导后，请使用 **“分发服务器属性”** 对话框来添加发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4de89-109">Instead, use the **Distributor Properties** dialog box to add Publishers after you complete the Configure Distribution Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4de89-110">选项</span><span class="sxs-lookup"><span data-stu-id="4de89-110">Options</span></span>  
 <span data-ttu-id="4de89-111">**发布服务器**</span><span class="sxs-lookup"><span data-stu-id="4de89-111">**Publishers**</span></span>  
 <span data-ttu-id="4de89-112">选择允许使用此分发服务器的服务器。</span><span class="sxs-lookup"><span data-stu-id="4de89-112">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="4de89-113">请单击发布服务器旁边的属性按钮 ( **...** ) 以查看和设置其他属性。</span><span class="sxs-lookup"><span data-stu-id="4de89-113">Click the properties button (**...**) next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="4de89-114">**添加**</span><span class="sxs-lookup"><span data-stu-id="4de89-114">**Add**</span></span>  
 <span data-ttu-id="4de89-115">如果希望允许的服务器没有列出，请单击“添加”向可用发布服务器列表中添加   发布服务器或 Oracle 发布服务器[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4de89-115">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de89-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4de89-116">See Also</span></span>  
 <span data-ttu-id="4de89-117">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="4de89-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="4de89-118">[配置发布和分发](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="4de89-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="4de89-119">[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4de89-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="4de89-120">创建发布</span><span class="sxs-lookup"><span data-stu-id="4de89-120">Create a Publication</span></span>](publish/create-a-publication.md)  
  
  
