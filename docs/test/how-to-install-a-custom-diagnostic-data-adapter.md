---
title: 'Porady: Instalowanie niestandardowego adaptera danych diagnostycznych w programie Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24ce9f954164cd8d243edfab4387f6b174c0648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>Porady: instalowanie niestandardowego adaptera danych diagnostycznych

Jeśli utworzono adaptera danych diagnostycznych lub otrzymany z niestandardowego adaptera danych diagnostycznych do użycia, należy zainstalować z zestaw adaptera danych diagnostycznych przez skopiowanie pliku zestawu dla niego w poprawnym katalogu na komputerze lokalnym.

 Jeśli chcesz użyć Twojego adaptera danych diagnostycznych dla roli w środowisku, należy zainstalować na wszystkich komputerach z systemem agentów testowych, które mogą być używane dla tej roli Twojego adaptera danych diagnostycznych.

 Poniższa procedura należy zainstalować karta diagnostyki niestandardowej w odpowiednich lokalizacjach. Konieczne będzie uprawnienia administratora na dowolnym komputerze, na którym jest instalowany adaptera danych diagnostycznych.

## <a name="installing-a-custom-diagnostic-data-adapter"></a>Instalowanie niestandardowego adaptera danych diagnostycznych

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>Aby zainstalować adapter danych diagnostycznych

1.  Aby używać adapter danych diagnostycznych, po uruchomieniu testów na komputerze klienckim lub na maszynie agenta, skopiuj wszystkie pliki z katalogu kompilacji do następującego katalogu na komputerze docelowym, na podstawie ścieżki instalacji:

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     Aby skopiować pliki są:

    -   Adapter danych diagnostycznych zestawu (.dll) (wymagana).

    -   Dane pliku debugowania (.pdb) dla karty (opcjonalnie).

    -   Plik konfiguracji dla Twojego adaptera (`<diagnostic data adapter name>.dll.config`), jeśli masz domyślne ustawienia konfiguracji (opcjonalnie).

    -   Zestaw edytora konfiguracji, jeśli został utworzony Aby edytować ustawienia konfiguracji dla karty (opcjonalnie). Jest to tylko dla komputerów klienckich. Agent maszyny nie należy używać edytora.

    > [!NOTE]
    > Mimo że można tworzyć w tym samym projekcie i wbudowane w tym samym zestawie Twojego adaptera danych diagnostycznych i edytora konfiguracji, można używać oddzielnego projektów i utworzyć oddzielne zestawy dla ich, jeśli wolisz.

     Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testu do korzystania ze środowiska, po uruchomieniu testów, zobacz [zbierania danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

2.  Aby wybrać Twojego adaptera danych diagnostycznych dla testu, należy najpierw wybrać istniejące ustawienia testu lub Utwórz nową z Microsoft Test Manager lub programu Visual Studio a następnie wybierz Twojego adaptera danych diagnostycznych na **danych i informacji diagnostycznych** Karta ustawienia wybranego testu.

3.  Jeśli zostały utworzone i zainstalowane diagnostycznych edytora konfiguracji adaptera danych, aby skonfigurować Twojego adaptera danych diagnostycznych dla ustawień testu wybierz **Konfiguruj** obok swoją kartę i sprawdź wszystkie dokonane zmiany. Następnie wybierz pozycję **zapisać**. Aby uzyskać więcej informacji o sposobie tworzenia konfiguracji edytor dla Twojego zbierania danych diagnostycznych, zobacz [porady: tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych Your](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

4.  Jeśli korzystasz z testów z Microsoft Test Manager, można przypisać te ustawienia do planu testu testu, aby uruchomić testy lub użyj **Uruchom z opcjami** polecenie, aby przypisać ustawień testu i zastąpić ustawienia testu. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

     Jeśli korzystasz z testów w programie Visual Studio, należy ustawić te ustawienia jako aktywne testu. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

5.  Uruchom testy przy użyciu ustawień testów adaptera danych diagnostycznych wybrane.

## <a name="see-also"></a>Zobacz także

- [Porady: tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Porady: tworzenie edytora niestandardowego dla danych dla Twojego adaptera danych diagnostycznych](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Tworzenie adaptera danych diagnostycznych zbieranie danych niestandardowych lub mają wpływ na maszynę testową](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)