---
title: " (SSAS) 连接到报表或数据馈送 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connreportdatafeed.f1
ms.assetid: e0ccfb0b-e646-4de8-b7da-f88c986c96e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76dd51c32d13e64b0368267ba7ac66aa6d76a784
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579206"
---
# <a name="connect-to-a-report-or-data-feed-ssas"></a><span data-ttu-id="7b088-102">连接到报表或数据馈送 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="7b088-102">Connect to a Report or Data Feed (SSAS)</span></span>
  <span data-ttu-id="7b088-103">**“表导入向导”** 的这一页可用于连接到数据馈送。</span><span class="sxs-lookup"><span data-stu-id="7b088-103">This page of the **Table Import Wizard** enables you to connect to a data feed.</span></span> <span data-ttu-id="7b088-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="7b088-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="from-a-report"></a><span data-ttu-id="7b088-105">从报表</span><span class="sxs-lookup"><span data-stu-id="7b088-105">From a Report</span></span>  
 <span data-ttu-id="7b088-106">**友好连接名称**</span><span class="sxs-lookup"><span data-stu-id="7b088-106">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="7b088-107">键入数据馈送连接的友好名称。</span><span class="sxs-lookup"><span data-stu-id="7b088-107">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="7b088-108">**报表路径**</span><span class="sxs-lookup"><span data-stu-id="7b088-108">**Report Path**</span></span>  
 <span data-ttu-id="7b088-109">列出生成数据馈送的 SQL Server Reporting Services 报表的 URL。</span><span class="sxs-lookup"><span data-stu-id="7b088-109">Lists the URL for a SQL Server Reporting Services report that generates data feeds.</span></span> <span data-ttu-id="7b088-110">单击 **“浏览”** 可以指定报表的 URL。</span><span class="sxs-lookup"><span data-stu-id="7b088-110">Click **Browse** to specify the URL for the report.</span></span>  
  
 <span data-ttu-id="7b088-111">单击“查看报告”\*\*\*\* 以显示报告。</span><span class="sxs-lookup"><span data-stu-id="7b088-111">Click **View Report** to display the report.</span></span>  
  
 <span data-ttu-id="7b088-112">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="7b088-112">**Browse**</span></span>  
 <span data-ttu-id="7b088-113">导航至报表所在的位置。</span><span class="sxs-lookup"><span data-stu-id="7b088-113">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="7b088-114">**高级**</span><span class="sxs-lookup"><span data-stu-id="7b088-114">**Advanced**</span></span>  
 <span data-ttu-id="7b088-115">通过使用“设置高级属性”\*\*\*\* 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="7b088-115">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="7b088-116">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="7b088-116">**Test Connection**</span></span>  
 <span data-ttu-id="7b088-117">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="7b088-117">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="7b088-118">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="7b088-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-an-azure-datamarket-dataset"></a><span data-ttu-id="7b088-119">从 Azure DataMarket 数据集</span><span class="sxs-lookup"><span data-stu-id="7b088-119">From an Azure DataMarket Dataset</span></span>  
 <span data-ttu-id="7b088-120">**友好连接名称**</span><span class="sxs-lookup"><span data-stu-id="7b088-120">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="7b088-121">键入数据馈送连接的友好名称。</span><span class="sxs-lookup"><span data-stu-id="7b088-121">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="7b088-122">**数据馈送 URL**</span><span class="sxs-lookup"><span data-stu-id="7b088-122">**Data Feed URL**</span></span>  
 <span data-ttu-id="7b088-123">键入 Atom 服务文档（.atomsvc、.atom）的完整路径或者键入单个数据馈送的 URL，或者单击“浏览”\*\*\*\* 以便选择某一 Atom 服务文档。</span><span class="sxs-lookup"><span data-stu-id="7b088-123">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="7b088-124">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="7b088-124">**Browse**</span></span>  
 <span data-ttu-id="7b088-125">导航至报表所在的位置。</span><span class="sxs-lookup"><span data-stu-id="7b088-125">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="7b088-126">单击 **“查看可用的 Azure DataMarket 数据集”** 可显示可用数据集。</span><span class="sxs-lookup"><span data-stu-id="7b088-126">Click **View available Azure DataMarket datasets** to display available datasets.</span></span>  
  
 <span data-ttu-id="7b088-127">**帐户密钥**</span><span class="sxs-lookup"><span data-stu-id="7b088-127">**Account key**</span></span>  
 <span data-ttu-id="7b088-128">指定用于访问 Azure Marketplace 数据集订阅的帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="7b088-128">Specify the account key used to access your Azure Marketplace dataset subscriptions.</span></span>  
  
 <span data-ttu-id="7b088-129">**查找**</span><span class="sxs-lookup"><span data-stu-id="7b088-129">**Find**</span></span>  
 <span data-ttu-id="7b088-130">查找与 Windows Live 帐户关联的帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="7b088-130">Locate an account key associated with a Windows Live account.</span></span>  
  
 <span data-ttu-id="7b088-131">**保存我的帐户密钥**</span><span class="sxs-lookup"><span data-stu-id="7b088-131">**Save my account key**</span></span>  
 <span data-ttu-id="7b088-132">使用数据连接保存帐户密钥（已加密）。</span><span class="sxs-lookup"><span data-stu-id="7b088-132">Saves the account key (encrypted) with the data connection.</span></span>  
  
 <span data-ttu-id="7b088-133">**高级**</span><span class="sxs-lookup"><span data-stu-id="7b088-133">**Advanced**</span></span>  
 <span data-ttu-id="7b088-134">通过使用“设置高级属性”\*\*\*\* 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="7b088-134">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="7b088-135">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="7b088-135">**Test Connection**</span></span>  
 <span data-ttu-id="7b088-136">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="7b088-136">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="7b088-137">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="7b088-137">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-other-feeds"></a><span data-ttu-id="7b088-138">从其他馈送</span><span class="sxs-lookup"><span data-stu-id="7b088-138">From Other Feeds</span></span>  
 <span data-ttu-id="7b088-139">**友好连接名称**</span><span class="sxs-lookup"><span data-stu-id="7b088-139">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="7b088-140">键入数据馈送连接的友好名称。</span><span class="sxs-lookup"><span data-stu-id="7b088-140">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="7b088-141">**数据馈送 URL**</span><span class="sxs-lookup"><span data-stu-id="7b088-141">**Data Feed URL**</span></span>  
 <span data-ttu-id="7b088-142">键入 Atom 服务文档（.atomsvc、.atom）的完整路径或者键入单个数据馈送的 URL，或者单击“浏览”\*\*\*\* 以便选择某一 Atom 服务文档。</span><span class="sxs-lookup"><span data-stu-id="7b088-142">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="7b088-143">单击 **“包括所有馈送列”** 可以指定是否导入所有数据馈送列。</span><span class="sxs-lookup"><span data-stu-id="7b088-143">Click **Include all feed columns** to specify whether all the data feed columns are imported.</span></span>  
  
 <span data-ttu-id="7b088-144">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="7b088-144">**Browse**</span></span>  
 <span data-ttu-id="7b088-145">导航至数据馈送所在的位置。</span><span class="sxs-lookup"><span data-stu-id="7b088-145">Navigate to a location where a data feed is available.</span></span>  
  
 <span data-ttu-id="7b088-146">**高级**</span><span class="sxs-lookup"><span data-stu-id="7b088-146">**Advanced**</span></span>  
 <span data-ttu-id="7b088-147">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="7b088-147">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="7b088-148">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="7b088-148">**Test Connection**</span></span>  
 <span data-ttu-id="7b088-149">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="7b088-149">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="7b088-150">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="7b088-150">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
