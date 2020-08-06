---
title: 使用 WMI 提供程序进行配置管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80f311fb0abae2337f6ea4a5d5d85aaa0d320b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586538"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="e25c5-102">使用 WMI 提供程序进行配置管理</span><span class="sxs-lookup"><span data-stu-id="e25c5-102">Working with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="e25c5-103">在使用用于计算机管理的 WMI 提供程序编程之前，请考虑下列事项：</span><span class="sxs-lookup"><span data-stu-id="e25c5-103">Consider the following before programming with the WMI Provider for Computer Management:</span></span>  
  
## <a name="binding"></a><span data-ttu-id="e25c5-104">绑定</span><span class="sxs-lookup"><span data-stu-id="e25c5-104">Binding</span></span>  
 <span data-ttu-id="e25c5-105">用于配置管理的 WMI 提供程序是一个 COM 对象模型，它支持早期绑定和后期绑定。</span><span class="sxs-lookup"><span data-stu-id="e25c5-105">The WMI Provider for Configuration Management is a COM object model and it supports early and late binding.</span></span> <span data-ttu-id="e25c5-106">借助后期绑定，您可以使用脚本语言（如 VBScript）以编程方式操作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务、网络设置和别名。</span><span class="sxs-lookup"><span data-stu-id="e25c5-106">With late binding you can use script languages, such as VBScript, to manipulate the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and aliases programmatically.</span></span>  
  
 <span data-ttu-id="e25c5-107">有关使用脚本语言对 WMI 提供程序实现进行编程的详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN[网站](https://go.microsoft.com/fwlink/?linkid=15426)。</span><span class="sxs-lookup"><span data-stu-id="e25c5-107">For further information about programming WMI Provider implementations using scripting languages, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="specifying-a-connection-string"></a><span data-ttu-id="e25c5-108">指定连接字符串</span><span class="sxs-lookup"><span data-stu-id="e25c5-108">Specifying a Connection String</span></span>  
 <span data-ttu-id="e25c5-109">应用程序通过连接到 WMI 提供程序所定义的 WMI 命名空间，将用于配置管理的该提供程序定向到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="e25c5-109">Applications direct the WMI Provider for Configuration Management to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by connecting to a WMI namespace defined by the provider.</span></span> <span data-ttu-id="e25c5-110">Windows WMI 服务将此命名空间映射到提供程序 DLL 并将其加载到内存。</span><span class="sxs-lookup"><span data-stu-id="e25c5-110">The Windows WMI service maps this namespace to the provider DLL and loads it into memory.</span></span> <span data-ttu-id="e25c5-111">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例均由一个 WMI 命名空间表示。</span><span class="sxs-lookup"><span data-stu-id="e25c5-111">All instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are represented with a single WMI namespace.</span></span> <span data-ttu-id="e25c5-112">默认命名空间为</span><span class="sxs-lookup"><span data-stu-id="e25c5-112">The namespace defaults to</span></span>  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 <span data-ttu-id="e25c5-113">其中 `instance_name` 默认为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认安装中的 `MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="e25c5-113">where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e25c5-114">**注意：** 如果要通过 Windows 防火墙进行连接，则需要确保计算机配置正确。</span><span class="sxs-lookup"><span data-stu-id="e25c5-114">**Note:** If you are connecting through Windows Firewall you will need to make sure your computers are configured appropriately.</span></span> <span data-ttu-id="e25c5-115">请参阅 MSDN 网站上 Windows Management Instrumentation 文档中的 "通过 Windows 防火墙连接" 一文 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。 [Web site](https://go.microsoft.com/fwlink/?linkid=15426)</span><span class="sxs-lookup"><span data-stu-id="e25c5-115">See the "Connecting Through Windows Firewall" article in the Windows Management Instrumentation documentation on [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="permissions-and-server-authentication"></a><span data-ttu-id="e25c5-116">权限和服务器身份验证</span><span class="sxs-lookup"><span data-stu-id="e25c5-116">Permissions and Server Authentication</span></span>  
 <span data-ttu-id="e25c5-117">若要访问用于配置管理的 WMI 提供程序，客户端 WMI 管理脚本必须在目标计算机上的管理员上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="e25c5-117">To access the WMI Provider for Configuration Management, the client WMI management script must be running in the context of an administrator on the target computer.</span></span> <span data-ttu-id="e25c5-118">您需要具有要管理的计算机上的本地 Windows Administrators 组的成员身份。</span><span class="sxs-lookup"><span data-stu-id="e25c5-118">You need to be a member of the local Windows administrators group on the computer you want to manage.</span></span>  
  
 <span data-ttu-id="e25c5-119">管理员可以设置组策略以控制用户对 WMI 提供程序的访问。</span><span class="sxs-lookup"><span data-stu-id="e25c5-119">The administrator can set group policies to control user access to WMI providers.</span></span> <span data-ttu-id="e25c5-120">有关设置组策略的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器帮助中的“组策略和 MMC”。</span><span class="sxs-lookup"><span data-stu-id="e25c5-120">For more information about setting group policies see "Group Policy and MMC" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help.</span></span>  
  
 <span data-ttu-id="e25c5-121">WMI 管理脚本可用于更新运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务所使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="e25c5-121">The WMI management script can be used to update the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services run.</span></span>  
  
 <span data-ttu-id="e25c5-122">用于配置管理的 WMI 提供程序支持安全证书。</span><span class="sxs-lookup"><span data-stu-id="e25c5-122">Security certificates are supported by the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="e25c5-123">有关证书的详细信息，请参阅[加密层次结构](../security/encryption/encryption-hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="e25c5-123">For more information about certificates, see [Encryption Hierarchy](../security/encryption/encryption-hierarchy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25c5-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e25c5-124">See Also</span></span>  
 [<span data-ttu-id="e25c5-125">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="e25c5-125">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
