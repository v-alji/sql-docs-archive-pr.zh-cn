---
title: 新别名 (别名选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90742e5de3da0cac83c8b18eebba242ddb9a865d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586034"
---
# <a name="new-alias-alias-tab"></a><span data-ttu-id="52d19-102">新建别名（“别名”选项卡）</span><span class="sxs-lookup"><span data-stu-id="52d19-102">New Alias (Alias Tab)</span></span>
  <span data-ttu-id="52d19-103">别名是可用于进行连接的备用名称。</span><span class="sxs-lookup"><span data-stu-id="52d19-103">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="52d19-104">别名封装了连接字符串所必需的元素，并使用用户所选择的名称显示这些元素。</span><span class="sxs-lookup"><span data-stu-id="52d19-104">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="52d19-105">使用“别名 - 新建”对话框中的“别名”页可以指定别名连接字符串的元素。  </span><span class="sxs-lookup"><span data-stu-id="52d19-105">Use the **Alias** page on the **Alias - New** dialog box to specify the elements of the connection string for an alias.</span></span> <span data-ttu-id="52d19-106">若要更改现有别名的连接字符串，请参阅 [<别名> 属性（别名选项卡）](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)。</span><span class="sxs-lookup"><span data-stu-id="52d19-106">To change the connection string of an existing alias, see [&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md).</span></span>  
  
 <span data-ttu-id="52d19-107">无需在 **“属性”** 的所有网格中都填写值。</span><span class="sxs-lookup"><span data-stu-id="52d19-107">All values in the **Properties** grid do not have to be completed.</span></span> <span data-ttu-id="52d19-108">有效组合因所选协议的不同而有所变化。</span><span class="sxs-lookup"><span data-stu-id="52d19-108">Valid combinations vary depending on the protocol selected.</span></span> <span data-ttu-id="52d19-109">请参阅下面列出的有关有效组合示例的主题。</span><span class="sxs-lookup"><span data-stu-id="52d19-109">See the topics listed below for examples of valid combinations.</span></span>  
  
 <span data-ttu-id="52d19-110">**别名**</span><span class="sxs-lookup"><span data-stu-id="52d19-110">**Alias Name**</span></span>  
 <span data-ttu-id="52d19-111">用于引用此连接的名称（别名）。</span><span class="sxs-lookup"><span data-stu-id="52d19-111">The name (alias) that you want to use to refer to this connection.</span></span>  
  
 <span data-ttu-id="52d19-112">**管道名称** / **端口号**</span><span class="sxs-lookup"><span data-stu-id="52d19-112">**Pipe Name** / **Port No**</span></span>  
 <span data-ttu-id="52d19-113">连接字符串的其他元素。</span><span class="sxs-lookup"><span data-stu-id="52d19-113">Additional elements of the connection string.</span></span> <span data-ttu-id="52d19-114">此框的名称随所选协议的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="52d19-114">The name of this box varies with the selected protocol.</span></span>  
  
 <span data-ttu-id="52d19-115">协议 </span><span class="sxs-lookup"><span data-stu-id="52d19-115">**Protocol**</span></span>  
 <span data-ttu-id="52d19-116">连接所用的协议。</span><span class="sxs-lookup"><span data-stu-id="52d19-116">The protocol used for the connection.</span></span>  
  
 <span data-ttu-id="52d19-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="52d19-117">**Server**</span></span>  
 <span data-ttu-id="52d19-118">所连接的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="52d19-118">The name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance being connected to.</span></span>  
  
## <a name="when-to-use-an-alias"></a><span data-ttu-id="52d19-119">何时使用别名</span><span class="sxs-lookup"><span data-stu-id="52d19-119">When to Use an Alias</span></span>  
 <span data-ttu-id="52d19-120">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “共享内存” **协议连接到** 的本地实例，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “TCP/IP” **或** “命名管道” **连接到其他计算机上的**实例。</span><span class="sxs-lookup"><span data-stu-id="52d19-120">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to a local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **Shared Memory** protocol, and to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on another computer using either **TCP/IP** or **Named Pipes**.</span></span> <span data-ttu-id="52d19-121">请在以下情况下创建别名：使用 TCP/IP 或命名管道，并且希望提供自定义连接字符串时；希望使用服务器名称之外的其他名称进行连接时。</span><span class="sxs-lookup"><span data-stu-id="52d19-121">Create an alias when you are using TCP/IP or named pipes, and you want to provide a customized connection string, or when you want to use a name other than the server name for the connection.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52d19-122">示例</span><span class="sxs-lookup"><span data-stu-id="52d19-122">Examples</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="52d19-123">不会侦听默认 TCP/IP 端口 1433，因此你希望提供一个包含另一端口号的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="52d19-123">is not listening on the default TCP/IP port of 1433 so you want to provide a connection string with a different port number.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="52d19-124">不会侦听默认命名管道，因此您希望提供一个包含不同管道名称的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="52d19-124">is not listening on the default named pipe so you want to provide a connection string with a different pipe name.</span></span>  
  
-   <span data-ttu-id="52d19-125">希望将应用程序连接到名为 `ACCT`的服务器上的数据库，但该数据库已合并为名为 `ACCT` 的服务器上的 `CENTRAL`实例。</span><span class="sxs-lookup"><span data-stu-id="52d19-125">An application expects to connect to a database on the server named `ACCT`, but that database has been consolidated as an instance named `ACCT` on a server named `CENTRAL`.</span></span> <span data-ttu-id="52d19-126">该应用程序不能轻易更改。</span><span class="sxs-lookup"><span data-stu-id="52d19-126">The application cannot easily be changed.</span></span> <span data-ttu-id="52d19-127">创建一个别名 `ACCT`，其中包含指向 `CENTRAL\ACCT`的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="52d19-127">Create an alias named `ACCT`, with a connection string pointing to `CENTRAL\ACCT`.</span></span>  
  
## <a name="creating-a-valid-connection-string"></a><span data-ttu-id="52d19-128">创建有效连接字符串</span><span class="sxs-lookup"><span data-stu-id="52d19-128">Creating a Valid Connection String</span></span>  
 <span data-ttu-id="52d19-129">有关别名属性的有效组合的说明和示例，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="52d19-129">See the following topics for a description and examples of valid combinations of alias properties:</span></span>  
  
-   [<span data-ttu-id="52d19-130">使用 Shared Memory 协议创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="52d19-130">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [<span data-ttu-id="52d19-131">使用 TCP IP 创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="52d19-131">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [<span data-ttu-id="52d19-132">使用命名管道创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="52d19-132">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
