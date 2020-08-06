---
title: Unicode 数据和服务器代码页 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- Unicode [SQL Server], extended stored procedures
- extended stored procedures [SQL Server], metadata
ms.assetid: 52310260-a892-4b27-ad2e-bf164b98ee80
author: rothja
ms.author: jroth
ms.openlocfilehash: e88a43ee242e9fa84ac3a5573c7d3ca3dc0369d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576763"
---
# <a name="unicode-data-and-server-code-pages"></a><span data-ttu-id="e36a5-102">Unicode 数据和服务器代码页</span><span class="sxs-lookup"><span data-stu-id="e36a5-102">Unicode Data and Server Code Pages</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="e36a5-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="e36a5-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="e36a5-104">扩展存储过程 API 将对 Unicode 数据启用；但是，它不对 Unicode 元数据启用。</span><span class="sxs-lookup"><span data-stu-id="e36a5-104">The Extended Stored Procedure API is enabled for Unicode data; however, it is not enabled for Unicode metadata.</span></span> <span data-ttu-id="e36a5-105">#define Unicode 指令不影响扩展存储过程 API。</span><span class="sxs-lookup"><span data-stu-id="e36a5-105">The #define Unicode directive does not have any effect on the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="e36a5-106">由扩展存储过程 API 返回的或由您的扩展存储过程应用程序提供给它的所有元数据都假定位于服务器的多字节代码页中。</span><span class="sxs-lookup"><span data-stu-id="e36a5-106">All metadata returned by, or provided to the Extended Stored Procedure API by your extended stored procedure application is assumed to be in the multibyte code page of the server.</span></span> <span data-ttu-id="e36a5-107">扩展存储过程 API 服务器应用程序的默认代码页是运行应用程序的计算机的 ANSI 代码页，可以通过调用**srv_pfield** ，并将字段参数设置为 SRV_SPROC_CODEPAGE 来获取此页。</span><span class="sxs-lookup"><span data-stu-id="e36a5-107">The default code page of an Extended Stored Procedure API server application is the ANSI code page of the computer on which the application is running, which can be obtained by calling **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE.</span></span>  
  
 <span data-ttu-id="e36a5-108">如果您的扩展存储过程 API 应用程序启用了 Unicode，则必须将您的 Unicode 元数据列名称、错误消息等转换为多字节数据，然后才能将该数据传递给扩展存储过程 API。</span><span class="sxs-lookup"><span data-stu-id="e36a5-108">If your Extended Stored Procedure API application is Unicode-enabled, you must convert your Unicode metadata column names, error messages, and so on, to multibyte data before passing this data to the Extended Stored Procedure API.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e36a5-109">示例</span><span class="sxs-lookup"><span data-stu-id="e36a5-109">Example</span></span>  
 <span data-ttu-id="e36a5-110">以下扩展存储过程提供了上述 Unicode 转换的示例。</span><span class="sxs-lookup"><span data-stu-id="e36a5-110">The following extended stored procedure provides an example of the Unicode conversions discussed.</span></span> <span data-ttu-id="e36a5-111">请注意：</span><span class="sxs-lookup"><span data-stu-id="e36a5-111">Note that:</span></span>  
  
-   <span data-ttu-id="e36a5-112">列数据将作为 Unicode 数据传递到**srv_describe** ，因为该列被描述为 SRVNVARCHAR。</span><span class="sxs-lookup"><span data-stu-id="e36a5-112">Column data is passed as Unicode data to **srv_describe** because the column is described to be SRVNVARCHAR.</span></span>  
  
-   <span data-ttu-id="e36a5-113">列名元数据将作为多字节数据传递到**srv_describe** 。</span><span class="sxs-lookup"><span data-stu-id="e36a5-113">Column name metadata is passed to **srv_describe** as multibyte data.</span></span>  
  
     <span data-ttu-id="e36a5-114">扩展存储过程调用**srv_pfield** ，并将字段参数设置为 SRV_SPROC_CODEPAGE 以获取的多字节代码页 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e36a5-114">The extended stored procedure calls **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE to obtain the multibyte code page of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e36a5-115">错误消息将作为多字节数据传递到**srv_sendmsg** 。</span><span class="sxs-lookup"><span data-stu-id="e36a5-115">Error messages are passed to **srv_sendmsg** as multibyte data.</span></span>  
  
    ```  
    __declspec(dllexport) RETCODE proc1 (SRV_PROC *srvproc)  
    {  
        #define MAX_COL_NAME_LEN 25  
        #define MAX_COL_DATA_LEN 50  
        #define MAX_ERR_MSG_LEN 250  
        #define MAX_SERVER_ERROR 20000  
        #define XP_ERROR_NUMBER MAX_SERVER_ERROR+1  
  
        int retval;  
        UINT serverCodePage;  
        CHAR *szServerCodePage;  
  
        WCHAR unicodeColumnName[MAX_COL_NAME_LEN];  
        CHAR multibyteColumnName[MAX_COL_NAME_LEN];  
  
        WCHAR unicodeColumnData[MAX_COL_DATA_LEN];  
  
        WCHAR unicodeErrorMessage[MAX_ERR_MSG_LEN];  
        CHAR  multibyteErrorMessage[MAX_ERR_MSG_LEN];  
  
        lstrcpyW (unicodeColumnName, L"column1");  
        lstrcpyW (unicodeColumnData, L"column1 data");  
        lstrcpyW (unicodeErrorMessage, L"No Error!");  
  
        // Obtain server code page.  
        //  
        szServerCodePage = srv_pfield (srvproc, SRV_SPROC_CODEPAGE, NULL);      
        if (NULL != szServerCodePage)  
            serverCodePage = atol(szServerCodePage);  
        else   
        {   // Problem situation exists.  
            srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
            return 1;  
        }  
  
        // Convert column name for Unicode to multibyte using the   
        // server code page.  
        //  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeColumnName,              // wide-character string  
            -1,                             // string is null terminated  
            multibyteColumnName,            // address of buffer for new  
                                            //   string  
            sizeof (multibyteColumnName),   // size of buffer  
            NULL, NULL);  
  
        if (0 == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"Conversion to multibyte  
            failed.");  
            goto Error;  
        }  
  
        retval = srv_describe (srvproc, 1, multibyteColumnName,  
        SRV_NULLTERM,   
          SRVNVARCHAR, MAX_COL_DATA_LEN*sizeof(WCHAR), // destination  
            SRVNVARCHAR, lstrlenW(unicodeColumnData)*sizeof(WCHAR),  
            unicodeColumnData); //source  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_describe failed.");  
            goto Error;  
        }  
  
       retval = srv_sendrow(srvproc);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_sendrow failed.");  
            goto Error;  
        }  
  
        retval = srv_senddone (srvproc, SRV_DONE_MORE|SRV_DONE_COUNT, 0, 1);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_senddone failed.");  
            goto Error;  
        }  
  
        return 0;  
    Error:  
        // convert error message from Unicode to multibyte.  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeErrorMessage,            // wide-character string  
            -1,                             // string is null terminated  
            multibyteErrorMessage,          // address of buffer for new  
                                            //   string  
            sizeof (multibyteErrorMessage), // size of buffer  
            NULL, NULL);  
  
    srv_sendmsg(srvproc, SRV_MSG_ERROR, XP_ERROR_NUMBER, SRV_INFO, 1,  
                NULL, 0, __LINE__,   
                multibyteErrorMessage,  
                SRV_NULLTERM);  
  
        srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
  
        return 1;  
    }  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e36a5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e36a5-116">See Also</span></span>  
 [<span data-ttu-id="e36a5-117">扩展存储过程 API srv_wsendmsg &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="e36a5-117">srv_wsendmsg &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-wsendmsg-extended-stored-procedure-api.md)  
  
  
