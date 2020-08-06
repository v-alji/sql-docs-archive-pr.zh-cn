---
title: 更改故障转移群集实例的 IP 地址 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45d3ef0b70282efd870e4a076663719c2549deaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586272"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a><span data-ttu-id="a9ce8-102">更改故障转移群集实例的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="a9ce8-102">Change the IP Address of a Failover Cluster Instance</span></span>
  <span data-ttu-id="a9ce8-103">本主题说明如何使用故障转移群集管理器管理单元更改 AlwaysOn 故障转移群集实例 (FCI) 中的 IP 地址资源。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-103">This topic describes how to change the IP address resource in an AlwaysOn Failover Cluster Instance (FCI) by using the Failover Cluster Manager snap-in.</span></span> <span data-ttu-id="a9ce8-104">故障转移群集管理器管理单元是用于 Windows Server 故障转移群集 (WSFC) 服务的群集管理应用程序。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Server Failover Clustering (WSFC) service.</span></span>  
  
-   <span data-ttu-id="a9ce8-105">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="a9ce8-105">**Before you begin:**  [Security](#Security)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a9ce8-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="a9ce8-106">Before You Begin</span></span>  
 <span data-ttu-id="a9ce8-107">在开始之前，请查看以下 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书主题︰ [安装故障转移群集前的准备工作](../install/before-installing-failover-clustering.md)。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-107">Before you begin, review the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online topic: [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a9ce8-108">Security</span><span class="sxs-lookup"><span data-stu-id="a9ce8-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a9ce8-109">权限</span><span class="sxs-lookup"><span data-stu-id="a9ce8-109">Permissions</span></span>  
 <span data-ttu-id="a9ce8-110">若要维护或更新 FCI，您必须在 FCI 的所有节点上是拥有“作为服务登录”权限的本地管理员。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-110">To maintain or update an FCI, you must be a local administrator with permission to logon as a service on all nodes of the FCI.</span></span>  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="a9ce8-111">使用故障转移群集管理器管理单元</span><span class="sxs-lookup"><span data-stu-id="a9ce8-111">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="a9ce8-112">**更改 FCI 的 IP 地址资源**</span><span class="sxs-lookup"><span data-stu-id="a9ce8-112">**To change the IP address resource for an FCI**</span></span>  
  
1.  <span data-ttu-id="a9ce8-113">打开故障转移群集管理器管理单元。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-113">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="a9ce8-114">在左窗格中展开 **“服务和应用程序”** 节点，然后单击 FCI。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-114">Expand the **Services and applications** node, in the left pane and click on the FCI.</span></span>  
  
3.  <span data-ttu-id="a9ce8-115">在右窗格的\*\*\*\*“服务器名称”类别下，右键单击该 SQL Server 实例，然后选择\*\*\*\*“属性”选项以打开\*\*\*\*“属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-115">On the right pane, under the **Server Name** category, right-click the SQL Server Instance, and select **Properties** option to open the **Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="a9ce8-116">在 **“常规”** 选项卡上更改 IP 地址资源。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-116">On the **General** tab, change the IP address resource.</span></span>  
  
5.  <span data-ttu-id="a9ce8-117">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-117">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="a9ce8-118">在右侧窗格中，右键单击“SQL IP Address1”（故障转移群集实例名称）并选择\*\*\*\*“脱机”。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-118">In the right-hand pane, right-click the SQL IP Address1(failover cluster instance name) and select **Take Offline**.</span></span> <span data-ttu-id="a9ce8-119">将会看到 SQL IP Address1（故障转移群集实例名称）、SQL Network Name（故障转移群集实例名称）和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的状态从联机更改为脱机挂起，然后再更改为脱机。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-119">You will see the SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name), and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] status change from Online to Offline Pending, and then to Offline.</span></span>  
  
7.  <span data-ttu-id="a9ce8-120">在右侧窗格中，右键单击 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，然后选择\*\*\*\*“联机”。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-120">In the right-hand pane, right-click [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and then select **Bring Online**.</span></span> <span data-ttu-id="a9ce8-121">将会看到 SQL IP Address1（故障转移群集实例名称）、SQL Network Name（故障转移群集实例名称）和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的状态从脱机更改为联机挂起，然后再更改为联机。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-121">You will see the SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name), and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] status change from Offline to Online Pending, and then to Online.</span></span>  
  
8.  <span data-ttu-id="a9ce8-122">关闭故障转移群集管理器管理单元。</span><span class="sxs-lookup"><span data-stu-id="a9ce8-122">Close the Failover Cluster Manager snap-in.</span></span>  
  
  
