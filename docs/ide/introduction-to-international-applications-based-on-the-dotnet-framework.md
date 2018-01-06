---
title: "Wprowadzenie do aplikacji międzynarodowych oparte na programie .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 9acc8f2e015b6ca2ad26881eeb1f53012d96e56d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Wprowadzenie do aplikacji międzynarodowych na podstawie .NET Framework
W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], można wyróżnić dwie części do tworzenia aplikacji gotowych: lokalizacja, proces tłumaczenie zasobów dla określonej kultury i globalizacja, proces projektowania aplikacji, które można dostosować do innych kultur. Aby uzyskać ogólne informacje dotyczące projektowania aplikacji międzynarodowych odbiorców, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](http://msdn.microsoft.com/Library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Model lokalizacji składa się z głównego zestawu, który zawiera zarówno kod aplikacji, jak i zasoby rezerwowe — ciągi, obrazy i inne obiekty, dla języka, w którym aplikacja jest przeznaczony głównie. Każda aplikacja zlokalizowanych będzie mieć zestawy satelickie lub zestawów, które zawierają zlokalizowanych zasobów. Ponieważ główny zestaw zawsze zawiera zasoby rezerwowe, jeśli zasób nie zostanie znaleziony w zestawie zlokalizowanych satelity <xref:System.Resources.ResourceManager> próbuje załadować go w hierarchiczny sposób, po pewnym czasie nastąpi powrót do zasobu w zestawie głównym. System rezerwowy zasobów jest omówiona szczegółowo w temacie większa [hierarchiczna organizacja zasobów do lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Jeden zasób lokalizacji, należy rozważyć użycie jest słownik wszystkie usługi Microsoft są zlokalizowane produktów. Ten plik CSV zawiera ponad 12 000 terminy w języku angielskim oraz tłumaczenia warunki do 59 w różnych językach. Słownik jest dostępny do pobrania na [tłumaczeń terminologii Microsoft](http://go.microsoft.com/fwlink/?LinkId=128146) strony sieci Web.  
  
 System projektu dla aplikacji formularzy systemu Windows można wygenerować plików zasobów dla obu powrotu i każdego potrzebne dodatkowe kultury interfejsu użytkownika. Plik zasobów rezerwowego jest wbudowana w zestawie głównym, a pliki zasobów specyficzne dla kultury następnie są wbudowane w zestawy satelickie, po jednej dla każdego kultury interfejsu użytkownika. Podczas tworzenia projektu, pliki zasobów są kompilowane z formatu XML usługi Visual Studio (resx) na format binarny pośredniego (.resources), które następnie są osadzone w zestawy satelickie.  
  
 System projektu dla formularzy systemu Windows i formularzy sieci Web pozwala na tworzenie plików zasobów przy użyciu szablonu pliku zasobu zestawu, dostępu do zasobów i skompilowanie projektu. Zestawy satelickie zostanie utworzony wraz z głównym zestawu.  
  
 Podczas zlokalizowanej aplikacji, jej wygląd jest określana przez dwie wartości kultury. (A *kultury* jest zestawem preferencji użytkownika związanych z języka i środowiska oraz konwencje kultury użytkownika.) Ustawienie kultury interfejsu użytkownika określa, jakie zasoby zostaną załadowane. Kultura interfejsu użytkownika jest ustawiony jako `UICulture` w plikach Web.config i dyrektywy strony i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> w kodzie języka Visual Basic lub Visual C#. Ustawienie kultury Określa format wartości, takich jak dat, liczb, waluty i tak dalej. Kultura jest ustawiony jako `Culture` w plikach Web.config i dyrektywy strony <xref:System.Globalization.CultureInfo.CurrentCulture%2A> w kodzie języka Visual Basic lub Visual C#.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)   
 [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)