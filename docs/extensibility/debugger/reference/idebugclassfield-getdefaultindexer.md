---
title: IDebugClassField::GetDefaultIndexer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::GetDefaultIndexer
helpviewer_keywords: IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d30388b170f4a7de672fbdda11ccead83acce32c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Pobiera nazwę indeksatora domyślne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```csharp  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrIndexer`  
 [out] Zwraca ciąg zawierający nazwę indeksatora domyślne.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia zwraca S_OK lub zwraca wartości S_FALSE, jeśli nie indeksatora nie domyślne. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Indeksator domyślnej klasy jest właściwość, która jest oznaczona jako `Default` właściwość uzyskuje dostęp do tablicy. To jest specyficzne dla [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Oto przykład indeksatora domyślne, zadeklarowany w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] i sposobie ich użycia.  
  
```vb  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)