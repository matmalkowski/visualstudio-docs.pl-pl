---
title: Konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika w programie Visual Studio
ms.date: 2015-10-04
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3fc4d5a6c1a4ae3cabbbb2426d7a4fdf011b9e0e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693890"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji

W poniższej tabeli wymieniono obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika dla programu Visual Studio Enterprise. Te konfiguracje mają zastosowanie również do rejestrowania akcji utworzone za pomocą [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)].

> [!NOTE]
> Proces kodowanego testu interfejsu użytkownika musi mieć takie same uprawnienia, jak aplikacja poddawana testom.


 **Wymagania**

-   Visual Studio Enterprise

## <a name="supported-configurations"></a>Obsługiwane konfiguracje

|Konfiguracja|Obsługiwane|
|-------------------|---------------|
|Systemy operacyjne|[!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10|
|Obsługa wersji 32-/64-bitowej|32-bitowego systemu Windows uruchomiona 32-bitowych [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] można testować aplikacje 32-bitowe.<br /><br /> 64-bitowego systemu Windows uruchomiona 32-bitowych [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] można przetestować aplikacje WOW 32-bitowy, który ma Synchronization.n interfejsu użytkownika.<br /><br /> 64-bitowego systemu Windows uruchomiona 32-bitowych [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] można przetestować formularzy systemu Windows i aplikacje WPF, którego nie ma interfejsu użytkownika synchronizacji 64-bitowych.|
|Architektura|x86 i x64 **Uwaga:** programu Internet Explorer nie jest obsługiwane w trybie 64-bitowym z wyjątkiem podczas uruchamiania [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszy.|
|.NET|.NET 2.0, 3.0, 3.5, 4 i 4.5. **Uwaga:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] zarówno programu Visual Studio będzie wymagać .NET 4 do działania. Jednak aplikacje opracowane za pomocą wymienionych wersji środowiska .NET są obsługiwane.|

> [!NOTE]
> *Interfejs użytkownika synchronizacji* to funkcja, której odtwarzanie jest weryfikowana w kolejce wiadomości każdej kontrolki. Jeśli formant nie odpowiedział na zdarzenie, które zostało do niego wysłane, zdarzenie jest wysyłane ponownie.


## <a name="platform-support"></a>Obsługa platformy

|Platforma|Poziom wsparcia|
|--------------|----------------------|
|Aplikacje Windows Phone|Tylko WinRT-opartych na języku XAML Phone aplikacje są obsługiwane.|
|Aplikacji platformy uniwersalnej systemu Windows|Obsługiwane są tylko aplikacje platformy uniwersalnej systemu Windows opartych na języku XAML.|
|Aplikacje uniwersalne systemu Windows|Obsługiwane są tylko opartych na języku XAML uniwersalnych aplikacji systemu Windows Phone i pulpitu.|
|Krawędź|Rejestrowanie kroków akcji lub przy użyciu konstruktora do wyświetlania właściwości obiektów nie jest obsługiwana. Testy można odtworzyć w przeglądarce Microsoft Edge przy użyciu programu Visual Studio 2015 Update 2 lub nowszym [kodowanego interfejsu użytkownika dla wielu przeglądarki rozszerzenie testowania](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **ważne:** programu Internet Explorer 10, jest obsługiwana tylko na pulpicie. <br /><br /> Internet Explorer 11 **ważne:** programu Internet Explorer 11 jest obsługiwana tylko na pulpicie.|W pełni obsługiwane.<br /><br /> -   **Obsługa HTML5 w programie Internet Explorer 9 i programu Internet Explorer 10:** kodowanych testów interfejsu użytkownika obsługuje rekordu, odtwarzania i sprawdzania poprawności formantów HTML5: Audio i wideo, ProgressBar oraz Slider. Aby uzyskać więcej informacji, zobacz [za pomocą formantów HTML5 w kodowanych testów interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md). **Ostrzeżenie:** w przypadku utworzenia kodowanych testów interfejsu użytkownika w programie Internet Explorer 10, może nie zostać uruchomiony przy użyciu programu Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane tym, że Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.<br />-   **Obsługa sprawdzanie pisowni, Internet Explorer 10:** programu Internet Explorer 10 zawiera możliwości dla wszystkich pól tekstowych sprawdzania pisowni. Pozwala to na wybranie z listy sugerowanych poprawek. Kodowany test interfejsu użytkownika będzie ignorować czynności użytkownika, takie jak zaznaczenie sugestii alternatywnej pisowni. Rejestrowany będzie tylko końcowy tekst wpisany w polu tekstowym.<br />     Następujące akcje są rejestrowane dla kodowanych testów interfejsu użytkownika, które używają formantu sprawdzania pisowni: Dodaj do słownika, Kopiuj, Zaznacz wszystko, Dodaj do słownika i Ignoruj.<br />-   **Obsługa 64-bitowy program Internet Explorer do uruchamiania systemu Windows 8:** wcześniej, 64-bitowej wersji programu Internet Explorer nie są obsługiwane dla rejestrowaniem i odtwarzaniem. Z [!INCLUDE[win8](../debugger/includes/win8_md.md)] i [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], kodowanych testów interfejsu użytkownika zostały włączone dla 64-bitowych wersji programu Internet Explorer. **Ostrzeżenie:** Obsługa 64-bitowego dla programu Internet Explorer ma zastosowanie, tylko jeśli uruchamiasz [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszym.<br />-   **Obsługę przypięty witryn w programie Internet Explorer 9:** w programie Internet Explorer 9, przypięty lokacji zostały wprowadzone. Dzięki przypiętym witrynom można przejść do ulubionych witryn bezpośrednio z paska zadań systemu Windows — bez konieczności wcześniejszego otwierania Internet Explorer. Kodowane testy interfejsu użytkownika mogą teraz świadomie generować akcje na przypiętych witrynach. Aby uzyskać więcej informacji o lokacjach przypięte, zobacz [przypięty witryny](http://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Obsługa tagów semantycznego Internet Explorer 9:** programu Internet Explorer 9 wprowadzono następujące znaczniki semantycznego: sekcji, nav, artykuł, Zarezerwuj, hgroup, nagłówek, stopka, ilustracji, figcaption i znak. Kodowane testy interfejsu użytkownika ignorują wszystkie te znaczniki semantyczne podczas nagrywania. Możesz dodać potwierdzenia na tych tagach za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można użyć pokrętła nawigacji w Konstruktorze kodowanego testu interfejsu użytkownika, aby nawigować do jednego z tych elementów i przeglądać ich właściwości.<br />-   **Bezproblemowe obsługi z znaki odstępu między wersjami programu Internet Explorer:** istnieją różnice w obsłudze białych znaków programu Internet Explorer 8, Internet Explorer 9 i programu Internet Explorer 10. Kodowany test interfejsu użytkownika bezproblemowo obsługuje te różnice. Dlatego kodowany test interfejsu użytkownika, utworzony na przykład w Internet Explorer 8, będzie z powodzeniem odtwarzany w Internet Explorer 9 i Internet Explorer 10.<br />-   **Powiadomienia obszaru programu Internet Explorer są teraz rejestrowane z ustawiony atrybut "Kontynuować on Error":** wszystkie akcje w obszarze powiadomień programu Internet Explorer są teraz rejestrowane z ustawionym atrybutem "Kontynuować on Error". Jeśli nie ma paska powiadomień podczas odtwarzania, operacje na nim zostaną zignorowane i kodowany test interfejsu użytkownika przejdzie do następnej akcji.|
|Formanty Windows Forms i WPF innych firm|W pełni obsługiwane.<br /><br /> Aby włączyć formanty innych firm w formularzach Windows Forms i aplikacjach WPF, należy dodać odwołania i kod. Aby uzyskać więcej informacji, zobacz [włączyć kodowanego kontrolek interfejsu użytkownika testowania z Your](../test/enable-coded-ui-testing-of-your-controls.md).|
|Program Internet Explorer 6<br /><br /> Internet Explorer 7|Nieobsługiwane.|
|Chrome<br /><br /> Firefox|Rejestrowanie czynności nie jest obsługiwane. Zakodowane testy interfejsu użytkownika mogą być odtwarzane w przeglądarkach Chrome i Firefox z programu Visual Studio 2012 aktualizacja 4 lub nowsza. Przejdź [tutaj](http://msdn.microsoft.com/library/jj835758.aspx) więcej szczegółów.|
|Opera<br /><br /> Safari|Nieobsługiwane.|
|Silverlight|Nieobsługiwane.<br /><br /> Jednak Visual 2013 Studo można pobrać [Microsoft Visual Studio 2013 kodowanego interfejsu użytkownika testu dodatek dla programu Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) z galerii programu Visual Studio.|
|Flash/Java|Nieobsługiwane.|
|Windows Forms 2.0 i nowsze wersje|W pełni obsługiwane. **Uwaga:** NetFx formanty są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane.|
|WPF 3.5 i nowsze wersje|W pełni obsługiwane.<br /><br /> **Uwaga** NetFx formanty są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane.|
|Windows Win32|Może pracować z niektórymi znanymi problemami, ale nie jest oficjalnie obsługiwany.|
|MFC|Obsługiwane częściowo. Zobacz następujące tematy [witrynę sieci Web](http://go.microsoft.com/fwlink/?LinkId=206511) informacji o jakie funkcje są obsługiwane.|
|Program SharePoint|W pełni obsługiwane.|
|Aplikacje klienckie pakietu Office|Nieobsługiwane.|
|Klient sieci web Dynamics CRM|W pełni obsługiwane.|
|Klient Dynamics (Ax) 2012|Akcje odtwarzania i nagrywania są obsługiwane częściowo. Zobacz następujące tematy [witrynę sieci Web](http://go.microsoft.com/fwlink/?LinkId=232677) szczegółowe informacje.|
|SAP|Nieobsługiwane.|
|Citrix/usługi terminalowe|Nie zaleca się rejestrowanie czynności serwera terminali. Rejestrator nie obsługuje uruchamianie wielu wystąpień w tym samym czasie.|
|PowerBuilder|Obsługiwane częściowo.<br /><br /> Obsługa zakresu ułatwień dostępu jest włączona dla formantów PowerBuilder.|

 Aby uzyskać informacje o sposobie tworzenia rozszerzenia obsługi innych platform, zobacz [włączyć kodowanego kontrolek interfejsu użytkownika testowania z Your](../test/enable-coded-ui-testing-of-your-controls.md) i [rozszerzenie kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
