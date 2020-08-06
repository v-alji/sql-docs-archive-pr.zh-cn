---
title: SqlServiceType 属性 (SqlServiceAdvancedProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 774c8599fd21e330fa3228336ab1ed3c73d65c85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591160"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a><span data-ttu-id="a8dea-102">SqlServiceType 方法（SqlServiceAdvancedProperty 类）</span><span class="sxs-lookup"><span data-stu-id="a8dea-102">SqlServiceType Property (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="a8dea-103">获取与高级属性关联的托管服务的类型。</span><span class="sxs-lookup"><span data-stu-id="a8dea-103">Gets the type of the managed service associated with the advanced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8dea-104">语法</span><span class="sxs-lookup"><span data-stu-id="a8dea-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a8dea-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a8dea-105">Parts</span></span>  
 <span data-ttu-id="a8dea-106">对象</span><span class="sxs-lookup"><span data-stu-id="a8dea-106">*object*</span></span>  
 <span data-ttu-id="a8dea-107">一个表示高级属性的 [SqlServiceAdvancedProperty 类](sqlserviceadvancedproperty-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="a8dea-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a8dea-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="a8dea-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="a8dea-109">一个指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务类型的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="a8dea-109">A uint32 value that specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8dea-110">备注</span><span class="sxs-lookup"><span data-stu-id="a8dea-110">Remarks</span></span>  
 <span data-ttu-id="a8dea-111">返回值可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="a8dea-111">Return values can be one of the following:</span></span>  
  
|<span data-ttu-id="a8dea-112">类型</span><span class="sxs-lookup"><span data-stu-id="a8dea-112">Type</span></span>|<span data-ttu-id="a8dea-113">定义</span><span class="sxs-lookup"><span data-stu-id="a8dea-113">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="a8dea-114">*1*</span><span class="sxs-lookup"><span data-stu-id="a8dea-114">*1*</span></span>|<span data-ttu-id="a8dea-115">MSSQLSERVER 为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-115">MSSQLSERVER is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="a8dea-116">*2*</span><span class="sxs-lookup"><span data-stu-id="a8dea-116">*2*</span></span>|<span data-ttu-id="a8dea-117">SQLSERVERAGENT 为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-117">SQLSERVERAGENT is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service.</span></span>|  
|<span data-ttu-id="a8dea-118">*3*</span><span class="sxs-lookup"><span data-stu-id="a8dea-118">*3*</span></span>|<span data-ttu-id="a8dea-119">MSFTESQL 为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-119">MSFTESQL is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine service.</span></span>|  
|<span data-ttu-id="a8dea-120">*4*</span><span class="sxs-lookup"><span data-stu-id="a8dea-120">*4*</span></span>|<span data-ttu-id="a8dea-121">MsDtsServer 为 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-121">MsDtsServer is the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="a8dea-122">*5*</span><span class="sxs-lookup"><span data-stu-id="a8dea-122">*5*</span></span>|<span data-ttu-id="a8dea-123">MSSQLServerOLAPService 为 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-123">MSSQLServerOLAPService is the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="a8dea-124">*6*</span><span class="sxs-lookup"><span data-stu-id="a8dea-124">*6*</span></span>|<span data-ttu-id="a8dea-125">ReportServer 为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-125">ReportServer is the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="a8dea-126">*7*</span><span class="sxs-lookup"><span data-stu-id="a8dea-126">*7*</span></span>|<span data-ttu-id="a8dea-127">SQLBrowser 为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="a8dea-127">SQLBrowser is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8dea-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8dea-128">See Also</span></span>  
 <span data-ttu-id="a8dea-129">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a8dea-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
