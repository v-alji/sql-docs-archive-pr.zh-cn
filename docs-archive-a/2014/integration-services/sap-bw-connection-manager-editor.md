---
title: SAP BW 连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 527af979fc9c92062f24e1fe161b93e88ed4ab4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688989"
---
# <a name="sap-bw-connection-manager-editor"></a><span data-ttu-id="e362d-102">SAP BW 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="e362d-102">SAP BW Connection Manager Editor</span></span>
  <span data-ttu-id="e362d-103">使用 **“SAP BW 连接管理器编辑器”** 指定用于连接 SAP Netweaver BW 版本 7 系统的属性。</span><span class="sxs-lookup"><span data-stu-id="e362d-103">Use the **SAP BW Connection Manager Editor** to specify the properties to use to connect to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="e362d-104">SAP BW 连接管理器向 SAP BW 源或目标提供与 SAP Netweaver BW 7 系统的连接。</span><span class="sxs-lookup"><span data-stu-id="e362d-104">The SAP BW connection manager provides connectivity to an SAP Netweaver BW 7 system for use by the SAP BW source or destination.</span></span> <span data-ttu-id="e362d-105">若要了解 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 连接管理器的详细信息，请参阅 [SAP BW 连接管理器](connection-manager/sap-bw-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e362d-105">To learn more about the SAP BW connection manager of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Connection Manager](connection-manager/sap-bw-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e362d-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="e362d-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="e362d-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="e362d-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="e362d-108">**打开“SAP BW 连接管理器编辑器”**</span><span class="sxs-lookup"><span data-stu-id="e362d-108">**To open the SAP BW Connection Manager Editor**</span></span>  
  
1.  <span data-ttu-id="e362d-109">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 连接管理器的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e362d-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that contains the SAP BW connection manager.</span></span>  
  
2.  <span data-ttu-id="e362d-110">在 **“控制流”** 选项卡上的“连接管理器”区域中执行以下步骤之一：</span><span class="sxs-lookup"><span data-stu-id="e362d-110">In the Connection Managers area on the **Control Flow** tab, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="e362d-111">双击 SAP BW 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e362d-111">Double-click the SAP BW connection manager.</span></span>  
  
         <span data-ttu-id="e362d-112">- 或 -</span><span class="sxs-lookup"><span data-stu-id="e362d-112">-or-</span></span>  
  
    -   <span data-ttu-id="e362d-113">右键单击 SAP BW 连接管理器，然后选择“编辑”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e362d-113">Right-click the SAP BW connection manager, and then select **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e362d-114">选项</span><span class="sxs-lookup"><span data-stu-id="e362d-114">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e362d-115">如果您不知道配置连接管理器所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="e362d-115">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="e362d-116">**客户端**</span><span class="sxs-lookup"><span data-stu-id="e362d-116">**Client**</span></span>  
 <span data-ttu-id="e362d-117">指定系统的客户端编号。</span><span class="sxs-lookup"><span data-stu-id="e362d-117">Specify the client number of the system.</span></span>  
  
 <span data-ttu-id="e362d-118">**语言**</span><span class="sxs-lookup"><span data-stu-id="e362d-118">**Language**</span></span>  
 <span data-ttu-id="e362d-119">指定系统使用的语言。</span><span class="sxs-lookup"><span data-stu-id="e362d-119">Specify the language that the system uses.</span></span> <span data-ttu-id="e362d-120">例如，指定 **“EN”** 表示英语。</span><span class="sxs-lookup"><span data-stu-id="e362d-120">For example, specify **EN** for English.</span></span>  
  
 <span data-ttu-id="e362d-121">**用户名**</span><span class="sxs-lookup"><span data-stu-id="e362d-121">**User name**</span></span>  
 <span data-ttu-id="e362d-122">指定将用于连接到系统的用户名。</span><span class="sxs-lookup"><span data-stu-id="e362d-122">Specify the user name that will be used to connect to the system.</span></span>  
  
 <span data-ttu-id="e362d-123">**密码**</span><span class="sxs-lookup"><span data-stu-id="e362d-123">**Password**</span></span>  
 <span data-ttu-id="e362d-124">指定将与该用户名一起使用的密码。</span><span class="sxs-lookup"><span data-stu-id="e362d-124">Specify the password that will be used with the user name.</span></span>  
  
 <span data-ttu-id="e362d-125">**使用单一应用程序服务器**</span><span class="sxs-lookup"><span data-stu-id="e362d-125">**Use single application server**</span></span>  
 <span data-ttu-id="e362d-126">连接到单一应用程序服务器。</span><span class="sxs-lookup"><span data-stu-id="e362d-126">Connect to a single application server.</span></span>  
  
 <span data-ttu-id="e362d-127">若要连接到一组负载平衡的服务器，请改用“使用负载平衡”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="e362d-127">To connect to a group of load-balanced servers, use the **Use load balancing** option instead.</span></span>  
  
 <span data-ttu-id="e362d-128">**主机**</span><span class="sxs-lookup"><span data-stu-id="e362d-128">**Host**</span></span>  
 <span data-ttu-id="e362d-129">如果连接到单一应用程序服务器，请指定主机名。</span><span class="sxs-lookup"><span data-stu-id="e362d-129">If connecting to a single application server, specify the host name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e362d-130"> 只有在已选择 **“使用单一应用程序服务器”** 选项的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="e362d-130">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="e362d-131">**系统编号**</span><span class="sxs-lookup"><span data-stu-id="e362d-131">**System number**</span></span>  
 <span data-ttu-id="e362d-132">如果连接到单一应用程序服务器，请指定系统编号。</span><span class="sxs-lookup"><span data-stu-id="e362d-132">If connecting to a single application server, specify the system number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e362d-133"> 只有在已选择 **“使用单一应用程序服务器”** 选项的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="e362d-133">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="e362d-134">**使用负载平衡**</span><span class="sxs-lookup"><span data-stu-id="e362d-134">**Use load balancing**</span></span>  
 <span data-ttu-id="e362d-135">连接到一组负载平衡的服务器。</span><span class="sxs-lookup"><span data-stu-id="e362d-135">Connect to a group of load-balanced servers.</span></span>  
  
 <span data-ttu-id="e362d-136">要连接单一应用程序服务器，请使用 **“使用单一应用程序服务器”** 选项。</span><span class="sxs-lookup"><span data-stu-id="e362d-136">To connect to a single application server, use the **Use single application server** option instead.</span></span>  
  
 <span data-ttu-id="e362d-137">**消息服务器**</span><span class="sxs-lookup"><span data-stu-id="e362d-137">**Message server**</span></span>  
 <span data-ttu-id="e362d-138">要连接一组负载平衡的服务器，请指定消息服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e362d-138">If connecting to a group of load-balanced servers, specify the name of the message server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e362d-139">只有在已选择“使用负载平衡”选项的情况下，此选项才可用。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e362d-139">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="e362d-140">**组**</span><span class="sxs-lookup"><span data-stu-id="e362d-140">**Group**</span></span>  
 <span data-ttu-id="e362d-141">要连接一组负载平衡的服务器，请指定服务器组名称。</span><span class="sxs-lookup"><span data-stu-id="e362d-141">If connecting to a group of load-balanced servers, specify the name of the server group name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e362d-142">只有在已选择“使用负载平衡”选项的情况下，此选项才可用。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e362d-142">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="e362d-143">**SID**</span><span class="sxs-lookup"><span data-stu-id="e362d-143">**SID**</span></span>  
 <span data-ttu-id="e362d-144">要连接一组负载平衡的服务器，请指定连接的“系统 ID”。</span><span class="sxs-lookup"><span data-stu-id="e362d-144">If connecting to a group of load-balanced servers, specify the System ID for the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e362d-145">只有在已选择“使用负载平衡”选项的情况下，此选项才可用。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e362d-145">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="e362d-146">**日志目录**</span><span class="sxs-lookup"><span data-stu-id="e362d-146">**Log directory**</span></span>  
 <span data-ttu-id="e362d-147">启用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW 组件的日志记录。</span><span class="sxs-lookup"><span data-stu-id="e362d-147">Enable logging for the components of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 <span data-ttu-id="e362d-148">要启用日志记录，请指定一个目录用来存储每次 RFC 函数调用前后创建的日志文件。</span><span class="sxs-lookup"><span data-stu-id="e362d-148">To enable logging, specify a directory for the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="e362d-149">（此日志记录功能会创建许多个 XML 格式的日志文件。</span><span class="sxs-lookup"><span data-stu-id="e362d-149">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="e362d-150">这些日志文件还包含传输的所有数据行，因此可能会消耗大量的磁盘空间。）</span><span class="sxs-lookup"><span data-stu-id="e362d-150">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e362d-151">如果传输的数据包含敏感信息，日志文件中也会包含该敏感信息。</span><span class="sxs-lookup"><span data-stu-id="e362d-151">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
 <span data-ttu-id="e362d-152">要指定日志目录，您可以手动输入目录路径，也可以单击 **“浏览”** 并浏览到要使用的日志目录。</span><span class="sxs-lookup"><span data-stu-id="e362d-152">To specify the log directory, you can either enter the directory path manually, or click **Browse** and browse to the log directory.</span></span>  
  
 <span data-ttu-id="e362d-153">如果不选择日志目录，则不启用日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="e362d-153">If you do not select a log directory, logging is not enabled.</span></span>  
  
 <span data-ttu-id="e362d-154">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="e362d-154">**Browse**</span></span>  
 <span data-ttu-id="e362d-155">浏览以选择一个用作日志目录的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e362d-155">Browse to select a folder for the log directory.</span></span>  
  
 <span data-ttu-id="e362d-156">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="e362d-156">**Test Connection**</span></span>  
 <span data-ttu-id="e362d-157">使用您提供的值来测试连接。</span><span class="sxs-lookup"><span data-stu-id="e362d-157">Test the connection using the values that you have provided.</span></span> <span data-ttu-id="e362d-158">单击 **“测试连接”** 后，将显示一个消息框，指示连接成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="e362d-158">After clicking **Test Connection**, a message box appears and indicates whether the connection succeeded or failed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e362d-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e362d-159">See Also</span></span>  
 [<span data-ttu-id="e362d-160">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="e362d-160">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
  
  
