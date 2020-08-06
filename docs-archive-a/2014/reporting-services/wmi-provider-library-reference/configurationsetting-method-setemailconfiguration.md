---
title: SetEmailConfiguration 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19068d7d7fff8c31c455ef76e8d2c2caa26b743f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692189"
---
# <a name="setemailconfiguration-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6e5f1-102">SetEmailConfiguration 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6e5f1-102">SetEmailConfiguration Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6e5f1-103">配置报表服务器用来发送电子邮件的电子邮件传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-103">Configures the e-mail delivery extension used by the report server to send e-mail.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5f1-104">语法</span><span class="sxs-lookup"><span data-stu-id="6e5f1-104">Syntax</span></span>  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5f1-105">parameters</span><span class="sxs-lookup"><span data-stu-id="6e5f1-105">Parameters</span></span>  
 <span data-ttu-id="6e5f1-106">*SendUsingSMTPServer*</span><span class="sxs-lookup"><span data-stu-id="6e5f1-106">*SendUsingSMTPServer*</span></span>  
 <span data-ttu-id="6e5f1-107">指示相应服务器是否将使用 SMTP 服务器发送电子邮件的布尔值。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-107">A Boolean value indicating whether the server is to use the SMTP server to send email.</span></span> <span data-ttu-id="6e5f1-108">此值仅可设置为 true。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-108">This value can only be set to true.</span></span> <span data-ttu-id="6e5f1-109">默认值为 false。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-109">Default value is false.</span></span>  
  
 <span data-ttu-id="6e5f1-110">*SMTPServer*</span><span class="sxs-lookup"><span data-stu-id="6e5f1-110">*SMTPServer*</span></span>  
 <span data-ttu-id="6e5f1-111">包含 SMTP 服务器的名称或 IP 地址的字符串。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-111">A string containing the name or IP address of an SMTP server.</span></span>  
  
 <span data-ttu-id="6e5f1-112">*SenderEmailAddress*</span><span class="sxs-lookup"><span data-stu-id="6e5f1-112">*SenderEmailAddress*</span></span>  
 <span data-ttu-id="6e5f1-113">从报表服务器发出的电子邮件的“发件人:”字段中使用的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-113">The e-mail address used in the 'From:' field for e-mails sent from the report server.</span></span>  
  
 <span data-ttu-id="6e5f1-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="6e5f1-114">*HRESULT*</span></span>  
 <span data-ttu-id="6e5f1-115">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e5f1-116">返回值</span><span class="sxs-lookup"><span data-stu-id="6e5f1-116">Return Value</span></span>  
 <span data-ttu-id="6e5f1-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="6e5f1-118">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="6e5f1-119">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e5f1-120">备注</span><span class="sxs-lookup"><span data-stu-id="6e5f1-120">Remarks</span></span>  
 <span data-ttu-id="6e5f1-121">将*SendUsingSMTPServer*参数设置为时 `true` ，Report Server 配置文件中的**SendUsing**条目将设置为1。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-121">When the *SendUsingSMTPServer* parameter is set to `true`, the **SendUsing** entry in the report server configuration file is set to 1.</span></span> <span data-ttu-id="6e5f1-122">如果将*SendUsingSMTPServer*设置为 `false` ，则不会配置**SendUsing**条目。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-122">When *SendUsingSMTPServer* is set to `false`, the **SendUsing** entry is not configured.</span></span>  
  
 <span data-ttu-id="6e5f1-123">此方法并不适合用户将报表服务器配置文件中的 **SendUsing** 条目设置为 1 以外的其他值。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-123">This method does not provide a way for users to set the **SendUsing** entry in the report server configuration file to a value other than 1.</span></span> <span data-ttu-id="6e5f1-124">若要为报表服务器配置除 SMTP 邮件以外的其他设置，必须手动编辑配置文件。</span><span class="sxs-lookup"><span data-stu-id="6e5f1-124">To configure the report server for anything other than SMTP mail, you must edit the configuration file manually.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e5f1-125">要求</span><span class="sxs-lookup"><span data-stu-id="6e5f1-125">Requirements</span></span>  
 <span data-ttu-id="6e5f1-126">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5f1-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5f1-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e5f1-127">See Also</span></span>  
 [<span data-ttu-id="6e5f1-128">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="6e5f1-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
