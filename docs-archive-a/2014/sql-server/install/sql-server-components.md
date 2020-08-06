---
title: SQL Server 组件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95fe39ce8e616b238cf7c70763e7cf1819341f16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694228"
---
# <a name="sql-server-components"></a><span data-ttu-id="3fe6a-102">SQL Server 组件</span><span class="sxs-lookup"><span data-stu-id="3fe6a-102">SQL Server Components</span></span>
  <span data-ttu-id="3fe6a-103">您可以对 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 安装了、、或的本地或远程计算机运行升级顾问分析 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 向导 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-103">You can run the Upgrade Advisor Analysis Wizard against a local or remote computer that has [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installed.</span></span> <span data-ttu-id="3fe6a-104">升级前分析的第一步是确定要分析的计算机和组件。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-104">The first step in the pre-upgrade analysis is to identify the computer and components for analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3fe6a-105">选项</span><span class="sxs-lookup"><span data-stu-id="3fe6a-105">Options</span></span>  
 <span data-ttu-id="3fe6a-106">**计算机名称**</span><span class="sxs-lookup"><span data-stu-id="3fe6a-106">**Computer name**</span></span>  
 <span data-ttu-id="3fe6a-107">指定要分析的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-107">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="3fe6a-108">升级顾问会将 "**服务器名称**" 框填充为本地计算机名称。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-108">Upgrade Advisor populates the **Server name** box with the local computer name.</span></span> <span data-ttu-id="3fe6a-109">也可以使用“.”和“localhost”连接本地计算机。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-109">You can also use "." and "localhost" to connect to the local computer.</span></span>  
  
 <span data-ttu-id="3fe6a-110">若要对其他计算机进行分析，请遵循下列准则：</span><span class="sxs-lookup"><span data-stu-id="3fe6a-110">To analyze a different computer, use the following guidelines:</span></span>  
  
-   <span data-ttu-id="3fe6a-111">若要扫描非群集实例，请输入计算机名。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-111">To scan nonclustered instances, enter the computer name.</span></span>  
  
-   <span data-ttu-id="3fe6a-112">若要扫描群集实例，请输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例的名称。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-112">To scan clustered instances, enter the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
-   <span data-ttu-id="3fe6a-113">若要扫描安装在群集节点上的非群集组件，请输入故障转移群集节点的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-113">To scan nonclustered components that are installed on a node of a cluster, enter the computer name of the failover cluster node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3fe6a-114">切勿包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-114">Do not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="3fe6a-115">可以不指定计算机名称，而指定 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-115">Instead of specifying the computer name, you can specify the IP address.</span></span>  
  
 <span data-ttu-id="3fe6a-116">如果扫描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，则必须指定本地计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-116">If scanning [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must specify the name of the local computer.</span></span> <span data-ttu-id="3fe6a-117">升级顾问仅扫描本地报表服务器。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-117">Upgrade Advisor scans local report servers only.</span></span>  
  
 <span data-ttu-id="3fe6a-118">**Detect**</span><span class="sxs-lookup"><span data-stu-id="3fe6a-118">**Detect**</span></span>  
 <span data-ttu-id="3fe6a-119">"**检测**" 按钮访问指定的计算机并检测要分析的组件：</span><span class="sxs-lookup"><span data-stu-id="3fe6a-119">The **Detect** button accesses the specified computer and detects components to analyze:</span></span>  
  
-   <span data-ttu-id="3fe6a-120">如果要分析远程计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，则必须在远程计算机上启用远程注册表服务。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-120">If you are analyzing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance on a remote computer, you must enable the remote registry services on the remote computer.</span></span>  
  
-   <span data-ttu-id="3fe6a-121">如果在计算机的注册表中发现 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 的实例，将检测到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is detected if an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is found in the computer's registry.</span></span>  
  
-   <span data-ttu-id="3fe6a-122">如果在计算机的注册表中发现 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，将检测到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is detected if an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is found in the computer's registry.</span></span>  
  
-   <span data-ttu-id="3fe6a-123">如果在计算机的注册表中发现 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，将检测到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-123">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is detected if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is found in the computer's registry.</span></span> <span data-ttu-id="3fe6a-124">不过，升级顾问仅扫描本地报表服务器。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-124">However, Upgrade Advisor scans local report servers only.</span></span>  
  
 <span data-ttu-id="3fe6a-125">**组件**</span><span class="sxs-lookup"><span data-stu-id="3fe6a-125">**Components**</span></span>  
 <span data-ttu-id="3fe6a-126">选择要分析的组件。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-126">Select the components to analyze.</span></span> <span data-ttu-id="3fe6a-127">可以单击 "**检测**" 按钮，选择计算机上安装的所有组件。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-127">You can click the **Detect** button to select all the components installed on the computer.</span></span> <span data-ttu-id="3fe6a-128">检测为已安装在计算机上的组件旁边会出现一个复选标记。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-128">A check mark will appear next to the components that are detected as installed on the computer.</span></span> <span data-ttu-id="3fe6a-129">还可以通过选中或清除各个组件旁边的复选框来手动选择所要分析的组件。</span><span class="sxs-lookup"><span data-stu-id="3fe6a-129">You can also manually select the components to analyze by selecting or clearing the check box next to each component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe6a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fe6a-130">See Also</span></span>  
 <span data-ttu-id="3fe6a-131">[使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="3fe6a-131">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="3fe6a-132">升级顾问用户界面参考</span><span class="sxs-lookup"><span data-stu-id="3fe6a-132">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
