---
title: 结束域管理活动 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c776674a369bfae8c7da6fa0deabfbd932029570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689596"
---
# <a name="end-the-domain-management-activity"></a><span data-ttu-id="49dde-102">结束域管理活动</span><span class="sxs-lookup"><span data-stu-id="49dde-102">End the Domain Management Activity</span></span>
  <span data-ttu-id="49dde-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中完成、关闭或取消域管理活动。</span><span class="sxs-lookup"><span data-stu-id="49dde-103">This topic describes how to complete, close, or cancel the domain management activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="49dde-104">由于向导不执行域管理，因此，可以从域管理活动的任意页面中使用下面描述的控件。</span><span class="sxs-lookup"><span data-stu-id="49dde-104">Domain management is not performed by a wizard, so the controls described below can used from any of the pages of the domain management activity.</span></span>  
  
## <a name="end-domain-management"></a><span data-ttu-id="49dde-105">结束域管理</span><span class="sxs-lookup"><span data-stu-id="49dde-105">End Domain Management</span></span>  
 <span data-ttu-id="49dde-106">**“完成”**</span><span class="sxs-lookup"><span data-stu-id="49dde-106">**Finish**</span></span>  
 <span data-ttu-id="49dde-107">单击可完成域管理。</span><span class="sxs-lookup"><span data-stu-id="49dde-107">Click to complete domain management.</span></span> <span data-ttu-id="49dde-108">将显示一个弹出窗口，支持您执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="49dde-108">A popup will be displayed enabling you to do the following:</span></span>  
  
-   <span data-ttu-id="49dde-109">**是 - 发布知识库并退出**：将发布该知识库，以供当前用户或他人使用。</span><span class="sxs-lookup"><span data-stu-id="49dde-109">**Yes - Publish the knowledge base and exit**: The knowledge base will be published for the current user or others to use.</span></span> <span data-ttu-id="49dde-110">将不锁定该知识库，该知识库（在知识库表中）的状态将设置为空，且域管理和知识发现活动都将可用。</span><span class="sxs-lookup"><span data-stu-id="49dde-110">The knowledge base will not be locked, the state of the knowledge base (in the knowledge base table) will be set to empty, and both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="49dde-111">您将返回到“打开知识库”屏幕。</span><span class="sxs-lookup"><span data-stu-id="49dde-111">You will be returned to the Open Knowledge Base screen.</span></span>  
  
-   <span data-ttu-id="49dde-112">**否-保存对知识库所做的工作并退出**：将保存您的工作，该知识库将保持锁定状态，且该知识库的状态将设置为 "正在工作"。</span><span class="sxs-lookup"><span data-stu-id="49dde-112">**No - Save the work on the knowledge base and exit**: Your work will be saved, the knowledge base will remained locked, and the state of the knowledge base will be set to In work.</span></span> <span data-ttu-id="49dde-113">域管理和知识发现活动都将可用。</span><span class="sxs-lookup"><span data-stu-id="49dde-113">Both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="49dde-114">您将返回到主页。</span><span class="sxs-lookup"><span data-stu-id="49dde-114">You will be returned to the home page.</span></span>  
  
-   <span data-ttu-id="49dde-115">**取消-停留在当前屏幕上**：弹出窗口将关闭，你将返回到域管理屏幕。</span><span class="sxs-lookup"><span data-stu-id="49dde-115">**Cancel - Stay on the current screen**: The popup will be closed and you will be returned to the Domain Management screen.</span></span>  
  
 <span data-ttu-id="49dde-116">**取消**</span><span class="sxs-lookup"><span data-stu-id="49dde-116">**Cancel**</span></span>  
 <span data-ttu-id="49dde-117">单击可终止域管理活动，不保存所做的工作，并返回到 DQS 主页。</span><span class="sxs-lookup"><span data-stu-id="49dde-117">Click to terminate the Domain Management activity, losing your work, and return to the DQS home page.</span></span>  
  
 <span data-ttu-id="49dde-118">**关闭**</span><span class="sxs-lookup"><span data-stu-id="49dde-118">**Close**</span></span>  
 <span data-ttu-id="49dde-119">单击可保存所做的工作，并返回到 DQS 主页。</span><span class="sxs-lookup"><span data-stu-id="49dde-119">Click to save your work, and return to the DQS home page.</span></span> <span data-ttu-id="49dde-120">知识库将被锁定，且该知识库在 **“打开知识库”** 屏幕的知识库表中的状态将为 **“域管理”**。</span><span class="sxs-lookup"><span data-stu-id="49dde-120">The knowledge base will be locked, and the state of the knowledge base in the knowledge base table in the **Open Knowledge Base** screen will be **Domain Management**.</span></span> <span data-ttu-id="49dde-121">单击 **“关闭”** 后，若要执行知识发现活动，您必须返回 **“域管理”** 屏幕，单击 **“完成”**，然后单击 **“是”** 发布该知识库，或单击 **“否”** 保存对该知识库所做的工作并退出。</span><span class="sxs-lookup"><span data-stu-id="49dde-121">After clicking **Close**, to perform the Knowledge Discovery activity, you would have to return to the **Domain Management** screen, click **Finish**, and then click either **Yes** to publish the knowledge base or **No** to save the work on the knowledge base and exit.</span></span>  <span data-ttu-id="49dde-122">有关打开锁定的知识库的详细信息，请参阅 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="49dde-122">For more information on opening a locked knowledge base, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
  
