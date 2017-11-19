---
title: Funkcja SccCreateSubProject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCreateSubProject
helpviewer_keywords: SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce9c4ec33a76afbba1b334fdc5bac5aee17e334
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="scccreatesubproject-function"></a>Funkcja SccCreateSubProject
Ta funkcja powoduje utworzenie podprojektu o podanej nazwie w obszarze istniejącego projektu nadrzędnego określony przez `lpParentProjPath` argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [w, out] Nazwa użytkownika (do SCC_USER_SIZE, włącznie z terminatorem NULL).  
  
 lpParentProjPath  
 [in] Ciąg identyfikujący ścieżkę projektu nadrzędnego (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpSubProjName  
 [in] Nazwa sugerowane podprojektu (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpAuxProjPath  
 [w, out] Pomocnicze ciąg identyfikujący projektu (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpSubProjPath  
 [w, out] Dane wyjściowe ciąg identyfikujący ścieżkę dla podprojektu (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie utworzono podprojektu.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu nadrzędnego.|  
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować do systemu kontroli źródła.|  
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć podprojektu.|  
|SCC_E_PROJSYNTAXERR|Składnia nieprawidłowy projekt.|  
|SCC_E_UNKNOWNPROJECT|Projekt nadrzędny jest nieznany w wtyczkę kontroli źródła.|  
|SCC_E_INVALIDFILEPATH|Ścieżka pliku nieprawidłowy lub korzystanie z niej.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_CONNECTIONFAILURE|Wystąpił problem podczas połączenia dodatku plug-in kontroli źródła.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli podprojektu o tej nazwie już istnieje, funkcja może zmienić domyślną nazwę można utworzyć unikatowe, na przykład przez dodanie "_\<liczba >" do niego. Obiekt wywołujący musi być przygotowana do zmiany `lpUser`, `lpSubProjPath`, i `lpAuxProjPath`. `lpSubProjPath` i`lpAuxProjPath` argumenty są następnie używane w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). Nie powinny one być modyfikowane przez obiekt wywołujący po powrocie. Te ciągi umożliwiają dla wtyczki do śledzenia informacji wymaganych do skojarzenia z projektu kontroli źródła. Obiekt wywołujący IDE nie będą wyświetlane tych dwóch parametrów po powrocie, ponieważ wtyczki mogą używać sformatowany ciąg, który może nie nadawać się do wyświetlenia. Funkcja zwraca kod powodzenie lub Niepowodzenie i, jeśli to się powiedzie, wypełnia zmiennej `lpSubProjPath` projektu pełną ścieżkę do nowego projektu.  
  
 Ta funkcja jest podobny do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), z tym, że w trybie dyskretnym tworzy projekt, a nie monitowania użytkownika o wybranie jednej. Gdy `SccCreateSubProject` funkcja jest wywoływana, `lpParentProjName` i `lpAuxProjPath` nie będzie pusty i odpowiada to poprawny projekt. Te ciągi są zwykle odbierane IDE z poprzedniego wywołania `SccGetProjPath` funkcji lub [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 `lpUser` Argument jest nazwą użytkownika. Przekazuje IDE w tej samej nazwy użytkownika, który wcześniej otrzymała z `SccGetProjPath`, i wtyczkę kontroli źródła, należy użyć nazwy jako domyślny. Jeśli użytkownik ma już otwartego połączenia z wtyczki, następnie wtyczkę należy spróbować wyeliminowania żadne monity, aby upewnić się, że funkcja działa w trybie dyskretnym. Jednak w przypadku niepowodzenia logowania wtyczkę należy Monituj użytkownika dla nazwy logowania, a po odebraniu prawidłową nazwą logowania, Przekaż ponownie nazwę `lpUser`. Ponieważ wtyczki mogą zmienić tego ciągu, IDE zawsze spowoduje przydzielenie bufor o rozmiarze (SCC_USER_LEN + 1 lub SCC_USER_SIZE, w tym miejsce terminatorem null). Jeśli ciąg zostanie zmieniona, nowe parametry musi być prawidłową nazwą logowania (co najmniej jako prawidłowy jako stary ciąg).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące SccCreateSubProject i SccGetParentProjectPath  
 Dodawanie rozwiązania i projekty do kontroli źródła zostały uproszczone w Visual Studio, aby zminimalizować liczbę razy, które użytkownik jest monitowany o wybranie lokalizacji w systemie kontroli źródła. Te zmiany zostaną aktywowane przez program Visual Studio, jeśli wtyczka do kontroli źródła obsługuje zarówno nowych funkcji `SccCreateSubProject` i `SccGetParentProjectPath`. Jednak następujący wpis rejestru można wyłączyć te zmiany i powrócić do poprzedniej zachowanie środowiska Visual Studio (źródła formantu wtyczek interfejsu API w wersji 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 Jeśli ten wpis rejestru nie istnieje lub ma ustawioną wartość DWORD: 00000000, Visual Studio próbuje użyć nowych funkcji, `SccCreateSubProject` i `SccGetParentProjectPath`.  
  
 Jeśli wpis rejestru jest ustawiony na DWORD: 00000001, Visual Studio zrezygnować z korzystania z tych nowych funkcji i operacje dodania do kontroli źródła działają tak samo jak w poprzednich wersjach programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)