---
title: Profilowanie wydajności aplikacji SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50e40b1a1b336f4547ed7eb446837cb0f300397d
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237617"
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>Profilowanie wydajności aplikacji SharePoint

Jeśli aplikacji SharePoint działają wolno lub Niewydajne, może używać profilowania funkcji w programie Visual Studio, aby zidentyfikować problematyczne kodu i inne elementy. Za pomocą funkcji testowania obciążenia, można określić sposób wykonywania aplikacji SharePoint mocno obciążony, np. gdy wielu użytkowników dostępu do aplikacji jednocześnie. Uruchamianie testów wydajności sieci web, można zmierzyć, sposób wykonywania aplikacji w sieci web. Za pomocą kodowanych testów interfejsu użytkownika, można sprawdzić, czy całej aplikacji programu SharePoint, w tym interfejs użytkownika działa prawidłowo. Jeśli korzystasz ze sobą te testy, można pomagają zidentyfikować problemy z wydajnością, przed wdrożeniem aplikacji.

## <a name="profiling-tools-overview"></a>Omówienie narzędzia profilowania

Profilowanie odwołuje się do procesu obserwowania i rejestrowanie zachowania wydajności aplikacji, podczas jego wykonywania. Przy ponownym sprofilowaniem aplikacji, można ujawnić problemów, takich jak wąskich gardeł, niewydajny kod i problemów z alokacją pamięci, które aplikacje działają wolno lub użyj zbyt dużej ilości pamięci. Można na przykład użyć profilowania Aby zidentyfikować punkty aktywne w kodzie, które są segmenty kodu, które są często nazywane i może to spowolnić ogólną wydajność aplikacji. Po zidentyfikowaniu hotspotami często można zoptymalizować lub usuń je.

Kilku narzędzi profilowania w zintegrowane środowisko programistyczne (IDE) służy do identyfikowania i lokalizowania tego rodzaju problemy z wydajnością. Te narzędzia działają tak samo dla projektów programu SharePoint, tak jak w przypadku innych typów projektów programu Visual Studio. Kreator wydajności narzędzi profilowania poprowadzi Cię przez tworzenie sesji wydajności, która używa testy, które określisz. Sesja wydajności jest zestawem danych konfiguracji, który służy do zbierania informacji o wydajności z aplikacji, oraz wyniki co najmniej jeden przebieg profilowania. Sesje wydajności są przechowywane w folderze projektu i możesz przeglądać w **Eksplorator wydajności**. Aby uzyskać więcej informacji, zobacz [metoda zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md).

Po utworzeniu i uruchomieniu analizę profilu dla aplikacji, raport zawiera szczegółowe informacje o jego wydajności. Ten raport może zawierać elementy, takie jak wykres użycia procesora CPU w czasie, stos wywołań funkcji hierarchiczna lub drzewo wywołań. Pełna zawartość raportu może się różnić w zależności od typu testu, który można uruchamiać, na przykład próbkowania i instrumentacji. Aby uzyskać więcej informacji, zobacz [Przegląd raportów narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Wydajność sesji procesu

Do profilu aplikacji, Rozpocznij od utworzenia sesji wydajności przy użyciu Kreatora wydajności narzędzi profilowania. Na pasku menu wybierz **Analizuj**, **Uruchom Kreatora osiągów**. Jak możesz ukończyć pracę kreatora, możesz wprowadzić wymagane informacje dotyczące sesji wydajności, takich jak żądanej metody profilu i aplikacji, która ma być profilu. Aby uzyskać więcej informacji, zobacz [porady: profilowanie witryny sieci Web lub aplikacji sieci Web przy użyciu Kreatora osiągów](http://go.microsoft.com/fwlink/?LinkId=224692). Alternatywnie można użyć opcji wiersza polecenia można skonfigurować i uruchomić sesję wydajności. Aby uzyskać więcej informacji, zobacz [przy użyciu profilowania narzędzia z wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=224703). Jeśli chcesz ręcznie skonfigurować każdego aspektu sesji wydajności, zobacz [porady: ręczne tworzenie sesji wydajności przy użyciu narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224691). Można również utworzyć sesję wydajności z testu jednostkowego, w **wyników testu** okna, otwieranie menu skrótów dla testu jednostkowego, a następnie wybierając **Tworzenie sesji wydajności**.


Po skonfigurowaniu sesję wydajności z konfiguracji sesji jest zapisywany, serwer jest skonfigurowany w celu zapewnienia danych profilowania i jest uruchomiona aplikacja. Jak używać aplikacji, dane dotyczące wydajności są zapisywane w pliku dziennika. Sesje wydajności są wymienione w **Eksplorator wydajności** w obszarze **cele** folderu. Po zakończeniu sesji wydajności, jego raport jest wyświetlany w **raporty** folderu w **Eksplorator wydajności**. Aby wyświetlić raport, otwórz go w **Eksplorator wydajności**. Aby wyświetlić lub skonfigurować właściwości sesji wydajności, otwórz menu skrótów w **Eksplorator wydajności**, a następnie wybierz pozycję **właściwości**. Aby uzyskać więcej informacji na temat określonych właściwości sesji wydajności, zobacz [Konfigurowanie sesji wydajności dla narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224694). Aby uzyskać informacje na temat interpretacji wyników sesji wydajności, zobacz [analizowanie danych narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-testing"></a>Testowanie obciążeniowe

Wydajność obciążenia aplikacji można analizować, tworząc testów obciążenia oraz testy wydajności sieci web w programie Visual Studio. Podczas tworzenia testu obciążenia w programie Visual Studio, należy określić kombinację czynników, nazywany scenariusza, aby przetestować aplikację na. Czynniki te obejmują wzorca obciążenia, model testu mieszanego testu mieszanego, mieszany profil sieciowy i rozkład przeglądarek sieci web. Scenariusze testowania obciążenia mogą obejmować zarówno testów jednostkowych i wydajności sieci web.

Rysunek 1: Przykład wyników testów obciążenia

![Uruchamianie testu obciążenia wykresach widoku](../sharepoint/media/load-webgraphs.png "widoku wykresach Uruchamianie testu obciążenia")

Testy wydajności sieci Web symulować, użytkownik końcowy może interakcji z aplikacją programu SharePoint. Testy wydajności sieci web można utworzyć rejestrowania żądań HTTP w sesji przeglądarki lub za pomocą **Rejestrator testu wydajności sieci Web**. Żądania sieci web są wyświetlane w **edytora testów wydajności sieci Web** po zakończeniu sesji przeglądarki. Następnie można debugować wyniki w **przeglądarka wyników testu wydajności sieci Web**. Testy wydajności sieci web można tworzyć ręcznie za pomocą **edytora testów wydajności sieci Web**.

## <a name="testing-user-interfaces"></a>Testowanie interfejsów użytkownika

Kodowane testy interfejsu użytkownika automatycznie stacji aplikacji programu SharePoint za pomocą jego interfejsu użytkownika (UI). Te testy obejmują kontrolek interfejsu użytkownika, takie jak przyciski i menu, aby sprawdzić, czy działają poprawnie. Tego rodzaju testowania jest szczególnie przydatne, jeśli sprawdzanie poprawności lub innych logiki jest wykonywana w Interfejsie użytkownika, takie jak na stronie sieci web. Kodowane testy interfejsu użytkownika umożliwia również automatyzację testy ręczne. Tworzenia kodowanych testów interfejsu użytkownika dla aplikacji programu SharePoint w taki sam sposób jak tworzenie testów dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Profilowanie aplikacji SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Pokazuje, jak przeprowadzić analizę profil próbkowania w aplikacji programu SharePoint.|
|[Testowanie wydajności aplikacji z przed wprowadzeniem](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|Opisuje sposób tworzenia testów obciążenia, które ułatwiają testowania obciążenia aplikacji SharePoint.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Opisuje sposób wyszukiwania logiki błędów w kodzie za pomocą testów jednostkowych.|
|[Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Opisuje sposoby testowania interfejsu użytkownika aplikacji programu SharePoint.|

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Podnoszenie jakości kodu](../test/improve-code-quality.md)