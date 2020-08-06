---
title: 连接到服务器（“其他连接参数”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5c6a23df6a6b9ea324d54fd270f5aa2269471ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591571"
---
# <a name="connect-to-server-additional-connection-parameters-page"></a><span data-ttu-id="892e9-102">连接到服务器（“其他连接参数”页）</span><span class="sxs-lookup"><span data-stu-id="892e9-102">Connect to Server (Additional Connection Parameters Page)</span></span>
  <span data-ttu-id="892e9-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的“连接到”\*\*\*\* 对话框将最常用的连接字符串值作为选项提供。</span><span class="sxs-lookup"><span data-stu-id="892e9-103">The **Connect to** dialog box of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] presents the most common connection string values as options.</span></span> <span data-ttu-id="892e9-104">使用“其他连接参数”\*\*\*\* 页可以将更多连接参数添加到连接字符串。</span><span class="sxs-lookup"><span data-stu-id="892e9-104">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span>  
  
-   <span data-ttu-id="892e9-105">其他连接参数可以是任一 ODBC 连接参数。</span><span class="sxs-lookup"><span data-stu-id="892e9-105">Additional connection parameters can be any ODBC connection parameter.</span></span>  
  
-   <span data-ttu-id="892e9-106">应以 **;parameter1=value1;parameter2=value2**格式添加其他连接参数。</span><span class="sxs-lookup"><span data-stu-id="892e9-106">Additional connection parameters should be added in the format **;parameter1=value1;parameter2=value2**.</span></span>  
  
-   <span data-ttu-id="892e9-107">使用“其他连接参数”\*\*\*\* 页添加的参数添加到使用“连接到”\*\*\*\* 对话框选项选择的参数中。</span><span class="sxs-lookup"><span data-stu-id="892e9-107">Parameters added using the **Additional Connection Parameters** page are added to the parameters selected using the **Connect to** dialog box options.</span></span>  
  
-   <span data-ttu-id="892e9-108">所提供的各个参数的最后一个实例均覆盖该参数的任何以前的实例。</span><span class="sxs-lookup"><span data-stu-id="892e9-108">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="892e9-109">使用“其他连接参数”\*\*\*\* 页添加的参数跟踪并替换“登录名”\*\*\*\* 或“连接属性”\*\*\*\* 选项卡中提供的参数。</span><span class="sxs-lookup"><span data-stu-id="892e9-109">Parameters added using the **Additional Connection Parameters** page follow and replace the parameters provided in the **Login** or **Connection Properties** tabs.</span></span> <span data-ttu-id="892e9-110">例如，如果“登录名”\*\*\*\* 选项卡给出的“服务器名称”\*\*\*\* 为 **SERVER1**，而“其他连接参数”\*\*\*\* 页包含 **;SERVER=SERVER2**，则会连接到 **SERVER2**。</span><span class="sxs-lookup"><span data-stu-id="892e9-110">For example, if the **Login** tab provides **SERVER1** as the **Server name**, and the **Additional Connection Parameters** page contains **;SERVER=SERVER2**, the connection will be made to **SERVER2**.</span></span>  
  
-   <span data-ttu-id="892e9-111">使用“其他连接参数”\*\*\*\* 页添加的参数始终作为纯文本传递。</span><span class="sxs-lookup"><span data-stu-id="892e9-111">Parameters added using the **Additional Connection Parameters** page are always passed as plain text.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="892e9-112">“其他连接参数”\*\*\*\* 页中不可包括登录凭据和密码。</span><span class="sxs-lookup"><span data-stu-id="892e9-112">Do not include login credentials and passwords in the **Additional Connection Parameters** page.</span></span> <span data-ttu-id="892e9-113">否则，它们将在没有加密的情况下通过网络传递。</span><span class="sxs-lookup"><span data-stu-id="892e9-113">They will not be encrypted when they are passed across the network.</span></span> <span data-ttu-id="892e9-114">请改用“登录名”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="892e9-114">Use the **Login** tab instead.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="892e9-115">任务列表</span><span class="sxs-lookup"><span data-stu-id="892e9-115">Task List</span></span>  
  
### <a name="to-show-the-additional-connection-parameters-page"></a><span data-ttu-id="892e9-116">显示“其他连接参数”页</span><span class="sxs-lookup"><span data-stu-id="892e9-116">To show the Additional Connection Parameters page</span></span>  
  
1.  <span data-ttu-id="892e9-117">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的“查询”\*\*\*\* 菜单上指向“连接”\*\*\*\*，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="892e9-117">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Query** menu, point to **Connection**, and then click **Connect**.</span></span>  
  
2.  <span data-ttu-id="892e9-118">在“连接到”\*\*\*\* 对话框中，单击“选项”\*\*\*\*，然后单击“其他连接参数”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="892e9-118">In the **Connect to** dialog box, click **Options**, and then click the **Additional Connection Parameters** tab.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="892e9-119">示例</span><span class="sxs-lookup"><span data-stu-id="892e9-119">Examples</span></span>  
  
### <a name="example-a-connecting-to-the-database-engine"></a><span data-ttu-id="892e9-120">示例 A：连接到数据库引擎</span><span class="sxs-lookup"><span data-stu-id="892e9-120">Example A: Connecting to the Database Engine</span></span>  
 <span data-ttu-id="892e9-121">若要连接到名为 ACCOUNTING 的服务器上的 [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] 数据库，请在“其他连接参数”\*\*\*\* 页中输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="892e9-121">To connect to the [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] database on a server named ACCOUNTING, enter the following in the **Additional connection parameters** page:</span></span>  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a><span data-ttu-id="892e9-122">示例 B：连接到 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="892e9-122">Example B: Connecting to Analysis Services</span></span>  
 <span data-ttu-id="892e9-123">若要连接到 Analysis Server 并实时（跳过缓存）查询侦听通知的各部分，且将写回超时值设置为 5，则请在“其他连接参数”\*\*\*\* 页中输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="892e9-123">To connect to the Analysis Servers and cause all the partitions listening for notifications to be queried as real time (bypassing caching), and to set the writeback time out value to 5, enter the following in the **Additional connection parameters** page:</span></span>  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  
  
