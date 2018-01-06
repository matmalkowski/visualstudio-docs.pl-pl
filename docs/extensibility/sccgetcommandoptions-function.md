---
title: Funkcja SccGetCommandOptions | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetCommandOptions
helpviewer_keywords: SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3bce2922c961bf29f320f047a91057a638fe708a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetcommandoptions-function"></a>Funkcja SccGetCommandOptions
Ta funkcja monituje użytkownika o zaawansowane opcje dla danego polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 iCommand  
 [in] Polecenia, dla których wymagane są zaawansowane opcje (zobacz [kod polecenia](../extensibility/command-code-enumerator.md) możliwe wartości).  
  
 ppvOptions  
 [in] Struktura opcji (można też `NULL`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_I_ADV_SUPPORT|Wtyczka do kontroli źródła obsługuje zaawansowane opcje dla polecenia.|  
|SCC_I_OPERATIONCANCELED|Użytkownik anulował źródła formantu plug w **opcje** okno dialogowe.|  
|SCC_E_OPTNOTSUPPORTED|Wtyczka do kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ISCHECKEDOUT|Nie można wykonać tej operacji na pliku, który jest obecnie wyewidencjonowywany.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołania tej funkcji po raz pierwszy z `ppvOptions` = `NULL` do określenia, czy wtyczkę kontroli źródła obsługuje funkcję Zaawansowane opcje dla tego polecenia. Jeśli wtyczka obsługuje funkcji dla tego polecenia, IDE wywołania tej funkcji ponownie, gdy użytkownik zażąda zaawansowane opcje (zwykle implementowany jako **zaawansowane** przycisk w oknie dialogowym) i dostarcza wskaźnik inną niż NULL dla `ppvOptions` wskazującego `NULL` wskaźnika. Wtyczka przechowuje opcje zaawansowane określone przez użytkownika w strukturze prywatnych i zwraca wskaźnik do tej struktury w `ppvOptions`. Ta struktura są następnie przekazywane do wszystkich funkcji API dodatku typu Plug-in kontroli źródła, w które należy się dowiedzieć, łącznie z kolejnych wywołań `SccGetCommandOptions` funkcji.  
  
 Przykładem mogą pomóc wyjaśnienia tej sytuacji.  
  
 Użytkownik wybierze **uzyskać** Wyświetla polecenia i IDE **uzyskać** okno dialogowe. Wywołania IDE `SccGetCommandOptions` działać z `iCommand` ustawioną `SCC_COMMAND_GET` i `ppvOptions` ustawioną `NULL`. To jest interpretowany przez wtyczka do kontroli źródła jako pytanie, "Masz opcje zaawansowane dla tego polecenia?" Jeśli wtyczka zwraca `SCC_I_ADV_SUPPORT`, wyświetla IDE **zaawansowane** przycisku na jego **uzyskać** okno dialogowe.  
  
 Po raz pierwszy użytkownik klika polecenie **zaawansowane** przycisku IDE ponownie wywołuje `SccGetCommandOptions` działanie, tym razem z innej`NULL``ppvOptions` wskazującego `NULL` wskaźnika. Wyświetla wtyczki własną **opcji Pobierz** okno dialogowe monituje użytkownika o informacje, umieszcza w własną strukturę i zwraca wskaźnik do tej struktury w `ppvOptions`.  
  
 Gdy użytkownik kliknie **zaawansowane** ponownie w tym samym oknie dialogowym IDE wywołuje `SccGetCommandOptions` funkcja ponownie bez zmieniania `ppvOptions`, dzięki czemu struktury jest przekazywana do wtyczki. Dzięki temu dodatek plug-in ponownie zainicjować jej okno dialogowe na wartości, które użytkownik ma ustawione wcześniej. Wtyczka modyfikuje struktury w miejscu przed zwróceniem.  
  
 Ponadto, kiedy użytkownik kliknie **OK** w IDE **uzyskać** okno dialogowe, wywołania IDE [SccGet](../extensibility/sccget-function.md), przekazanie struktury zwracane w `ppvOptions` zawierający Opcje zaawansowane.  
  
> [!NOTE]
>  Polecenie `SCC_COMMAND_OPTIONS` jest używany podczas wyświetlania IDE **opcje** okno dialogowe, w którym użytkownik może ustawić preferencje, które kontrolują sposób działania integracji. Jeśli wtyczka do kontroli źródła chce dostarczyć własny okno dialogowe preferencji, będzie możliwe wyświetlenie jej **zaawansowane** przycisk w oknie dialogowym Preferencje programu IDE. Wtyczka jest ponosi uzyskanie i przechowywanie tych informacji; IDE nie używać jej lub zmodyfikuj go.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Polecenie kodu](../extensibility/command-code-enumerator.md)