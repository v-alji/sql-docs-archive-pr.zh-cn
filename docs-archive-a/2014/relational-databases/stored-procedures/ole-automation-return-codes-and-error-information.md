---
title: OLE 自动化返回代码和错误信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- return codes [SQL Server]
- OLE Automation [SQL Server], return codes
- OLE Automation [SQL Server], errors
ms.assetid: 9696fb05-e9e8-4836-b359-d4de0be0eeb2
author: stevestein
ms.author: sstein
ms.openlocfilehash: aecdbaedca42b7456dbdbda0407760959e546f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591859"
---
# <a name="ole-automation-return-codes-and-error-information"></a><span data-ttu-id="4178f-102">OLE 自动化返回代码和错误信息</span><span class="sxs-lookup"><span data-stu-id="4178f-102">OLE Automation Return Codes and Error Information</span></span>
  <span data-ttu-id="4178f-103">OLE 自动化系统存储过程返回一个 `int` 返回代码，该代码是基础 OLE 自动化操作返回的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="4178f-103">The OLE Automation system stored procedures return an `int` return code that is the HRESULT returned by the underlying OLE Automation operation.</span></span> <span data-ttu-id="4178f-104">HRESULT 为 0 表示成功。</span><span class="sxs-lookup"><span data-stu-id="4178f-104">An HRESULT of 0 indicates success.</span></span> <span data-ttu-id="4178f-105">非零 HRESULT 是十六进制形式 0x800*nnnnn*的 OLE 错误代码，但在 `int` 存储过程返回代码中作为值返回时，HRESULT 的形式为 214*nnnnnnn*。</span><span class="sxs-lookup"><span data-stu-id="4178f-105">A nonzero HRESULT is an OLE error code of the hexadecimal form 0x800*nnnnn*, but when returned as an `int` value in a stored procedure return code, HRESULT has the form 214*nnnnnnn*.</span></span>  
  
 <span data-ttu-id="4178f-106">例如， (SQLDMO 传递无效的对象名称。Sqldmo.xyzzy) 到 sp_OACreate 将导致过程返回2147221005的 `int` HRESULT，这是0x800401f3 的十六进制。</span><span class="sxs-lookup"><span data-stu-id="4178f-106">For example, passing an invalid object name (SQLDMO.Xyzzy) to sp_OACreate causes the procedure to return an `int` HRESULT of 2147221005, which is 0x800401f3 in hexadecimal.</span></span>  
  
 <span data-ttu-id="4178f-107">可以使用 `CONVERT(binary(4), @hresult)` 将 `int` HRESULT 转换为 `binary` 值。</span><span class="sxs-lookup"><span data-stu-id="4178f-107">You can use `CONVERT(binary(4), @hresult)` to convert an `int` HRESULT to a `binary` value.</span></span> <span data-ttu-id="4178f-108">但是，使用 `CONVERT(char(10), CONVERT(binary(4), @hresult))` 将产生一个不可读的字符串，因为 HRESULT 的每个字节都被转换成一个 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="4178f-108">However, using `CONVERT(char(10), CONVERT(binary(4), @hresult))` results in an unreadable string, because each byte of the HRESULT is converted to a single ASCII character.</span></span> <span data-ttu-id="4178f-109">您可以使用以下示例 HexToChar 存储过程将 `int` HRESULT 转换为 `char` 包含可读十六进制字符串的值。</span><span class="sxs-lookup"><span data-stu-id="4178f-109">You can use the following sample HexToChar stored procedure to convert an `int` HRESULT to a `char` value that contains a readable hexadecimal string.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT name FROM sys.objects  
          WHERE name = N'dbo.sp_HexToChar')  
    DROP PROCEDURE HexToChar;  
GO  
CREATE PROCEDURE dbo.sp_HexToChar  
    @BinValue varbinary(255),  
    @HexCharValue nvarchar(255) OUTPUT  
AS  
    DECLARE @CharValue nvarchar(255);  
    DECLARE @Position int;  
    DECLARE @Length int;  
    DECLARE @HexString nchar(16);  
    SELECT @CharValue = N'0x';  
    SELECT @Position = 1;  
    SELECT @Length = DATALENGTH(@BinValue);  
    SELECT @HexString = N'0123456789ABCDEF';  
    WHILE (@Position <= @Length)  
    BEGIN  
        DECLARE @TempInt int;  
        DECLARE @FirstInt int;  
        DECLARE @SecondInt int;  
        SELECT @TempInt = CONVERT(int, SUBSTRING(@BinValue,@Position,1));  
        SELECT @FirstInt = FLOOR(@TempInt/16);  
        SELECT @SecondInt = @TempInt - (@FirstInt*16);  
        SELECT @CharValue = @CharValue +  
            SUBSTRING(@HexString, @FirstInt+1, 1) +  
            SUBSTRING(@HexString, @SecondInt+1, 1);  
        SELECT @Position = @Position + 1;  
    END  
    SELECT @HexCharValue = @CharValue;  
GO  
DECLARE @BinVariable varbinary(35);  
DECLARE @CharValue nvarchar(35);  
  
SET @BinVariable = 123456;  
  
EXECUTE dbo.sp_HexToChar  
    @binvalue = @BinVariable,  
    @HexCharValue = @CharValue OUTPUT;  
  
SELECT @BinVariable AS BinaryValue,  
    @CharValue AS CharacterRep;  
GO  
```  
  
 <span data-ttu-id="4178f-110">当其中一个 OLE 自动化过程返回非零的 HRESULT 返回代码时，可以使用以下示例存储过程 **sp_displayoaerrorinfo** 显示 OLE 自动化错误信息。</span><span class="sxs-lookup"><span data-stu-id="4178f-110">You can use the following sample stored procedure, **sp_displayoaerrorinfo** to display OLE Automation error information when one of the OLE Automation procedures returns a nonzero HRESULT return code.</span></span> <span data-ttu-id="4178f-111">此示例存储过程使用 `HexToChar` 。</span><span class="sxs-lookup"><span data-stu-id="4178f-111">This sample stored procedure uses `HexToChar`.</span></span>  
  
```  
CREATE PROCEDURE dbo.sp_DisplayOAErrorInfo  
    @Object int,  
    @HResult int  
AS  
    DECLARE @Output nvarchar(255);  
    DECLARE @HRHex nchar(10);  
    DECLARE @HR int;  
    DECLARE @Source nvarchar(255);  
    DECLARE @Description nvarchar(255);  
    PRINT N'OLE Automation Error Information';  
    EXEC HexToChar @HResult, @HRHex OUT;  
    SELECT @Output = N'  HRESULT: ' + @HRHex;  
    PRINT @Output;  
    EXEC @HR = sp_OAGetErrorInfo  
        @Object,  
        @Source OUT,  
        @Description OUT;  
    IF @HR = 0  
    BEGIN  
        SELECT @Output = N'  Source: ' + @Source;  
        PRINT @Output;  
        SELECT @Output = N'  Description: '  
               + @Description;  
        PRINT @Output;  
    END  
    ELSE  
    BEGIN  
       PRINT N' sp_OAGetErrorInfo failed.';  
       RETURN;  
    END  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="4178f-112">相关内容</span><span class="sxs-lookup"><span data-stu-id="4178f-112">Related Content</span></span>  
 [<span data-ttu-id="4178f-113">sp_OAGetErrorInfo (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4178f-113">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
  
