---
title: 连接到 Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6546e3bbde666107ed7757c41d98d5b7b598924
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692492"
---
# <a name="connect-to-oracle"></a><span data-ttu-id="5b0d5-102">连接到 Oracle</span><span class="sxs-lookup"><span data-stu-id="5b0d5-102">Connect to Oracle</span></span>
  <span data-ttu-id="5b0d5-103">在您首次添加或编辑在 CDC 实例中使用的表时，系统可能会请求您连接到 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="5b0d5-103">When you add or edit the tables used in the CDC instance for the first time, you may be asked to connect to the Oracle database.</span></span> <span data-ttu-id="5b0d5-104">您应该输入可访问要捕获表的架构的 Oracle 用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="5b0d5-104">You should enter the credentials of an Oracle user who can access the schema of the tables to be captured.</span></span> <span data-ttu-id="5b0d5-105">在此对话框中输入以下信息：</span><span class="sxs-lookup"><span data-stu-id="5b0d5-105">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="5b0d5-106">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="5b0d5-106">**Authentication**</span></span>  
  
 <span data-ttu-id="5b0d5-107">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="5b0d5-107">Select one of the following:</span></span>  
  
-   <span data-ttu-id="5b0d5-108">**Windows 身份验证**：选择此选项可使用当前的 Windows 域凭据。</span><span class="sxs-lookup"><span data-stu-id="5b0d5-108">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="5b0d5-109">只有当 Oracle 数据库配置为使用 Windows 身份验证时，才可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="5b0d5-109">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="5b0d5-110">**Oracle 身份验证**：如果选择此选项，则必须在您连接到的 Oracle 数据库中为用户键入 **“用户名”** 和 **“密码”** 。</span><span class="sxs-lookup"><span data-stu-id="5b0d5-110">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0d5-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b0d5-111">See Also</span></span>  
 [<span data-ttu-id="5b0d5-112">将表添加到 CDC 实例</span><span class="sxs-lookup"><span data-stu-id="5b0d5-112">Add Tables to a CDC Instance</span></span>](add-tables-to-a-cdc-instance.md)  
  
  
