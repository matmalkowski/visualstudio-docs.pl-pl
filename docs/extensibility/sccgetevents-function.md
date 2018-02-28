---
title: Funkcja SccGetEvents | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e2e9a22d0340774087fab8dd7dc564f415d9d9aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetevents-function"></a>Funkcja SccGetEvents
Ta funkcja pobiera zdarzeń w kolejce stanu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 lpFileName  
 [w, out] Bufor, w którym wtyczkę kontroli źródła umieszcza nazwa zwróconego pliku (maksymalnie _max_path — znaków).  
  
 lpStatus  
 [w, out] Zwraca kod stanu (zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md) możliwe wartości).  
  
 pnEventsRemaining  
 [w, out] Zwraca liczbę wpisów, które pozostanie w kolejce po tym wywołaniu. Jeśli ta liczba jest duży, wywołujący może podjąć [SccQueryInfo](../extensibility/sccqueryinfo-function.md) uzyskanie wszystkich informacji naraz.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pobierz zdarzenia zakończyło się pomyślnie.|  
|SCC_E_OPNOTSUPPORTED|Ta funkcja nie jest obsługiwana.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana podczas przetwarzania bezczynności, aby zobaczyć, czy zostały wszystkie aktualizacje stanu plików pod kontrolą źródła. Stan wszystkich plików, które przechowuje wtyczkę kontroli źródła i zawsze, gdy zmiana stanu jest odnotowany przez wtyczkę, stan i skojarzony plik są przechowywane w kolejce. Gdy `SccGetEvents` jest nazywany górnej element kolejki jest pobierany i zwracane. Ta funkcja jest ograniczona do zwracania tylko buforowanych informacji i musi mieć bardzo sprawność (czyli, nie odczytu dysku lub system kontroli źródła jest proszony o podanie stanu); w przeciwnym razie wydajność IDE może rozpocząć zmniejszenie.  
  
 Jeśli nie ma stanu aktualizacji do raportu, wtyczkę kontroli źródła są przechowywane pustego ciągu w buforze wskazywana przez `lpFileName`. W przeciwnym razie wtyczki przechowuje pełną nazwę ścieżki pliku, dla których informacje o stanie został zmieniony i zwraca kod stanu odpowiednie (jedna z wartości w [kod stanu pliku](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)