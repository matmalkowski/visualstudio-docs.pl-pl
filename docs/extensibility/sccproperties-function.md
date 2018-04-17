---
title: Funkcja SccProperties | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d126a4691332f1121ebfc99a84b180d1e99f3d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccproperties-function"></a>Funkcja SccProperties
Ta funkcja zawiera właściwości kontroli źródła dla pliku lub projektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpFileName  
 [in] W pełni kwalifikowana nazwa pliku lub projektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Właściwości pomyślnie zostały wyświetlone.|  
|SCC_I_RELOADFILE|System kontroli wersji zmodyfikował właściwości pliku, więc IDE należy załadować ponownie ten plik.|  
|SCC_E_PROJNOTOPEN|Określony projekt nie został otwarty w kontroli źródła.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do wyświetlania właściwości tego pliku lub projektu.|  
|SCC_E_FILENOTCONTROLLED|Określony plik lub projektu nie jest pod kontrolą źródła.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieznany lub ogólny błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła są wyświetlane właściwości w jego własnej okno dialogowe.  
  
 Właściwości są definiowane przez wtyczkę kontroli źródła i może różnić się od wtyczki do wtyczki. Jeśli wtyczka umożliwia użytkownikowi zmianę właściwości kontroli źródła pliku, powinien on zwrócić `SCC_I_RELOAD` sygnalizują IDE, do którego ten plik lub projekt musi zostać ponownie załadowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)