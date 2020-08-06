---
title: “添加 IP 地址”对话框 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5192e6414b34bee6de09d45a7284f25404235dc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578452"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a><span data-ttu-id="f9315-102">“添加 IP 地址”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f9315-102">Add IP Address Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f9315-103">本 F1 帮助主题介绍“添加 IP 地址”对话框中的选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9315-103">This F1 help topic describes the options of the **Add IP Address** dialog box.</span></span> <span data-ttu-id="f9315-104">可通过 **“新的可用性组侦听器”** 对话框和 \*\*\*\* 或 **的** “指定副本” [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 页的 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] “侦听器” [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]选项卡访问此对话框。</span><span class="sxs-lookup"><span data-stu-id="f9315-104">This dialog box accessed from the **New Availability Group Listener** dialog box and the **Listener** tab of the **Specify Replicas** page of the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9315-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="f9315-105">Prerequisites</span></span>  
 <span data-ttu-id="f9315-106">开始向可用性组侦听器添加子网之前，确保了解每个子网的 IP 地址以及子网掩码（对于 IPv4 地址）。</span><span class="sxs-lookup"><span data-stu-id="f9315-106">Before you begin to add subnets to an availability group listener, ensure that know the IP address for each subnet and, for an IPv4 address, the subnet mask.</span></span>  
  
##  <a name="add-ip-address-options"></a><a name="PageOptions"></a><span data-ttu-id="f9315-107">添加 IP 地址选项</span><span class="sxs-lookup"><span data-stu-id="f9315-107">Add IP Address Options</span></span>  
 <span data-ttu-id="f9315-108">**子网**</span><span class="sxs-lookup"><span data-stu-id="f9315-108">**Subnet**</span></span>  
 <span data-ttu-id="f9315-109">使用下拉列表选择要添加到可用性组侦听器的子网地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-109">Use the drop list to select an address for the subnet that you are adding to the availability group listener.</span></span> <span data-ttu-id="f9315-110">默认情况下，一个子网同时具有 IPv4 地址和 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-110">By default a subnet possesses both an IPv4 address and an IPv6 address.</span></span> <span data-ttu-id="f9315-111">首次使用 **“添加 IP 地址”** 对话框时， **“子网”** 下拉列表将显示承载可用性组副本的每个子网的这两种子网地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-111">The first time you use the **Add IP Address** dialog,  the **Subnet** drop list displays both subnet addresses for each subnet that hosts a replica for the availability group.</span></span> <span data-ttu-id="f9315-112">若要向侦听器添加给定子网，请选择它的子网地址之一。</span><span class="sxs-lookup"><span data-stu-id="f9315-112">To add a given subnet to the listener, select one of its subnet addresses.</span></span>  
  
 <span data-ttu-id="f9315-113">完成 **“添加 IP 地址”** 对话框的操作并单击 **“确定”** 后，可以将所选子网地址添加到该侦听器， **“子网”** 下拉列表会筛选出该子网地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-113">After you complete the **Add IP Address** dialog box and click **OK** to add a selected subnet address to the listener, the **Subnet** drop list filters out that subnet address.</span></span> <span data-ttu-id="f9315-114">所有未选定的子网地址仍保留在下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="f9315-114">All unselected subnet addresses remain on the drop list.</span></span> <span data-ttu-id="f9315-115">确保为每个子网向侦听器仅添加一个子网地址，否则侦听器创建将失败。</span><span class="sxs-lookup"><span data-stu-id="f9315-115">Be sure that you add one and only one subnet address per subnet to the listener, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="f9315-116">**地址**</span><span class="sxs-lookup"><span data-stu-id="f9315-116">**Addresses**</span></span>  
 <span data-ttu-id="f9315-117">使用此字段可为所选子网地址输入一个静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-117">Use this field to enter a static IP address for the selected subnet address.</span></span> <span data-ttu-id="f9315-118">请与您的网络管理员联系以获取此 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-118">Contact your network administrator for this IP address.</span></span> <span data-ttu-id="f9315-119">确保您为所选子网地址输入一个有效的地址，否则侦听器创建将失败。</span><span class="sxs-lookup"><span data-stu-id="f9315-119">Ensure that you enter a valid address for the selected subnet address, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="f9315-120">**IPv4 地址**</span><span class="sxs-lookup"><span data-stu-id="f9315-120">**IPv4 Address**</span></span>  
 <span data-ttu-id="f9315-121">如果您选择了子网的 IPv4 子网地址，请在此输入有效的 IPv4 静态地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-121">If you selected the IPv4 subnet address of a subnet, enter a valid IPv4 static address here.</span></span>  
  
 <span data-ttu-id="f9315-122">**子网掩码**</span><span class="sxs-lookup"><span data-stu-id="f9315-122">**Subnet Mask**</span></span>  
 <span data-ttu-id="f9315-123">对于 IPv4 地址，此只读字段显示所选子网的子网掩码。</span><span class="sxs-lookup"><span data-stu-id="f9315-123">For an IPv4 address, this read-only field displays the subnet mask of the selected subnet.</span></span>  
  
 <span data-ttu-id="f9315-124">**IPv6 地址**</span><span class="sxs-lookup"><span data-stu-id="f9315-124">**IPv6 Address**</span></span>  
 <span data-ttu-id="f9315-125">如果您选择了子网的 IPv6 子网地址，请在此输入有效的 IPv6 静态地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-125">If you selected the IPv6 subnet address of a subnet, enter a valid IPv6 static address here.</span></span>  
  
 <span data-ttu-id="f9315-126">**确定**</span><span class="sxs-lookup"><span data-stu-id="f9315-126">**OK**</span></span>  
 <span data-ttu-id="f9315-127">单击以添加已选定其地址的子网，同时添加您指定的静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-127">Click to create add the subnet whose address you selected, along with the static IP address that you specified.</span></span> <span data-ttu-id="f9315-128">包含这些值的行将添加到 **“新的可用性组侦听器”** 或 **“指定副本”** 对话框的子网网格中。</span><span class="sxs-lookup"><span data-stu-id="f9315-128">A row containing these values will be added to the subnet grid of the **New Availability Group Listener** or **Specify Replicas** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f9315-129">**“添加 IP 地址”** 对话框并不验证该 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-129">The **Add IP Address** dialog does not verify the IP address.</span></span> <span data-ttu-id="f9315-130">该对话框也不会阻止您为已经添加到可用性组侦听器的子网继续添加其他子网地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-130">Also the dialog does not prevent you from adding the second subnet address for a subnet that you have already added to the availability group listener.</span></span>  
  
 <span data-ttu-id="f9315-131">**取消**</span><span class="sxs-lookup"><span data-stu-id="f9315-131">**Cancel**</span></span>  
 <span data-ttu-id="f9315-132">单击以取消所做选择，并返回“新的可用性组侦听程序”\*\*\*\* 对话框或“侦听程序”\*\*\*\* 选项卡，不为任何子网添加静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f9315-132">Click to cancel your selections, and return to the **New Availability Group Listener** dialog box or **Listener** tab without adding a static IP address for any subnet.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f9315-133">相关任务</span><span class="sxs-lookup"><span data-stu-id="f9315-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f9315-134">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f9315-134">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="f9315-135">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f9315-135">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f9315-136">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f9315-136">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="f9315-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9315-137">See Also</span></span>  
 <span data-ttu-id="f9315-138">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f9315-138">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="f9315-139">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="f9315-139">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="f9315-140">AlwaysOn 客户端连接 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f9315-140">AlwaysOn Client Connectivity (SQL Server)</span></span>](always-on-client-connectivity-sql-server.md)  
  
  
