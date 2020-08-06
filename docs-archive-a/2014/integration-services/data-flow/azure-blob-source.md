---
title: Azure blob 源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobsrc.f1
- sql11.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a14c7022437c8a23f898a0f29c211bd9ae82aa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590324"
---
# <a name="azure-blob-source"></a><span data-ttu-id="bba53-102">Azure blob 源</span><span class="sxs-lookup"><span data-stu-id="bba53-102">Azure Blob Source</span></span>
 <span data-ttu-id="bba53-103">借助“Azure blob 源”  组件，SSIS 包可以读取 Azure blob 中的数据。</span><span class="sxs-lookup"><span data-stu-id="bba53-103">The **Azure Blob Source** component enables an SSIS package to read data from an Azure blob.</span></span> <span data-ttu-id="bba53-104">支持的文件格式：CSV 和 AVRO。</span><span class="sxs-lookup"><span data-stu-id="bba53-104">The supported file formats are: CSV and AVRO.</span></span> <span data-ttu-id="bba53-105">若要查看 Azure blob 源的编辑器，请将“Azure blob 源”  拖放到数据流设计器上，然后双击它打开编辑器。</span><span class="sxs-lookup"><span data-stu-id="bba53-105">To see the editor for the Azure Blob Source, drag and drop **Azure Blob Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
1.  <span data-ttu-id="bba53-106">对于“Azure 存储空间连接管理器” \*\*\*\* 字段，请指定一个现有的 Azure 存储空间连接管理器，或新建一个引用 Azure 存储空间帐户的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="bba53-106">For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
2.  <span data-ttu-id="bba53-107">对于“blob 容器名称” \*\*\*\* 字段，请指定包含源文件的 blob 容器的名称。</span><span class="sxs-lookup"><span data-stu-id="bba53-107">For the **Blob container name** field, specify the name of the blob container that contains source files.</span></span>  
  
3.  <span data-ttu-id="bba53-108">对于“blob 名称” \*\*\*\* 字段，请指定 blob 的路径。</span><span class="sxs-lookup"><span data-stu-id="bba53-108">For the **Blob name** field, specify the path for the blob.</span></span>  
  
4.  <span data-ttu-id="bba53-109">对于“blob 文件格式” \*\*\*\* 字段，请指定要使用的 blob 格式。</span><span class="sxs-lookup"><span data-stu-id="bba53-109">For the **Blob file format** field, specify the blob format you want to use.</span></span>  
  
5.  <span data-ttu-id="bba53-110">如果文件格式是 CSV，你必须指定“列分隔符字符” \*\*\*\* 值。</span><span class="sxs-lookup"><span data-stu-id="bba53-110">If the file format is CSV, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="bba53-111">此外，如果文件中的第一行包含列名称，请选择“在第一个数据行中显示列名称” \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="bba53-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
6.  <span data-ttu-id="bba53-112">指定连接信息后，切换到“列” \*\*\*\* 页，将源列映射到 SSIS 数据流的目标列。</span><span class="sxs-lookup"><span data-stu-id="bba53-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
  
  
