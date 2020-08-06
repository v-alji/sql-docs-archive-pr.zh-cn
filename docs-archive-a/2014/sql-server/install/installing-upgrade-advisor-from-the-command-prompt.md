---
title: 从命令提示符安装升级顾问 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b0c5193f0b235b6d37170992d9d7ca9568b1f675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688447"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a><span data-ttu-id="35626-102">从命令提示符安装升级顾问</span><span class="sxs-lookup"><span data-stu-id="35626-102">Installing Upgrade Advisor from the Command Prompt</span></span>
  <span data-ttu-id="35626-103">您可以使用安装向导或从命令提示符安装升级顾问。</span><span class="sxs-lookup"><span data-stu-id="35626-103">You can install Upgrade Advisor either by using the Setup Wizard or from the command prompt.</span></span> <span data-ttu-id="35626-104">使用命令提示符，可以执行无人参与的自动安装。</span><span class="sxs-lookup"><span data-stu-id="35626-104">By using the command prompt you can perform unattended and automated installations.</span></span>  
  
## <a name="installation-syntax"></a><span data-ttu-id="35626-105">安装语法</span><span class="sxs-lookup"><span data-stu-id="35626-105">Installation Syntax</span></span>  
 <span data-ttu-id="35626-106">从命令提示符安装升级顾问的基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="35626-106">The basic syntax for installing Upgrade Advisor from the command prompt is as follows:</span></span>  
  
 `SQLUA.msi [options]`  
  
 <span data-ttu-id="35626-107">下表列出了最常用的选项。</span><span class="sxs-lookup"><span data-stu-id="35626-107">The following table shows the most common options.</span></span>  
  
|<span data-ttu-id="35626-108">参数</span><span class="sxs-lookup"><span data-stu-id="35626-108">Argument</span></span>|<span data-ttu-id="35626-109">说明</span><span class="sxs-lookup"><span data-stu-id="35626-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="35626-110">/q [n&#124;b&#124;r&#124;f]</span><span class="sxs-lookup"><span data-stu-id="35626-110">/q[n&#124;b&#124;r&#124;f]</span></span>|<span data-ttu-id="35626-111">设置用户界面 (UI) 级别：</span><span class="sxs-lookup"><span data-stu-id="35626-111">Sets user interface (UI) level:</span></span><br /><br /> <span data-ttu-id="35626-112">n = 无 UI</span><span class="sxs-lookup"><span data-stu-id="35626-112">n = no UI</span></span><br /><br /> <span data-ttu-id="35626-113">b = 基本 UI（仅显示进度，不显示提示）</span><span class="sxs-lookup"><span data-stu-id="35626-113">b = basic UI (progress only, no prompts)</span></span><br /><br /> <span data-ttu-id="35626-114">r = 简化的 UI（在安装结束时显示对话框）</span><span class="sxs-lookup"><span data-stu-id="35626-114">r = reduced UI (dialog box at the end of installation)</span></span><br /><br /> <span data-ttu-id="35626-115">f = 完整的 UI</span><span class="sxs-lookup"><span data-stu-id="35626-115">f = full UI</span></span>|  
|<span data-ttu-id="35626-116">/L</span><span class="sxs-lookup"><span data-stu-id="35626-116">/L</span></span>|<span data-ttu-id="35626-117">指定日志文件选项。</span><span class="sxs-lookup"><span data-stu-id="35626-117">Specifies log file options.</span></span> <span data-ttu-id="35626-118">若要将所有消息记录到*log_file_name*，请使用 **-L \* v**_log_file_name_。</span><span class="sxs-lookup"><span data-stu-id="35626-118">To log all messages to *log_file_name*, use **-L\*v**_log_file_name_.</span></span> <span data-ttu-id="35626-119">若要仅记录错误消息，请使用 `-Le` *log_file_name*。</span><span class="sxs-lookup"><span data-stu-id="35626-119">To log error messages only, use `-Le`*log_file_name*.</span></span>|  
|<span data-ttu-id="35626-120">ADDLOCAL = ALL&#124; REMOVE = ALL&#124;重新安装 = 全部</span><span class="sxs-lookup"><span data-stu-id="35626-120">ADDLOCAL=ALL&#124; REMOVE=ALL&#124;REINSTALL=ALL</span></span>|<span data-ttu-id="35626-121">指定安装 (ADDLOCAL)、删除 (REMOVE) 或重新安装 (REINSTALL) 升级顾问。</span><span class="sxs-lookup"><span data-stu-id="35626-121">Specifies to install (ADDLOCAL), remove (REMOVE), or reinstall (REINSTALL) Upgrade Advisor.</span></span>|  
|<span data-ttu-id="35626-122">UAINSTALLDIR=路径</span><span class="sxs-lookup"><span data-stu-id="35626-122">UAINSTALLDIR=path</span></span>|<span data-ttu-id="35626-123">将升级顾问安装到路径指定的位置。</span><span class="sxs-lookup"><span data-stu-id="35626-123">Installs Upgrade Advisor to the location specified by path.</span></span>|  
  
## <a name="installation-examples"></a><span data-ttu-id="35626-124">安装示例</span><span class="sxs-lookup"><span data-stu-id="35626-124">Installation Examples</span></span>  
 <span data-ttu-id="35626-125">下面的示例说明如何使用命令提示符安装升级顾问：</span><span class="sxs-lookup"><span data-stu-id="35626-125">The following example shows how to install Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="35626-126">您也可以在运行此命令时使用 Msiexec 程序：</span><span class="sxs-lookup"><span data-stu-id="35626-126">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="35626-127">如果必须使用其他安装选项，这一方法会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="35626-127">This can be helpful if you have to use additional installation options.</span></span>  
  
## <a name="removal-examples"></a><span data-ttu-id="35626-128">删除示例</span><span class="sxs-lookup"><span data-stu-id="35626-128">Removal Examples</span></span>  
 <span data-ttu-id="35626-129">下面的示例说明如何使用命令提示符删除升级顾问：</span><span class="sxs-lookup"><span data-stu-id="35626-129">The following example shows how to remove Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 <span data-ttu-id="35626-130">您也可以在运行此命令时使用 Msiexec 程序：</span><span class="sxs-lookup"><span data-stu-id="35626-130">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a><span data-ttu-id="35626-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35626-131">See Also</span></span>  
 <span data-ttu-id="35626-132">[安装升级顾问](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="35626-132">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="35626-133">升级顾问必备组件</span><span class="sxs-lookup"><span data-stu-id="35626-133">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
