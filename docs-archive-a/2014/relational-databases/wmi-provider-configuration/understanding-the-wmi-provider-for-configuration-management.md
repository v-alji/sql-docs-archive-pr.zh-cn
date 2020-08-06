---
title: 了解用于配置管理的 WMI 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0f4f38265093fdb0c27d6bd49ff64ba4b572111e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576554"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="be6f4-102">了解用于配置管理的 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="be6f4-102">Understanding the WMI Provider for Configuration Management</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="be6f4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]提供用于配置管理的 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="be6f4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="be6f4-104">这样，您便可以使用 Windows Management Instrumentation (WMI) 来管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端和服务器网络设置以及服务器别名。</span><span class="sxs-lookup"><span data-stu-id="be6f4-104">This lets you use Windows Management Instrumentation (WMI) to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client and server network settings, and server aliases.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="be6f4-105">服务、网络设置和别名由计算机的 root\Microsoft\SqlServer\ComputerManagement*nn*命名空间中的 WMI 对象表示。</span><span class="sxs-lookup"><span data-stu-id="be6f4-105">services, network settings, and aliases are represented by WMI objects in the root\Microsoft\SqlServer\ComputerManagement*nn* namespace of the computer.</span></span> <span data-ttu-id="be6f4-106">与指定计算机上的 WMI 提供程序建立连接后，可以使用 WQL 或脚本撰写语言查询服务、网络设置和别名。</span><span class="sxs-lookup"><span data-stu-id="be6f4-106">After a connection is established with the WMI provider on the specified computer, the services, network settings, and aliases can be queried using WQL or a scripting language.</span></span>  
  
 <span data-ttu-id="be6f4-107">WMI 提供程序是一个实例提供程序。</span><span class="sxs-lookup"><span data-stu-id="be6f4-107">The WMI Provider is an instance provider.</span></span> <span data-ttu-id="be6f4-108">它提供[WMI 类](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md)的实例，并支持以下异步操作。</span><span class="sxs-lookup"><span data-stu-id="be6f4-108">It supplies instances of the [WMI Classes](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) and supports the following asynchronous operations.</span></span>  
  
 <span data-ttu-id="be6f4-109">实例检索</span><span class="sxs-lookup"><span data-stu-id="be6f4-109">Instance retrieval</span></span>  
 <span data-ttu-id="be6f4-110">检索特定的类类型实例。</span><span class="sxs-lookup"><span data-stu-id="be6f4-110">Retrieval of a particular class type instance.</span></span>  
  
 <span data-ttu-id="be6f4-111">枚举</span><span class="sxs-lookup"><span data-stu-id="be6f4-111">Enumeration</span></span>  
 <span data-ttu-id="be6f4-112">枚举类类型的所有实例。</span><span class="sxs-lookup"><span data-stu-id="be6f4-112">Enumeration of all instances of a class type.</span></span>  
  
 <span data-ttu-id="be6f4-113">修改</span><span class="sxs-lookup"><span data-stu-id="be6f4-113">Modification</span></span>  
 <span data-ttu-id="be6f4-114">修改类类型的特定实例。</span><span class="sxs-lookup"><span data-stu-id="be6f4-114">Modification of a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="be6f4-115">类具有用于修改其属性的方法。</span><span class="sxs-lookup"><span data-stu-id="be6f4-115">Classes have methods that allow the modification of their properties.</span></span>  
  
 <span data-ttu-id="be6f4-116">删除</span><span class="sxs-lookup"><span data-stu-id="be6f4-116">Deletion</span></span>  
 <span data-ttu-id="be6f4-117">删除类类型的特定实例。</span><span class="sxs-lookup"><span data-stu-id="be6f4-117">Removing a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="be6f4-118">查询处理</span><span class="sxs-lookup"><span data-stu-id="be6f4-118">Query processing</span></span>  
 <span data-ttu-id="be6f4-119">根据筛选器枚举类类型的实例。</span><span class="sxs-lookup"><span data-stu-id="be6f4-119">Enumeration of instances of a class type based on a filter.</span></span>  
  
 <span data-ttu-id="be6f4-120">有关使用 WMI 提供程序进行配置管理的管理应用程序的示例，请参阅[将 WQL 和脚本语言与用于配置管理的 Wmi 提供程序结合使用](using-wql-and-scripting-languages-with-the-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="be6f4-120">For examples of management application using the WMI Provider for Configuration Management, see [Using WQL and Scripting Languages with the WMI Provider for Configuration Management](using-wql-and-scripting-languages-with-the-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="be6f4-121">有关使用 WMI 提供程序的编程管理应用程序的详细信息，请参阅 .NET Framework SDK 中的 WMI 文档 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="be6f4-121">For more information about programming management applications using the WMI Provider, see the WMI documentation in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be6f4-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be6f4-122">See Also</span></span>  
 <span data-ttu-id="be6f4-123">[使用 WMI 提供程序进行配置管理](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="be6f4-123">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="be6f4-124">将 WQL 和脚本语言用于配置管理的 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="be6f4-124">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
