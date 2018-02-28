---
title: IDebugDocumentHost::GetPathName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42fffa160a1f5b55dc9ba0287c2fdf3073e27e0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Zwraca pełną ścieżkę i nazwę pliku źródłowego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 [out] Ciąg zawierający nazwę długo.  
  
 `pfIsOriginalFile`  
 [out] Flaga oznacza to PRAWDA, jeśli `pbstrLongName` odwołuje się do oryginalnego pliku dokumentu, wartość false w przeciwnym razie wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Plik źródłowy nie można utworzyć lub określić.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pełną ścieżkę i nazwę pliku źródłowego dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)