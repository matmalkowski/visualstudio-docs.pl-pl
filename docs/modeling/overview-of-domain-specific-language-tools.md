---
title: "Omówienie narzędzia języka specyficznego dla domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1fcba975443deb768a2b3de36bd2744183cdcf40
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
Narzędzia języka specyficznego dla domeny (narzędzia DSL), które znajdują się w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]systemowi projektowania języka specyficznego dla domeny, a następnie wygenerować wszystkie czynności, które użytkownicy muszą mieć do tworzenia modeli, które są oparte na języku.  
  
 Narzędzia DSL obejmuje następujące narzędzia:  
  
-   Kreator projektu, który korzysta z szablonów inne rozwiązanie ułatwiające rozpocząć tworzenie języka specyficznego dla domeny.  
  
-   Graficzny projektant tworzenia i edytowania definicję języka specyficznego dla domeny.  
  
-   Aparat do sprawdzania poprawności, który sprawia, że definicja języka specyficznego dla domeny są dobrze sformułowane i wyświetla błędy i ostrzeżenia, jeśli występują problemy.  
  
-   Generator kodu, która przyjmuje jako dane wejściowe definicji języka specyficznego dla domeny i tworzy kod źródłowy jako dane wyjściowe.  
  
## <a name="the-dsl-tools-solution"></a>Rozwiązanie narzędzia DSL  
 Kreator projektanta specyficznego dla domeny zawiera następujące szablony rozwiązań:  
  
-   Przepływ zadań  
  
-   Diagramy klas  
  
-   Minimalny języka  
  
-   Modele składnika  
  
-   Minimalny WPF  
  
-   Minimal Windows.Forms  
  
-   Biblioteka DSL  
  
 Aby uzyskać więcej informacji, zobacz [wybieranie szablonów rozwiązania języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 Kreator tworzy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, które ma w następujących projektach:  
  
-   Dsl  
  
     Projekt Dsl definiuje języka specyficznego dla domeny i jej narzędzi edycji i przetwarzania.  
  
-   **DslPackage**  
  
     Projekt DslPackage Określa, jak narzędzia językowe zintegrować z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>Interfejs graficzny narzędzia DSL  
 Interfejs graficzny narzędzia DSL służy do dodawania elementów i relacji do języka specyficznego dla domeny. Po dodaniu elementów można zdefiniować ich wyglądu, mapując je do kształtów, dostosowywanie kolorów i dodawanie elementów decorator. Możesz również dodać elementy do przybornika.  
  
## <a name="validation-in-dsl-tools"></a>Sprawdzanie poprawności w narzędziach DSL  
 DSL zapewnia jeden poziom weryfikacji, aby upewnić się, że model domeny spełnia wymagania podstawowe dotyczące generowania kodu. Zazwyczaj podczas tworzenia własnych języka specyficznego dla domeny, możesz dodać własne weryfikacji Express logikę reguł biznesowych. Aby uzyskać więcej informacji na temat niestandardowego sprawdzania poprawności, zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
 Zaleca się sprawdzenie poprawności języka specyficznego dla domeny często podczas projektowania. Jeśli języka specyficznego dla domeny występują błędy sprawdzania poprawności, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów jest wykonywane przez kliknięcie przycisku **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań. Zawsze, gdy należy zmodyfikować definicję język, warto również **Przekształć wszystkie szablony**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie rozwiązania języka specyficznego dla domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Dostosowywanie narzędzia DSL  
 Możesz podać dodatkowy kod, aby dostosować zachowanie modelu oraz do definiowania ograniczeń przez język. W razie potrzeby możesz wprowadzić znaczących zmian, modyfikując szablony tekstowe.  
  
## <a name="distributing-your-dsl-solution"></a>Dystrybucja rozwiązania DSL  
 Narzędzia DSL generuje pakietu, który znajduje się w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pakiet zawiera przybornik, Eksploratora DSL i inne elementy interfejsu użytkownika, które pozwalają użytkownikom na tworzenie modeli przy użyciu języka specyficznego dla domeny.  
  
 Podczas tworzenia i uruchamianie rozwiązania narzędzia DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], drugie wystąpienie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pokazuje, jak wygląda języka specyficznego dla domeny użytkownika języka. Po upewnieniu się, że wszystko działa prawidłowo, można rozpowszechniać `.vsix` pliku, który znajduje się w folderze kompilacji projektu DslPackage. Ten plik może służyć do instalowania DSL jako [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia na innych komputerach.  Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Eksperymentalne wystąpienie programu](../extensibility/the-experimental-instance.md)   
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)