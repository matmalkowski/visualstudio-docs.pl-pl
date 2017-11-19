---
title: Interfejs IDebugDocumentProvider | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>Interfejs IDebugDocumentProvider
Zapewnia metodę dla wystąpienia dokumentu na żądanie.  
  
## <a name="remarks"></a>Uwagi  
 Oznacza to, pośrednie dla wystąpienia dokumentu:  
  
-   Umożliwia dokumentu do załadowania, gdy jest to potrzebne.  
  
-   Umożliwia obiektu dokumentu muszą być zawarte w debugerze IDE.  
  
-   Zezwala na wiele sposobów uzyskać dostęp do tego samego obiektu dokumentu.  
  
 To skutecznie oddziela go od jego dostawcy i dostawca może zawierać dodatkowe informacje o kontekście czasu wykonywania.  
  
 Oprócz dziedziczone z metody `IDebugDocumentInfo`, `IDebugDocumentProvider` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Powoduje, że dokument utworzone, jeśli jeszcze nie istnieje.|