---
redirect_url: shell/visual-studio-isolated-shell
title: "Visual Studio izolowana powłoka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a69b93f05619b16657d045cc7ef833d468ae7a51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio izolowane powłoki
Powłoka programu Visual Studio izolowane służy do tworzenia aplikacji autonomicznych, które można uruchomić side-by-side z innymi wersjami programu Visual Studio. Jest używany głównie w celu hostowania specjalne narzędzia, które mogą używać usługi Visual Studio, ale również dostosowanego wyglądu i znakowania. Funkcje programu Visual Studio i grupami polecenia menu mogą być łatwo włączać i wyłączać. Tytuły aplikacji, ikony aplikacji i ekrany powitalny są można swobodnie dostosowywać. Listę można dostosowywać funkcji, zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md).  
  
 Aby pracować z projektu programu isolated shell, należy zainstalować program Visual Studio SDK. Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Aby utworzyć aplikację programu isolated shell, rozpoczynać projektu programu Visual Studio Shell izolowanym. Ten projekt zawiera wszystko, co jest potrzebne do projektowania i testowania aplikacji programu isolated shell. Gdy wszystko będzie gotowe do zapisania Instalatora, która wdraża aplikację, należy pobrać pakiet redystrybucyjny programu isolated shell z [pakiet redystrybucyjny programu Microsoft Visual Studio Shell (izolowany)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Aby korzystać z pakietu redystrybucyjnego programu isolated shell, poprosimy Cię o ankiety krótki klienta.  Po wypełnieniu ankiety, nastąpi przekierowanie do strony Połącz program Visual Studio z łącza pobierania pakietu redystrybucyjnego.  Łącza pobierania przy kolejnych wizytach do witryny Visual Studio Connect w obszarze **programy &#124; VISUAL STUDIO 2015 zintegrowanego i ISOLATED SHELL** kartę.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat izolowane powłoki aplikacja wdrażania, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Praca z programu isolated shell  
 Aplikacji programu Visual Studio izolowane powłoki ma pełny dostęp do usługi Visual Studio i obsługuje specjalnego dostosowania i znakowanie. Istnieje kilka sposobów, można dostosować aplikacji isolated shell:  
  
-   Składniki pakiety VSPackage i Managed Extensibility Framework (MEF) umożliwia rozszerzanie aplikacji isolated shell tak samo, jak mogłaby być używana w innych rozszerzeń programu Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie Isolated Shell](../extensibility/extending-the-isolated-shell.md).  
  
-   Aby funkcje programu Visual Studio i grupy menu polecenie dostępne lub niedostępne, należy zaktualizować pliku vsct w projekcie interfejsu użytkownika aplikacji.  
  
-   Aby usunąć **opcje** stron lub innych składników powłoki programu Visual Studio z aplikacji, należy zaktualizować plik .pkgundef aplikacji.  
  
-   Aby zmodyfikować zachowanie powłoki lub innych aspektów wyglądu, zaktualizuj plik .pkgdef aplikacji.  
  
-   Niektóre aspekty powłoki można również określić po uruchomieniu aplikacji. Aby to zrobić, należy zaktualizować parametry w wywołaniu początkowy punkt wejścia appenvstub.dll.  
  
 Aby uzyskać więcej informacji o różnych elementów, które można dostosować, zobacz [elementy programu Isolated Shell](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardowe funkcje programu Isolated Shell  
 Następujące funkcje są standardowe dla wszystkich wersji programu Visual Studio.  
  
|Funkcja kategorii|Funkcja|  
|----------------------|-------------|  
|Funkcje środowiska IDE|Import/eksport ustawień<br /><br /> Instalator kontroli przybornika<br /><br /> Lista zadań & listy błędów<br /><br /> Okno wyniku<br /><br /> Strona początkowa<br /><br /> Okno Właściwości<br /><br /> Przybornik<br /><br /> Eksplorator rozwiązań<br /><br /> Okno zakładek<br /><br /> Widok klas<br /><br /> Przeglądarka obiektów<br /><br /> Okno polecenia<br /><br /> Konspekt dokumentu<br /><br /> Widok zasobów<br /><br /> Narzędzia zewnętrzne<br /><br /> Windows Communication Foundation (WCF) Dodaj odwołanie do usługi<br /><br /> Język zintegrowanej obsłudze zapytania (LINQ)|  
|Projektant/edytora|Narzędzia (Znajdź ujednoliconą, definicji źródła, dziedziczenia) przeglądania kodu<br /><br /> IntelliSense<br /><br /> Tagi inteligentne<br /><br /> Menedżer wstawek kodu<br /><br /> Wstawki kodu<br /><br /> Refaktoryzacja<br /><br /> Lista pretty<br /><br /> Filtrowania IntelliSense<br /><br /> Okno definicji kodu<br /><br /> Projektant aplikacji<br /><br /> Projektant Windows Forms<br /><br /> Projektant dla systemu Windows Presentation Foundation (WPF)|  
|Debugowanie|Ewaluator wyrażeń C#<br /><br /> Debugowanie lokalne<br /><br /> Debugowania zarządzanego<br /><br /> Edytuj i kontynuuj<br /><br /> Debugowanie między wątkami<br /><br /> Wizualizacji<br /><br /> DataTips<br /><br /> Debugowanie w trybie macierzystym<br /><br /> Debugowanie skryptów<br /><br /> Debugowanie międzyoperacyjne<br /><br /> Debugowanie just-in-time (JIT)<br /><br /> Debugowanie wielu procesów<br /><br /> Profilowanie XSLT<br /><br /> Dołączanie do procesu lokalnego<br /><br /> Punkty śledzenia<br /><br /> Ograniczenia punktu przerwania|  
|Dane|W Eksploratorze serwera (uproszczony — tylko dane)<br /><br /> Dane wiązania danych lokalnych (. MDF lub. MDB)<br /><br /> Wiązanie danych z obiektu<br /><br /> Wiązanie danych do usługi sieci Web<br /><br /> Pełny zestaw danych formantów<br /><br /> Edytor XML<br /><br /> Wiązanie danych z lokalną bazą danych serwera<br /><br /> Data Sources — Okno|  
|sieć Web|Edytor HTML<br /><br /> Przeglądarki sieci Web<br /><br /> Projektant formularzy sieci Web<br /><br /> Projekt witryny sieci Web<br /><br /> Projekt aplikacji sieci Web|  
|Rozszerzalność|Wykorzystuje pakiety VSPackage i MEF składników|  
  
## <a name="see-also"></a>Zobacz też  
 [Shell (Isolated lub Integrated)](../extensibility/shell-isolated-or-integrated.md)