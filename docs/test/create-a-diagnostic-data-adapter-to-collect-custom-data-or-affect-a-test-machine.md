---
title: Tworzenie adaptera danych diagnostycznych do testowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 91f340fee26b908ea90ad540e9c9fb2fdb1acf81
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Tworzenie adaptera danych diagnostycznych zbieranie danych niestandardowych lub mają wpływ na maszynę testową

Można chcieć tworzyć własne adaptery danych diagnostycznych do zbierania danych, gdy zostanie uruchomiony test lub potrzeba wpłynąć na maszynę testową, jako część testu. Na przykład należy zebrać pliki dziennika, które są tworzone przez testowaną aplikację i dołączyć je do wyników testu lub należy uruchomić testy przy ograniczonym miejscu na dysku na komputerze. Za pomocą interfejsów API dostarczonych w Visual Studio Enterprise, można napisać kod, aby wykonać zadania w określonych punktach w testu. Na przykład można wykonywać zadania po rozpoczęciu przebiegu testowego, przed i po poszczególnych testach oraz po zakończeniu przebiegu testowego.

Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Mogą być wyświetlane i edytowanych przy użyciu domyślnego edytora dostarczane z Microsoft Test Manager lub mogą tworzyć własne kontrolki użytkownika edytora. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.

Jeśli korzystasz z testów w programie Visual Studio, należy ustawić te ustawienia jako aktywne testu. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

## <a name="tasks"></a>Zadania

 Użyj następujących tematów pomocnych przy tworzeniu Adapterów danych diagnostycznych:

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Tworzenie adaptera danych diagnostycznych:** utworzyć adaptera danych diagnostycznych, tworząc biblioteki klas, a następnie zbierać informacje lub mieć wpływ na system testowy, którego używasz do uruchamiania testów za pomocą adaptera danych diagnostycznych interfejsów API.|-   [Porady: tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Instalowanie niestandardowego adaptera danych diagnostycznych:** można zainstalować Twojego adaptera danych diagnostycznych lub adapter dostarczony przez inną osobę, kopiując je w poprawnym katalogu.|-   [Porady: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/how-to-install-a-custom-diagnostic-data-adapter.md)|
|**Wybranie niestandardowego adaptera danych diagnostycznych do użycia gdy testy są uruchamiane:** adaptera danych diagnostycznych, które do użycia na potrzeby ustawień testu, można wybrać tak, że karta jest używany podczas uruchamiania testów.|-   [Zbierane dane diagnostyczne podczas testowania (VSTS)](/vsts/manual-test/collect-diagnostic-data)<br />-   [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Konfigurowanie adaptera danych diagnostycznych jest:** można skonfigurować ustawienia, aby kontrolować akcje adaptera danych diagnostycznych w ustawieniach tego określonego testu.|-   [Porady: tworzenie edytora niestandardowego dla danych dla Twojego adaptera danych diagnostycznych](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)|

## <a name="see-also"></a>Zobacz także

- [Przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)