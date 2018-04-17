---
title: Visual Studio SDK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b6b75deb576e5cb4e23975e80428433fbbc143a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK pomaga rozszerzania funkcji programu Visual Studio lub zintegrować nowe funkcje programu Visual Studio. Można rozpowszechniać rozszerzeń do innych użytkowników, a także do programu Visual Studio Marketplace. Oto niektóre sposoby, w którym można rozszerzyć Visual Studio:  
  
-   Dodawanie poleceń, przyciski menu i inne elementy interfejsu użytkownika do środowiska IDE  
  
-   Dodawanie do okien narzędzi dla nowych funkcji  
  
-   Rozszerzenie IntelliSense dla danego języka, lub podaj IntelliSense dla nowych języków programowania  
  
-   Umożliwia żarówki znajdują się wskazówki i sugestii, które ułatwiają deweloperom pisanie kodu lepsze  
  
-   Włączanie obsługi nowego języka  
  
-   Dodaj typ projektu niestandardowych  
  
-   Dotarcie do milionów deweloperów za pomocą programu Visual Studio Marketplace  
  
 Jeśli rozszerzenia programu Visual Studio przed nigdy nie zostały zapisane, należy znaleźć więcej informacji o tych funkcjach i w [rozpoczyna tworzenie rozszerzenia dla programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalacja programu Visual Studio SDK  
 Visual Studio SDK jest opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Co to jest nowa w programie Visual Studio 2017 SDK  
 Visual Studio SDK ma niektóre nowe funkcje, takie jak VSIX v3 format, jak również istotne zmiany, które mogą wymagać aktualizacji Twoje rozszerzenie. Aby uzyskać więcej informacji, zobacz [What's New in Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Wskazówki dotyczące czynności użytkownika dla programu Visual Studio  
 Bardzo porady dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Można też uzyskać porady: Tworzenie rozszerzenia wygląda świetnie w przypadku wysokiej rozdzielczości DPI urządzeń z naszych [adresowania problemów DPI](../extensibility/addressing-dpi-issues2.md) tematu.  
  
 Korzystać z [Usługa obrazów i wykaz](../extensibility/image-service-and-catalog.md) zarządzania obrazami dużą i obsługę wysokiej rozdzielczości i motywów.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Znajdowanie i instalowanie istniejących rozszerzeń programu Visual Studio  
 Można znaleźć rozszerzenia programu Visual Studio w **rozszerzenia i aktualizacje** okna dialogowego na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Znajdowanie i rozszerzenia przy użyciu programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Możesz również znaleźć rozszerzenia w [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Odwołanie do zestawu SDK programu Visual Studio  
 Znajduje się odwołanie do interfejsu API zestawu SDK programu Visual Studio na [odwołania do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Przykłady programu Visual Studio SDK  
 Typu open source przykładami zestawu SDK rozszerzenia można znaleźć w witrynie GitHub pod [przykłady dotyczące programu Visual Studio](https://aka.ms/vs2015sdksamples). To repozytorium GitHub zawiera przykłady ilustrujące różnych extensible funkcji w programie Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Inne zasoby zestawu SDK programu Visual Studio  
 Jeśli masz pytania dotyczące VSSDK lub chcesz podzielić się doświadczeniami opracowywania rozszerzeń, możesz użyć [programu Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) lub [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).  
  
 Więcej informacji można znaleźć [blog VSX Arcana](http://blogs.msdn.com/b/vsx/) i liczba zapisanych przez Microsoft MVPs blogi:  
  
-   [Rozszerzenia ulubionych programu Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Rozszerzalności programu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Rozszerzanie programu Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Porady: Migracja rozszerzalności projekty do programu Visual Studio 2017 r](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Często zadawane pytania: Konwertowanie dodatki do rozszerzeń pakiet VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Zarządzanie wiele wątków w kodzie zarządzanym](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Dodawanie poleceń do pasków narzędzi](../extensibility/adding-commands-to-toolbars.md)   
 [Rozszerzanie i dostosowywanie narzędzi systemu Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Edytora i rozszerzenia usługi języka](../extensibility/editor-and-language-service-extensions.md)   
 [Rozszerzanie projektów](../extensibility/extending-projects.md)   
 [Opcje i rozszerzanie ustawień użytkownika](../extensibility/extending-user-settings-and-options.md)   
 [Tworzenie niestandardowych projekt oraz szablony elementów](../extensibility/creating-custom-project-and-item-templates.md)   
 [Rozszerzanie właściwości i w oknie właściwości](../extensibility/extending-properties-and-the-property-window.md)   
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Przy użyciu i świadczenia usług](../extensibility/using-and-providing-services.md)   
 [Zarządzanie VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio izolowane powłoki](../extensibility/visual-studio-isolated-shell.md)   
 [Wysyłanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [W programie Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Obsługa programu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiwum](../extensibility/archive.md)   
 [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
