---
title: 任务10：配置复合域以使用引用数据服务 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d70966b4cde110540bf5008eda4e3151fe32f28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694191"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a><span data-ttu-id="47d41-102">任务 10：配置复合域以使用引用数据服务</span><span class="sxs-lookup"><span data-stu-id="47d41-102">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>
  <span data-ttu-id="47d41-103">在此任务中，将 "**地址验证**" 复合域配置为使用**Melissa 数据地址检查**服务。</span><span class="sxs-lookup"><span data-stu-id="47d41-103">In this task, you configure the **Address Validation** composite domain to use the **Melissa Data - Address Check** service.</span></span> <span data-ttu-id="47d41-104">在运行时，在清理活动期间，DQS 将“地址验证”域中各域的值传递给此服务以进行清理。</span><span class="sxs-lookup"><span data-stu-id="47d41-104">At runtime, during cleansing activity, DQS passes the values of domains in the Address Validation domain to the service for cleansing.</span></span> <span data-ttu-id="47d41-105">有关更多详细信息，请参阅[将域/复合域映射到引用数据](https://msdn.microsoft.com/library/hh213030.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47d41-105">See [Map Domain/Composite Domain to Reference Data](https://msdn.microsoft.com/library/hh213030.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="47d41-106">在**DQS 客户端**的主页中，单击 "**最新知识库**" 下的 "**供应商 (域管理) **以启动"**域管理**"页。</span><span class="sxs-lookup"><span data-stu-id="47d41-106">In the main page of **DQS Client**, click **Suppliers (Domain Management)** under **Recent Knowledge Bases** to launch the **Domain Management** page.</span></span>  
  
2.  <span data-ttu-id="47d41-107">在**域列表**中选择 "**地址验证**" 复合域。</span><span class="sxs-lookup"><span data-stu-id="47d41-107">Select the **Address Validation** composite domain in the **list of domains**.</span></span>  
  
3.  <span data-ttu-id="47d41-108">在右侧窗格中，切换到 "**引用数据**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="47d41-108">In the right pane, switch to the **Reference Data** tab.</span></span>  
  
     <span data-ttu-id="47d41-109">![“引用数据”选项卡](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "“引用数据”选项卡")</span><span class="sxs-lookup"><span data-stu-id="47d41-109">![Reference Data Tab](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "Reference Data Tab")</span></span>  
  
4.  <span data-ttu-id="47d41-110">单击工具栏上的 "**浏览**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="47d41-110">Click **Browse** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="47d41-111">在 "**联机引用数据提供程序目录**" 对话框中，选中 " **Melissa 数据-地址检查**" 旁边的**复选框**。</span><span class="sxs-lookup"><span data-stu-id="47d41-111">On the **Online Reference Data Providers Catalog** dialog box, select **check box** next to **Melissa Data - Address Check**.</span></span>  
  
     <span data-ttu-id="47d41-112">![选择 Melissa 数据 - 地址检查](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "选择 Melissa 数据 - 地址检查")</span><span class="sxs-lookup"><span data-stu-id="47d41-112">![Select Melissa Data - Address Check](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Select Melissa Data - Address Check")</span></span>  
  
6.  <span data-ttu-id="47d41-113">在右窗格的 "**架构**" 部分中，使用下拉列表将**地址行**域映射到\*\*地址行 (M) \*\* Schema item。</span><span class="sxs-lookup"><span data-stu-id="47d41-113">In the right pane, in the **Schema** section, map **Address Line** domain to the **Address Line (M)** schema item by using the drop-down list.</span></span>  
  
     <span data-ttu-id="47d41-114">![将 RDS 架构项映射到域](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "将 RDS 架构项映射到域")</span><span class="sxs-lookup"><span data-stu-id="47d41-114">![Map RDS Schema Item to Domain](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "Map RDS Schema Item to Domain")</span></span>  
  
7.  <span data-ttu-id="47d41-115">单击工具栏上的 "\*\*添加架构项" ("+) \*\* " 按钮，在列表中创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="47d41-115">Click **Add Schema Entry (+)** button on the toolbar to create an entry in the list.</span></span>  
  
     <span data-ttu-id="47d41-116">![“添加架构项”工具栏按钮](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "“添加架构项”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="47d41-116">![Add Schema Entry Toolbar Button](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Add Schema Entry Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="47d41-117">通过使用下图中所示的下拉列表，映射以下 DQS 域。</span><span class="sxs-lookup"><span data-stu-id="47d41-117">Map the following DQS domains by using the drop-down lists as shown in the following picture.</span></span>  
  
     <span data-ttu-id="47d41-118">![将 RDS 架构项映射到域](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "将 RDS 架构项映射到域")</span><span class="sxs-lookup"><span data-stu-id="47d41-118">![Map RDS Schema Items to Domains](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Map RDS Schema Items to Domains")</span></span>  
  
9. <span data-ttu-id="47d41-119">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="47d41-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="47d41-120">下一步</span><span class="sxs-lookup"><span data-stu-id="47d41-120">Next Step</span></span>  
 [<span data-ttu-id="47d41-121">任务 11：发布知识库</span><span class="sxs-lookup"><span data-stu-id="47d41-121">Task 11: Publishing the Knowledge Base</span></span>](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
