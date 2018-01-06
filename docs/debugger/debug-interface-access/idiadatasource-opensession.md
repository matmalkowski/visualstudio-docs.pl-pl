---
title: IDiaDataSource::openSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6b7cfaf3e2cf7331576ca79b9820bafb761fc44c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Otwiera sesji podczas wykonywania zapytań symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppSession  
 [out] Zwraca [idiasession —](../../debugger/debug-interface-access/idiasession.md) obiekt reprezentujący otwarty sesji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_UNEXPECTED|[Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md) obiekt nie został wcześniej zainicjowany ze źródłem symboli.|  
|E_INVALIDARG|Nieprawidłowy `ppSession` parametru.|  
|E_OUTOFMEMORY|Za mało pamięci, aby otworzyć sesję.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje otwarcie [idiasession —](../../debugger/debug-interface-access/idiasession.md) obiektów dla źródła danych.  
  
 `IDiaSession`obiekty wykonania zapytania w źródle danych. Sesja zarządza jednej przestrzeni adresowej dla każdego zestawu symboli debugowania. Jeśli plik .exe lub .dll opisanego przez symbole źródła danych jest aktywny w adresie wielu zakresów (na przykład, ponieważ wiele procesów jest załadowany), a następnie należy użyć jednej sesji dla każdego zakresu adresów.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)