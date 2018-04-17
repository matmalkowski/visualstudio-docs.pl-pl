---
title: Pakiet VSPackage rejestracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 348010982b015eaf19ba4de559eca66bb24930a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vspackage-registration"></a>Pakiet VSPackage rejestracji
Poinformowanie VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są zainstalowane i powinny zostać załadowany. Ten proces jest realizowane za pomocą informacji w rejestrze. To jest typowe zadania Instalatora.  
  
> [!NOTE]
>  Praktyką jest podczas tworzenia pakiet VSPackage, aby użyć rejestracji automatycznej. Jednak [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partnerów nie może wysłać ich produktów w ramach instalacji przy użyciu rejestracji automatycznej.  
  
 Wpisy rejestru w pakiet Instalatora Windows składają się zazwyczaj w tabeli rejestru. Można również zarejestrować rozszerzeń plików, w tabeli rejestru. Jednak Instalator systemu Windows udostępnia wbudowaną obsługę za pośrednictwem identyfikator programowy (ProgId), klasy, rozszerzenia i tabele zlecenia. Aby uzyskać więcej informacji, zobacz [tabel bazy danych](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Pamiętaj, że wpisy rejestru są skojarzone ze składnikiem, który jest odpowiedni dla wybranego strategii side-by-side. Na przykład wpisy rejestru dotyczące pliku udostępnionego powinna być skojarzona z tego pliku składnika Instalator systemu Windows. Podobnie wpisy rejestru dotyczące określonej wersji pliku powinna być skojarzona ze składnikiem tego pliku. W przeciwnym razie Instalowanie lub odinstalowywanie VSPackage dla jednej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] może spowodować przerwanie VSPackage w innych wersjach. Aby uzyskać więcej informacji, zobacz [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Najprostszym sposobem umożliwia zarządzanie rejestracją ma używać tych samych danych w tych samych plików zarówno dla deweloperów rejestracji i rejestracji czas instalacji. Na przykład niektóre narzędzia Instalatora programowanie można używać pliku w formacie reg w czasie kompilacji. Jeśli deweloperzy Obsługa plików reg dla bieżącego rozwoju i debugowanie, tych samych plików może być uwzględniony w Instalatorze automatycznie. Jeśli nie można automatycznie udostępnić dane rejestracji, musi zapewnić, że Instalator kopię danych rejestracji jest aktualna.  
  
## <a name="registering-unmanaged-vspackages"></a>Rejestrowanie VSPackages niezarządzane  
 Niezarządzane VSPackages (włącznie z wygenerowanymi przez szablon pakietu Visual Studio) Użyj plików .rgs stylu ATL do przechowywania informacji o rejestracji. Format pliku .rgs jest przeznaczony dla ATL i zazwyczaj nie mogą być używane jako-przy instalacji narzędzie autorskie. Informacje rejestracyjne Instalatora pakiet VSPackage muszą zostać zachowane oddzielnie. Na przykład deweloperzy mogą synchronizowania plików w formacie reg z .rgs zmiany pliku. Plik reg można scalone z RegEdit dla pracach programistycznych lub używane przez Instalatora.  
  
## <a name="registering-managed-vspackages"></a>Rejestrowanie VSPackages zarządzanych  
 Narzędzie RegPkg odczytuje atrybutów rejestracji z zarządzanego pakiet VSPackage i albo zapisywać informacje bezpośrednio do rejestru lub plików reg format zapisu, które mogą być używane przez Instalatora.  
  
> [!NOTE]
>  Narzędzie RegPkg nie jest do dystrybucji i nie można zarejestrować pakiet VSPackage użytkownika w systemie.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Dlaczego VSPackages nie należy samodzielnie zarejestrować w czasie instalacji  
 Instalatora pakiet VSPackage, nie należy polegać na rejestracji automatycznej. Na pierwszy rzut oka zachowania wartości rejestru pakiet VSPackage tylko w pakiecie VSPackage, sama prawdopodobnie dobrym rozwiązaniem. Biorąc pod uwagę, że deweloperzy muszą dostępne wartości rejestru do wykonywania rutynowych pracy i testowania, warto uniknąć utrzymywania osobnych kopii danych rejestru w Instalatorze. Instalator może polegać na VSPackage można zapisać wartości rejestru.  
  
 Podczas dobrej teoretycznie Autorejestracja ma kilka wad wchodzące nie nadaje się do instalacji pakiet VSPackage:  
  
-   Poprawnie obsługi instalacji, dezinstalacja wycofanie instalacji i dezinstalacji wycofywania wymaga utworzenia cztery akcje niestandardowe dla każdego zarządzanego pakiet VSPackage, który rejestruje własnym wywołując RegPkg.  
  
-   Swoje podejście do obsługi side-by-side może wymagać tworzenie cztery akcje niestandardowe, które wywołują RegSvr32 lub RegPkg dla każdej obsługiwanej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Instalacja z własnym zarejestrowany moduł nie może bezpiecznie wycofana, ponieważ nie istnieje sposób z informacją, jeśli zarejestrują klucze są używane przez inną funkcję lub aplikację.  
  
-   Zarejestrują biblioteki DLL czasami łącze do pomocniczego bibliotek DLL, które nie są dostępne lub nieprawidłowej wersji. Z kolei Instalatora Windows można zarejestrować biblioteki DLL przy użyciu tabel rejestru z nie zależności od bieżącego stanu systemu.  
  
-   Kod rejestracji automatycznej można odmówić dostępu do zasobów sieciowych, takich jak biblioteki typów, jeśli składnik jest zarówno określony jako uruchamianie ze źródła i to wymienione w tabeli SelfReg. Może to spowodować instalacji składnika się niepowodzeniem podczas instalacji administracyjnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalator systemu Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Rejestracja pakietu zarządzanych](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)