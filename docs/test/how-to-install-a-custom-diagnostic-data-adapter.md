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
ms.openlocfilehash: 0755f77b2eea2860a3514480504c7aed041711d4
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379292"
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>Porady: Instalowanie niestandardowego adaptera danych diagnostycznych

Jeśli utworzono niestandardowego adaptera danych diagnostycznych lub dostarczono z niestandardowego adaptera danych diagnostycznych do użycia, można zainstalować zestaw adaptera danych diagnostycznych przez skopiowanie pliku zestawu dla niego do poprawnego katalogu na komputerze lokalnym.

 Jeśli chcesz użyć Twojego niestandardowego adaptera danych diagnostycznych dla roli w środowisku, należy zainstalować adapter danych diagnostycznych na wszystkich komputerach, na których działają agenci testowi, których można użyć dla tej roli.

 Użyj poniższej procedury do instalowania niestandardowej karty diagnostycznej w odpowiednich miejscach. Będą potrzebne uprawnienia administracyjne na dowolnym komputerze, na którym instalujesz adapter danych diagnostycznych.

## <a name="install-a-custom-diagnostic-data-adapter"></a>Instalowanie niestandardowego adaptera danych diagnostycznych

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>Aby zainstalować adapter danych diagnostycznych

1.  Aby użyć karty danych diagnostycznych, po uruchomieniu testów na komputerze klienckim lub na maszynie agenta, należy skopiować wszystkie pliki z katalogu kompilacji do następującego katalogu na komputerze docelowym, na podstawie ścieżki instalacji:

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     Pliki do skopiowania są:

    -   Zestaw adaptera danych diagnostycznych (*.dll*) (wymagane).

    -   Plik danych debugowania (*.pdb*) dla karty (opcjonalnie).

    -   Plik konfiguracji dla karty (`<diagnostic data adapter name>.dll.config`), jeżeli istnieją domyślne ustawienia konfiguracji (opcjonalnie).

    -   Zestaw edytora konfiguracji, jeśli utworzono go, aby edytować ustawienia konfiguracji dla karty (opcjonalnie). Te informacje dotyczą tylko komputerów klienckich. Maszyny agentowe nie korzystają z edytora.

    > [!NOTE]
    > Chociaż adapter danych diagnostycznych i Edytor konfiguracji można tworzyć w tym samym projekcie i wbudowane w tym samym zestawie, można użyć osobnych projektów i utworzyć dla nich, oddzielne zestawy, jeśli użytkownik sobie tego życzy.

     Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testów w celu używania środowiska podczas wykonywania testów, zobacz [zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

2.  Aby wybrać karty danych diagnostycznych dla testu, musisz najpierw wybrać istniejące ustawienia testu lub Utwórz nową z Microsoft Test Manager lub programu Visual Studio a następnie wybierz adaptera danych diagnostycznych na **dane i Diagnostyka** Karta wybrane ustawienia testu.

3.  Jeśli utworzono i zainstalowano edytora adaptera danych diagnostycznych konfiguracji, aby skonfigurować adapter danych diagnostycznych dla ustawień testu, wybierz opcję **Konfiguruj** obok swojego adaptera i wprowadź zmiany. Następnie wybierz **Zapisz**. Aby uzyskać więcej informacji o tym, jak utworzyć konfigurację edytor dla usługi modułu zbierającego dane diagnostyczne, zobacz [porady: tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

4.  Jeśli używasz testów z Microsoft Test Manager, można przypisać te ustawienia testów do planu testów przed uruchomieniem testów lub użyć **Uruchom z opcjami** polecenia w celu przypisywania ustawień testów i zastępowania ustawień testu. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

     Jeśli używasz testów z programu Visual Studio, musisz ustawić te ustawienia testów, aby być aktywne. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

5.  Uruchom testy przy użyciu ustawień testowych z wybraną kartą danych diagnostycznych.

## <a name="see-also"></a>Zobacz także

- [Porady: tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Porady: tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Przykładowy projekt dotyczący tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Tworzenie adaptera danych diagnostycznych do zbierania danych niestandardowych lub wpływać na komputer testowy](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)