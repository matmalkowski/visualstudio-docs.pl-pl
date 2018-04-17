---
title: Kontroler testów i wymagania agenta testowego dla obciążenia, testowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 1c6ae9d8200d6e8f32b7f8a96b222b4bfb4c75d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Wymagania dla kontrolera testów i agentów testowych niezbędnych do testów obciążenia

Przetestuj kilka typów w tym jednostki, wydajności sieci web, obciążenia i testy ręczne są zintegrowane z programu Visual Studio. Visual Studio umożliwia użytkownikom zarządzanie cyklem życia aplikacji w usłudze Visual Studio do uruchomienia testów na komputerach zdalnych przy użyciu kontrolera testu i jeden lub więcej agentów. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="hardware-and-software-requirements"></a>Wymagania sprzętowe i programowe

Kontroler testów i komputerach agenta testowego ma szczególne wymagania dotyczące sprzętu i oprogramowania. Ponadto do wdrożenia kontrolera testów i przetestowania komputery agenta w wielu językach, należy zaplanować jak obsługiwać tych języków.

### <a name="hardware-requirements"></a>Wymagania sprzętowe

W poniższej tabeli przedstawiono zalecane wymagania sprzętowe dotyczące wdrażania kontrolera testów i agentów testowych.

|**Konfiguracja**|**Składnik**|**CPU**|**HD**|**Pamięci**|
|-----------------------|-------------------|-------------|------------|----------------|
|< 500 wirtualnych użytkowników|Agent testowy|2.6 GHz|10 GB|2 GB|
|< 1000 wirtualnych użytkowników|Agent testowy|Procesor dwurdzeniowy 2.6 GHz|10 GB|2 GB|
|N x 1000 wirtualnych użytkowników|Agent testowy|Skalowanie w poziomie do N agentów każdego z podwójną 2.6 Ghz|10GB|2GB|
|\< 30 komputerów w środowisku testowym. W tym agenci i serwery w ramach testu.|Kontroler testów|2.6 GHz|||
|N x 30 komputerów w środowisku testowym. W tym agenci i serwery w ramach testu.|Kontroler testów|N 2.6 procesorów GHz|||

> [!NOTE]
> Liczba wirtualnych użytkowników różnią się powszechnie z testu do testu. Klucza przyczyna tego odchylenia jest wariancji w *czasy reakcji*, lub opóźnienia użytkownika. Aby uzyskać więcej informacji, zobacz [edytowanie czasów reakcji w sposób symulować witryny sieci Web człowieka opóźnienia](../test/edit-think-times-in-load-test-scenarios.md). W czasie testu obciążenia testy sieci Web są zazwyczaj bardziej wydajny i wygenerować obciążenie więcej niż testy jednostkowe. Liczby w powyższej tabeli są prawidłowe dla uruchamiania testów sieci Web z 3 – 5 sekundę czasów reakcji w typowej aplikacji sieci Web.

Wytycznych przedstawionych tutaj podano jako ogólne wskazówki dotyczące planowania sprzętu. Test wydajności różnią się znacznie na podstawie ilości danych testowych i liczba agentów testowych. Agentów testowych szybkości procesora CPU i pamięci ograniczy testu obciążenia. Test kontrolerów większe zasoby, w zależności od liczby agentów testu i ilość danych, które są związane z testów.

Serwer, który jest uruchomiony program Visual Studio ma niezawodne połączenie sieciowe z minimalną przepustowość 1 MB/s i opóźnieniu maksymalnie 350ms. Nie powinno być nie zapory między agentów testowych i kontrolera testu. Jeśli wydajność testu, ponieważ nie spełnia Twoich oczekiwań, zmodernizowanie konfiguracji sprzętu.

### <a name="additional-hardware-considerations"></a>Zagadnienia dotyczące sprzętu dodatkowe

Agenci testowi generowanie dużej ilości danych na kontrolerach testowego, w zależności od czas trwania testu i rozmiar testu. Ogólnie rzecz biorąc należy również zaplanować dodatkowe 10 GB miejsca do magazynowania dysku twardego dla danych testowych co 24 godziny.

Oprócz sprzętu zalecane w tym miejscu należy wziąć pod uwagę dodatkowego sprzętu dla serwerów o znaczeniu, takie jak nadmiarowe zasilacze i wentylatory nadmiarowe.

### <a name="language-requirements"></a>Wymagania językowe

Aby uniknąć pomyłek i uprościć operacji, kontrolera i testowania agentów testowych należy skonfigurować do używania tego samego języka jako systemu operacyjnego i programu Team Foundation Server. Jeśli agent testowy i kontroler testów są zainstalowane na różnych komputerach, musi być skonfigurowany do używania tego samego języka. Można jednak zainstalować innej wersji językowej programu Visual Studio w systemie operacyjnym język angielski, tak długo, jak ten język jest zgodny ze wdrożenia programu Team Foundation Server.

## <a name="monitor-agent-resources"></a>Monitor zasobów agenta

Można monitorować maszynami agenta, aby określić ich zapotrzebowanie na zasoby obserwując **QTAgent\*.exe** procesów, które wykonania i skalować podczas testów. Najbardziej typowym wąskim gardłem na procesach QTAgent*.exe jest użycie procesora CPU. Jeśli wykorzystanie procesora CPU jest stale w wysokiej nineties to wskazanie, że agent jest ładowany silnie. Następny typowym wąskim gardłem jest użycie pamięci. Dla wymagających testy, monitorowanie tych zasobów może pomóc określenia, czy należy zwiększyć zasobów maszyny i dystrybucję testów inaczej.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)