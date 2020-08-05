---
title: System.Data.dll 中不允许的类型和成员 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: cd62f6f0a90bd167f20a33f8de749acc982f39b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580299"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a><span data-ttu-id="805f8-102">System.Data.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="805f8-102">Disallowed Types and Members in System.Data.dll</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="805f8-103">公共语言集成 (CLR) 编程不允许使用具有、、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` **SharedState**、 `Synchronization` 或 `UI` 值指定枚举的类型或成员。</span><span class="sxs-lookup"><span data-stu-id="805f8-103">common language integration (CLR) programming disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="805f8-104">下表列出了宿主保护属性 (HPA) 值被禁用的 System.Data.dll 程序集的成员和类型。</span><span class="sxs-lookup"><span data-stu-id="805f8-104">The following table lists the members and types of the System.Data.dll assembly whose Host Protection Attribute (HPA) values are disallowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="805f8-105">此列表是通过支持的程序集生成的。</span><span class="sxs-lookup"><span data-stu-id="805f8-105">This list was generated from the supported assemblies.</span></span> <span data-ttu-id="805f8-106">有关详细信息，请参阅[支持的 .NET Framework 库](../clr-integration/database-objects/supported-net-framework-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="805f8-106">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
|<span data-ttu-id="805f8-107">类型或成员</span><span class="sxs-lookup"><span data-stu-id="805f8-107">Type or Member</span></span>|<span data-ttu-id="805f8-108">HPA 值</span><span class="sxs-lookup"><span data-stu-id="805f8-108">HPA Value(s)</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="805f8-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span><span class="sxs-lookup"><span data-stu-id="805f8-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span></span>|<span data-ttu-id="805f8-110">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="805f8-110">ExternalThreading</span></span>|  
|<span data-ttu-id="805f8-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span><span class="sxs-lookup"><span data-stu-id="805f8-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span></span>|<span data-ttu-id="805f8-112">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="805f8-112">ExternalThreading</span></span>|  
|<span data-ttu-id="805f8-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span><span class="sxs-lookup"><span data-stu-id="805f8-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span></span>|<span data-ttu-id="805f8-114">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="805f8-114">ExternalThreading</span></span>|  
|<span data-ttu-id="805f8-115">System.Data.SqlClient.SqlDependency..ctor()</span><span class="sxs-lookup"><span data-stu-id="805f8-115">System.Data.SqlClient.SqlDependency..ctor()</span></span>|<span data-ttu-id="805f8-116">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="805f8-116">ExternalThreading</span></span>|  
|<span data-ttu-id="805f8-117">System.Data.SqlClient.SqlDependency.Start()</span><span class="sxs-lookup"><span data-stu-id="805f8-117">System.Data.SqlClient.SqlDependency.Start()</span></span>|<span data-ttu-id="805f8-118">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="805f8-118">ExternalThreading</span></span>|  
|<span data-ttu-id="805f8-119">System.Data.SqlClient.SqlDependency.Stop()</span><span class="sxs-lookup"><span data-stu-id="805f8-119">System.Data.SqlClient.SqlDependency.Stop()</span></span>|<span data-ttu-id="805f8-120">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="805f8-120">ExternalThreading</span></span>|  
|<span data-ttu-id="805f8-121">System.Data.TypedDataSetGenerator</span><span class="sxs-lookup"><span data-stu-id="805f8-121">System.Data.TypedDataSetGenerator</span></span>|<span data-ttu-id="805f8-122">SharedState, Synchronization</span><span class="sxs-lookup"><span data-stu-id="805f8-122">SharedState, Synchronization</span></span>|  
|<span data-ttu-id="805f8-123">System.Xml.XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="805f8-123">System.Xml.XmlDataDocument</span></span>|<span data-ttu-id="805f8-124">同步</span><span class="sxs-lookup"><span data-stu-id="805f8-124">Synchronization</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="805f8-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="805f8-125">See Also</span></span>  
 <span data-ttu-id="805f8-126">[宿主保护属性和 CLR 集成编程](host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="805f8-126">[Host Protection Attributes and CLR Integration Programming](host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 <span data-ttu-id="805f8-127">[Microsoft.VisualBasic.dll中不允许的类型和成员](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span><span class="sxs-lookup"><span data-stu-id="805f8-127">[Disallowed Types and Members in Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span></span>  
 <span data-ttu-id="805f8-128">[mscorlib.dll中不允许的类型和成员](disallowed-types-and-members-in-mscorlib-dll.md) </span><span class="sxs-lookup"><span data-stu-id="805f8-128">[Disallowed Types and Members in mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md) </span></span>  
 <span data-ttu-id="805f8-129">[System.dll中不允许的类型和成员](disallowed-types-and-members-in-system-dll.md) </span><span class="sxs-lookup"><span data-stu-id="805f8-129">[Disallowed Types and Members in System.dll](disallowed-types-and-members-in-system-dll.md) </span></span>  
 [<span data-ttu-id="805f8-130">System.Core.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="805f8-130">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
  
  
