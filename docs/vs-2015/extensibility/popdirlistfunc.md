---
title: POPDIRLISTFUNC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed4cb154b1b1f74a6b0b6e64063a826b80364dd3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694117"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [POPDIRLISTFUNC](https://docs.microsoft.com/visualstudio/extensibility/popdirlistfunc).  
  
Jest to funkcja wywołania zwrotnego do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funkcję, aby zaktualizować kolekcję katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które są pod kontrolą źródła.  
  
 `POPDIRLISTFUNC` Wywołania zwrotnego powinna być wywoływana tylko w przypadku katalogów i nazwy plików (na liście umożliwiającej `SccPopulateDirList` funkcji) rzeczywistości będące pod kontrolą źródła.  
  
## <a name="signature"></a>Podpis  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] Wartość użytkownika do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 polecenie bOpcje folderów  
 [in] `TRUE` Jeśli nazwy w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.  
  
 lpDirectoryOrFileName  
 [in] Pełną ścieżkę lokalną do nazwa katalogu lub pliku, który jest pod kontrolą kodu źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 IDE zwraca kod odpowiedni komunikat o błędzie:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Kontynuować przetwarzanie.|  
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|  
|SCC_E_xxx|Wszelkie błędy kontroli odpowiedniego źródła należy zatrzymać przetwarzanie.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `fOptions` parametru `SccPopulateDirList` funkcja zawiera `SCC_PDL_INCLUDEFILES` Flaga, a następnie zawierać będzie lista prawdopodobnie nazw plików, a także nazwy katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Kody błędów](../extensibility/error-codes.md)

