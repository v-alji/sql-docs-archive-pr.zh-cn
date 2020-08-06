---
title: CDC 设计器控制台简介 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45298179-4ac1-4723-8b3c-56f5926be40a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 888b111790cf3979e9d08a78502d24880fa034b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577767"
---
# <a name="the-cdc-designer-console-introduction"></a><span data-ttu-id="18b5f-102">CDC 设计器控制台简介</span><span class="sxs-lookup"><span data-stu-id="18b5f-102">The CDC Designer Console Introduction</span></span>
  <span data-ttu-id="18b5f-103">本节介绍用于 Change Data Capture Designer for Oracle by Attunity 的安装过程。</span><span class="sxs-lookup"><span data-stu-id="18b5f-103">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="18b5f-104">安装</span><span class="sxs-lookup"><span data-stu-id="18b5f-104">Installation</span></span>  
 <span data-ttu-id="18b5f-105">本节介绍用于 Change Data Capture Designer for Oracle by Attunity 的安装过程。</span><span class="sxs-lookup"><span data-stu-id="18b5f-105">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span> <span data-ttu-id="18b5f-106">若要安装 CDC 设计器控制台，请从 SQL Server 安装媒体中手动运行**AttunityOracleCdcDesigner.msi** 。</span><span class="sxs-lookup"><span data-stu-id="18b5f-106">To install the CDC Designer Console, manually run **AttunityOracleCdcDesigner.msi** from the SQL Server installation media.</span></span>  <span data-ttu-id="18b5f-107">适用于 x86 和 x64 的安装包位于 SQL Server 安装媒体上的 \*\*.\Tools\AttunityCDCOracle \\ \*\*中。</span><span class="sxs-lookup"><span data-stu-id="18b5f-107">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="18b5f-108">支持的 Windows 环境</span><span class="sxs-lookup"><span data-stu-id="18b5f-108">Supported Windows Environments</span></span>  
 <span data-ttu-id="18b5f-109">CDC 设计器控制台可在以下 Windows 环境中运行：</span><span class="sxs-lookup"><span data-stu-id="18b5f-109">The CDC Designer Console can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="18b5f-110">具有 Service Pack 2 的 Windows Vista 32 位 (x86) 和 64 位 (x64)</span><span class="sxs-lookup"><span data-stu-id="18b5f-110">Windows Vista 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
-   <span data-ttu-id="18b5f-111">Windows 7 32 位 (x86) 和 64 位 (x64)</span><span class="sxs-lookup"><span data-stu-id="18b5f-111">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="18b5f-112">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="18b5f-112">Windows Server 2008 R2</span></span>  
  
-   <span data-ttu-id="18b5f-113">具有 Service Pack 2 的 Windows Server 2008 32 位 (x86) 和 64 位 (x64)</span><span class="sxs-lookup"><span data-stu-id="18b5f-113">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="18b5f-114">数据库必备组件</span><span class="sxs-lookup"><span data-stu-id="18b5f-114">Database Prerequisites</span></span>  
 <span data-ttu-id="18b5f-115">若要使用 Change Data Capture Designer for Oracle by Attunity，需使用 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="18b5f-115">To work with the Change Data Capture Designer for Oracle by Attunity, you work with an Oracle database.</span></span> <span data-ttu-id="18b5f-116">Change Data Capture Designer for Oracle by Attunity 支持以下版本：</span><span class="sxs-lookup"><span data-stu-id="18b5f-116">The Change Data Capture Designer for Oracle by Attunity supports the following versions:</span></span>  
  
 <span data-ttu-id="18b5f-117">**Oracle Database**</span><span class="sxs-lookup"><span data-stu-id="18b5f-117">**Oracle Database**</span></span>  
  
-   <span data-ttu-id="18b5f-118">Oracle Database 10g 发行版 2：10.2.0.1-10.2.0.5（修补程序集截至 2010 年 4 月）</span><span class="sxs-lookup"><span data-stu-id="18b5f-118">Oracle Database 10g Release 2: 10.2.0.1-10.2.0.5 (patchset as of April 2010)</span></span>  
  
-   <span data-ttu-id="18b5f-119">Oracle Database 11g 发行版 1：11.1.0.6-11.1.0.7（修补程序集截至 2008 年 9 月）</span><span class="sxs-lookup"><span data-stu-id="18b5f-119">Oracle Database 11g Release 1: 11.1.0.6-11.1.0.7 (patchset as of September 2008)</span></span>  
  
-   <span data-ttu-id="18b5f-120">Oracle Database 11g 发行版 2：11.2.0.1-11.2.0.3（修补程序集截至 2011 年 9 月）</span><span class="sxs-lookup"><span data-stu-id="18b5f-120">Oracle Database 11g Release 2: 11.2.0.1-11.2.0.3 (patchset as of September 2011)</span></span>  
  
 <span data-ttu-id="18b5f-121">**SQL Server 数据库**</span><span class="sxs-lookup"><span data-stu-id="18b5f-121">**SQL Server Database**</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="18b5f-122">版本</span><span class="sxs-lookup"><span data-stu-id="18b5f-122">edition with support for SQL Server CDC</span></span>  
  
## <a name="software-prerequisites"></a><span data-ttu-id="18b5f-123">必备软件</span><span class="sxs-lookup"><span data-stu-id="18b5f-123">Software Prerequisites</span></span>  
 <span data-ttu-id="18b5f-124">以下软件是必需的：</span><span class="sxs-lookup"><span data-stu-id="18b5f-124">The following software is required:</span></span>  
  
-   <span data-ttu-id="18b5f-125">Oracle 8.x 客户端</span><span class="sxs-lookup"><span data-stu-id="18b5f-125">Oracle 10.x client</span></span>  
  
-   <span data-ttu-id="18b5f-126">Oracle 11.x 客户端</span><span class="sxs-lookup"><span data-stu-id="18b5f-126">Oracle 11.x client</span></span>  
  
 <span data-ttu-id="18b5f-127">**注意**：必须根据安装的 Oracle CDC 设计器控制台版本使用此软件的32位或64位版本。</span><span class="sxs-lookup"><span data-stu-id="18b5f-127">**Note**: You must use the 32-bit or 64-bit version of this software according to the version of the Oracle CDC Designer console installed.</span></span>  
  
 <span data-ttu-id="18b5f-128">Oracle CDC 设计器控制台使用 Oracle ODBC 提供程序与源 Oracle 数据库通信。</span><span class="sxs-lookup"><span data-stu-id="18b5f-128">The Oracle CDC Designer Console uses the Oracle ODBC provider to communicate with the source Oracle database.</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="18b5f-129">运行安装程序</span><span class="sxs-lookup"><span data-stu-id="18b5f-129">Running the Installation Program</span></span>  
 <span data-ttu-id="18b5f-130">本节介绍如何安装 CDC 设计器控制台。</span><span class="sxs-lookup"><span data-stu-id="18b5f-130">This section describes how to install the CDC Designer Console.</span></span>  
  
 <span data-ttu-id="18b5f-131">**安装 CDC 设计器控制台**</span><span class="sxs-lookup"><span data-stu-id="18b5f-131">**To install the CDC Designer Console**</span></span>  
  
 <span data-ttu-id="18b5f-132">双击 CDC 设计器控制台安装套件，然后按照安装向导中的指示执行。</span><span class="sxs-lookup"><span data-stu-id="18b5f-132">Double-click the CDC Designer Console installation kit and follow the directions in the installation wizard.</span></span>  
  
## <a name="uninstalling-the-cdc-designer-console"></a><span data-ttu-id="18b5f-133">卸载 CDC 设计器控制台</span><span class="sxs-lookup"><span data-stu-id="18b5f-133">Uninstalling the CDC Designer Console</span></span>  
 <span data-ttu-id="18b5f-134">可使用“控制面板”的“程序和功能”卸载 CDC 设计器控制台。</span><span class="sxs-lookup"><span data-stu-id="18b5f-134">You uninstall the CDC Designer Console using Control Panel, Programs and Features.</span></span>  
  
  
