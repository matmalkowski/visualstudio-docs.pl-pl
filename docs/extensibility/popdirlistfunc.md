---
title: POPDIRLISTFUNC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44a11e6edc9666fcd7614d467a2c9ffaa86b4365
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Jest to funkcja wywołania zwrotnego do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funkcji, aby zaktualizować kolekcję katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które są pod kontrolą źródła.  
  
 `POPDIRLISTFUNC` Wywołania zwrotnego powinna być wywoływana tylko dla tych katalogów i nazwy pliku (na liście nadawane `SccPopulateDirList` funkcji) faktycznie będących pod kontrolą źródła.  
  
## <a name="signature"></a>Podpis  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] Wartość użytkownika [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 polecenie bOpcje folderów  
 [in] `TRUE` Jeśli nazwa w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.  
  
 lpDirectoryOrFileName  
 [in] Pełną ścieżkę lokalną do pliku lub katalogu nazwę, która jest pod kontrolą kodu źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 IDE zwraca kod błędu odpowiednie:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Kontynuować przetwarzania.|  
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|  
|SCC_E_xxx|Błąd sterowania wszystkie odpowiedniego źródła powinna zostać przerwana przetwarzania.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `fOptions` parametr `SccPopulateDirList` funkcja zawiera `SCC_PDL_INCLUDEFILES` Flaga, a następnie lista prawdopodobnie będzie zawierać nazw plików, a także nazw katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego zaimplementowana IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Kody błędów](../extensibility/error-codes.md)