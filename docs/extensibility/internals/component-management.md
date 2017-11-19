---
title: "Składnik Zarządzanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a3100252dd5ddfcebd791588a4041c8d588e8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="component-management"></a>Składnik zarządzania
Jednostki zadań w Instalatorze systemu Windows są określane jako składniki Instalatora Windows (czasami nazywany WICs lub po prostu składników). Identyfikator GUID identyfikuje każda usługa WIC to podstawowa jednostka instalacji i zliczanie dla ustawień używające Instalatora Windows.  
  
 Mimo korzystania z kilku produktów, aby utworzyć Instalatora pakiet VSPackage, przyjęto korzystania z plików Instalatora Windows (msi). Podczas tworzenia Instalatorem, należy poprawnie zarządzać wdrożenia plików dzięki temu liczenie odwołań poprawne odbywa się przez cały czas. W związku z tym różne wersje produktu nie zakłóca lub przerwanie siebie w różnych instalacji i odinstalować scenariuszy.  
  
 W Instalatorze Windows liczenie odwołań występuje na poziomie składnika. Należy dokładnie organizowania zasobów — pliki, wpisy rejestru i tak dalej — na składniki. Brak innych poziomach organizacji — takie jak moduły, funkcji i produktów — które mogą pomóc w różnych scenariuszach. Aby uzyskać więcej informacji, zobacz [podstawy Instalatora systemu Windows](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Wskazówki dotyczące tworzenia Instalatora w celu instalacji Side-by-side  
  
-   Tworzenie plików i kluczy rejestru, które są współużytkowane przez wersje do ich własnych składników.  
  
     Dzięki temu można łatwo korzystać z nich w następnej wersji. Na przykład bibliotek typów, które są zarejestrowane globalnie, pliku rozszerzenia i inne elementy zarejestrowane wpisów z HKEY_CLASSES_ROOT i tak dalej.  
  
-   Grupy składników współużytkowanych do modułów scalania oddzielne.  
  
     Ułatwia to tworzenie poprawnie dla następnych side-by-side.  
  
-   Zainstaluj udostępnione pliki i klucze rejestru przy użyciu tego samego składników Instalatora Windows w wersjach.  
  
     Jeśli używasz różnych składników, pliki i wpisy rejestru są odinstalowywane podczas jednego kontrolą wersji pakiet VSPackage zostanie odinstalowana, ale nadal jest zainstalowany inny pakiet VSPackage.  
  
-   Nie można mieszać wersji i udostępnionych elementów w tym samym składnikiem.  
  
     Dzięki temu uniemożliwia instalacji elementów udostępnionych w globalnej lokalizacji i numerów wersji elementów do lokalizacje izolowanego.  
  
-   Nie masz kluczy rejestru udostępnionego, które wskazują wersji plików.  
  
     Jeśli to zrobisz, kluczy współużytkowanych zostaną zastąpione po zainstalowaniu inny pakiet VSPackage numerów wersji. Po usunięciu druga wersja pliku, do którego wskazuje klucz został usunięty.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór między VSPackages udostępnionego i wersji](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenariusze instalacji pakiet VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)