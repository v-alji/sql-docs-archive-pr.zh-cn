---
title: LINKEDSERVERS 行集 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: rothja
ms.author: jroth
ms.openlocfilehash: 80eded31ebae744e272757a53a7fd1f4b56bf358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578844"
---
# <a name="linkedservers-rowset-ole-db"></a><span data-ttu-id="96e5b-102">LINKEDSERVERS 行集 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="96e5b-102">LINKEDSERVERS Rowset (OLE DB)</span></span>
  <span data-ttu-id="96e5b-103">LINKEDSERVERS 行集用于枚举可以参与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分布式查询的组织数据源\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96e5b-103">The **LINKEDSERVERS** rowset enumerates organization data sources that can participate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries.</span></span>  
  
 <span data-ttu-id="96e5b-104">LINKEDSERVERS 行集包含以下列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96e5b-104">The **LINKEDSERVERS** rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="96e5b-105">列名称</span><span class="sxs-lookup"><span data-stu-id="96e5b-105">Column name</span></span>|<span data-ttu-id="96e5b-106">类型指示符</span><span class="sxs-lookup"><span data-stu-id="96e5b-106">Type indicator</span></span>|<span data-ttu-id="96e5b-107">说明</span><span class="sxs-lookup"><span data-stu-id="96e5b-107">Description</span></span>|  
|-----------------|--------------------|-----------------|  
|<span data-ttu-id="96e5b-108">SVR_NAME</span><span class="sxs-lookup"><span data-stu-id="96e5b-108">SVR_NAME</span></span>|<span data-ttu-id="96e5b-109">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="96e5b-109">DBTYPE_WSTR</span></span>|<span data-ttu-id="96e5b-110">链接服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="96e5b-110">Name of a linked server.</span></span>|  
|<span data-ttu-id="96e5b-111">SVR_PRODUCT</span><span class="sxs-lookup"><span data-stu-id="96e5b-111">SVR_PRODUCT</span></span>|<span data-ttu-id="96e5b-112">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="96e5b-112">DBTYPE_WSTR</span></span>|<span data-ttu-id="96e5b-113">标识由链接服务器的名称所表示的数据存储的类型的制造商或其他名称。</span><span class="sxs-lookup"><span data-stu-id="96e5b-113">Manufacturer or other name identifying the type of data store represented by the name of the linked server.</span></span>|  
|<span data-ttu-id="96e5b-114">SVR_PROVIDERNAME</span><span class="sxs-lookup"><span data-stu-id="96e5b-114">SVR_PROVIDERNAME</span></span>|<span data-ttu-id="96e5b-115">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="96e5b-115">DBTYPE_WSTR</span></span>|<span data-ttu-id="96e5b-116">用于从服务器使用数据的 OLE DB 访问接口的友好名称。</span><span class="sxs-lookup"><span data-stu-id="96e5b-116">Friendly name of the OLE DB provider used to consume data from the server.</span></span>|  
|<span data-ttu-id="96e5b-117">SVR_DATASOURCE</span><span class="sxs-lookup"><span data-stu-id="96e5b-117">SVR_DATASOURCE</span></span>|<span data-ttu-id="96e5b-118">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="96e5b-118">DBTYPE_WSTR</span></span>|<span data-ttu-id="96e5b-119">用于从提供程序获得数据源的 OLE DB DBPROP_INIT_DATASOURCE 字符串。</span><span class="sxs-lookup"><span data-stu-id="96e5b-119">OLE DB DBPROP_INIT_DATASOURCE string used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="96e5b-120">SVR_PROVIDERSTRING</span><span class="sxs-lookup"><span data-stu-id="96e5b-120">SVR_PROVIDERSTRING</span></span>|<span data-ttu-id="96e5b-121">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="96e5b-121">DBTYPE_WSTR</span></span>|<span data-ttu-id="96e5b-122">用于从提供程序获得数据源的 OLE DB DBPROP_INIT_PROVIDERSTRING 值。</span><span class="sxs-lookup"><span data-stu-id="96e5b-122">OLE DB DBPROP_INIT_PROVIDERSTRING value used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="96e5b-123">SVR_LOCATION</span><span class="sxs-lookup"><span data-stu-id="96e5b-123">SVR_LOCATION</span></span>|<span data-ttu-id="96e5b-124">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="96e5b-124">DBTYPE_WSTR</span></span>|<span data-ttu-id="96e5b-125">用于从提供程序获得数据源的 OLE DB DBPROP_INIT_LOCATION 字符串。</span><span class="sxs-lookup"><span data-stu-id="96e5b-125">OLE DB DBPROP_INIT_LOCATION string used to acquire a data source from the provider.</span></span>|  
  
 <span data-ttu-id="96e5b-126">行集按 SRV_NAME 排序，并支持对 SRV_NAME 的单个限制。</span><span class="sxs-lookup"><span data-stu-id="96e5b-126">The rowset is sorted on SRV_NAME and a single restriction is supported on SRV_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e5b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96e5b-127">See Also</span></span>  
 [<span data-ttu-id="96e5b-128">架构行集支持 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="96e5b-128">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
  
