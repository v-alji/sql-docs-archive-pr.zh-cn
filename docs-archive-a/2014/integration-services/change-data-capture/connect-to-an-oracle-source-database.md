---
title: 连接到 Oracle 源数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fccba3d11adc67b3f5ef4f8648ec5d0de07a5648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691334"
---
# <a name="connect-to-an-oracle-source-database"></a><span data-ttu-id="d0d75-102">连接到 Oracle 源数据库</span><span class="sxs-lookup"><span data-stu-id="d0d75-102">Connect to an Oracle Source Database</span></span>
  <span data-ttu-id="d0d75-103">使用“Oracle 源”页可提供连接到 Oracle 源数据库所需的信息。</span><span class="sxs-lookup"><span data-stu-id="d0d75-103">Use the Oracle Source page to provide the information necessary to connect to the Oracle source database.</span></span> <span data-ttu-id="d0d75-104">CDC 实例将读取您连接到的 Oracle 数据库的重做日志。</span><span class="sxs-lookup"><span data-stu-id="d0d75-104">The CDC instance will read the redo logs of the Oracle database you are connected to.</span></span>  
  
 <span data-ttu-id="d0d75-105">**Oracle 连接字符串**</span><span class="sxs-lookup"><span data-stu-id="d0d75-105">**Oracle Connect String**</span></span>  
 <span data-ttu-id="d0d75-106">输入正使用 Oracle 数据库的计算机的 Oracle 连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d0d75-106">Enter the Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="d0d75-107">连接字符串按以下方法之一编写：</span><span class="sxs-lookup"><span data-stu-id="d0d75-107">The connect string is written in one of the following ways:</span></span>  
  
 `host[:port][/service name]`  
  
 <span data-ttu-id="d0d75-108">连接字符串还可以指定 Oracle Net 连接描述符，例如 `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span><span class="sxs-lookup"><span data-stu-id="d0d75-108">The connection string can also specify an Oracle Net connect descriptor, for example, `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span></span>  
  
 <span data-ttu-id="d0d75-109">如果使用目录服务器或 tnsnames，则连接字符串可以是连接的名称。</span><span class="sxs-lookup"><span data-stu-id="d0d75-109">If using a directory server or tnsnames, the connect string can be the name of the connection.</span></span>  
  
 <span data-ttu-id="d0d75-110">**Oracle 日志挖掘身份验证**</span><span class="sxs-lookup"><span data-stu-id="d0d75-110">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="d0d75-111">若要输入授权执行日志挖掘的 Oracle 数据库用户的凭据，请选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="d0d75-111">To enter the credentials for the Oracle database user that is authorized for log mining, select one of the following:</span></span>  
  
-   <span data-ttu-id="d0d75-112">**Windows 身份验证**：选择此选项可使用当前的 Windows 域凭据。</span><span class="sxs-lookup"><span data-stu-id="d0d75-112">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="d0d75-113">只有当 Oracle 数据库配置为使用 Windows 身份验证时，才可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="d0d75-113">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="d0d75-114">**Oracle 身份验证**：如果选择此选项，则必须在您连接到的 Oracle 数据库中为用户键入 **“用户名”** 和 **“密码”** 。</span><span class="sxs-lookup"><span data-stu-id="d0d75-114">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0d75-115">用户必须在 Oracle 数据库中被授予以下权限才能成为日志挖掘用户。</span><span class="sxs-lookup"><span data-stu-id="d0d75-115">A user must have the following privileges granted in the Oracle database to be a log-mining user.</span></span>  
> 
>  -   <span data-ttu-id="d0d75-116">SELECT on \<any-captured-table></span><span class="sxs-lookup"><span data-stu-id="d0d75-116">SELECT on \<any-captured-table></span></span>  
> -   <span data-ttu-id="d0d75-117">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="d0d75-117">SELECT ANY TRANSACTION</span></span>  
> -   <span data-ttu-id="d0d75-118">EXECUTE on DBMS LOGMNR</span><span class="sxs-lookup"><span data-stu-id="d0d75-118">EXECUTE on DBMS LOGMNR</span></span>  
> -   <span data-ttu-id="d0d75-119">SELECT on V$LOGMNR CONTENTS</span><span class="sxs-lookup"><span data-stu-id="d0d75-119">SELECT on V$LOGMNR CONTENTS</span></span>  
> -   <span data-ttu-id="d0d75-120">SELECT on V$ARCHIVED LOG</span><span class="sxs-lookup"><span data-stu-id="d0d75-120">SELECT on V$ARCHIVED LOG</span></span>  
> -   <span data-ttu-id="d0d75-121">SELECT on V$LOG</span><span class="sxs-lookup"><span data-stu-id="d0d75-121">SELECT on V$LOG</span></span>  
> -   <span data-ttu-id="d0d75-122">SELECT on V$LOGFILE</span><span class="sxs-lookup"><span data-stu-id="d0d75-122">SELECT on V$LOGFILE</span></span>  
> -   <span data-ttu-id="d0d75-123">SELECT on V$DATABASE</span><span class="sxs-lookup"><span data-stu-id="d0d75-123">SELECT on V$DATABASE</span></span>  
> -   <span data-ttu-id="d0d75-124">SELECT on V$THREAD</span><span class="sxs-lookup"><span data-stu-id="d0d75-124">SELECT on V$THREAD</span></span>  
> -   <span data-ttu-id="d0d75-125">SELECT on ALL INDEXES</span><span class="sxs-lookup"><span data-stu-id="d0d75-125">SELECT on ALL INDEXES</span></span>  
> -   <span data-ttu-id="d0d75-126">SELECT on ALL OBJECTS</span><span class="sxs-lookup"><span data-stu-id="d0d75-126">SELECT on ALL OBJECTS</span></span>  
> -   <span data-ttu-id="d0d75-127">SELECT on DBA OBJECTS</span><span class="sxs-lookup"><span data-stu-id="d0d75-127">SELECT on DBA OBJECTS</span></span>  
> -   <span data-ttu-id="d0d75-128">SELECT on ALL TABLES</span><span class="sxs-lookup"><span data-stu-id="d0d75-128">SELECT on ALL TABLES</span></span>  
> 
>  <span data-ttu-id="d0d75-129">如果无法将上述任何权限授予 V$xxx，则向其授予 V_S$xxx。</span><span class="sxs-lookup"><span data-stu-id="d0d75-129">If any of these privileges cannot be granted to a V$xxx, then grant them to the V_S$xxx.</span></span>  
  
 <span data-ttu-id="d0d75-130">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="d0d75-130">**Test Connection**</span></span>  
 <span data-ttu-id="d0d75-131">单击  “测试连接”可确定是否已建立与具有 Oracle 数据库的远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="d0d75-131">Click **Test Connection** to determine whether you established a connection with the remote computer that has the Oracle database.</span></span> <span data-ttu-id="d0d75-132">将打开一个对话框，通知您连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="d0d75-132">A dialog box opens to inform you whether the connection was successful.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d0d75-133">由于一个已知问题，如果 CDC 设计器未以管理员的身份运行，与 Oracle 源数据库的连接可能会失败。</span><span class="sxs-lookup"><span data-stu-id="d0d75-133">Due to a known issue connection to the Oracle source database may fail if the CDC Designer is not run as an administrator.</span></span> <span data-ttu-id="d0d75-134">如果连接失败，请使用 **“以管理员身份运行”** 选项关闭后重新启动 CDC 设计器。</span><span class="sxs-lookup"><span data-stu-id="d0d75-134">If connection fails, close and restart the CDC Designer using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="d0d75-135">在此页上输入完信息后，单击 **“下一步”** 以便 [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="d0d75-135">After you finish entering information on this page, click **Next** to [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d75-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0d75-136">See Also</span></span>  
 <span data-ttu-id="d0d75-137">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d0d75-137">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="d0d75-138">编辑实例属性</span><span class="sxs-lookup"><span data-stu-id="d0d75-138">Edit Instance Properties</span></span>](edit-instance-properties.md)  
  
  
