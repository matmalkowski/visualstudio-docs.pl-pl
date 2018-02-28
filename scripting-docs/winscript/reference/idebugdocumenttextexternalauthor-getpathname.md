---
title: IDebugDocumentTextExternalAuthor::GetPathName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Zwraca pełną ścieżkę i nazwę dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 [out] Ciąg zawierający Pełna ścieżka i nazwa pliku.  
  
 `pfIsOriginalFile`  
 [out] Wartość logiczna wskazująca, czy nazwa i ścieżka pliku odwoływać się do oryginalnego dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Plik źródłowy nie można utworzyć ani określić.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca Pełna ścieżka i nazwa pliku dokumentu.  
  
 Jeśli `pfIsOriginalFile` jest wartość FAŁSZ, ścieżkę i nazwę pliku w `pbstrLongName` odwoływać się do nowo utworzonego pliku tymczasowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)