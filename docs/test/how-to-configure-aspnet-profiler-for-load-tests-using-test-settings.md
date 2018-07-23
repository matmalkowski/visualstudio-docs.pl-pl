---
title: Konfigurowanie Profiler platformy ASP.NET dla testów obciążenia w programie Visual Studio
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
ms.openlocfilehash: c6e863ed52402dd56a81924f8ef7f4ecbd6ad258
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39175555"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Porady: konfiguracja profilera ASP.NET do ładowania testów za pomocą opcji ustawień testów w Visual Studio

Adapter danych diagnostycznych profilera ASP.NET służy do zbierania informacji z profilera środowiska ASP.NET. Ten adapter danych diagnostycznych zbiera dane wydajności dla aplikacji ASP.NET.

> [!NOTE]
> Nie można użyć tego adaptera danych diagnostycznych dla testów, które są uruchamiane przy użyciu programu Microsoft Test Manager. Można użyć adaptera diagnostycznego programu ASP.NET Profiler testy obciążeniowe wykonywane tylko witryny sieci Web, która wymaga programu Visual Studio Enterprise.

Adapter danych diagnostycznych profilera ASP.NET umożliwia zbieranie danych profilera platformy ASP.NET z warstwy aplikacji, po uruchomieniu testu obciążenia. Profilera nie należy uruchamiać dla długich testów obciążeniowych, na przykład trwających ponad godzinę. Wynika to z faktu, że plik profilera może się rozrosnąć, nawet do kilkuset megabajtów. Zamiast tego należy wykonywać krótsze testy obciążeniowe przy użyciu profilera platformy ASP.NET, który wciąż daje korzyści też bardzo szczegółowo diagnozuje problemy z wydajnością.

> [!NOTE]
> Adapter danych diagnostycznych profilera ASP.NET profiluje proces Internet Information Services (IIS). W związku z tym nie będzie on działał dla serwera sieci web development. Profilowanie witryny sieci Web w teście obciążenia, musisz zainstalować agenta testowego na komputerze, na którym działa program IIS. Agent testowy nie będzie generował obciążenia, a jedynie pośredniczył w zbieraniu danych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

Aby uzyskać więcej informacji, zobacz [jak: utworzyć ustawienia testu dla testu obciążeniowego rozproszonych](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

Poniższa procedura opisuje sposób konfigurowania adaptera danych diagnostycznych profilera platformy ASP.NET.

## <a name="to-configure-the-aspnet-profiler-for-your-test-settings"></a>Aby skonfigurować profiler środowiska ASP.NET według ustawień testu

Przed wykonaniem kroków w tej procedurze należy otworzyć Ustawienia testu z programu Visual Studio i wybrać **dane i Diagnostyka** strony.

### <a name="to-configure-the-aspnet-profiler-for-your-test-settings"></a>Aby skonfigurować profiler środowiska ASP.NET według ustawień testu

1.  Wybierz rolę, która ma zbierać dane profilera platformy ASP.NET.

    > [!WARNING]
    > Ta rola musi być serwerem sieci web.

2.  Wybierz **ASP.NET Profiler** włączy zbieranie danych profilowania ASP.NET, a następnie wybierz polecenie **Konfiguruj**.

     Wyświetlane jest okno dialogowe, aby skonfigurować zbieranie danych z profilowania ASP.NET.

3.  W **interwał próbkowania Profiler**, wpisz wartość, która wskazuje, ile niewstrzymanych Procesora zegara cykle oczekiwania między pobieraniem próbek profilowania ASP.NET.

4.  Aby włączyć profilowanie interakcji pomiędzy warstwami, zaznacz **Włącz profilowanie interakcji pomiędzy warstwami**.

     Liczba żądań, które są wysyłane do serwera sieci web dla każdego artefaktu (np. MyPage.aspx lub CompanyLogo.gif) profilowanie interakcji pomiędzy warstwami, a czas, jaki zajęła Obsługa każdego żądania. Ponadto są zbierane informacje o tym, które połączenia środowiska ADO.NET były używane w ramach żądania o stronę oraz jak wiele zapytań i wywołań procedur przechowywanych zostało wykonanych w ramach obsługi tego żądania.

     Mechanizm zbiera dwa różne zestawy informacji o czasie:

    -   Informacje o czasie (Min., Maks., Średnia i Suma) obsługi każdego żądania sieci web.

    -   Informacje o czasie (Min., Maks., Średnia i Suma) wykonania każdego zapytania.

Adapter danych diagnostycznych profilera ASP.NET skonfigurowany w ustawieniach testu można teraz zbierać dane na aplikację sieci web platformy ASP.NET profilowania ASP.NET.

## <a name="see-also"></a>Zobacz także

- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Porady: Tworzenie ustawień testu dla testu obciążenia rozłożonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)