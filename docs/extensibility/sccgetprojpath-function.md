---
title: Funkcja SccGetProjPath | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetProjPath
helpviewer_keywords: SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ce41826a3a0d778c5a417496d47f290e97806fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetprojpath-function"></a>Funkcja SccGetProjPath
Ta funkcja monituje użytkownika o ścieżkę projektu, który jest ciągiem, który jest przydatny tylko do wtyczkę kontroli źródła. Jest ona wywoływana, gdy użytkownik jest:  
  
-   Tworzenie nowego projektu  
  
-   Dodawanie istniejącego projektu do kontroli wersji  
  
-   Próby znalezienia istniejącego projektu kontroli wersji  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [w, out] Nazwa użytkownika (nie może przekraczać SCC_USER_SIZE, włącznie z terminatorem NULL)  
  
 lpProjName  
 [w, out] Nazwa projektu IDE, obszar roboczy projektu ani pliku reguł programu make (nie może przekraczać SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 lpLocalPath  
 [w, out] Ścieżka roboczego projektu. Jeśli `bAllowChangePath` jest `TRUE`, wtyczkę kontroli źródła można zmodyfikować tego ciągu (nie może przekraczać _max_path —, włącznie z terminatorem null).  
  
 lpAuxProjPath  
 [w, out] Bufor dla ścieżki zwrócony projektu (nie może przekraczać SCC_PRJPATH_SIZE, włącznie z terminatorem NULL).  
  
 bAllowChangePath  
 [in] Jeśli jest to `TRUE`, wtyczkę kontroli źródła może monitować o podanie i modyfikowania `lpLocalPath` ciągu.  
  
 pbNew  
 [w, out] Wartość przychodzących wskazuje, czy można utworzyć nowy projekt. Wartość zwracana wskazuje sukces tworzenia projektu:  
  
|przychodzące|Interpretacja|  
|--------------|--------------------|  
|WARTOŚĆ TRUE|Użytkownik może utworzyć nowy projekt.|  
|FAŁSZ|Użytkownik nie może utworzyć nowego projektu.|  
  
|Wychodzące|Interpretacja|  
|--------------|--------------------|  
|WARTOŚĆ TRUE|Nowy projekt został utworzony.|  
|FAŁSZ|Wybrano istniejący projekt.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Projekt został pomyślnie utworzony lub pobrać.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji.|  
|SCC_E_CONNECTIONFAILURE|Wystąpił problem podczas próby połączenia z systemu kontroli źródła.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Celem tej funkcji jest dla IDE w celu uzyskania parametry `lpProjName` i `lpAuxProjPath`. Po wtyczkę kontroli źródła monituje użytkownika o informacje, przekazuje te dwa ciągi do środowiska IDE. IDE będzie się powtarzać te ciągi w pliku rozwiązania i przekazuje je do [SccOpenProject](../extensibility/sccopenproject-function.md) zawsze, gdy użytkownik otwiera tego projektu. Te ciągi włączyć dodatek do śledzenia informacji skojarzone z projektem.  
  
 Podczas wywołania funkcji `lpAuxProjPath` jest ustawiony na pusty ciąg. `lProjName`może być pusta, lub może zawierać nazwy projektu IDE, która wtyczkę kontroli źródła może używać lub zignorować. Gdy funkcja zwraca wartość pomyślnie, wtyczkę zwraca dwa ciągi odpowiednie. IDE nie czyni żadnych założeń dotyczących te ciągi, nie będzie używać ich, a nie zezwoli użytkownikowi na modyfikowanie ich. Jeśli użytkownik chce zmienić ustawienia, wywoła IDE `SccGetProjPath` ponownie, przekazywanie w tej samej wartości otrzymała poprzednio. Dzięki temu wtyczki pełną kontrolę nad tych dwóch ciągów.  
  
 Aby uzyskać `lpUser`, IDE może przekazać nazwę użytkownika lub po prostu może przekazywać do ciągu pustego wskaźnika. W przypadku nazwy użytkownika, wtyczkę kontroli źródła należy używać go jako domyślny. Jednak nie przekazano żadnej nazwy lub nazwy logowania nie powiodła się o podanej nazwie, wtyczkę należy Monituj użytkownika o logowania i hasło ponownie nazwę `lpUser` po otrzymaniu prawidłową nazwą logowania. Ponieważ wtyczki mogą zmienić tego ciągu, IDE zawsze spowoduje przydzielenie buforu o rozmiarze (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  Pierwszą akcją, który wykonuje IDE może być wywołania `SccOpenProject` funkcji lub `SccGetProjPath` funkcji. W związku z tym obie z nich ma takie same `lpUser` parametr, który umożliwia logowania użytkownika w każdej chwili wtyczkę kontroli źródła. Nawet jeśli powrót z funkcji oznacza błąd, wtyczkę należy podać ten ciąg z prawidłową nazwą logowania.  
  
 `lpLocalPath`jest to katalog, w którym użytkownik przechowuje projektu. Może on być pustym ciągiem. Jeśli nie ma katalog nie jest obecnie zdefiniowane (jak w przypadku próby pobrania projektu z systemu kontroli źródła użytkownika) oraz jeśli `bAllowChangePath` jest `TRUE`, wtyczkę kontroli źródła można monit o podanie danych wejściowych lub użyć innej metody do umieszczenia jej ciąg do własnych `lpLocalPath`. Jeśli `bAllowChangePath` jest `FALSE`, wtyczka nie należy zmieniać ciągu, ponieważ użytkownik pracuje się już w określonym katalogu.  
  
 Jeśli użytkownik tworzy nowy projekt, które należy umieścić pod kontrolą źródła, wtyczkę kontroli źródła może nie powoduje utworzenia go w systemie kontroli źródła w czasie `SccGetProjPath` jest wywoływana. Zamiast tego ponownie przekazuje ciąg wraz z różną od zera wartość `pbNew`, wskazując, że projekt zostanie utworzony w systemie kontroli źródła.  
  
 Na przykład, jeśli użytkownik w **nowy projekt** kreatora w programie Visual Studio dodaje własny projekt do kontroli źródła, ta funkcja wymaga programu Visual Studio i wtyczki Określa, czy można utworzyć nowy projekt w systemie kontroli źródła do zawiera projekt programu Visual Studio. Gdy użytkownik kliknie **anulować** przed zakończeniem działania kreatora, projekt nigdy nie zostanie utworzony. Gdy użytkownik kliknie **OK**, Visual Studio wymaga `SccOpenProject`, przekazując `SCC_OPT_CREATEIFNEW`, i projektu pod kontrolą źródła jest tworzony w tym czasie.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)