---
title: Azure Data Lake Store 源 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: chugu
ms.openlocfilehash: e5bce25e303b055d734da6a00c73851f4eb0d7ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587991"
---
# <a name="azure-data-lake-store-source"></a><span data-ttu-id="fb85d-102">Azure Data Lake Store 源</span><span class="sxs-lookup"><span data-stu-id="fb85d-102">Azure Data Lake Store Source</span></span>
  <span data-ttu-id="fb85d-103">“Azure Data Lake Store 源”  组件允许 SSIS 包读取 Azure Data Lake Store 中的数据。</span><span class="sxs-lookup"><span data-stu-id="fb85d-103">The **Azure Data Lake Store Source** component enables an SSIS package to read data from an Azure Data Lake Store.</span></span> <span data-ttu-id="fb85d-104">支持的文件格式为：文本和 Avro。</span><span class="sxs-lookup"><span data-stu-id="fb85d-104">The supported file formats are: Text and Avro.</span></span>
  
## <a name="configure-the-azure-data-lake-store-source"></a><span data-ttu-id="fb85d-105">配置 Azure Data Lake Store 源</span><span class="sxs-lookup"><span data-stu-id="fb85d-105">Configure the Azure Data Lake Store Source</span></span> 
  
1.  <span data-ttu-id="fb85d-106">若要查看 Azure Data Lake Store 源的编辑器，请将“Azure Data Lake Store 源” \*\*\*\* 拖放到数据流设计器上，然后双击打开编辑器。</span><span class="sxs-lookup"><span data-stu-id="fb85d-106">To see the editor for the Azure Data Lake Store Source, drag and drop **Azure Data Lake Store Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
2.  <span data-ttu-id="fb85d-107">对于“Azure Data Lake Store 连接管理器” \*\*\*\* 字段，请指定一个现有的 Azure Data Lake Store 连接管理器，或新建一个引用 Azure Data Lake Store 服务的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="fb85d-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="fb85d-108">对于“文件路径” \*\*\*\* 字段，请指定 Azure Data Lake Store 中源文件的文件路径。</span><span class="sxs-lookup"><span data-stu-id="fb85d-108">For the **File Path** field, specify the file path of the source file in Azure Data Lake Store.</span></span>   
  
    2.  <span data-ttu-id="fb85d-109">对于“文件格式” \*\*\*\* 字段，请指定源文件的文件格式。</span><span class="sxs-lookup"><span data-stu-id="fb85d-109">For the **File format** field, specify the file format of the source file.</span></span>  
  
        <span data-ttu-id="fb85d-110">如果文件格式是文本，则必须指定 "**列分隔符字符**" 值。</span><span class="sxs-lookup"><span data-stu-id="fb85d-110">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="fb85d-111">此外，如果文件中的第一行包含列名称，请选择“在第一个数据行中显示列名称” \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="fb85d-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
3.  <span data-ttu-id="fb85d-112">指定连接信息后，切换到“列” \*\*\*\* 页，将源列映射到 SSIS 数据流的目标列。</span><span class="sxs-lookup"><span data-stu-id="fb85d-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
