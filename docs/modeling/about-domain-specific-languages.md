---
title: "O językach specyficznego dla domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9357c55b204d521eb5cd77af328636485c490ff4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="about-domain-specific-languages"></a>Języki specyficzne dla domeny — informacje

W przeciwieństwie do języka ogólnego przeznaczenia, takich jak C# lub UML języka specyficznego dla domeny (DSL) jest przeznaczony do express instrukcje w konkretnych problemów miejsca lub domeny.  
  
Dobrze znane DSLs obejmują wyrażeń regularnych i SQL. Każdy DSL jest znacznie lepszą niż uniwersalny język opisu operacji ciągów tekstowych lub bazy danych, ale co znacznie gorsza opisu pomysły, znajdujących się poza własny zakres. Konkretnych branżach również mieć własne DSLs. Na przykład w branży telekomunikacyjnych wywołać opis języki są powszechnie używane do określ stanów połączenia telefonicznego i niebu z podróży branży DSL jest używana do opisu rezerwacje transmitowane standard.  
  
Firmy i projektu również uwzględniać specjalne zestawów pojęcia, które można nazwać z DSL. Na przykład można zdefiniować DSL dla jednej z tych aplikacji:  
  
-   Plan ścieżek nawigacji w witrynie sieci Web.  
  
-   Diagramy okablowania elektronicznych.  
  
-   Sieci taśmy przenoszące i bagażu obsługi urządzeń dla lokalnej na lotnisku.  
  
Podczas projektowania DSL, zdefiniuj *klasy domeny* dla każdego ważne pojęcia w domenie, takich jak strony sieci Web, światła lub lotnisku biurku zaewidencjonowania. Należy zdefiniować *relacje domeny* przykład hiperłącze, podczas transmisji lub taśmy taśmy, aby połączyć ze sobą pojęcia.  
  
Tworzenie użytkowników sieci DSL *modeli.* Modele są *wystąpień* z DSL. Na przykład opisują one określonej witryny lub okablowania określonego urządzenia lub bagażu systemu, w szczególności lotnisku obsługi.  
  
Użytkownicy mogą wyświetlać modelu jako diagramu lub formularza systemu Windows. Modele można również wyświetlać formacie XML, który jest, jak są przechowywane. Podczas definiowania DSL, należy zdefiniować sposób wystąpień każdej klasy domeny i relacje są wyświetlane na ekranie użytkownika. Typowy DSL jest wyświetlana jako zbiór ikony lub prostokąty połączonymi strzałki.  
  
Na poniższej ilustracji przedstawiono małego modelu w podającą DSL:  
  
![Model drzewa rodziny Tudorów](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>Co można zrobić DSLs  

Typowa aplikacja DSL jest do generowania kodu programu lub inne artefaktów. Podczas definiowania sieci DSL, można określić *szablony tekstowe* czy odczytywanie modelu DSL i generowanie plików tekstowych.  
  
Na przykład można zapisać szablonów, które zająć plan lotniska i generowanie część oprogramowania dla bagażu obsługi, a także niektóre dokumenty użytkowników, które opisują planu.  
  
Po zdefiniowaniu DSL rozpowszechnienie go do innych użytkowników, którzy mogą zainstalować ją na swoich komputerach. Użytkownicy z DSL można tworzyć i edytować modeli w Visual Studio.  
  
Istnieje również możliwość definiowania polecenia menu i innych narzędzi, które pomagają użytkownikom edytowanie DSL, ograniczenia walidacji pomaga zapewnić, że DSL jest używana poprawnie i szablony elementów, które pomagają użytkownikom tworzenie nowych wystąpień. Jako zintegrowany pakiet może zawijać się DSLs co najmniej jednego ze swoich narzędzi oraz innych rozszerzeń programu Visual Studio.  
  
Zazwyczaj języka specyficznego dla domeny jest tworzona po zespół deweloperów do pisania kodu podobne do kilku produktów. Na przykład w firmie, która specjalizuje się w bagażu obsługi systemów zdefiniować bagażu DSL ścieżki, w którym można generują one części kodu dla każdej instalacji. Zalety DSL są, że jej zostały zrozumiane przez klientów, czy z niego wygenerować kod jest niezawodna i czy system można szybko zaktualizować zmiany wymagań dotyczących klientów.  
  
[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Umożliwia tworzenie własnych graficznego projektanta i własne notacji diagram języka specyficznego dla domeny, a następnie użyj języka aby wygenerować kod źródłowy odpowiednie dla każdego projektu.  
  
## <a name="domain-specific-development"></a>Programowanie specyficznego dla domeny

Tworzenie specyficznego dla domeny jest proces identyfikowania części aplikacji, które mogą być modelowane przy użyciu języka specyficznego dla domeny, a następnie konstruowanie języku i wdrażania dla deweloperów aplikacji. Deweloperzy używać języka specyficznego dla domeny do tworzenia modeli, które są specyficzne dla aplikacji, użyj modeli do generowania kodu źródłowego, a następnie użyć kodu źródłowego do tworzenia aplikacji.  

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekty graficznego programowanie specyficznego dla domeny

Graficzny języka specyficznego dla domeny musi zawierać następujące funkcje:  
  
- Notacja  
  
- Model domeny  
  
- Generowanie artefaktów  
  
- Serializacja  
  
- Integracja z programem Visual Studio  
  
### <a name="notation"></a>Notacja

Języka specyficznego dla domeny musi mieć rozsądnych niewielki zestaw elementów, które można łatwo zdefiniowany i rozszerzone do reprezentowania konstrukcje specyficznego dla domeny. Notacja składa się z kształtów, które reprezentują elementów, i łączniki, które reprezentują relacje między elementami na powierzchni graficzny diagram. W [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], można ją rozszerzać oraz wprowadzono ulepszenia reprezentujące elementy języka specyficznego dla domeny kształtów.  
  
### <a name="domain-model"></a>Domain Model

Zbiór elementów i relacji między nimi w spójnej gramatyki połączyć języka specyficznego dla domeny. Również muszą definiować, czy kombinacje elementów i relacji są prawidłowe. Języki programowania zapobiec zwykle Dziedziczenie cykliczne, w której jedna klasa pochodzi od klasy sekundę i drugiej klasy jest pochodną klasy pierwszy. Ograniczenia może również służyć do express logiki biznesowej, na przykład jedna osoba nie może być zależne od siebie. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]używa ograniczenia Express rodzaje ograniczenia, które wymagają większości języków specyficznego dla domeny.  
  
### <a name="artifact-generation"></a>Generowanie artefaktów

Jednym z głównych celów języka specyficznego dla domeny jest Generowanie artefaktów na przykład kod źródłowy, plik XML lub innych danych użytecznego. Zazwyczaj zmiany w modelu oznacza zmianę w artefaktu. Można użyć [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Generowanie artefakty i ponowne ich wygenerowanie, po zmianie modelu.  
  
### <a name="serialization"></a>Serializacja

W niektórych formularz, który można można edytowane, zapisane zamknięte i ponownie załadować musi zostać utrwalony języka specyficznego dla domeny. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]używa formacie XML, który umożliwia definiowanie i dostosowywanie sposób serializacji lub utrwalone języka specyficznego dla domeny.  
  
### <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio

Ponieważ [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] znajduje się w programie Visual Studio rozszerza wiele windows Visual Studio i kontrolek. Umożliwia on również dostosować zachowanie polecenia menu, elementy przybornika i inne elementy interfejsu użytkownika.  
  
Można również utworzyć adaptera magistrali modelu dla danego języka specyficznego dla domeny. Ta karta umożliwia odwołanie modelu i elementów w obrębie modelu i umożliwia pisanie kodu, które mogą uzyskać dostęp i zaktualizować wystąpienia DSL. Przy użyciu zaawansowanego mechanizmu magistrali modelu, można napisać rozszerzeń programu Visual Studio, które współpracują z wielu modeli. Można również pisać aplikacje autonomiczne, które współpracują z modelami. Aby uzyskać więcej informacji, zobacz [integrowanie modeli przy użyciu programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Korzyści wynikające z rozwoju specyficznego dla domeny

Języka specyficznego dla domeny zapewniają następujące korzyści:  
  
- Zawiera konstrukcje, dokładnie spełniających miejsca problem.  
  
     W przeciwieństwie do ogólnego przeznaczenia języków języka specyficznego dla domeny składa się z elementów i relacje, które reprezentują bezpośrednio logiki miejsca problem. Na przykład aplikacja ubezpieczenia musi zawierać elementy zasady i oświadczeń. Języka specyficznego dla domeny ułatwia projektowanie aplikacji i Znajdź i usuń błędy logiki.  
  
- Umożliwia z systemem innym niż deweloperów i osoby, które nie jest znany domeny zrozumienie ogólnego projektu.  
  
     Przy użyciu graficznego języka specyficznego dla domeny, można utworzyć wizualną reprezentację domeny, dzięki czemu deweloperzy nie można łatwo zrozumieć projekt aplikacji.  
  
- Łatwiejsze tworzenie prototypów końcowego aplikacji.  
  
     Deweloperzy mogą używać kod, który generuje ich modelu do utworzenia aplikacji prototyp, która pokazywały do klientów.  
  
## <a name="the-process-of-domain-specific-development"></a>Proces tworzenia specyficznego dla domeny

Większości zespołów deweloperów oprogramowania używające języków specyficznego dla domeny wykonaj następujące kroki tworzenia i używania ich modeli:  
  
-   Zespół odróżnia zmiennej części domeny z części, które nigdy nie ulegną zmianie.  
  
-   Deweloperzy pisanie kodu dla stałej części i pozostawić punkty rozszerzeń dla zmiennej części.  
  
-   Deweloper oprogramowania realizacji lub Architekt tworzy języka specyficznego dla domeny, która będzie zawierała wzorce projektowe stałej części domeny oraz punkty rozszerzeń dla zmiennej części.  
  
-   Deweloper oprogramowania realizacji lub Architekt wdraża języka specyficznego dla domeny deweloperzy różne aplikacje, które spowoduje utworzenie zespołu.  
  
-   Każdy deweloper tworzy modelu, który ma zastosowanie do określonej aplikacji.