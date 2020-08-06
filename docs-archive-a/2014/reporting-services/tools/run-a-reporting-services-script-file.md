---
title: 运行 Reporting Services 脚本文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c787d860838a57a2bd0f51aac1e9159833f038d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691562"
---
# <a name="run-a-reporting-services-script-file"></a><span data-ttu-id="46ae9-102">运行 Reporting Services 脚本文件</span><span class="sxs-lookup"><span data-stu-id="46ae9-102">Run a Reporting Services Script File</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="46ae9-103">使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 脚本环境 (RS.exe) 从命令提示符处运行脚本文件。</span><span class="sxs-lookup"><span data-stu-id="46ae9-103">script files are run from the command prompt using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment (RS.exe).</span></span> <span data-ttu-id="46ae9-104">RS.exe 有许多可供使用的命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="46ae9-104">RS.exe has many command prompt arguments available for you to use.</span></span> <span data-ttu-id="46ae9-105">有关命令提示符选项的详细信息，请参阅 [RS.exe 实用工具 (SSRS)](rs-exe-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="46ae9-105">For more information about the command prompt options, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span> <span data-ttu-id="46ae9-106">有关更多脚本示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="46ae9-106">For more script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="sample-command-lines"></a><span data-ttu-id="46ae9-107">示例命令行</span><span class="sxs-lookup"><span data-stu-id="46ae9-107">Sample Command Lines</span></span>  
  
-   <span data-ttu-id="46ae9-108">在指定目标报表服务器的脚本环境中运行 Script.rss。</span><span class="sxs-lookup"><span data-stu-id="46ae9-108">Run Script.rss in the script environment designating the target report server.</span></span> <span data-ttu-id="46ae9-109">默认情况下会应用 Windows 身份验证：</span><span class="sxs-lookup"><span data-stu-id="46ae9-109">Windows Authentication is applied by default:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   <span data-ttu-id="46ae9-110">在指定用来对 Web 服务调用进行身份验证的用户名和密码的脚本环境中运行 Script.rss：</span><span class="sxs-lookup"><span data-stu-id="46ae9-110">Run Script.rss in the script environment specifying a user name and password for authenticating the Web service calls:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   <span data-ttu-id="46ae9-111">在将服务器超时值指定为 30 秒的脚本环境中运行 Script.rss：</span><span class="sxs-lookup"><span data-stu-id="46ae9-111">Run Script.rss in the script environment specifying a server time-out of 30 seconds:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   <span data-ttu-id="46ae9-112">在指定名为 *report*的全局脚本变量的脚本环境中运行 Script.rss。</span><span class="sxs-lookup"><span data-stu-id="46ae9-112">Run Script.rss in the script environment specifying a global script variable called *report*.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   <span data-ttu-id="46ae9-113">在指定以批处理方式运行脚本文件中的 Web 服务操作的脚本环境中运行 Script.rss。</span><span class="sxs-lookup"><span data-stu-id="46ae9-113">Run Script.rss in the script environment specifying that the Web service operations in the script file are run as a batch.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="46ae9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46ae9-114">See Also</span></span>  
 [<span data-ttu-id="46ae9-115">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="46ae9-115">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
