---
title: Dane funkcji IntelliTrace w programie Visual Studio
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c6b34993e011a8bf539b6ec2dd70beddf9c96caf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Porady: gromadzenie danych IntelliTrace pomocnych w debugowaniu trudnych problemów

Adapter danych diagnostycznych dla funkcji IntelliTrace do zbierania informacji śledzenia diagnostycznego określonych w programie Visual stdio — można skonfigurować. Adapter może być wykorzystywany przez testy do zbierania informacji o ważnych zdarzeniach diagnostycznych dotyczących aplikacji, na podstawie których deweloper później prześledzi kod i znajdzie przyczyny usterki. Adaptera danych diagnostycznych narzędzia IntelliTrace można używać w testach ręcznych i automatycznych.

> [!NOTE]
> Narzędzie IntelliTrace działa tylko wobec aplikacji napisanych przy użyciu kodu zarządzanego. Podczas testowania aplikacji sieci Web, która jako klienta używa przeglądarki, nie należy w ustawieniach testu włączać narzędzia dla tego klienta, ponieważ nie jest dostępny żaden kod zarządzany, który można by śledzić. W takim przypadku najlepiej skonfigurować środowisko i zbierać dane z narzędzia IntelliTrace zdalnie na serwerze sieci Web.

Dane z narzędzia IntelliTrace są przechowywane w pliku z rozszerzeniem .iTrace. Po uruchomieniu testu i krok testu kończy się niepowodzeniem, można utworzyć usterki. Plik narzędzia IntelliTrace zawierający informacje diagnostyczne jest automatycznie dołączany do tej usterki.

> [!NOTE]
> Adapter danych diagnostycznych narzędzia IntelliTrace nie tworzy pliku, jeśli test przyniesie wynik pomyślny. Plik jest zapisywany tylko po nieudanym teście albo po przesłaniu usterki.

 Dane gromadzone w pliku narzędzia IntelliTrace usprawniają debugowanie, ponieważ umożliwiają szybsze odtwarzanie i diagnozowanie błędów w kodzie. Dodatkowo plik można udostępniać innym osobom w celu zreplikowania sesji na ich komputerach, co zmniejsza ryzyko, że usterki nie uda się odtworzyć.

> [!NOTE]
> W przypadku włączenia narzędzia IntelliTrace w ustawieniach testu funkcja zbierania danych o pokryciu kodu nie będzie działać.

> [!WARNING]
> Adapter danych diagnostycznych narzędzia IntelliTrace działa poprzez instrumentowanie zarządzanego procesu. Operację tę należy wykonać po załadowaniu testów dla przebiegu testowego. Jeśli proces, który ma być monitorowany, już się rozpoczął, nie będą zapisywane żadne pliki narzędzia IntelliTrace. Aby obejść ten problem, przed załadowaniem testów należy zatrzymać proces. Gdy tylko testy zostaną załadowane lub rozpocznie się pierwszy test, należy znów zainicjować proces.

 Poniższa procedura opisuje konfigurowanie zbierania określonych danych przez narzędzie IntelliTrace. Te kroki dotyczą edytora konfiguracji okno dialogowe Ustawienia testu i Microsoft Test Manager w programie Visual Studio.

> [!NOTE]
> Konto użytkownika agenta testów wykorzystywane do zbierania danych przez narzędzie IntelliTrace musi być członkiem grupy administratorów. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Określanie danych, które mają być zbierane przez adapter danych diagnostycznych narzędzia IntelliTrace

Przed wykonaniem kroków tej procedury należy otworzyć ustawień testu z Microsoft Test Manager lub programu Visual Studio i wybierz **danych i informacji diagnostycznych** strony.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Aby określić dane, które mają być zbierane przez adapter danych diagnostycznych narzędzia IntelliTrace

1.  Wybierz rolę, na której narzędzie IntelliTrace będzie zbierać dane.

2.  Wybierz **IntelliTrace**.

3.  W przypadku dodawania funkcji IntelliTrace dla roli klienta sieci Web lub aplikacji sieci Web ASP.NET, należy również wybrać **serwer Proxy klienta ASP.NET dla funkcji IntelliTrace i wpływ testu**.

     Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci Web dla adapterów danych diagnostycznych narzędzia IntelliTrace i wpływie na testy.

    > [!WARNING]
    > Jeśli dla tożsamości wykorzystywanej w puli aplikacji na serwerze IIS (Internet Information Server) mającym służyć do zbierania danych z narzędzia IntelliTrace zostanie użyte niestandardowe konto, należy na komputerze z programem IIS utworzyć lokalny profil użytkownika dla takiego konta. W celu utworzenia profilu można się zalogować jeden raz lokalnie na komputerze z programem IIS albo wykonać następujące polecenie w wierszu polecenia, podając poświadczenia niestandardowego konta:
    >
    > **cmd.exe/profile /user:domain\name runas**

4.  Wybierz **Konfiguruj** dla **IntelliTrace** Aby zmodyfikować domyślne ustawienia funkcji IntelliTrace.

     Zostanie wyświetlone okno dialogowe z opcjami określenia danych, które mają być zbierane.

    > [!WARNING]
    > Po włączeniu funkcji gromadzenia danych przez narzędzie IntelliTrace funkcja zbierania danych o pokryciu kodu nie będzie działać.

5.  Wybierz **ogólne** kartę. Wybierz **tylko zdarzenia IntelliTrace** do rejestrowania znaczących zdarzeń diagnostycznych, które ma minimalny wpływ na wydajność podczas testowania.

     **-** lub -

     Wybierz **zdarzeń funkcji IntelliTrace i informacji o wywołaniach** do rejestrowania zdarzeń diagnostycznych i metody poziom śledzenia, który zawiera informacje wywołania. Ten poziom śledzenia może podczas wykonywania testów odczuwalnie obciążać system.

6.  Aby zbierać dane z aplikacji platformy ASP.NET, która działa w programie Internet Information Services, wybierz **zbierania danych z aplikacji ASP.NET, które są uruchomione w programie Internet Information Services**. Zainstaluj i skonfiguruj agenta testów na serwerze sieci Web. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

7.  Wybierz **modułów** kartę. Wybierz opcję **zbierać dane ze wszystkich modułów oprócz następujących** i użyj **Dodaj** do dodania do listy modułów i **Usuń** można usunąć modułu. Ta opcja pozwala objąć wszystkie moduły działające w systemie poza konkretnie wskazanymi.

     —lub—

     Wybierz **zbierania danych z następujących modułów** i użyj **Dodaj** do dodania do listy modułów i **Usuń** można usunąć modułu. Ta opcja pozwala wskazać konkretne moduły, z których mają być gromadzone dane.

    > [!NOTE]
    > O ile to tylko możliwe, należy zaznaczać konkretne procesy, które mają być monitorowane. Zapewni to optymalne działanie systemu.

8.  Wybierz **procesów** kartę. Wybierz **zbierania danych od wszystkich procesów oprócz następujących** i użyj **Dodaj** można dodać do listy procesów i **Usuń** Aby usunąć proces. Ta opcja pozwala objąć gromadzeniem danych wszystkie procesy działające w systemie poza konkretnie wskazanymi.

     —lub—

     Wybierz **zbierania danych tylko z określonych procesów** i użyj **Dodaj** można dodać do listy procesów i **Usuń** Aby usunąć proces. Ta opcja pozwala wskazać konkretne procesy, z których mają być gromadzone dane.

9. (Opcjonalnie) Wybierz **zdarzeń funkcji IntelliTrace** kartę. Zaznacz lub wyczyść każdą kategorię zdarzeń narzędzia IntelliTrace, która ma być uwzględniona lub pominięta przy zbieraniu informacji o ważnych zdarzeniach diagnostycznych.

10. (Opcjonalnie) Rozwiń każdą kategorię zdarzeń narzędzia IntelliTrace i zaznacz lub wyczyść konkretne zdarzenia, o których narzędzie ma zbierać informacje.

11. (Opcjonalnie) Wybierz **zaawansowane** kartę. Następnie wybierz strzałkę obok pozycji **maksymalna ilość miejsca na dysku dla nagrywania** i wybierz maksymalny rozmiar, który chcesz włączyć dla pliku IntelliTrace do użycia.

    > [!NOTE]
    > Zbyt wysoki limit ilości rejestrowanych danych może sprawić, że podczas zapisywania danych razem z wynikami testu upłynie limit czasu. Aby uzyskać więcej informacji na temat zwiększyć wartości limitów czasu dla adapterów danych diagnostycznych, zobacz [porady: zapobieganie limitów czasu dla adapterów danych diagnostycznych](../test/how-to-prevent-time-outs-for-diagnostic-data-adapters.md).

12. Jeśli korzystasz z programu Microsoft Test Manager, wybierz **zapisać**. Jeśli używasz programu Visual Studio, wybierz **OK**. Ustawienia narzędzia IntelliTrace są teraz skonfigurowane i zapisane w ustawieniach testu.

    > [!NOTE]
    > Można zresetować konfiguracji dla tego adaptera danych diagnostycznych, wybierz **przywrócić konfigurację domyślną** dla programu Visual Studio lub **Przywróć ustawienia domyślne** dla programu Microsoft Test Manager.

## <a name="see-also"></a>Zobacz także

- [Zbierane dane diagnostyczne podczas testowania (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych funkcji IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)