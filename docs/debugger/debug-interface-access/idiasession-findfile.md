---
title: IDiaSession::findFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 99f3d58b444f2bf360c76dcd5f95b03ac50f7e32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Pobiera pliki źródłowe compiland i nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCompiland`  
 [in] [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt reprezentujący compiland do użycia jako kontekst dla wyszukiwania. Ustaw ten parametr, `NULL` można znaleźć plików źródłowych w wszystkie jednostki kompilacji.  
  
 `name`  
 [in] Określa nazwę pliku źródłowego, które mają zostać pobrane. Ustaw ten parametr, `NULL` źródła wszystkie pliki do pobrania.  
  
 `option`  
 [in] Określa opcje porównania stosowane do wyszukiwania nazwy. Wartości z [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md) wyliczenie można samodzielnie lub w połączeniu.  
  
 `ppResult`  
 [out] Zwraca [idiaenumsourcefiles —](../../debugger/debug-interface-access/idiaenumsourcefiles.md) pobrać obiekt, który zawiera listę plików źródłowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsourcefiles —](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)