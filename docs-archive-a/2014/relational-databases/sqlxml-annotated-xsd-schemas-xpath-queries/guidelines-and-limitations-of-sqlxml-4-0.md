---
title: SQLXML 4.0 的指导原则和限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: rothja
ms.author: jroth
ms.openlocfilehash: e020cbf0ac32e4c878b0b74b67e7c9c679d5d178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576607"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a><span data-ttu-id="8b0c7-102">SQLXML 4.0 的准则和限制</span><span class="sxs-lookup"><span data-stu-id="8b0c7-102">Guidelines and Limitations of SQLXML 4.0</span></span>
  <span data-ttu-id="8b0c7-103">使用 SQLXML 4.0 时请记住以下事项：</span><span class="sxs-lookup"><span data-stu-id="8b0c7-103">Remember the following when working with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="8b0c7-104">不针对生成 XML 的映射架构验证作为查询结果返回的 XML。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-104">XML returned as a query result is not validated against the mapping schema that generated the XML.</span></span>  
  
-   <span data-ttu-id="8b0c7-105">SQLXML 4.0 既包括与版本无关的 PROGID，也包括与版本相关的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-105">SQLXML 4.0 includes version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="8b0c7-106">建议所有生产应用程序都使用与版本相关的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-106">It is recommended that all production applications use version-dependent PROGIDs.</span></span> <span data-ttu-id="8b0c7-107">由于 SQLXML 4.0 不完全向后兼容，这一点尤其重要。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-107">This is especially important because SQLXML 4.0 is not fully backward compatible.</span></span> <span data-ttu-id="8b0c7-108">只有使用与版本相关的 PROGID，在安装较新版本时，才能保证您的应用程序可继续工作，而不会失败。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-108">Using version dependent PROGIDs protects from possible production failures when you install newer releases.</span></span> <span data-ttu-id="8b0c7-109">不同版本的程序行为可能出于多种原因（如错误修复、可能的设计更改等）而有所变化。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-109">From release to release, program behavior may change for a variety of reasons, such as bug fixes, possible design changes, and so on.</span></span> <span data-ttu-id="8b0c7-110">使用与版本相关的 PROGID 可防止在安装较新版本时出现意外失败。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-110">Using version-dependent PROGIDs protects from unexpected failure when you install newer releases.</span></span> <span data-ttu-id="8b0c7-111">使用与版本相关的 PROGID 安装较新版本时，您的应用程序将继续工作，而不会失败。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-111">With version-dependent PROGIDs, when you install a newer release, your application will continue to work without failure.</span></span> <span data-ttu-id="8b0c7-112">如果决定更改以前的与版本相关的 PROGID，转而使用较新版本中最近的与版本相关的 PROGID，您必须在投入使用前测试您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-112">If you decide to change the previous version-dependent PROGIDs and use the recent version-dependent PROGIDs in a newer release, you must test your application before putting it into production.</span></span> <span data-ttu-id="8b0c7-113">例如，使用与版本无关的 PROGID 的应用程序将在以下情况下失败：</span><span class="sxs-lookup"><span data-stu-id="8b0c7-113">For example, applications using version-independent PROGIDs may fail in the following scenario:</span></span>  
  
     <span data-ttu-id="8b0c7-114">正在运行使用 SQLXML 4.0 和与版本无关的 PROGID 的应用程序，而且您决定安装其他某种软件程序。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-114">You are running an application that uses SQLXML 4.0 and version-independent PROGIDs, and you decide to install some other software program.</span></span> <span data-ttu-id="8b0c7-115">此程序可能安装较早版本的 SQLXML。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-115">This program might install an earlier version of SQLXML.</span></span> <span data-ttu-id="8b0c7-116">由于您的应用程序中的与版本无关的 PROGID 现在指向较早版本的 SQLXML（其中可能具有或不具有您的应用程序正在使用的 SQLXML 功能），您的应用程序可能失败。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-116">Your application may fail because the version-independent PROGIDS in your application now point to the earlier version of SQLXML, which may or may not have the SQLXML feature that your application is using.</span></span>  
  
-   <span data-ttu-id="8b0c7-117">如果出于任何原因而不想使用 SQLXMLOLEDB 提供程序，而是希望使用 SQLOLEDB 提供程序执行 SQLXML 功能，请将**Sqlxml 版本**属性设置为 "sqlxml. 4.0"。</span><span class="sxs-lookup"><span data-stu-id="8b0c7-117">If for any reason you don't want to use the SQLXMLOLEDB provider, and instead want to use the SQLOLEDB provider for SQLXML features, set the **SQLXML Version** property to "SQLXML.4.0".</span></span>  
  
  
