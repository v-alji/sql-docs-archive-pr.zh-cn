---
title: 使用 rs.exe 实用工具和 Web 服务编写脚本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Web service [Reporting Services], scripts
- rs utility
- XML Web service [Reporting Services], scripts
- Report Server Web service, scripts
- scripts [Reporting Services], Web service
ms.assetid: 0ec5ac6e-b3cf-49cd-96f6-6b4b7dc29982
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d84bb8722fd31a08ff7788ad31c601b377c23d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587716"
---
# <a name="script-with-the-rsexe-utility-and-the-web-service"></a><span data-ttu-id="d4659-102">使用 rs.exe 实用工具和 Web 服务编写脚本</span><span class="sxs-lookup"><span data-stu-id="d4659-102">Script with the rs.exe Utility and the Web Service</span></span>
  <span data-ttu-id="d4659-103">开发人员和报表服务器管理员可以使用 **rs** 实用工具 (RS.exe) 在报表服务器上执行操作。</span><span class="sxs-lookup"><span data-stu-id="d4659-103">Developers and report server administrators can perform operations on a report server through the use of the **rs** utility (RS.exe).</span></span> <span data-ttu-id="d4659-104">利用此实用工具，可以通过用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]编写的脚本以编程方式管理报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d4659-104">Using this utility, you can programmatically administer a report server using scripts written with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d4659-105">脚本可用来运行任何报表服务器 Web 服务操作。</span><span class="sxs-lookup"><span data-stu-id="d4659-105">scripts can be used to run any of the Report Server Web service operations.</span></span> <span data-ttu-id="d4659-106">使用脚本，可以将安全性复制到服务器上的多个报表，添加和删除项，将报表服务器项从一台服务器复制到另一台服务器，等等。</span><span class="sxs-lookup"><span data-stu-id="d4659-106">Scripting can be used to copy security to multiple reports on a server, to add and delete items, to copy report server items from one server to another and more.</span></span> <span data-ttu-id="d4659-107">有关脚本环境的详细信息，请参阅 [运行 Reporting Services 脚本文件](run-a-reporting-services-script-file.md)。</span><span class="sxs-lookup"><span data-stu-id="d4659-107">For more information about the scripting environment, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md).</span></span> <span data-ttu-id="d4659-108">脚本文件是用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 编写的，并采用特定的格式。</span><span class="sxs-lookup"><span data-stu-id="d4659-108">Script files take a certain format and are written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET.</span></span> <span data-ttu-id="d4659-109">有关详细信息，请参阅 [设置 Reporting Services 脚本文件的格式](format-a-reporting-services-script-file.md)。</span><span class="sxs-lookup"><span data-stu-id="d4659-109">For more information, see [Format a Reporting Services Script File](format-a-reporting-services-script-file.md).</span></span>  
  
 <span data-ttu-id="d4659-110">有关脚本示例，请参阅下面内容：</span><span class="sxs-lookup"><span data-stu-id="d4659-110">For script samples, see the following:</span></span>  
  
 <span data-ttu-id="d4659-111">[用于在报表服务器之间迁移内容的示例 Reporting Services rs.exe 脚本](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="d4659-111">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="d4659-112">[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="d4659-112">[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4659-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4659-113">See Also</span></span>  
 <span data-ttu-id="d4659-114">[为部署和管理任务编写脚本](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d4659-114">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="d4659-115">[报表服务器 Web 服务](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="d4659-115">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="d4659-116">[技术参考 (SSRS)](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d4659-116">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="d4659-117">RS.exe 实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d4659-117">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
