---
title: 生成和运行补充日志记录脚本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1437a4b0f790376268095d8e52afa981af865b44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683024"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a><span data-ttu-id="465f7-102">生成和运行补充日志记录脚本</span><span class="sxs-lookup"><span data-stu-id="465f7-102">Generate and Run the Supplemental Logging Script</span></span>
  <span data-ttu-id="465f7-103">使用“为捕获变更设置表”页可对 Oracle 源数据库运行一个将设置补充日志记录的脚本。</span><span class="sxs-lookup"><span data-stu-id="465f7-103">Use the Set up Tables for Capturing Changes page to run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
 <span data-ttu-id="465f7-104">**运行补充日志记录脚本**</span><span class="sxs-lookup"><span data-stu-id="465f7-104">**To run the supplemental logging scripts**</span></span>  
  
 <span data-ttu-id="465f7-105">单击 **“运行脚本”** 可对为 CDC 实例定义的表运行补充日志记录脚本。</span><span class="sxs-lookup"><span data-stu-id="465f7-105">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="465f7-106">此脚本指示 Oracle 数据库在将 UPDATE 操作记录到捕获表时将有关的所有列写入其事务日志。</span><span class="sxs-lookup"><span data-stu-id="465f7-106">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="465f7-107">此脚本通常由 Oracle 系统管理员检查和执行。</span><span class="sxs-lookup"><span data-stu-id="465f7-107">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
 <span data-ttu-id="465f7-108">您还可以使用 SQL \* Plus 手动运行脚本。</span><span class="sxs-lookup"><span data-stu-id="465f7-108">You can also run the scripts manually using SQL \* Plus.</span></span>  
  
 <span data-ttu-id="465f7-109">**手动运行脚本**</span><span class="sxs-lookup"><span data-stu-id="465f7-109">**To run the scripts manually**</span></span>  
  
 <span data-ttu-id="465f7-110">单击 **“复制”** 将脚本粘贴到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="465f7-110">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="465f7-111">打开 SQL\* Plus 并且转到具有您的 Oracle 源数据库的目录。</span><span class="sxs-lookup"><span data-stu-id="465f7-111">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="465f7-112">将脚本粘贴到 SQL\*Plus 中，以便运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="465f7-112">Paste the script into SQL\*Plus to run it.</span></span>  
  
 <span data-ttu-id="465f7-113">若要在文本文件中保存补充日志记录脚本，请单击 **“另存为”** 并且浏览到要保存该文件的位置。</span><span class="sxs-lookup"><span data-stu-id="465f7-113">To save the supplemental logging script in a text file, click **Save as** and browse to the location where you want to save the file.</span></span> <span data-ttu-id="465f7-114">为该文件提供一个名称，然后单击 **“保存”** 以便保存该文件。</span><span class="sxs-lookup"><span data-stu-id="465f7-114">Give the file a name and click **Save** to save the file.</span></span>  
  
 <span data-ttu-id="465f7-115">单击 **“下一步”** 以便 [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="465f7-115">Click **Next** to [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465f7-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="465f7-116">See Also</span></span>  
 <span data-ttu-id="465f7-117">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="465f7-117">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="465f7-118">查看和生成补充日志记录脚本</span><span class="sxs-lookup"><span data-stu-id="465f7-118">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
