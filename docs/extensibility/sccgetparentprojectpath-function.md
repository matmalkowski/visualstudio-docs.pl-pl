---
title: Funkcja SccGetParentProjectPath | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetParentProjectPath
helpviewer_keywords: SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8395d73a48d4c8501ba834b2168b5bcbc8019b8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetparentprojectpath-function"></a>Funkcja SccGetParentProjectPath
Ta funkcja określa ścieżkę projektu nadrzędnego określonego projektu. Ta funkcja jest wywoływana, gdy użytkownik dodaje projektu programu Visual Studio do kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [w, out] Nazwa użytkownika (do SCC_USER_SIZE, włącznie z terminatorem NULL).  
  
 lpProjPath  
 [in] Ciąg identyfikujący ścieżka projektu (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpAuxProjPath  
 [w, out] Pomocnicze ciąg identyfikujący projektu (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpParentProjPath  
 [w, out] Dane wyjściowe ciąg identyfikujący ścieżkę projektu nadrzędnego (maksymalnie SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie uzyskano ścieżkę projektu nadrzędnego.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|  
|SCC_E_INVALIDUSER|Użytkownik może nie logują się do dodatku plug-in kontroli źródła.|  
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany w wtyczkę kontroli źródła.|  
|SCC_E_INVALIDFILEPATH|Ścieżka pliku nieprawidłowy lub korzystanie z niej.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_PROJSYNTAXERR|Składnia nieprawidłowy projekt.|  
|SCC_E_CONNECTIONFAILURE|Problem z połączeniem magazynu.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca powodzenie lub niepowodzenie kod i w razie powodzenia wypełnia zmiennej `lpParentProjPath` ze ścieżką pełną projektu do określonego projektu.  
  
 Ta funkcja zwraca element nadrzędny ścieżka projektu do istniejącego projektu. W projekcie głównym, funkcja zwraca ścieżkę projektu, która została przekazana (to znaczy tej samej ścieżce katalogu głównego projektu). Należy pamiętać, że ścieżka projektu jest ciągiem, który jest przydatny tylko do wtyczkę kontroli źródła.  
  
 IDE przygotowany do zmiany `lpUser` i `lpAuxProjPath` również parametry. IDE zostanie zachować te ciągi i przekazywać je do [SccOpenProject](../extensibility/sccopenproject-function.md) po otwarciu tego projektu w przyszłości. Te ciągi, w związku z tym umożliwiają dla wtyczki do śledzenia informacji wymaganych do skojarzenia z projektu kontroli źródła.  
  
 Ta funkcja jest podobny do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ale nie monituje użytkownika o wybranie projektu. Nigdy nie tworzy nowy projekt, ale działa tylko z istniejącego projektu.  
  
 Gdy `SccGetParentProjectPath` jest nazywany `lpProjPath` i `lpAuxProjPath` nie będzie pusty i odpowiada to poprawny projekt. Te ciągi są zwykle odbierane IDE z poprzedniego wywołania `SccGetProjPath` funkcji.  
  
 `lpUser` Argument jest nazwą użytkownika. Przekazuje IDE w tej samej nazwy użytkownika, który wcześniej otrzymała z `SccGetProjPath` funkcji i wtyczkę kontroli źródła, należy użyć nazwy jako domyślny. Jeśli użytkownik ma już otwartego połączenia z wtyczki, następnie wtyczkę należy spróbować wyeliminowania żadne monity, aby upewnić się, że funkcja działa w trybie dyskretnym. Jednak w przypadku niepowodzenia logowania wtyczkę należy Monituj użytkownika dla nazwy logowania, a po odebraniu prawidłową nazwą logowania, Przekaż ponownie nazwę `lpUser`. Ponieważ wtyczki mogą zmienić tego ciągu, IDE zawsze spowoduje przydzielenie buforu o rozmiarze (`SCC_USER_LEN`+ 1). Jeśli ciąg zostanie zmieniona, nowe parametry musi być prawidłową nazwą logowania (co najmniej jako prawidłowy jako stary ciąg).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące SccCreateSubProject i SccGetParentProjectPath  
 Dodawanie rozwiązania i projekty do kontroli źródła zostały uproszczone w Visual Studio, aby zminimalizować liczbę razy, które użytkownik jest monitowany o wybranie lokalizacji w systemie kontroli źródła. Te zmiany zostaną aktywowane przez program Visual Studio, jeśli wtyczka do kontroli źródła obsługuje zarówno nowych funkcji [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) i `SccGetParentProjectPath` funkcji. Jednak następujący wpis rejestru można wyłączyć te zmiany i powrócić do poprzedniej zachowanie środowiska Visual Studio (źródła formantu wtyczek interfejsu API w wersji 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 Jeśli ten wpis rejestru nie istnieje lub ma ustawioną wartość DWORD: 00000000, Visual Studio próbuje użyć nowych funkcji, `SccCreateSubProject`i`SccGetParentProjectPath`.  
  
 Jeśli wpis rejestru jest ustawiony na DWORD: 00000001, Visual Studio zrezygnować z korzystania z tych nowych funkcji i operacje dodania do kontroli źródła działają tak samo jak w poprzednich wersjach programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)