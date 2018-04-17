---
title: Omówienie integracji kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d75936e21729729dfeafaa041d800acbe01caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-overview"></a>Omówienie integracji kontroli źródła
Ta sekcja porównuje dwa sposoby integracji kontroli źródła programu Visual Studio; kontroli źródła wtyczek i pakiet VSPackage, który zapewnia rozwiązanie do kontroli źródła i zaznacza nowe funkcje kontroli źródła. Program Visual Studio umożliwia ręczne przełączanie między kontroli źródła VSPackages i plug-in kontroli źródła, a także automatyczne przełączanie oparte na rozwiązaniu.  
  
## <a name="source-control-integration"></a>Integracja kontroli źródła  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje dwa typy opcji integracji kontroli źródła. We wszystkich wersjach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], nadal można zintegrować wtyczki źródła formantu wtyczek interfejsu API (wcześniej również nazywany MSSCCI API), który udostępnia funkcje kontroli źródła podstawowe podczas korzystania z programu Visual Studio źródła kontrolki użytkownika interfejsu (w oparciu INTERFEJS UŻYTKOWNIKA). Kontroli źródła pakiet VSPackage, z drugiej strony, zawiera nowe, integracja głębokiego [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ścieżka odpowiedni w przypadku integracji kontroli źródła, która żąda wysoki stopień zaawansowania i autonomię w jego model kontroli źródła.  
  
 ![Informacje o formancie źródła](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Wtyczka do kontroli źródła  
 Wszystkie wersje programu Visual Studio obsługuje API dodatku typu Plug-in kontroli źródła specyfikacji wersji 1.2 jako ścieżkę integracji. Realizator wtyczkę kontroli źródła zapisuje bibliotekę DLL, która implementuje funkcje interfejsu API dodatku typu Plug-in kontroli źródła dla integracji kontroli źródła i rejestracji, zgodnie z opisem w [tworzenie Plug-in kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md). W takie podejście, zintegrowane środowisko rozwoju (IDE) używa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika dla okien dialogowych, takich jak wyboru w realizacji transakcji, strony właściwości narzędzia/Opcje paski narzędzi i symboli kontroli źródła. Ścisłego przestrzegania API dodatku typu Plug-in kontroli źródła temu Łatwa integracja w Visual Studio i bezproblemowe środowisko użytkownika. Oznacza to, że wtyczka do kontroli źródła musi implementować większość funkcji i wywołania zwrotne w interfejsie API.  
  
 Aby zaimplementować wtyczka do kontroli źródła przy użyciu interfejsu API dodatku typu Plug-in kontroli źródła, wykonaj następujące kroki:  
  
1.  Utwórz bibliotekę DLL, która implementuje funkcje wymienione w [kontroli źródła wtyczek](../../extensibility/source-control-plug-ins.md).  
  
2.  Zarejestruj plik DLL, wprowadzając wpisy rejestru odpowiednich (opisanego w [porady: Instalowanie Plug-in kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Utwórz obiekt pomocnika interfejsu użytkownika i wyświetlania po wyświetleniu monitu przez pakiet karty kontroli źródła (składnika programu Visual Studio, który obsługuje funkcje kontroli źródła za pośrednictwem plug-in kontroli źródła)  
  
 W odpowiedzi na polecenie kontroli źródła środowiska IDE programu Visual Studio przedstawia standardowego interfejsu użytkownika dla podstawowych operacji, a następnie przekazuje informacje do kontroli źródła wtyczek za pośrednictwem funkcji zdefiniowanych w interfejsie API dodatku typu Plug-in kontroli źródła. Zaawansowane opcje wtyczkę kontroli źródła może być wywołana dla do prezentowania własnego interfejsu użytkownika, na przykład przeglądania dla projektu z kontrolą źródła. Oznacza to, że użytkownik mogą pojawić się dwa prawdopodobnie różnych stylów interfejsu użytkownika podczas pracy z kontrolą źródła: interfejs użytkownika, który przedstawia informacje o programie Visual Studio i interfejsu użytkownika, który przedstawia wtyczkę kontroli źródła. Jest to najbardziej zauważalne z operacji kontroli źródła zaawansowane.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Wady z implementacją wtyczka do kontroli źródła  
  
-   Funkcje zaawansowane użytkownik może dla dwóch różnych stylów interfejsów, co może prowadzić do potencjalne problemy.  
  
-   Wtyczka do kontroli źródła jest ograniczona do model kontroli źródła wskazuje API dodatku typu Plug-in kontroli źródła.  
  
-   Interfejs API dodatku typu Plug-in kontroli źródła może być zbyt restrykcyjne dla niektórych scenariuszy kontroli źródła.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Korzyści z implementacją wtyczka do kontroli źródła  
  
-   Visual Studio udostępnia wszystkie interfejsu użytkownika dla wszystkich operacji kontroli źródła podstawowych, aby wtyczkę kontroli źródła nie musi implementować interfejs złożonych.  
  
-   Z powodu strict interfejsu API wtyczkę kontroli źródła można łatwo interakcję z programami kontroli źródła zewnętrznego zapewnienie szerszej funkcjonalności. Visual Studio interesują zbyt dużo jak funkcja kontroli źródła jest przeprowadzane, tylko że odbywa się zgodnie z interfejsu API dodatku typu Plug-in kontroli źródła.  
  
-   Jest łatwiejsze do wdrożenia wtyczka do kontroli źródła niż kontroli źródła pakiet VSPackage.  
  
## <a name="source-control-vspackage"></a>Pakiet VSPackage kontroli źródła  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Umożliwia głęboką integrację do programu Visual Studio z pełną kontrolę nad funkcja kontroli źródła i całkowite zastąpienie interfejsu użytkownika kontroli źródła dostarczane do programu Visual Studio. Pakiet VSPackage kontroli źródła jest zarejestrowana w programie Visual Studio i udostępnia funkcje kontroli źródła. Mimo że kilka kontroli źródła VSPackages można zarejestrować za pomocą programu Visual Studio, tylko jeden z nich mogą być aktywne w dowolnym momencie. Kontroli źródła pakiet VSPackage ma pełną kontrolę nad funkcja kontroli źródła i wyglądu w programie Visual Studio, gdy jest aktywny. Wszystkie inne kontroli źródła VSPackages, które mogą być rejestrowane w systemie nie są aktywne i nie będzie wyświetlany elementów interfejsu użytkownika w ogóle.  
  
 Wdrożenie kontroli źródła pakiet VSPackage wymaga strategii "wszystkie lub żadne". Twórca kontroli źródła pakiet VSPackage należy zakupić znaczną ilość nakładu pracy w przypadku implementowania interfejsów kontroli źródła i nowe elementy interfejsu użytkownika (okien dialogowych, menu i pasków narzędzi) dotyczą funkcji kontroli źródła całego. Zobacz [tworzenie pakiet VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md) więcej szczegółów.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Wady z implementacją pakiet VSPackage kontroli źródła  
  
-   Pakiet VSPackage musi implementować liczba interfejsów złożonych pomyślnie integrację z programem Visual Studio.  
  
-   Pakiet VSPackage musisz podać wszystkie wymagane do kontroli źródła; interfejsu użytkownika Visual Studio będzie zapewniać nie pomoc w tym obszarze.  
  
-   Pakiet VSPackage kontroli źródła jest ściśle związany z programu Visual Studio i nie może działać z programami autonomiczna, dzięki funkcji nie można łatwo udostępniać zewnętrznych wersji programu kontroli źródła.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Korzyści z implementacją pakiet VSPackage kontroli źródła  
  
-   Ponieważ pakiet VSPackage ma pełną kontrolę nad kontroli źródła interfejsu użytkownika i funkcje, użytkownik zobaczy interfejs do kontroli źródła.  
  
-   Pakiet VSPackage nie jest ograniczona do danego źródła kontrolki modelu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola źródła](../../extensibility/internals/source-control.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Tworzenie pakiet VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Nowości dotyczące kontroli kodu źródłowego](../../extensibility/internals/what-s-new-in-source-control.md)