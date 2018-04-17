---
title: Funkcja SccDiff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 30d8d6a4b8b400088d5feed663c8257215a0f8a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccdiff-function"></a>Funkcja SccDiff
Ta funkcja wyświetla (lub opcjonalnie tylko wyszukuje) systemu kontroli różnice między bieżącego pliku (na dysku lokalnym) i jego ostatniej wersji w źródle.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpFileName  
 [in] Nazwa pliku, dla którego wnioskuje się różnicy.  
  
 fOptions  
 [in] Polecenie flagi. Aby uzyskać więcej informacji, zobacz uwagi.  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Działającą wersją kopiowania i serwera są identyczne.|  
|SCC_I_FILESDIFFERS|Kopia robocza różni się od wersji pod kontrolą źródła.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowana.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; Nie można uzyskać plik różnicy.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja służy do dwóch różnych celów. Domyślnie Wyświetla listę zmian w pliku. Wtyczka do kontroli źródła otwiera okna, niezależnie od format zdecyduje, aby wyświetlić różnice między użytkownika pliku na dysku i najnowszą wersję plików pod kontrolą źródła.  
  
 Alternatywnie IDE może po prostu musisz określić, czy plik został zmieniony. Na przykład IDE trzeba ustalić, czy jest bezpiecznie wyewidencjonować plik bez informowania o tym użytkownika. W takim przypadku przekazuje IDE w `SCC_DIFF_CONTENTS` flagi. Wtyczka do kontroli źródła należy sprawdź plik na dysku, po bicie, względem pliku kontrolowanego przez źródło i zwraca wartość wskazującą, czy dwa pliki różnią się bez wyświetlania niczego do użytkownika.  
  
 Jak zoptymalizować wydajność, wtyczkę kontroli źródła może używać zamiast na podstawie sumy kontrolnej lub sygnatury czasowej zamiast porównania po bicie wymagane przez `SCC_DIFF_CONTENTS`: formach porównania są oczywiście szybsze, ale mniej wiarygodne. Nie wszystkie systemy kontroli źródła może obsługują tych metod alternatywnych porównania i wtyczki może mieć wrócił do porównania zawartości. Wtyczki sterowania wszystkie źródła muszą co najmniej obsługuje porównania zawartości.  
  
> [!NOTE]
>  Flagi szybkiego różnica wzajemnie się wykluczają. Jest on prawidłowy do przekazania żadnych flag, ale nie jest prawidłową jednocześnie przekazać więcej niż jeden. `SCC_DIFF_QUICK_DIFF`, która jest maską łączy wszystkie flagi może służyć do testowania, ale nigdy nie powinien zostać przekazany jako parametr.  
  
|`fOption`|Znaczenie|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Porównania bez uwzględniania wielkości liter (może służyć do różnica szybkie lub visual).|  
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (może służyć do różnica szybkie lub visual).|  
|SCC_DIFF_QD_CONTENTS|Dyskretnie porównuje plik po bicie.|  
|SCC_DIFF_QD_CHECKSUM|Porównuje dyskretnie pliku za pośrednictwem sumy kontrolnej, jeśli są obsługiwane. Jeśli nie jest obsługiwana, powraca do porównania zawartości.|  
|SCC_DIFF_QD_TIME|Porównuje dyskretnie pliku za pośrednictwem jego sygnatury czasowej, jeśli są obsługiwane. Jeśli nie jest obsługiwana, powraca do porównania zawartości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)