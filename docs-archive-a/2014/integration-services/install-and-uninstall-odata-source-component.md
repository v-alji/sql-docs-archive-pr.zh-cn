---
title: 安装和卸载 OData 源组件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad0a86c6226f408b0495569d0a853dd7340aeca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586889"
---
# <a name="install-and-uninstall-odata-source-component"></a><span data-ttu-id="7aeb2-102">安装和卸载 OData 源组件</span><span class="sxs-lookup"><span data-stu-id="7aeb2-102">Install and Uninstall OData Source Component</span></span>
  <span data-ttu-id="7aeb2-103">本主题提供有关在计算机上安装或删除 OData 源组件的说明。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-103">This topic provides instructions for installing or removing OData Source Component on your computer.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="7aeb2-104">安装</span><span class="sxs-lookup"><span data-stu-id="7aeb2-104">Installation</span></span>  
 <span data-ttu-id="7aeb2-105">OData 源组件要求在计算机上安装以下必备组件。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-105">The OData Source Component requires following prerequisite components to be installed on your computer.</span></span>  
  
-   <span data-ttu-id="7aeb2-106">SQL Server Data Tools（用于设计包）</span><span class="sxs-lookup"><span data-stu-id="7aeb2-106">SQL Server Data Tools (to design packages)</span></span>  
  
-   <span data-ttu-id="7aeb2-107">SQL Server Integration Services（用于在 Visual Studio 外部运行包）</span><span class="sxs-lookup"><span data-stu-id="7aeb2-107">SQL Server Integration Services (to run packages outside Visual Studio)</span></span>  
  
 <span data-ttu-id="7aeb2-108">若要安装 OData 源组件，请下载[SQL Server 2014 功能包](https://go.microsoft.com/fwlink/p/?LinkId=391999)，并运行以下 MSI 文件之一。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-108">To install the OData Source Component, download [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999) and run one of the following MSI files.</span></span>  
  
-   <span data-ttu-id="7aeb2-109">用于 64 位平台的 ODataSourceForSQLServer2014-amd64.msi</span><span class="sxs-lookup"><span data-stu-id="7aeb2-109">ODataSourceForSQLServer2014-amd64.msi for 64bit platforms</span></span>  
  
-   <span data-ttu-id="7aeb2-110">用于 32 位平台的 ODataSourceForSQLServer2014-x86.msi</span><span class="sxs-lookup"><span data-stu-id="7aeb2-110">ODataSourceForSQLServer2014-x86.msi for 32bit platforms</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7aeb2-111">64 位安装程序将同时安装 32 位和 64 位版本的 OData 源组件。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-111">The 64bit installer will install both 32bit and 64bit versions of the OData Source Component.</span></span> <span data-ttu-id="7aeb2-112">如果使用 32 位操作系统，则只需运行 32 位安装程序。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-112">You only need to run the 32bit installer if you are using a 32bit OS.</span></span>  
  
## <a name="uninstallation"></a><span data-ttu-id="7aeb2-113">卸载</span><span class="sxs-lookup"><span data-stu-id="7aeb2-113">Uninstallation</span></span>  
 <span data-ttu-id="7aeb2-114">可以通过 "**程序和功能**" 菜单卸载 OData 源组件。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-114">The OData Source component can be uninstalled from the **Programs and Features** menu.</span></span> <span data-ttu-id="7aeb2-115">\*\* (x64) 项查找 MICROSOFT SQL SERVER SSIS OData 源组件**，并单击 "**卸载\*\*"。</span><span class="sxs-lookup"><span data-stu-id="7aeb2-115">Find the **Microsoft SQL Server SSIS OData Source Component (x64)** entry and click **Uninstall**.</span></span>  
  
  
