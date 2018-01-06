---
title: "Najlepsze rozwiązania dotyczące wdrażania dodatku Plug-in kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e406bc0cd5d7e4cb082e1f5e34fa6645538d02ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Najlepsze rozwiązania dotyczące wdrażania dodatku Plug-in kontroli źródła
Poniższe szczegóły techniczne ułatwia prawidłowo zaimplementować wtyczka do kontroli źródła w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problemy z pamięcią zarządzania  
 W większości przypadków zintegrowane środowisko programistyczne (IDE), czyli wywołującego zwalnia i przydziela pamięć. Wtyczka do kontroli źródła zwraca ciągów i innych elementów w buforów przydzielone przez obiekt wywołujący. Wyjątki w opisach określonych funkcji, w którym występują.  
  
## <a name="arrays-of-file-names"></a>Tablice nazw plików  
 Po upływie tablica plików nie jest przekazywany jako ciągłe tablica nazw plików. Jest przekazywany jako tablicy wskaźników do nazwy pliku. Na przykład w [SccGet](../extensibility/sccget-function.md), nazwy plików są przekazywane `lpFileNames` parametru, gdzie `lpFileNames` faktycznie wskaźnik do `char **`. `lpFileNames`[0] jest wskaźnikiem do pierwszej nazwy `lpFileNames`[1]. istnieje wskaźnik do drugiej nazwy i tak dalej.  
  
## <a name="large-model"></a>Duże modelu  
 Wszystkie wskaźniki są 32-bitowy, nawet w przypadku 16-bitowych systemach operacyjnych.  
  
## <a name="fully-qualified-paths"></a>Pełni kwalifikowanymi ścieżkami  
 Gdy nazwy plików lub katalogów są określone jako argumenty, muszą one być w pełni kwalifikowanych ścieżek lub ścieżek UNC, bez końcowej ukośników odwrotnych. Jest odpowiedzialny za wtyczka do kontroli źródła do tłumaczenia do ścieżek względnych, jeśli oznacza to wymaganie podstawowej systemu kontroli źródła.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Określ pełną ścieżkę dla zarejestrowanego biblioteki DLL  
 IDE nie jest już ładuje bibliotek DLL z ścieżek względnych (na przykład.\NewProvider.dll). Należy określić pełną ścieżkę pliku DLL (na przykład C:\Providers\NewProvider.dll). To wymaganie ich bezpieczeństwo środowiska IDE, zapobiegając ładowanie kontroli źródła nieautoryzowani lub personifikowanej biblioteki dll.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Sprawdź, czy istniejący VSSCI wtyczki, po zainstalowaniu dodatku Plug-in kontroli źródła  
 Użytkownik zamierza zainstalować wtyczka do kontroli źródła może już istniejących wtyczka do kontroli źródła zainstalowany na komputerze. Program instalacyjny (Konfiguracja) dla wtyczki, należy utworzyć należy ustalić, czy są istniejące wartości dla odpowiednie klucze rejestru. Jeśli te klucze są już skonfigurowane, program instalacyjny należy poprosić użytkownika czy zarejestrować Twoje wtyczki jako domyślny wtyczkę kontroli źródła i Zastąp ten, który jest już zainstalowana.  
  
## <a name="error-result-codes-and-reporting"></a>Kody błędów wyników i raportowania  
 `SCC_OK` Zwracany kod dla funkcji kontroli źródła wskazuje, że operacja zakończyła się pomyślnie dla wszystkich plików. W przypadku niepowodzenia operacji oczekuje się zwrócić kod ostatniego błędu napotkano.  
  
 Reguła dla raportowania jest Jeśli wystąpi błąd w środowisku IDE, IDE odpowiedzialny za raportowania go. Jeśli wystąpi błąd w systemie kontroli źródła, wtyczkę kontroli źródła jest odpowiedzialny za raportowania go. Na przykład "obecnie nie wybrano żadnych plików" będzie zgłaszane IDE, "ten plik został już wyewidencjonowany" czy zgłoszone przez wtyczkę.  
  
## <a name="the-context-structure"></a>Struktura kontekstu  
 Podczas wywołania [SccInitialize](../extensibility/sccinitialize-function.md), przekazuje obiekt wywołujący `ppvContext` parametru, który jest niezainicjowany uchwyt do void. Wtyczka do kontroli źródła, można zignorować ten parametr lub można przydzielić struktury dowolnego rodzaju i umieścić wskaźnik do tej struktury w wskaźnik przekazany. IDE nie rozpoznaje tej struktury, ale przekazuje wskaźnik do struktury do każdego innego wywołania w dodatku plug-in. Udostępnia kontekst cenne informacje o pamięci podręcznej do wtyczki, czy można użyć do zarządzania danymi stan globalny, która pozostaje między wywołania funkcji bez używania zmiennych globalnych. Dodatek jest odpowiedzialny za zwalnianie Struktura na wywołanie [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Jeśli wtyczka zestawy `SCC_CAP_REENTRANT` bitu w [SccInitialize](../extensibility/sccinitialize-function.md) (w szczególności w `lpSccCaps` parametru), wielu struktur kontekstu są używane do śledzenia wszystkich projektów, które są otwarte.  
  
## <a name="bitflags-and-other-command-options"></a>Flag bitowych i innymi opcjami polecenia  
 Dla każdego polecenia takich jak [SccGet](../extensibility/sccget-function.md), IDE, można określić wiele opcji, które należy zmienić to zachowanie polecenia.  
  
 Interfejs API obsługuje ustawienie niektórych opcji IDE za pośrednictwem `fOptions` parametru. Te opcje są opisane w temacie [flag bitowych używane przez określonego polecenia](../extensibility/bitflags-used-by-specific-commands.md) wraz z poleceniami, które wpływają na. Ogólnie rzecz biorąc są to opcje, dla których użytkownik nie otrzyma monitu.  
  
 Najbardziej użytkownika można skonfigurować ustawienie opcji nie są zdefiniowane w ten sposób, ponieważ znacznie różnić między plug-in kontroli źródła. W związku z tym mechanizm zalecane jest **zaawansowane** przycisku. Na przykład w **uzyskać** okno dialogowe IDE wyświetla tylko te informacje, które sam, ale także przedstawia **zaawansowane** przycisku, jeśli wtyczka zawiera opcje dla tego polecenia. Po kliknięciu przez użytkownika **zaawansowane** przycisk wywołania IDE [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) umożliwiające wtyczka do kontroli źródła do monitowania użytkownika o informacje, takie jak flag bitowych lub daty/godziny. Wtyczka zwraca te informacje w strukturze, która jest przekazywany w trakcie `SccGet` polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Plug-in kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)