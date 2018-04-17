---
title: Funkcja SccEnumChangedFiles | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 762bda21f8480224347bd0c8c202c282298e07cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccenumchangedfiles-function"></a>Funkcja SccEnumChangedFiles
Podana lista lokalnych plików, ta funkcja określa pliki, które różnią się od odpowiedniej wersji w bazie danych kontroli kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 cFiles  
 [in] Liczba nazw plików określonych w `lpFileNames` tablicy. Określa rozmiar `plIsFileDifferent` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików lokalnych do sprawdzenia.  
  
 plIsFileDifferent  
 [w, out] Tablica wartości wskazujący stan różnica każdego pliku (Tablica musi mieć co najmniej `cFiles` wpisy). Różną od zera oznacza, że plik jest inny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja została ukończona pomyślnie.|  
|SCC_UNSPECIFIEDERROR|Błąd rodzajowy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)