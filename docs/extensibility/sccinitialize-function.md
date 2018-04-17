---
title: Funkcja SccInitialize | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1146573f3d969ffc5cd56576ba92faa4e6ffdce0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccinitialize-function"></a>Funkcja SccInitialize
Ta funkcja inicjuje wtyczkę kontroli źródła i zapewnia możliwości i ograniczeń dotyczących zintegrowane środowisko programistyczne (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppvContext`  
 [in] Wtyczka do kontroli źródła może tutaj umieść wskaźnik do struktury jego kontekstu.  
  
 `hWnd`  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 `lpCallerName`  
 [in] Nazwa programu wywoływania wtyczka do kontroli źródła.  
  
 `lpSccName`  
 [w, out] Buforu, w którym wtyczkę kontroli źródła umieszcza własną nazwę (aby nie przekroczyć `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Zwraca dodatku plug-in flagi możliwości kontroli źródła.  
  
 `lpAuxPathLabel`  
 [w, out] Buforu, w którym wtyczkę kontroli źródła umieszcza ciąg opisujący `lpAuxProjPath` zwrócona przez parametr [SccOpenProject](../extensibility/sccopenproject-function.md) i [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (aby nie przekroczyć `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Zwraca wartość maksymalna dopuszczalna długość komentarz wyewidencjonowania.  
  
 `pnCommentLen`  
 [out] Zwraca maksymalną długość dopuszczalną wartość dla innych komentarzy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Inicjowanie kontroli źródła zakończyła się pomyślnie.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać podanej operacji.|  
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; Nie można zainicjować systemu kontroli źródła.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołanie tej funkcji po pierwszym załadowaniu wtyczkę kontroli źródła. Umożliwia on IDE w celu przekazania pewne informacje, takie jak nazwa wywołującego, wtyczki. IDE pobiera ponownie również pewne informacje, takie jak maksymalną dozwoloną długość komentarze oraz funkcje do podłączenia do firmy.  
  
 `ppvContext` Wskazuje `NULL` wskaźnika. Wtyczka do kontroli źródła można przydzielić do własnego użytku struktury i przechowywać wskaźnik do tej struktury w `ppvContext`. IDE przechodzą ten wskaźnik co innych funkcji VSSCI interfejsu API, umożliwiając wtyczki ma dostępne informacje o kontekście bez konieczności przechowywania globalnej i obsługuje wiele wystąpień wtyczki. Ta struktura powinien alokację kiedy [SccUninitialize](../extensibility/sccuninitialize-function.md) jest wywoływana.  
  
 `lpCallerName` i `lpSccName` parametry włączyć IDE i wtyczkę kontroli źródła do wymiany nazwy. Te nazwy mogą być stosowane jedynie w celu rozróżnienia wielu wystąpień lub może faktycznie pojawią się one w menu lub w oknach dialogowych.  
  
 `lpAuxPathLabel` Parametr jest używany jako komentarz do identyfikowania ścieżkę pomocniczą projektu, który jest przechowywany w pliku rozwiązania przekazany do kontroli źródła wtyczek w wywołaniu ciąg [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] ciąg "SourceSafe projektu:"; inne źródła formantu dodatków plug-in powinien zaniechania przy użyciu tego określonego ciągu.  
  
 `lpSccCaps` Parametru zapewnia kontrolę źródła wtyczki miejsce do przechowywania flag bitowych wskazującą możliwości podłączenia do firmy. (Aby uzyskać pełną listę możliwości flag bitowych, zobacz [flagi możliwości](../extensibility/capability-flags.md)). Na przykład jeśli wtyczka planów zapis wyniki do funkcję wywołania zwrotnego dostarczane przez obiekt wywołujący wtyczki ustawiał możliwości bit SCC_CAP_TEXTOUT. Spowoduje to sygnał IDE można utworzyć okna dla wyników kontroli wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Flagi możliwości](../extensibility/capability-flags.md)