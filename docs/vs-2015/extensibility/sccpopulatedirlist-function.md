---
title: Funkcja SccPopulateDirList | Dokumentacja firmy Microsoft
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
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358512c94f46971cc91ef3ed065c83ba56e5ad16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42672046"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja SccPopulateDirList](https://docs.microsoft.com/visualstudio/extensibility/sccpopulatedirlist-function).  
  
Ta funkcja określa, które pliki i katalogi (opcjonalnie) są przechowywane w kontroli źródła, biorąc pod uwagę listę katalogów do sprawdzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 nDirs  
 [in] Liczba ścieżek katalogów w `lpDirPaths` tablicy.  
  
 lpDirPaths  
 [in] Tablica ścieżek katalogów do sprawdzenia.  
  
 pfnPopulate  
 [in] Funkcja wywołania zwrotnego do wywołania dla każdej ścieżki katalogu i (opcjonalnie) Nazwa pliku w `lpDirPaths` (zobacz [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Aby uzyskać szczegółowe informacje).  
  
 pvCallerData  
 [in] Niezmieniona wartość, która zostanie przekazany do funkcji wywołania zwrotnego.  
  
 fOptions  
 [in] Kombinacja wartości, które kontrolują, jak są przetwarzane katalogów (zobacz sekcję "PopulateDirList flags" [flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) uzyskać odpowiednie wartości).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja została ukończona pomyślnie.|  
|SCC_E_UNKNOWNERROR|Wystąpił błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko te katalogi i (opcjonalnie) nazw plików, które są rzeczywiście repozytorium kontroli źródła są przekazywane do funkcji wywołania zwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Kody błędów](../extensibility/error-codes.md)

