---
title: Właściwości scenariusza testów obciążenia programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 144a875822034ef3ae10a4f0cb5f1771ebf61fb7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="load-test-scenario-properties"></a>Właściwości scenariusza testów obciążenia

Zmienić ustawienia właściwości scenariusza testów obciążenia w programie Visual Studio, aby spełnić wymagania dotyczące testowania obciążenia. W tym artykule wymieniono różne właściwości scenariusza testów obciążenia według kategorii.

## <a name="general"></a>Ogólne

|Właściwość|Definicja|
|--------------|----------------|
|**Nazwa**|Nazwa scenariusza.|

## <a name="mix"></a>Miks

|Właściwość|Definicja|
|--------------|----------------|
|**Rozkład przeglądarek**|Określa miks przeglądarki internetowej dla testu obciążeniowego. Można wybrać różne typy przeglądarek sieci Web oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropka (...), aby otworzyć okno dialogowe Edytuj rozkład przeglądarek i użyć **Dodaj** i **Usuń** wybierz typy przeglądarek sieci Web w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów przeglądarek sieci Web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Mieszany profil sieciowy**|Określa mieszany profil sieciowy dla testu obciążeniowego. Można określić, które typy sieci mają zostać objęte testem, oraz rozkład obciążenia między nimi.<br /><br />Kliknij przycisk wielokropka (...), aby otworzyć **Edytuj mieszany profil sieciowy** okno dialogowe i użyj **Dodaj** i **Usuń** wybierz typy sieci w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Mieszanka testów**|Określa miks testów wydajności sieci Web i testów jednostkowych w teście obciążeniowym. Można określić, które testy mają zostać wykonane, oraz rozkład obciążenia między nimi.<br /><br />Kliknij przycisk wielokropka (...), aby otworzyć **edytowanie mieszanki testów** okno dialogowe i użyj **Dodaj** i **Usuń** do wyboru testów w teście obciążenia.<br /><br />Aby uzyskać więcej informacji [edytowanie mieszanki testów dla scenariusza testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ testu mieszanego**|Określa model testu mieszanego dla testu obciążenia.<br /><br />Kliknij przycisk wielokropka (...), aby otworzyć **edytowanie mieszanki testów** okno dialogowe i użyj listy rozwijanej w obszarze **model testu mieszanego** wybierz model testu mieszanego do użycia w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Opcje

|Właściwość|Definicja|
|--------------|----------------|
|**Agentów**|Określa, że agenci, którzy mają scenariusz do użycia, jeśli używasz obciążenia test zdalnie. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Agenci mogą być również rozproszeni geograficznie, tak aby istniała koligacja między skryptami wykonywanymi przez agentów a lokalizacją agentów.<br /><br />Agenci muszą być oddzielone przecinkami, na przykład "**Agent3 Agent1, Agent2,**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.<br /><br />Aby uzyskać więcej informacji, zobacz [porady: Określanie agentów testowych stosowanych](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Zastosuj rozkład do opóźnienia kroku**|Wartość logiczna, która służy do określania, jeśli chcesz zastosować dystrybucji typowe opóźnienia użytkownika tempo model testu mieszanego. Ta właściwość ma zastosowanie tylko wtedy, gdy **typ testu mieszanego** właściwość jest ustawiona na **oparty na tempie użytkownika**.<br /><br />Aby uzyskać więcej informacji, zobacz [porady: zastosowanie dystrybucji do opóźnienia kroku](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Przełączania IP**|Wartość logiczna, która służy do określania, czy używane jest przełączanie IP.<br /><br />Przełączania IP umożliwia agenta testowego do wysyłania żądań do serwera przy użyciu szereg różnych adresów IP. Symuluje to wywołania, które pochodzą z różnych klientów. Ważne jest przełączania IP, gdy przetestować farmy sieci Web ze zrównoważonym obciążeniem. Większość modułów równoważenia obciążenia ustanowić koligację między klientem a serwerem sieci Web określonego za pomocą adresu IP klienta. Jeśli wszystkie żądania są one pochodzą z jednego klienta, usługi równoważenia obciążenia nie będą Równoważenie obciążenia. Uzyskanie Równoważenie obciążenia dobrej w kolektywie serwerów sieci Web, ważne jest, że żądania pochodzą z zakresu adresów IP.<br /><br />Funkcja przełączania adresów IP jest dostępna w przypadku używania agenta testowego.|
|**Maksymalnej liczby iteracji testu**|Wartość liczbowa służąca do określenia maksymalnej liczby testów, jakie mają zostać wykonane w scenariuszu. Wartość 0 oznacza brak maksimum.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Procent nowych użytkowników**|Wartość liczbowa określająca procent nowych użytkowników lub gości w scenariuszu.<br /><br />Aby uzyskać więcej informacji, zobacz [porady: Określanie wartości procentowej użytkowników wirtualnych sieci Web użycia pamięci podręcznej danych](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Wziąć pod uwagę profilu**|Określa, czy będzie używać tego scenariusza **rozkładu normalnego**, lub jeśli reakcji profil jest **na** lub **poza**.<br /><br />Aby uzyskać więcej informacji, zobacz [edytowanie czasów reakcji w sposób symulować witryny sieci Web człowieka opóźnienia](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Chronometraż

|Właściwość|Definicja|
|--------------|----------------|
|**Czas rozpoczęcia opóźnienia**|Wartość czasu, która wskazuje, ile godzin, minut i sekund ma trwać opóźnienie rozpoczęcia scenariusza po rozpoczęciu testu obciążeniowego. Jeśli **Wyłącz podczas rozgrzewania** właściwość jest ustawiona na **True**, czas oczekiwania stosuje się po zakończeniu okresu rozgrzewania.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień Uruchom scenariusz](../test/configure-scenario-start-delays.md).|
|**Wyłącz podczas rozgrzewania**|Wartość logiczna, która służy do określania, czy scenariusza należy uruchomić lub nie w czasie **ciepłych Duration** ustawienia do uruchamiania wartość czasu właściwości określona w teście obciążenia.<br /><br />Aby uzyskać więcej informacji o uruchomieniu właściwości ustawień testu obciążenia, zobacz [załadować Test ustawienia właściwości Uruchom](../test/load-test-run-settings-properties.md).<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień Uruchom scenariusz](../test/configure-scenario-start-delays.md).|
|**Czasy pomiędzy iteracjami testu reakcji**|Wartość liczbowa służąca do określenia czasu oczekiwania (w sekundach) między iteracjami testu.<br /><br />Aby uzyskać więcej informacji, zobacz [edytowanie czasów reakcji w sposób symulować witryny sieci Web człowieka opóźnienia](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)