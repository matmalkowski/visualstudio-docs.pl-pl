---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2185987f6b635dae4d537231fca3327d0aed003
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Umożliwia tworzenie obiektów w procesie aplikacji przez kod będący poza procesem do aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Identyfikator (CLSID) można utworzyć obiektu klasy.  
  
 `pUnkOuter`  
 [in] Jeśli `NULL`, obiekt nie jest tworzony jako część agregacji. W przeciwnym razie `pUnkOuter` jest wskaźnik do obiektu agregacji `IUnknown` interfejsu (kontrolowanie `IUnknown`).  
  
 `dwClsContext`  
 [in] Kontekst do uruchomienia kodu wykonywalnego. Wartości te są pobierane z wyliczenia `CLSCTX`.  
  
 `riid`  
 [in] Identyfikator interfejsu używany do komunikacji z obiektem.  
  
 `ppvObject`  
 [out] Adres wskaźnika zmienna, która odbiera wskaźnika interfejsu w `riid`. Po pomyślnym powrocie *`ppvObject` znajduje się wskaźnik żądanego interfejsu. W przypadku awarii \* `ppvObject` zawiera `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda deleguje do `CoCreateInstance`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)