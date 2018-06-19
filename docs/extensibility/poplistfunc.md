---
title: POPLISTFUNC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 950807b0568a28763b369fef4041c69b264d12fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138567"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Tego wywołania zwrotnego został dostarczony do [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE i jest używany przez wtyczkę kontroli źródła, aby zaktualizować listę plików lub katalogów (również dostarczony do `SccPopulateList` funkcji).  
  
 Gdy użytkownik wybierze **uzyskać** poleceń w środowisku IDE programu IDE Wyświetla pole listy wszystkich plików, które użytkownik może uzyskać. Niestety IDE nie może określić dokładnej listy wszystkich plików, które użytkownik może uzyskać; tylko dodatek ma tej listy. Jeśli inni użytkownicy dodane pliki do projektu kontroli kodu źródłowego, te pliki powinny zostać wyświetlone na liście, ale IDE nie wie o nich. IDE tworzy listę plików, które uważa, że użytkownik może uzyskać. Przed wyświetleniem tej listy do użytkownika wywołuje [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` nadanie wtyczkę kontroli źródła możliwość dodawania i usuwania plików z listy.  
  
## <a name="signature"></a>Podpis  
 Wtyczka do kontroli źródła modyfikuje listę przez wywołanie funkcji zaimplementowana IDE z prototypem następujące:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 `pvCallerData` Parametr przekazany przez wywołującego (IDE) do [SccPopulateList](../extensibility/sccpopulatelist-function.md). Wtyczkę kontroli źródła należy założono nic o wartości tego parametru.  
  
 fAddRemove  
 Jeśli `TRUE`, `lpFileName` plik, który powinien zostać dodany do listy plików. Jeśli `FALSE`, `lpFileName` plik, który powinien zostać usunięty z listy.  
  
 nStatus  
 Stan `lpFileName` (kombinację `SCC_STATUS` bitów; zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md) szczegółowe informacje).  
  
 lpFileName  
 Pełna ścieżka katalogu nazwy pliku, aby dodać lub usunąć z listy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`TRUE`|Wtyczki można kontynuować podczas wywoływania tej funkcji.|  
|`FALSE`|Wystąpił problem po stronie IDE (na przykład poza sytuacji pamięci). Wtyczkę należy zatrzymać operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego pliku, który chce wtyczkę kontroli źródła na dodawanie do lub usuwanie z listy plików, wywołuje tej funkcji, przekazując `lpFileName`. `fAddRemove` Flaga wskazuje nowy plik i dodać do listy lub stary plik do usunięcia. `nStatus` Parametru zapewnia stan pliku. Po zakończeniu SCC wtyczki dodawania i usuwania plików zwraca z [SccPopulateList](../extensibility/sccpopulatelist-function.md) wywołania.  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` Możliwości bit jest wymagana dla programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego zaimplementowana IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-in kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)