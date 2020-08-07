---
title: SQL Server Native Client 的组件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: rothja
ms.author: jroth
ms.openlocfilehash: 32438b9fb5473d9251acd0aceddb46db373f3548
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587777"
---
# <a name="components-of-sql-server-native-client"></a><span data-ttu-id="b7313-102">SQL Server Native Client 的组件</span><span class="sxs-lookup"><span data-stu-id="b7313-102">Components of SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="b7313-103">Native Client 包含下列组件：</span><span class="sxs-lookup"><span data-stu-id="b7313-103">Native Client contains the following components:</span></span>  
  
|<span data-ttu-id="b7313-104">组件</span><span class="sxs-lookup"><span data-stu-id="b7313-104">Component</span></span>|<span data-ttu-id="b7313-105">说明</span><span class="sxs-lookup"><span data-stu-id="b7313-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7313-106">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="b7313-106">sqlncli11.dll</span></span>|<span data-ttu-id="b7313-107">包含所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 功能的动态链接库 (DLL) 文件。</span><span class="sxs-lookup"><span data-stu-id="b7313-107">The dynamic-link library (DLL) file that contains all of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client functionality.</span></span> <span data-ttu-id="b7313-108">它包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="b7313-108">This includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>|  
|<span data-ttu-id="b7313-109">sqlnclir11.rll</span><span class="sxs-lookup"><span data-stu-id="b7313-109">sqlnclir11.rll</span></span>|<span data-ttu-id="b7313-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 库附带的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b7313-110">The accompanying resource file for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library.</span></span>|  
|<span data-ttu-id="b7313-111">s10ch_sqlncli.chm</span><span class="sxs-lookup"><span data-stu-id="b7313-111">s10ch_sqlncli.chm</span></span>|<span data-ttu-id="b7313-112">数据源向导帮助文件，对如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口创建 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据源作了文字说明。</span><span class="sxs-lookup"><span data-stu-id="b7313-112">The Data Source Wizard help file that documents how to create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data source using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>|  
|<span data-ttu-id="b7313-113">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="b7313-113">sqlncli.h</span></span>|<span data-ttu-id="b7313-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 头文件，其中包含使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 时所需的所有新定义。</span><span class="sxs-lookup"><span data-stu-id="b7313-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header file that contains all of the new definitions needed in order to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="b7313-115">该头文件取代了 odbcss.h 和 sqloledb.h 头文件。</span><span class="sxs-lookup"><span data-stu-id="b7313-115">This header file replaces both the odbcss.h and the sqloledb.h header files.</span></span> <span data-ttu-id="b7313-116">**注意：** 你不能在同一程序中引用 sqlncli.msi 和 odbcss.h，但只要先定义 sqloledb，就可以在同一程序中引用 sqlncli.msi 和 sqloledb。</span><span class="sxs-lookup"><span data-stu-id="b7313-116">**Note:**  You cannot reference sqlncli.h and odbcss.h in the same program, but you can reference sqlncli.h and sqloledb.h in same program as long as sqloledb.h is defined first.</span></span>|  
|<span data-ttu-id="b7313-117">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="b7313-117">sqlncli11.lib</span></span>|<span data-ttu-id="b7313-118">直接调用作为**bcp** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序的一部分的 bcp 实用工具函数所需的库文件。</span><span class="sxs-lookup"><span data-stu-id="b7313-118">The library file needed to directly call the **bcp** utility functions that are part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="b7313-119">**注意：** 如果您在编程代码中引用 sqlncli11 文件，则需要确保 sqlncli11.dll 文件位于您的系统路径中，并且在使用您的应用程序的用户的系统路径中。</span><span class="sxs-lookup"><span data-stu-id="b7313-119">**Note:**  If you do reference the sqlncli11.lib file in your programming code, you need to make sure that the sqlncli11.dll file is in your system path, and in the system path of the users that make use of your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7313-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7313-120">See Also</span></span>  
 [<span data-ttu-id="b7313-121">使用 SQL Server Native Client 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="b7313-121">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
