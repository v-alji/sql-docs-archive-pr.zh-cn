---
title: 任务9：配置引用数据服务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1e7c685de13a2f5c495482f816818ff6b838fc7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694160"
---
# <a name="task-9-configuring-a-reference-data-service"></a><span data-ttu-id="1ee98-102">任务 9：配置引用数据服务</span><span class="sxs-lookup"><span data-stu-id="1ee98-102">Task 9: Configuring a Reference Data Service</span></span>
  <span data-ttu-id="1ee98-103">在此任务中，将 DQS 配置为使用 Azure Marketplace 中的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="1ee98-103">In this task, you configure DQS to use a Reference Data Service on Azure Marketplace.</span></span> <span data-ttu-id="1ee98-104">在下一任务中，将配置**地址验证**域以使用此服务。</span><span class="sxs-lookup"><span data-stu-id="1ee98-104">In the next task, you will configure the **Address Validation** domain to use this service.</span></span> <span data-ttu-id="1ee98-105">在运行时，在清理活动期间，DQS 会将**地址验证**域中的域的值传递到服务进行清理。</span><span class="sxs-lookup"><span data-stu-id="1ee98-105">At runtime, during cleansing activity, DQS passes the values of domains in the **Address Validation** domain to the service for cleansing.</span></span> <span data-ttu-id="1ee98-106">有关更多详细信息，请参阅[配置 DQS 以使用引用数据](https://msdn.microsoft.com/library/hh213070.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1ee98-106">See [Configure DQS to Use Reference Data](https://msdn.microsoft.com/library/hh213070.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="1ee98-107">在**DQS 客户端**的主页中，在 "**管理**" 窗格中单击 "**配置**"。</span><span class="sxs-lookup"><span data-stu-id="1ee98-107">In the main page of **DQS Client**, in the **Administration** pane, click **Configuration**.</span></span>  
  
2.  <span data-ttu-id="1ee98-108">确保 "**引用数据**" 选项卡处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="1ee98-108">Ensure that **Reference Data** tab is active.</span></span>  
  
3.  <span data-ttu-id="1ee98-109">如果需要使用代理服务器连接到 Internet，请在 "**网络设置**" 区域中的 "**代理服务器**" 和 "**端口**" 字段中键入相应的值。</span><span class="sxs-lookup"><span data-stu-id="1ee98-109">In the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** fields if you need to use a proxy server to connect to Internet.</span></span>  
  
4.  <span data-ttu-id="1ee98-110">键入 " **DataMarket 帐户 ID** " 字段的**Azure Marketplace 帐户密钥**。</span><span class="sxs-lookup"><span data-stu-id="1ee98-110">Type your **Azure Marketplace Account Key** for the **DataMarket Account ID** field.</span></span>  
  
     <span data-ttu-id="1ee98-111">![Azure Data Market 引用数据服务帐户](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market 引用数据服务帐户")</span><span class="sxs-lookup"><span data-stu-id="1ee98-111">![Azure Data Market Reference Data Service Account](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market Reference Data Service Account")</span></span>  
  
5.  <span data-ttu-id="1ee98-112">单击文本框旁边的 "**验证**" 按钮以验证帐户 ID。</span><span class="sxs-lookup"><span data-stu-id="1ee98-112">Click **Validate** button next to the text box to validate the account ID.</span></span>  
  
6.  <span data-ttu-id="1ee98-113">在消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="1ee98-113">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="1ee98-114">单击页面底部的 "**关闭**" 以切换到 DQS 客户端的主页。</span><span class="sxs-lookup"><span data-stu-id="1ee98-114">Click **Close** at the bottom of the page to switch to the main page of DQS Client.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="1ee98-115">下一个任务</span><span class="sxs-lookup"><span data-stu-id="1ee98-115">Next Task</span></span>  
 [<span data-ttu-id="1ee98-116">任务 10：配置复合域以使用引用数据服务</span><span class="sxs-lookup"><span data-stu-id="1ee98-116">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
