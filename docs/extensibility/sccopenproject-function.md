---
title: Funkcja SccOpenProject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccOpenProject
helpviewer_keywords: SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d61b4fade0775c5e017a85fa5364779bc567b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sccopenproject-function"></a>Funkcja SccOpenProject
Ta funkcja otwiera istniejący projekt kontroli źródła lub tworzy nowy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [w, out] Nazwa użytkownika (nie może przekraczać SCC_USER_SIZE, włącznie z terminatorem NULL).  
  
 lpProjName  
 [in] Ciąg identyfikujący nazwę projektu.  
  
 lpLocalProjPath  
 [in] Ścieżka do folderu roboczego dla projektu.  
  
 lpAuxProjPath  
 [w, out] Opcjonalny ciąg pomocnicze identyfikujący projekt (nie może przekraczać SCC_AUXPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpComment  
 [in] Komentarz do nowego projektu, który jest tworzony.  
  
 lpTextOutProc  
 [in] Funkcja wywołania zwrotnego opcjonalne do wyświetlania tekstu dane wyjściowe z wtyczkę kontroli źródła.  
  
 wartość elementu dwFlags  
 [in] Sygnały czy nowy projekt musi zostać utworzona, jeśli projekt jest nieznany w źródle kontrolować wtyczki. Wartość może być kombinacją `SCC_OP_CREATEIFNEW` i`SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie podczas otwierania projektu.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|  
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować do systemu kontroli źródła.|  
|SCC_E_COULDNOTCREATEPROJECT|Projekt nie istnieje przed wywołaniem;  `SCC_OPT_CREATEIFNEW` została ustawiona flaga, ale nie można utworzyć projektu.|  
|SCC_E_PROJSYNTAXERR|Składnia nieprawidłowy projekt.|  
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany w wtyczka do kontroli źródła, a `SCC_OPT_CREATEIFNEW` nie ustawiono flagi.|  
|SCC_E_INVALIDFILEPATH|Ścieżka pliku nieprawidłowy lub korzystanie z niej.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; Nie można zainicjować systemu kontroli źródła.|  
  
## <a name="remarks"></a>Uwagi  
 IDE może przekazać nazwę użytkownika (`lpUser`), lub po prostu może przekazywać do ciągu pustego wskaźnika. W przypadku nazwy użytkownika, wtyczkę kontroli źródła należy używać go jako domyślny. Jednak jeśli nie przekazano żadnej nazwy lub nazwy logowania nie powiodła się o podanej nazwie, wtyczkę należy Monituj użytkownika do logowania się w i będzie zwracać prawidłową nazwę w `lpUser` po otrzymaniu prawidłową nazwą logowania`.` ponieważ wtyczki może zmienić ciąg nazwy użytkownika , IDE zawsze spowoduje przydzielenie buforu o rozmiarze (`SCC_USER_LEN`+ 1 lub SCC_USER_SIZE, w tym miejsce terminatorem null).  
  
> [!NOTE]
>  Pierwszą akcją IDE może być konieczne przeprowadzenie może być wywołanie `SccOpenProject` funkcji lub [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Z tego powodu z nich mają identyczne `lpUser` parametru.  
  
 `lpAuxProjPath`i`lpProjName` są odczytywane z pliku rozwiązania lub są zwracane po wywołaniu `SccGetProjPath` funkcji. Parametry te zawierają ciągi, które kojarzy wtyczkę kontroli źródła z projektu i mają znaczenie tylko dla wtyczki. Jeśli takie ciągi nie znajdują się w pliku rozwiązania, a użytkownik nie ma został poproszony o Przeglądaj (który zwróci ciąg za pośrednictwem `SccGetProjPath` funkcji), IDE przekazuje puste ciągi dla obu `lpAuxProjPath` i `lpProjName`i oczekuje wartości tych aktualizacji Wtyczka gdy ta funkcja zwraca.  
  
 `lpTextOutProc`jest wskaźnikiem do funkcji wywołania zwrotnego podał IDE na potrzeby wyświetlania danych wyjściowych polecenia wynik wtyczkę kontroli źródła. Ta funkcja wywołania zwrotnego jest szczegółowo opisane w [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Gdy wykorzystać to wtyczka do kontroli źródła, musi mieć ustawiony `SCC_CAP_TEXTOUT` oflagowane w [SccInitialize](../extensibility/sccinitialize-function.md). Jeśli nie ustawiono tę flagę lub IDE nie obsługują tej funkcji, `lpTextOutProc` będzie `NULL`.  
  
 `dwFlags` Parametr określa wynik, w przypadku gdy projekt otwierany obecnie nie istnieje. Składa się z dwóch flag bitowych, `SCC_OP_CREATEIFNEW` i `SCC_OP_SILENTOPEN`. Jeśli istnieje już otwarty projekt, funkcja po prostu otwiera projekt i zwraca `SCC_OK`. Jeśli projekt nie istnieje i `SCC_OP_CREATEIFNEW` flaga jest na, wtyczkę kontroli źródła można utworzyć projektu w systemie kontroli źródła, otwórz go i zwraca `SCC_OK`. Jeśli projekt nie istnieje, a `SCC_OP_CREATEIFNEW` flaga jest wyłączona, wtyczkę należy następnie sprawdzić, czy `SCC_OP_SILENTOPEN` flagi. Jeśli tej flagi nie jest włączony, wtyczka może Monituj użytkownika o nazwę projektu. Jeśli tę flagę znajduje się na, wtyczkę należy po prostu zwracać `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Kolejności wywoływania  
 W trakcie normalnego przebiegu zdarzenia [SccInitialize](../extensibility/sccinitialize-function.md) może zostać wywołane najpierw otworzyć sesji kontroli źródła. Sesja może składać się z wywołania `SccOpenProject`, następuje inne wywołania funkcji API dodatku typu Plug-in kontroli źródła i zakończy się wywołaniem do [SccCloseProject](../extensibility/scccloseproject-function.md). Takie sesjami może zostać powtórzony kilka razy przed [SccUninitialize](../extensibility/sccuninitialize-function.md) jest wywoływana.  
  
 Jeśli zestawy wtyczkę kontroli źródła `SCC_CAP_REENTRANT` bitu w `SccInitialize`, następnie powyżej sekwencji sesji może się powtarzać równolegle. Różne `pvContext` struktury śledzenia różne sesje, w których każdy `pvContext` jest skojarzony z jednym Otwórz projekt w czasie. Na podstawie`pvContext` parametr wtyczki można określić w żadnym wywołaniu konkretnego odwołuje się do projektu. Jeśli bit możliwości `SCC_CAP_REENTRANT` nie jest ustawiona, jest nonreentrant plug-in kontroli źródła są ograniczone możliwości do pracy z wieloma projektami.  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` Bit została wprowadzona w wersji 1.1 API dodatku typu Plug-in kontroli źródła. Nie jest ustawiona, lub w wersji 1.0 jest ignorowana, a wszystkie wersji 1.0 źródła formantu dodatków plug-in są rozpatrywane nonreentrant.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Ograniczenia długości ciągu](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)