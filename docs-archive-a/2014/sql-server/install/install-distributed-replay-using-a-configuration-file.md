---
title: 使用配置文件安装 Distributed Replay |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7757cce29c2e6b3ce4f1e91fc97cbf8be02ae521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691522"
---
# <a name="install-distributed-replay-using-a-configuration-file"></a><span data-ttu-id="02064-102">使用配置文件安装 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="02064-102">Install Distributed Replay Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="02064-103">安装程序提供基于用户输入和系统默认值生成配置文件的功能。</span><span class="sxs-lookup"><span data-stu-id="02064-103">Setup provides the ability to generate a configuration file based on user input and system defaults.</span></span> <span data-ttu-id="02064-104">如果您指定要安装管理工具，则可以使用配置文件来部署三个 Distributed Replay 组件（管理工具、Distributed Replay 控制器和 Distributed Replay 客户端）。</span><span class="sxs-lookup"><span data-stu-id="02064-104">If you specify that you want the Management tools installed, you can use the configuration file to deploy the three Distributed Replay components (administration tool, Distributed Replay controller, and the Distributed Replay client).</span></span> <span data-ttu-id="02064-105">它支持安装、修复和卸载 Distributed Replay 组件。</span><span class="sxs-lookup"><span data-stu-id="02064-105">It supports Installing, repairing, and uninstalling of the Distributed Replay components.</span></span>  
  
 <span data-ttu-id="02064-106">安装程序仅支持通过命令行使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="02064-106">Setup supports the use of the configuration file only through the command-line.</span></span> <span data-ttu-id="02064-107">下面列出了在使用配置文件时参数的处理顺序：</span><span class="sxs-lookup"><span data-stu-id="02064-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="02064-108">配置文件覆盖包中的默认值</span><span class="sxs-lookup"><span data-stu-id="02064-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="02064-109">命令行的值覆盖配置文件中的值</span><span class="sxs-lookup"><span data-stu-id="02064-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="02064-110">有关如何使用配置文件的详细信息，请参阅[使用配置文件安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="02064-110">For more information about how to use a configuration file, see [Install SQL Server 2014 Using a Configuration File](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="02064-111">安装 Distributed Replay 之后，您必须在控制器和客户端计算机上创建防火墙规则，并授予每台客户端计算机对目标服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="02064-111">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="02064-112">有关详细信息，请参阅 [完成安装后步骤](../../tools/distributed-replay/complete-the-post-installation-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="02064-112">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
### <a name="to-generate-a-configuration-file"></a><span data-ttu-id="02064-113">生成配置文件</span><span class="sxs-lookup"><span data-stu-id="02064-113">To generate a configuration file</span></span>  
  
1.  <span data-ttu-id="02064-114">按照安装向导的说明操作，直到出现 **“准备安装”** 页面。</span><span class="sxs-lookup"><span data-stu-id="02064-114">Follow the Setup wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="02064-115">配置文件的路径是在 **“准备安装”** 页的配置文件路径部分中指定的。</span><span class="sxs-lookup"><span data-stu-id="02064-115">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span>  
  
2.  <span data-ttu-id="02064-116">取消安装并且不要真正完成安装，以便生成 INI 文件。</span><span class="sxs-lookup"><span data-stu-id="02064-116">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
### <a name="to-install-distributed-replay-using-the-configuration-file"></a><span data-ttu-id="02064-117">使用配置文件安装 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="02064-117">To Install Distributed Replay Using the Configuration File</span></span>  
  
-   <span data-ttu-id="02064-118">通过命令提示符运行安装并使用 ConfigurationFile 参数提供 ConfigurationFile.ini。</span><span class="sxs-lookup"><span data-stu-id="02064-118">Run the installation through the command prompt and supply the ConfigurationFile.ini using the ConfigurationFile parameter.</span></span>  
  
 <span data-ttu-id="02064-119">**示例语法**</span><span class="sxs-lookup"><span data-stu-id="02064-119">**Sample Syntax**</span></span>  
  
 <span data-ttu-id="02064-120">下面是如何在命令提示符处指定配置文件的示例：</span><span class="sxs-lookup"><span data-stu-id="02064-120">Following is an example on how to specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  <span data-ttu-id="02064-121">您必须在命令行中指定这两个密码，因为您无法在配置文件中配置这些密码。</span><span class="sxs-lookup"><span data-stu-id="02064-121">You must specify both passwords in the command line because you cannot configure them in the configuration file.</span></span>  
  
  
