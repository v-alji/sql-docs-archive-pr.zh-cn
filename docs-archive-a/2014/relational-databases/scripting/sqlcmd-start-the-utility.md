---
title: 启动 sqlcmd 实用工具
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: rothja
ms.author: jroth
ms.openlocfilehash: d71e6f140238599b3f22850ee9b63a0ee25d900b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578771"
---
# <a name="start-the-sqlcmd-utility"></a><span data-ttu-id="9f612-102">启动 sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="9f612-102">Start the sqlcmd Utility</span></span>
  <span data-ttu-id="9f612-103">开始使用 `sqlcmd` 之前，必须先启动该实用工具并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的一个实例。</span><span class="sxs-lookup"><span data-stu-id="9f612-103">To begin using `sqlcmd`, you must first launch the utility and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9f612-104">可以连接到默认实例，也可以连接到命名实例。</span><span class="sxs-lookup"><span data-stu-id="9f612-104">You can connect to either a default or named instance.</span></span> <span data-ttu-id="9f612-105">第一步是启动 `sqlcmd` 实用工具。</span><span class="sxs-lookup"><span data-stu-id="9f612-105">The first step is to start the `sqlcmd` utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f612-106">Windows 身份验证是 `sqlcmd` 的默认身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="9f612-106">Windows Authentication is the default authentication mode for `sqlcmd`.</span></span> <span data-ttu-id="9f612-107">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则必须使用 **-U** 和 **-P** 选项指定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="9f612-107">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must specify a user name and password by using the **-U** and **-P** options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f612-108">默认情况下， [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 会安装为命名实例 **sqlexpress**。</span><span class="sxs-lookup"><span data-stu-id="9f612-108">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as the named instance **sqlexpress**.</span></span>  
  
 <span data-ttu-id="9f612-109">如果之前您尚未连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例，则可能需要将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为接受连接。</span><span class="sxs-lookup"><span data-stu-id="9f612-109">If you have not connected to this instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] before, you may have to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a><span data-ttu-id="9f612-110">启动 sqlcmd 实用工具并连接到 SQL Server 的默认实例</span><span class="sxs-lookup"><span data-stu-id="9f612-110">To start the sqlcmd utility and connect to a default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="9f612-111">在 "**开始**" 菜单上单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="9f612-111">On the **Start** menu click **Run**.</span></span> <span data-ttu-id="9f612-112">在 **“打开”** 框中，键入 **cmd**，然后单击 **“确定”** 打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="9f612-112">In the **Open** box type **cmd**, and then click **OK** to open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="9f612-113">在命令提示符处，键入 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="9f612-113">At the command prompt, type `sqlcmd`.</span></span>  
  
3.  <span data-ttu-id="9f612-114">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="9f612-114">Press ENTER.</span></span>  
  
     <span data-ttu-id="9f612-115">现在，您已与计算机上运行的默认 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例建立了可信连接。</span><span class="sxs-lookup"><span data-stu-id="9f612-115">You now have a trusted connection to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on your computer.</span></span>  
  
     <span data-ttu-id="9f612-116">**1>** 是 `sqlcmd` 指定行号的提示。</span><span class="sxs-lookup"><span data-stu-id="9f612-116">**1>** is the `sqlcmd` prompt that specifies the line number.</span></span> <span data-ttu-id="9f612-117">每按一次 Enter，该数字就会加 1。</span><span class="sxs-lookup"><span data-stu-id="9f612-117">Each time you press ENTER, the number increases by one.</span></span>  
  
4.  <span data-ttu-id="9f612-118">若要结束 `sqlcmd` 会话，请 `EXIT` 在 `sqlcmd` 提示符下键入。</span><span class="sxs-lookup"><span data-stu-id="9f612-118">To end the `sqlcmd` session, type `EXIT` at the `sqlcmd` prompt.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="9f612-119">启动 sqlcmd 实用工具并连接到的命名实例 SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f612-119">To start the sqlcmd utility and connect to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="9f612-120">打开 "命令提示符" 窗口，然后键入 " `sqlcmd -S` *myServer\instanceName*"。</span><span class="sxs-lookup"><span data-stu-id="9f612-120">Open a Command Prompt window, and type `sqlcmd -S`*myServer\instanceName*.</span></span> <span data-ttu-id="9f612-121">使用计算机名称和要连接的 *的实例替换* myServer\instanceName [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9f612-121">Replace *myServer\instanceName* with the name of the computer and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to.</span></span>  
  
2.  <span data-ttu-id="9f612-122">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="9f612-122">Press ENTER.</span></span>  
  
     <span data-ttu-id="9f612-123">`sqlcmd`提示符 (1>) 指示你已连接到的指定实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9f612-123">The `sqlcmd` prompt (1>) indicates that you are connected to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9f612-124">输入的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句存储在缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="9f612-124">Entered [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are stored in a buffer.</span></span> <span data-ttu-id="9f612-125">在遇到 GO 命令时，它们将作为批处理命令执行。</span><span class="sxs-lookup"><span data-stu-id="9f612-125">They are executed as a batch when the GO command is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f612-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f612-126">See Also</span></span>  
 [<span data-ttu-id="9f612-127">使用 sqlcmd 运行 Transact-SQL 脚本文件</span><span class="sxs-lookup"><span data-stu-id="9f612-127">Run Transact-SQL Script Files Using sqlcmd</span></span>](sqlcmd-run-transact-sql-script-files.md)  
  
  
