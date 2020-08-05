---
title: 安装适用于 1.1 SAP BW 的 Microsoft Connector |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ef96f38054f04e71de72bda0bbb12f8f003ef20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581378"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a><span data-ttu-id="578ce-102">安装 Microsoft Connector for 1.1 SAP BW</span><span class="sxs-lookup"><span data-stu-id="578ce-102">Installing the Microsoft Connector for 1.1 SAP BW</span></span>
  <span data-ttu-id="578ce-103">若要安装 [!INCLUDE[msCoName](../includes/msconame-md.md)] 连接器1.1 以获取 SAP BW 及其文档，请从 SQL Server 功能包网页下载并运行 Windows installer 包。</span><span class="sxs-lookup"><span data-stu-id="578ce-103">To install the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW and its documentation, download and run the Windows installer package from the SQL Server Feature Pack Web page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="578ce-104">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="578ce-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="578ce-105">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="578ce-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="578ce-106">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="578ce-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="578ce-107">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="578ce-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="required-sap-files"></a><span data-ttu-id="578ce-108">必需的 SAP 文件</span><span class="sxs-lookup"><span data-stu-id="578ce-108">Required SAP Files</span></span>  
 <span data-ttu-id="578ce-109">若要为 [!INCLUDE[msCoName](../includes/msconame-md.md)] SAP BW 使用连接器1.1，你不必在本地计算机上安装 Sap 前端软件 (SAP GUI) 。</span><span class="sxs-lookup"><span data-stu-id="578ce-109">To use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, you do not have to install the SAP Front End software (SAP GUI) on the local computer.</span></span>  
  
 <span data-ttu-id="578ce-110">但是，必须将 SAP .NET 连接器文件 librfc32.dll 复制到 Windows 文件夹的系统子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="578ce-110">However you must copy the SAP .NET connector file, librfc32.dll, into the system subfolder in the Windows folder.</span></span> <span data-ttu-id="578ce-111">（通常，此文件夹位置为 **C:\Windows\system32**。）</span><span class="sxs-lookup"><span data-stu-id="578ce-111">(Typically, this folder location is **C:\Windows\system32**.)</span></span>  
  
## <a name="considerations-for-64-bit-computers"></a><span data-ttu-id="578ce-112">针对 64 位计算机的注意事项</span><span class="sxs-lookup"><span data-stu-id="578ce-112">Considerations for 64-bit Computers</span></span>  
 <span data-ttu-id="578ce-113">[!INCLUDE[msCoName](../includes/msconame-md.md)]连接器 1.1 for SAP BW 完全支持64位版本的 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows。</span><span class="sxs-lookup"><span data-stu-id="578ce-113">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW fully supports the 64-bit version of [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="578ce-114">在64位计算机上， [!INCLUDE[msCoName](../includes/msconame-md.md)] 连接器 1.1 for SAP BW 具有以下附加要求：</span><span class="sxs-lookup"><span data-stu-id="578ce-114">On a 64-bit computer, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following additional requirements:</span></span>  
  
-   <span data-ttu-id="578ce-115">若要在任何 64 位 Windows 操作系统上的 64 位模式中运行包，请将 SAP GUI 文件 librfc32.dll 的 64 位版本复制到 Windows 文件夹的 **system32** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="578ce-115">To run packages in 64-bit mode on any 64-bit Windows operating system, copy the 64-bit version of the SAP GUI file, librfc32.dll, into the **system32** folder of the Windows folder.</span></span> <span data-ttu-id="578ce-116">（通常，此文件位置为 **C:\Windows\system32**。）</span><span class="sxs-lookup"><span data-stu-id="578ce-116">(Typically, this file location is **C:\Windows\system32**.)</span></span>  
  
-   <span data-ttu-id="578ce-117">若要在任何 64 位 Windows 操作系统上的 32 位模式中运行包，请将 SAP GUI 文件 librfc32.dll 复制到 Windows 文件夹的 **SysWow64** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="578ce-117">To run packages in 32-bit mode on any 64-bit Windows operating system, copy the SAP GUI file, librfc32.dll, into the **SysWow64** folder of the Windows folder.</span></span> <span data-ttu-id="578ce-118">（通常，此文件夹位置为 **C:\Windows\SysWow64**。）</span><span class="sxs-lookup"><span data-stu-id="578ce-118">(Typically, this folder location is **C:\Windows\SysWow64**.)</span></span>  
  
  
