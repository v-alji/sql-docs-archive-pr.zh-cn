---
title: " (WMI MSReportServer_ConfigurationSetting) 的 GenerateDatabaseCreationScript 方法 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581112"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="05ebd-102">GenerateDatabaseCreationScript 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="05ebd-102">GenerateDatabaseCreationScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="05ebd-103">生成可用于创建报表服务器数据库的 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="05ebd-103">Generates a SQL Script that can be used to create a report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ebd-104">语法</span><span class="sxs-lookup"><span data-stu-id="05ebd-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05ebd-105">parameters</span><span class="sxs-lookup"><span data-stu-id="05ebd-105">Parameters</span></span>  
 <span data-ttu-id="05ebd-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="05ebd-106">*Databasename*</span></span>  
 <span data-ttu-id="05ebd-107">包含要创建的报表服务器数据库名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="05ebd-107">A string containing the name of the report server database to create.</span></span>  
  
 <span data-ttu-id="05ebd-108">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="05ebd-108">*Lcid*</span></span>  
 <span data-ttu-id="05ebd-109">用于角色名称本地化的值。</span><span class="sxs-lookup"><span data-stu-id="05ebd-109">Value used for localization of role names.</span></span>  
  
 <span data-ttu-id="05ebd-110">*IsSharePointMode*</span><span class="sxs-lookup"><span data-stu-id="05ebd-110">*IsSharePointMode*</span></span>  
 <span data-ttu-id="05ebd-111">指示是以本机模式还是以 SharePoint 模式创建数据库。</span><span class="sxs-lookup"><span data-stu-id="05ebd-111">Indicates whether to create database in native mode or SharePoint mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="05ebd-112">从开始 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， *IsSharePointMode* = `True` 不支持 IsSharePointMode，因为在 sharepoint 模式下， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 是 sharepoint 共享服务，且不受 WMI 提供程序的控制。</span><span class="sxs-lookup"><span data-stu-id="05ebd-112">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode*=`True` is not supported because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is a SharePoint shared service and is not controlled by the WMI provider.</span></span> <span data-ttu-id="05ebd-113">您应始终将此参数设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="05ebd-113">You should always set this parameter to `False`.</span></span>  
  
 <span data-ttu-id="05ebd-114">*脚本*</span><span class="sxs-lookup"><span data-stu-id="05ebd-114">*Script*</span></span>  
 <span data-ttu-id="05ebd-115">[out] 包含所生成的 SQL 脚本的字符串。</span><span class="sxs-lookup"><span data-stu-id="05ebd-115">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="05ebd-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="05ebd-116">*HRESULT*</span></span>  
 <span data-ttu-id="05ebd-117">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="05ebd-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05ebd-118">返回值</span><span class="sxs-lookup"><span data-stu-id="05ebd-118">Return Value</span></span>  
 <span data-ttu-id="05ebd-119">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="05ebd-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="05ebd-120">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="05ebd-120">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="05ebd-121">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="05ebd-121">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05ebd-122">备注</span><span class="sxs-lookup"><span data-stu-id="05ebd-122">Remarks</span></span>  
 <span data-ttu-id="05ebd-123">此方法将生成一个 SQL 脚本，创建适用于当前所连接的报表服务器版本的报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="05ebd-123">This method generates an SQL script that creates report server databases for the version of the report server currently connected to.</span></span>  
  
 <span data-ttu-id="05ebd-124">在 DatabaseName  参数中提供的值必须符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库命名约定。</span><span class="sxs-lookup"><span data-stu-id="05ebd-124">The value supplied in the *DatabaseName* parameter must conform to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database naming conventions.</span></span>  
  
 <span data-ttu-id="05ebd-125">生成脚本时，该方法不会检查该数据库是否存在。</span><span class="sxs-lookup"><span data-stu-id="05ebd-125">The method does not check the existence of the database when generating the script.</span></span>  
  
 <span data-ttu-id="05ebd-126">生成脚本时，此方法不会检查报表服务器数据库是否存在。</span><span class="sxs-lookup"><span data-stu-id="05ebd-126">This method does not check for the existence of the report server database when generating the script.</span></span>  
  
 <span data-ttu-id="05ebd-127">生成的脚本支持 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05ebd-127">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ebd-128">要求</span><span class="sxs-lookup"><span data-stu-id="05ebd-128">Requirements</span></span>  
 <span data-ttu-id="05ebd-129">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ebd-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ebd-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05ebd-130">See Also</span></span>  
 [<span data-ttu-id="05ebd-131">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="05ebd-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
