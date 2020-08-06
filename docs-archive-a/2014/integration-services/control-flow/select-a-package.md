---
title: 选择包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b35276791b004a011a1c2656057046be05ed6770
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576921"
---
# <a name="select-a-package"></a><span data-ttu-id="21f79-102">选择包</span><span class="sxs-lookup"><span data-stu-id="21f79-102">Select a Package</span></span>
  <span data-ttu-id="21f79-103">可以使用 **“选择包”** 对话框，指定消息队列任务可从中接收消息的包。</span><span class="sxs-lookup"><span data-stu-id="21f79-103">Use the **Select a Package** dialog box to specify the package from which the Message Queue task can receive messages.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="21f79-104">静态选项</span><span class="sxs-lookup"><span data-stu-id="21f79-104">Static Options</span></span>  
 <span data-ttu-id="21f79-105">**位置**</span><span class="sxs-lookup"><span data-stu-id="21f79-105">**Location**</span></span>  
 <span data-ttu-id="21f79-106">指定包的位置。</span><span class="sxs-lookup"><span data-stu-id="21f79-106">Specify the location of the package.</span></span> <span data-ttu-id="21f79-107">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="21f79-107">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="21f79-108">值</span><span class="sxs-lookup"><span data-stu-id="21f79-108">Value</span></span>|<span data-ttu-id="21f79-109">说明</span><span class="sxs-lookup"><span data-stu-id="21f79-109">Description</span></span>|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<span data-ttu-id="21f79-110">将位置设置为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="21f79-110">Set the location to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="21f79-111">选择此值将显示以下动态选项： **Server**、 **Use Windows Authentication**、 **Use SQL Server Authentication**、 **User name**和 **Password**。</span><span class="sxs-lookup"><span data-stu-id="21f79-111">Selecting this value displays the dynamic options, **Server**, **Use Windows Authentication**, **Use SQL Server Authentication**, **User name**, and **Password**.</span></span>|  
|<span data-ttu-id="21f79-112">DTSX 文件</span><span class="sxs-lookup"><span data-stu-id="21f79-112">DTSX file</span></span>|<span data-ttu-id="21f79-113">将位置设置为 DTSX 文件。</span><span class="sxs-lookup"><span data-stu-id="21f79-113">Set the location to a DTSX file.</span></span> <span data-ttu-id="21f79-114">选择此值将显示动态选项 **File name**。</span><span class="sxs-lookup"><span data-stu-id="21f79-114">Selecting this value displays the dynamic option, **File name**.</span></span>|  
  
## <a name="location-dynamic-options"></a><span data-ttu-id="21f79-115">位置动态选项</span><span class="sxs-lookup"><span data-stu-id="21f79-115">Location Dynamic Options</span></span>  
  
### <a name="location--sql-server"></a><span data-ttu-id="21f79-116">位置 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="21f79-116">Location = SQL Server</span></span>  
 <span data-ttu-id="21f79-117">**包名称**</span><span class="sxs-lookup"><span data-stu-id="21f79-117">**Package name**</span></span>  
 <span data-ttu-id="21f79-118">选择指定服务器上存储的包。</span><span class="sxs-lookup"><span data-stu-id="21f79-118">Select a package that is stored on the specified server.</span></span>  
  
 <span data-ttu-id="21f79-119">**Server**</span><span class="sxs-lookup"><span data-stu-id="21f79-119">**Server**</span></span>  
 <span data-ttu-id="21f79-120">提供服务器名称或从列表中选择一个服务器。</span><span class="sxs-lookup"><span data-stu-id="21f79-120">Provide a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="21f79-121">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="21f79-121">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="21f79-122">单击此项可使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="21f79-122">Click to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="21f79-123">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="21f79-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="21f79-124">单击此项可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="21f79-124">Click to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="21f79-125">**用户名**</span><span class="sxs-lookup"><span data-stu-id="21f79-125">**User name**</span></span>  
 <span data-ttu-id="21f79-126">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则在登录服务器时应提供要使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="21f79-126">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a user name to use when logging on to the server.</span></span>  
  
 <span data-ttu-id="21f79-127">**密码**</span><span class="sxs-lookup"><span data-stu-id="21f79-127">**Password**</span></span>  
 <span data-ttu-id="21f79-128">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="21f79-128">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
### <a name="location--dtsx-file"></a><span data-ttu-id="21f79-129">位置 = DTSX 文件</span><span class="sxs-lookup"><span data-stu-id="21f79-129">Location = DTSX file</span></span>  
 <span data-ttu-id="21f79-130">**文件名**</span><span class="sxs-lookup"><span data-stu-id="21f79-130">**File name**</span></span>  
 <span data-ttu-id="21f79-131">提供包的路径，或单击浏览按钮“(…)”并查找包  。</span><span class="sxs-lookup"><span data-stu-id="21f79-131">Provide the path of a package or click the browse button **(...)** and locate the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f79-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21f79-132">See Also</span></span>  
 [<span data-ttu-id="21f79-133">消息队列任务</span><span class="sxs-lookup"><span data-stu-id="21f79-133">Message Queue Task</span></span>](message-queue-task.md)  
  
  
