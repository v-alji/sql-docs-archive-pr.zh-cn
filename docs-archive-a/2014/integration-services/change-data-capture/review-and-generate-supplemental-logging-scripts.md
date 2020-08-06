---
title: 查看和生成补充日志记录脚本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- scripts
ms.assetid: 5c858ae2-37d6-42e8-a252-7f6ed4e628a7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb735c0ee318ac68d48c71c09fc76ec305eb2552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580330"
---
# <a name="review-and-generate-supplemental-logging-scripts"></a><span data-ttu-id="b1094-102">查看和生成补充日志记录脚本</span><span class="sxs-lookup"><span data-stu-id="b1094-102">Review and Generate Supplemental Logging Scripts</span></span>
  <span data-ttu-id="b1094-103">使用“脚本”  选项卡可对 Oracle 源数据库运行或重新运行一个设置补充日志记录的脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-103">Use the **Scripts** tab to run or re-run a script on the Oracle source database that sets up supplemental logging.</span></span>  
  
 <span data-ttu-id="b1094-104">在运行脚本前，请选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="b1094-104">Before you run the scripts select one of the following:</span></span>  
  
 <span data-ttu-id="b1094-105">**包括此会话中的更改**</span><span class="sxs-lookup"><span data-stu-id="b1094-105">**Include changes in this session**</span></span>  
 <span data-ttu-id="b1094-106">选择此选项可对已添加到 CDC 实例的任何新表运行该脚本，或者对使用属性编辑器以任何方式更改的表运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-106">Select this to run the script on any new table that was added to the CDC instance or on tables that were changed in any way using the Properties editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1094-107">如果没有对 CDC 实例中的表进行任何更改，则 Oracle 补充日志记录脚本区域将是空的。</span><span class="sxs-lookup"><span data-stu-id="b1094-107">If no changes were made to the tables in the CDC instance, the Oracle supplemental logging script area will be empty.</span></span>  
  
 <span data-ttu-id="b1094-108">**包括所有表/捕获实例**</span><span class="sxs-lookup"><span data-stu-id="b1094-108">**Include all tables/capture instances**</span></span>  
 <span data-ttu-id="b1094-109">选择此选项可对 CDC 实例中的所有表和捕获实例运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-109">Select this to run the script on all of the tables and capture instances in the CDC instance.</span></span>  
  
 <span data-ttu-id="b1094-110">选择其中一个选项后，运行补充日志记录脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-110">After you select one of these options, run the supplemental logging script.</span></span>  
  
### <a name="to-run-the-supplemental-logging-scripts"></a><span data-ttu-id="b1094-111">运行补充日志记录脚本</span><span class="sxs-lookup"><span data-stu-id="b1094-111">To run the supplemental logging scripts</span></span>  
  
1.  <span data-ttu-id="b1094-112">单击 **“运行脚本”** 可对为 CDC 实例定义的表运行补充日志记录脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-112">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="b1094-113">此脚本指示 Oracle 数据库在将 UPDATE 操作记录到捕获表时将有关的所有列写入其事务日志。</span><span class="sxs-lookup"><span data-stu-id="b1094-113">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="b1094-114">此脚本通常由 Oracle 系统管理员检查和执行。</span><span class="sxs-lookup"><span data-stu-id="b1094-114">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
2.  <span data-ttu-id="b1094-115">在您运行补充日志记录脚本时，“用于运行脚本的 Oracle 凭据”对话框将打开，您可以在其中提供有效的 Oracle 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b1094-115">When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="b1094-116">有关如何提供适当的 Oracle 凭据的信息，请参阅 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)。</span><span class="sxs-lookup"><span data-stu-id="b1094-116">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
 <span data-ttu-id="b1094-117">您还可以根据需要使用 SQL \* Plus 手动运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-117">You can also run the scripts manually using SQL \* Plus, if necessary.</span></span>  
  
### <a name="to-run-the-scripts-manually"></a><span data-ttu-id="b1094-118">手动运行脚本</span><span class="sxs-lookup"><span data-stu-id="b1094-118">To run the scripts manually</span></span>  
  
1.  <span data-ttu-id="b1094-119">单击 **“复制”** 将脚本粘贴到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="b1094-119">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="b1094-120">打开 SQL\* Plus 并且转到具有您的 Oracle 源数据库的目录。</span><span class="sxs-lookup"><span data-stu-id="b1094-120">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="b1094-121">将脚本粘贴到 SQL\*Plus 中，以便运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="b1094-121">Paste the script into SQL\*Plus to run it.</span></span>  
  
### <a name="to-save-the-supplemental-logging-script-in-a-text-file"></a><span data-ttu-id="b1094-122">将补充日志记录脚本保存到一个文本文件中</span><span class="sxs-lookup"><span data-stu-id="b1094-122">To save the supplemental logging script in a text file</span></span>  
  
1.  <span data-ttu-id="b1094-123">单击 **“另存为”** 并且浏览到要保存该文件的位置。</span><span class="sxs-lookup"><span data-stu-id="b1094-123">Click **Save as** and browse to the location where you want to save the file.</span></span>  
  
2.  <span data-ttu-id="b1094-124">为该文件提供一个名称，然后单击 **“保存”** 以便保存该文件。</span><span class="sxs-lookup"><span data-stu-id="b1094-124">Give the file a name and click **Save** to save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1094-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1094-125">See Also</span></span>  
 <span data-ttu-id="b1094-126">[如何编辑 CDC 实例属性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b1094-126">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="b1094-127">用于运行脚本的 Oracle 凭据</span><span class="sxs-lookup"><span data-stu-id="b1094-127">Oracle Credentials for Running Script</span></span>](oracle-credentials-for-running-script.md)  
  
  
