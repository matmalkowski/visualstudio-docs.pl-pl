---
title: Wybieranie katalogu instalacyjnego dla pakiet VSPackage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Wybieranie katalogu instalacyjnego dla pakiet VSPackage
Pakiet VSPackage i towarzyszące mu pliki muszą być w systemie plików użytkownika. Lokalizacja zależy od tego, czy pakiet VSPackage jest zarządzane lub niezarządzane side-by-side wersji schematu, a wybór użytkownika.  
  
## <a name="unmanaged-vspackages"></a>Niezarządzane VSPackages  
 Niezarządzane pakiet VSPackage jest serwer COM, którą można zainstalować w dowolnym miejscu. Swoje informacje rejestracyjne musi dokładnie odzwierciedla jego lokalizacji. Instalator interfejsu użytkownika (UI) powinien zapewnić domyślną lokalizację jako podkatalog właściwości ProgramFilesFolder Instalatora Windows. Na przykład:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 Użytkownik powinien mieć możliwość zmiany domyślnego katalogu, aby pomieścić użytkowników, którzy zachować partycję rozruchową małych i wybrać opcję instalowania aplikacji i narzędzi na innym woluminie.  
  
 Jeśli schematem side-by-side korzysta z kontrolą wersji pakiet VSPackage, można użyć w podkatalogach przechowywać różne wersje. Na przykład:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages zarządzanych  
 Zarządzane VSPackages można również zainstalować w dowolnym miejscu. Jednak należy rozważyć zawsze instalowania ich do globalnej pamięci podręcznej zestawów (GAC), aby zmniejszyć czasy ładowania zestawu. Ponieważ VSPackages zarządzane są zawsze zestawy o silnych nazwach, instalowania ich w pamięci podręcznej GAC oznacza, że ich weryfikacji podpisu silnej nazwy przyjmuje tylko w czasie instalacji. Zestawów o silnej nazwie zainstalowany w innym miejscu w systemie plików muszą mieć swoje podpisy zweryfikować za każdym razem, gdy są załadowane. Po zainstalowaniu VSPackages zarządzanych w pamięci podręcznej GAC Użyj narzędzia regpkg **/Assembly** przełącznika na zapisywanie wpisów rejestru wskazujące silna nazwa zestawu.  
  
 Po zainstalowaniu VSPackages zarządzanych w lokalizacji innej niż Globalna pamięć podręczna wykonaj wcześniejszych przekazanej do VSPackages niezarządzane dotyczące wybierania hierarchii katalogu. Użyj narzędzia regpkg **/ codebase** przełącznika na zapisywanie wpisów rejestru wskazujący ścieżkę zestawu pakiet VSPackage.  
  
 Aby uzyskać więcej informacji, zobacz [rejestrowanie i wyrejestrowywanie VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Satelitarne biblioteki dll  
 Konwencja, biblioteki DLL satellite pakiet VSPackage — które zawierają zasoby dla konkretnego ustawień regionalnych — znajdują się w podkatalogach katalogu pakiet VSPackage. Podkatalogi odpowiadają wartościom identyfikator ustawień regionalnych.  
  
 [Zarządzanie VSPackages](../../extensibility/managing-vspackages.md) wskazuje, że wpisy rejestru kontrolują lokalizację [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] faktycznie szuka pakiet VSPackage satelitarne biblioteki DLL. Jednak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje załadować satelitarnej biblioteki DLL w podkatalogu o nazwie wartości LCID, w następującej kolejności:  
  
1.  Domyślny identyfikator LCID (VS LCID na przykład \1033 w języku angielskim)  
  
2.  Domyślny identyfikator LCID z odmianą języka domyślnego.  
  
3.  Domyślny identyfikator LCID.  
  
4.  Domyślny identyfikator LCID z odmianą języka domyślnego.  
  
5.  U.S. Angielski (. \1033 lub. \0x409).  
  
 Jeśli biblioteki DLL pakiet VSPackage zawiera zasoby i punkty wejścia rejestru SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje załadować je w podanej kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór między VSPackages udostępnionego i wersji](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Zarządzanie VSPackages](../../extensibility/managing-vspackages.md)   
 [Rejestracja pakietu zarządzanych](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)