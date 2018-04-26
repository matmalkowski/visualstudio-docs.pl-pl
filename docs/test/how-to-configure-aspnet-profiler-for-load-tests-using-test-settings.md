---
title: Konfiguracja profilera platformy ASP.NET, dla testów obciążenia w programie Visual Studio
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8910ee5aa73e057849ad6b72b67c8b27ba9b0e6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Porady: konfiguracja profilera ASP.NET do ładowania testów za pomocą opcji ustawień testów w Visual Studio

Adapter danych diagnostycznych profiler ASP.NET służy do zbierania informacji profilera platformy ASP.NET. Adapter danych diagnostycznych zbiera dane wydajności dla aplikacji ASP.NET.

> [!NOTE]
> Nie można użyć tego adaptera danych diagnostycznych dla testów, które są uruchamiane przy użyciu programu Microsoft Test Manager. Karta diagnostyki profilera platformy ASP.NET można używać z testów obciążenia za pomocą witryny sieci Web tylko co wymaga programu Visual Studio Enterprise.

Adapter danych diagnostycznych profiler ASP.NET umożliwia zbieranie danych profilera platformy ASP.NET z warstwy aplikacji, po uruchomieniu testu obciążenia. Profilera nie należy uruchamiać dla długich testów obciążeniowych, na przykład trwających ponad godzinę. Wynika to z faktu, że plik profilera może się rozrosnąć, nawet do kilkuset megabajtów. Zamiast tego należy uruchomić krótszą testów obciążenia przy użyciu profilera ASP.NET, które będą nadal zapewniać korzyści głębokie diagnozowanie problemów z wydajnością.

> [!NOTE]
> Adapter danych diagnostycznych profiler ASP.NET profile procesu usługi Internet Information Services (IIS). W związku z tym nie działa na deweloperskim serwerze sieci Web. Aby w teście obciążeniowym utworzyć profil witryny sieci Web, należy zainstalować agenta testowego na komputerze z programem IIS. Agent testowy nie będzie generował obciążenia, a jedynie pośredniczył w zbieraniu danych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

Aby uzyskać więcej informacji, zobacz [porady: Tworzenie ustawień testu dla rozproszonego testu obciążenia](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

W poniższej procedurze opisano sposób konfigurowania adaptera danych diagnostycznych profilera platformy ASP.NET.

## <a name="to-configure-the-aspnet-profiler-for-your-test-settings"></a>Aby skonfigurować profiler środowiska ASP.NET według ustawień testu

Przed wykonaniem kroków tej procedury należy otworzyć z ustawień testu w programie Visual Studio i wybrać **danych i informacji diagnostycznych** strony.

### <a name="to-configure-the-aspnet-profiler-for-your-test-settings"></a>Aby skonfigurować profiler środowiska ASP.NET według ustawień testu

1.  Wybierz rolę, która służy do zbierania danych profilera platformy ASP.NET.

    > [!WARNING]
    > Rolą musi być serwer internetowy.

2.  Wybierz **profilera ASP.NET** do włączenia zbierania danych profilowania platformy ASP.NET, a następnie wybierz **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe, aby skonfigurować zbierania danych profilowania ASP.NET.

3.  W **interwał próbkowania profilera**, wpisz wartość, która wskazuje, ile Procesora nie zostało zatrzymane zegara cykle oczekiwania między pobieraniem próbek profilowania ASP.NET.

4.  Aby włączyć profilowanie interakcji między warstwami, zaznacz **Włącz profilowanie interakcji między warstwami**.

     Profilowanie interakcji pomiędzy warstwami polega na zliczaniu liczby żądań wysyłanych do serwera internetowego dla każdego artefaktu (np. MyPage.aspx lub CompanyLogo.gif) oraz czasu, jaki zajęła obsługa każdego żądania. Ponadto są zbierane informacje o tym, które połączenia środowiska ADO.NET były używane w ramach żądania o stronę oraz jak wiele zapytań i wywołań procedur przechowywanych zostało wykonanych w ramach obsługi tego żądania.

     Mechanizm zbiera dwa różne zestawy informacji o czasie:

    -   Informacje o czasie (Min., Maks., Średnia i Suma) obsługi każdego żądania sieci web.

    -   Informacje o czasie (Min., Maks., Średnia i Suma) wykonania każdego zapytania.

Adapter danych diagnostycznych profiler ASP.NET skonfigurowane w ustawienia testu można teraz zebrać danych w aplikacji sieci ASP.NET Web profilowania platformy ASP.NET.

## <a name="see-also"></a>Zobacz także

- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Porady: Tworzenie ustawień testu dla rozproszonego testu obciążenia](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)