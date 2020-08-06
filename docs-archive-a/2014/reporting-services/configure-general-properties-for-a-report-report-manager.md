---
title: 配置报表的常规属性 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f30900158591afcd5997053dbb61cc22b495ed10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692797"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a><span data-ttu-id="3db8e-102">配置报表的常规属性（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="3db8e-102">Configure General Properties for a Report (Report Manager)</span></span>
  
### <a name="to-configure-general-report-properties"></a><span data-ttu-id="3db8e-103">配置常规报表属性</span><span class="sxs-lookup"><span data-stu-id="3db8e-103">To configure general report properties</span></span>

1.  <span data-ttu-id="3db8e-104">启动 [报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="3db8e-104">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>

2.  <span data-ttu-id="3db8e-105">在报表管理器中，导航到 "**内容**" 页。</span><span class="sxs-lookup"><span data-stu-id="3db8e-105">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="3db8e-106">导航到要配置常规属性的报表，并打开该报表。</span><span class="sxs-lookup"><span data-stu-id="3db8e-106">Navigate to the report that you want to configure general properties for and open it.</span></span>

3.  <span data-ttu-id="3db8e-107">单击“属性”选项卡。</span><span class="sxs-lookup"><span data-stu-id="3db8e-107">Click the **Properties** tab.</span></span>

     <span data-ttu-id="3db8e-108">或者，如果 "**内容**" 页在详细信息视图中，请单击属性页图标：</span><span class="sxs-lookup"><span data-stu-id="3db8e-108">Or, if the **Contents** page is in Details view, click the property page icon:</span></span>

     <span data-ttu-id="3db8e-109">![属性页图标](media/prop.gif "属性页图标")</span><span class="sxs-lookup"><span data-stu-id="3db8e-109">![Property page icon](media/prop.gif "Property page icon")</span></span>

4.  <span data-ttu-id="3db8e-110">将显示 "**常规**属性" 页，您可以按如下所示配置属性：</span><span class="sxs-lookup"><span data-stu-id="3db8e-110">The **General** properties page is displayed, and you can configure properties as follows:</span></span>

    -   <span data-ttu-id="3db8e-111">在 "**属性**" 部分中，可以修改报表名称和说明。</span><span class="sxs-lookup"><span data-stu-id="3db8e-111">In the **Properties** section, you can modify the report name and description.</span></span>

    -   <span data-ttu-id="3db8e-112">可以选中 "**在列表视图中隐藏**" 复选框，以便在默认页面布局中打开页面时隐藏项 (列表视图) ，在页面上和下排列项。</span><span class="sxs-lookup"><span data-stu-id="3db8e-112">You can select the **Hide in list view** checkbox to hide the item when the page is opened in the default page layout (list view) which arranges items across and down the page.</span></span>

    -   <span data-ttu-id="3db8e-113">在 "**报表定义**" 部分中，单击 "**编辑**" 以提取报表定义的副本。</span><span class="sxs-lookup"><span data-stu-id="3db8e-113">In the **Report Definition** section, click **Edit** to extract a copy of the report definition.</span></span> <span data-ttu-id="3db8e-114">在本地对报表定义所做的修改不保存在报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="3db8e-114">Modifications that you make locally to the report definition are not saved on the report server.</span></span>

         <span data-ttu-id="3db8e-115">或者，若要从 .rdl 文件中更新报表定义，请单击 "**更新**"。</span><span class="sxs-lookup"><span data-stu-id="3db8e-115">Or, to update the report definition from an .rdl file, click **Update**.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="3db8e-116">如果更新某一报表定义，则必须在更新完成后重置数据源设置。</span><span class="sxs-lookup"><span data-stu-id="3db8e-116">If you update a report definition, you must reset the data source settings after the update is completed.</span></span>

    -   <span data-ttu-id="3db8e-117">使用 "**删除**" 或 "**移动**" 按钮删除或移动报表。</span><span class="sxs-lookup"><span data-stu-id="3db8e-117">Use the **Delete** or **Move** buttons to delete or move the report.</span></span>

    -   <span data-ttu-id="3db8e-118">还可以创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="3db8e-118">You can also create a linked report.</span></span>

5.  <span data-ttu-id="3db8e-119">完成报表的常规属性配置后，单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="3db8e-119">When you have finished configuring general properties for the report, click **Apply**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3db8e-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3db8e-120">See Also</span></span>
 <span data-ttu-id="3db8e-121">[&#40;报表管理器&#41;内容 "页中移动或删除项](report-server/move-or-delete-an-item-report-manager.md) [&#40;报表管理器](../../2014/reporting-services/contents-page-report-manager.md)&#41;&#40;和 SSRS 报表生成器"[常规属性 "页，报表 &#41;&#40;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)报表管理器&#41;[查找、查看和管理报表](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="3db8e-121">[Move or Delete an Item &#40;Report Manager&#41;](report-server/move-or-delete-an-item-report-manager.md) [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)</span></span>


