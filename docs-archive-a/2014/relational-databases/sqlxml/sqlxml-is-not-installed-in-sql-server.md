---
title: SQLXML 未安装在 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: rothja
ms.author: jroth
ms.openlocfilehash: ffa4cfd8b18dbfd9b4ba05599e2a973ac5f6e888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588402"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a><span data-ttu-id="ba45b-102">SQL Server 中未安装 SQLXML</span><span class="sxs-lookup"><span data-stu-id="ba45b-102">SQLXML Is Not Installed in SQL Server</span></span>
  <span data-ttu-id="ba45b-103">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前，SQLXML 4.0 随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起发布，是所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本（[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 除外）默认安装的一部分。</span><span class="sxs-lookup"><span data-stu-id="ba45b-103">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and was part of the default installation of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions except for [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="ba45b-104">从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 开始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不再包括 SQLXML 的最新版本 (SQLXML 4.0 SP1)。</span><span class="sxs-lookup"><span data-stu-id="ba45b-104">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ba45b-105">若要在 SQLXML 4.0 SP1 可用时安装它，请从[SQLXML SP1 的安装位置进行](https://www.microsoft.com/download/details.aspx?id=44272)下载。</span><span class="sxs-lookup"><span data-stu-id="ba45b-105">To install SQLXML 4.0 SP1 when it is available, download it from [Install Location for SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
 <span data-ttu-id="ba45b-106">当某个应用程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上运行并且需要使用 SQLXML 4.0 时，如果计算机上没有安装 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]，则必须下载 SQLXML 4.0 SP1 并安装它。</span><span class="sxs-lookup"><span data-stu-id="ba45b-106">If an application runs on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and requires SQLXML 4.0, and if the computer does not have [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must download and install SQLXML 4.0 SP1.</span></span>  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a><span data-ttu-id="ba45b-107">在使用 SQLOLEDB 和 SQL Server Native Client OLE DB 访问接口的新数据类型时 SQLXML 4.0 SP1 的行为</span><span class="sxs-lookup"><span data-stu-id="ba45b-107">SQLXML 4.0 SP1 Behavior with New Data Types Using SQLOLEDB and SQL Server Native Client OLE DB Provider</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="ba45b-108">中引入了以下数据类型，使用 SQLXML 的开发人员可能需要使用这些数据类型：</span><span class="sxs-lookup"><span data-stu-id="ba45b-108">introduces the following data types, which developers using SQLXML might want to use:</span></span>  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 <span data-ttu-id="ba45b-109">如果将 SQLXML 4.0 SP1 与 SQLOLEDB（来自 Windows 数据访问组件，以前为 Microsoft 数据访问组件）或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB（来自 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]）一起使用，这些新类型将作为字符串显示给开发人员。</span><span class="sxs-lookup"><span data-stu-id="ba45b-109">When using SQLXML 4.0 SP1 with either SQLOLEDB (from Windows Data Access Components, formerly Microsoft Data Access Components) or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], these new types will appear as strings to a developer.</span></span> <span data-ttu-id="ba45b-110">如果将 SQLXML 4.0 SP1 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0 一起使用，SQLXML 4.0 SP1 会将这四种新数据类型作为内置标量类型来使用。</span><span class="sxs-lookup"><span data-stu-id="ba45b-110">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0.</span></span> <span data-ttu-id="ba45b-111">在下载 SQLXML 4.0 SP1 之前，将这些类型映射到非字符串类型可能会导致截断某些数据。</span><span class="sxs-lookup"><span data-stu-id="ba45b-111">Until you download SQLXML 4.0 SP1, mapping these types to non-string types might cause truncation of some data.</span></span> <span data-ttu-id="ba45b-112">例如，映射 `DateTime2` 到 `xsd:date` 将导致数据截断到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` 3.33 毫秒。</span><span class="sxs-lookup"><span data-stu-id="ba45b-112">For example, mapping `DateTime2` to `xsd:date` will cause data to be truncated to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` precision of 3.33 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba45b-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba45b-113">See Also</span></span>  
 [<span data-ttu-id="ba45b-114">SQLXML 4.0 编程概念</span><span class="sxs-lookup"><span data-stu-id="ba45b-114">SQLXML 4.0 Programming Concepts</span></span>](sqlxml-4-0-programming-concepts.md)  
  
  
