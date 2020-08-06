---
title: 用于运行脚本的 Oracle 凭据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 683b313e5b1065c3709c4637ddf968641612cc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683001"
---
# <a name="oracle-credentials-for-running-script"></a><span data-ttu-id="6c685-102">Oracle Credentials for Running Script</span><span class="sxs-lookup"><span data-stu-id="6c685-102">Oracle Credentials for Running Script</span></span>
  <span data-ttu-id="6c685-103">若要从 Oracle CDC 设计器控制台运行 Oracle 补充日志记录脚本，程序将提示您输入正运行该脚本的 Oracle 用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="6c685-103">To run the Oracle supplemental logging script from the Oracle CDC Designer console, the program prompts you for the credentials of the Oracle user who is running the script.</span></span> <span data-ttu-id="6c685-104">若要运行该脚本，Oracle 用户必须对要捕获的所有表具有 ALTER TABLE 权限，并且对 DBA_LOG_GROUPS 视图具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="6c685-104">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="6c685-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="6c685-105">Task List</span></span>  
 <span data-ttu-id="6c685-106">在此对话框中输入以下信息：</span><span class="sxs-lookup"><span data-stu-id="6c685-106">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="6c685-107">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="6c685-107">**Authentication**</span></span>  
  
 <span data-ttu-id="6c685-108">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="6c685-108">Select one of the following:</span></span>  
  
-   <span data-ttu-id="6c685-109">**Windows 身份验证**：选择此选项可使用当前的 Windows 域凭据。</span><span class="sxs-lookup"><span data-stu-id="6c685-109">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="6c685-110">只有当 Oracle 数据库配置为使用 Windows 身份验证时，才可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="6c685-110">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="6c685-111">**Oracle 身份验证**：如果选择此选项，则必须在您连接到的源 Oracle 数据库中为用户键入 **“用户名”** 和 **“密码”** 。</span><span class="sxs-lookup"><span data-stu-id="6c685-111">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Source Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c685-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c685-112">See Also</span></span>  
 <span data-ttu-id="6c685-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="6c685-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="6c685-114">查看和生成补充日志记录脚本</span><span class="sxs-lookup"><span data-stu-id="6c685-114">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
