---
title: Określanie typów sieci wirtualnych w scenariuszu testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a3c4a4e6db97e99d2ec2df5b27c6fd8293a182f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978300"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Określanie typów sieci wirtualnych w scenariuszu testu obciążenia

*Sieci mieszane* umożliwia Symulacja obciążenia bardziej realistycznie w scenariuszu testu obciążenia. Obciążenia jest generowany przy użyciu heterogenicznych mieszane typy sieci zamiast jednego typu jednej sieci. Możesz utworzyć bliżej zbliżenia interakcje użytkowników końcowych z aplikacji.

 Mieszany profil sieciowy określa prawdopodobieństwo wirtualny użytkownik korzystający z danym *sieci profilu*. Profil sieci jest symulacji przepustowości sieci w warstwie aplikacji. Go nie zasymulować opóźnienie.

 Podczas tworzenia testu obciążenia można symulować który obciążenia jest generowany przez więcej niż jeden typ połączenia sieciowego. Mieszany profil sieciowy oferuje kilka typów sieci. Symulowani są różnych sieciach. Po wybraniu opcji przykład `Cable-DSL 1.5Mbps`, czasy oczekiwania są wstrzykiwane do testu do symulowania wybranego przepustowości.

 Mieszany profil sieciowy działa jak inne opcje mieszanego. Typ sieci jest zaznaczone losowo skojarzony z użytkownikiem wirtualnego oparte na mieszany profil sieciowy. Testy tego użytkownika są uruchamiane przy użyciu określonego typu sieci, oparte na prawdopodobieństwo określone w zestawie.

 Po określeniu mieszany profil sieciowy można dodawać i usuwać typy sieci. Można również zmienić dystrybucji mieszany profil sieciowy za pomocą kontroli mieszanego.

 Formant mieszanego pozwala łatwo Dopasuj dystrybucji sieci w scenariuszu.

 Aby uzyskać więcej informacji, zobacz [o różnych kontroli](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

## <a name="true-network-emulation"></a>Emulacji sieci

 Visual Studio będzie korzystać emulacji sieci opartych na oprogramowaniu dla wszystkich typów testu, w tym testów obciążenia. Emulacji sieci symuluje warunków sieciowych przez bezpośredniej pakietów sieciowych. Emulator sieci może emulować zachowanie przewodowej i bezprzewodowej sieci przy użyciu niezawodnych łącza fizycznego, takie jak Ethernet. Następujące atrybuty sieci są włączone do emulacji sieci:

-   Czasu Rundy sieci (opóźnienie)

-   Dostępna przepustowość

-   Zachowanie kolejkowania

-   Utraty pakietów

-   Ponowne porządkowanie pakietów

-   Błąd propagacji.

Emulacji sieci, również zapewniają elastyczność filtrowanie pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i protokołu ICMP.

Emulacji sieci umożliwia deweloperom aplikacji opartych na sieci i testerów emulować środowiska testowego żądaną, oceny wydajności, prognozowania wpływ zmiany lub podjąć decyzje dotyczące optymalizacji technologii. W porównaniu do łóżek testu sprzętu, emulacji sieci jest znacznie tańsze i bardziej elastyczne rozwiązania.

## <a name="to-add-new-networks-to-a-scenario"></a>Umożliwia dodawanie nowych sieci na potrzeby scenariusza

1.  W trakcie określania mieszany profil sieciowy dla scenariusza wybierz **Dodaj**.

     Nowy wpis sieci jest dodawana do siatki.

    > [!NOTE]
    > Aby wyświetlić **Edytuj mieszany profil sieciowy** okno dialogowe pola, kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz pozycję **Edytuj mieszany profil sieciowy**.

2.  W **typu sieci** kolumny, wybierz strzałkę nowego wpisu. Wybierz typ żądanej sieci.

3.  (Opcjonalnie) Dostosuj kontroli mieszanego do określenia dystrybucji testu. Aby uzyskać więcej informacji, zobacz [o różnych kontroli](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4.  Po zakończeniu dodawania sieci, wybierz **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Aby usunąć sieci z scenariusza

1.  Otwórz testu obciążenia.

2.  Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć sieć, a następnie wybierz pozycję **Edytuj mieszany profil sieciowy**. **Edytuj mieszany profil sieciowy** zostanie wyświetlone okno dialogowe.

3.  Wybierz sieć w siatce, a następnie wybierz pozycję **Usuń**.

4.  (Opcjonalnie) Dostosuj kontroli mieszanego do określenia dystrybucji testu. Aby uzyskać więcej informacji, zobacz [o różnych kontroli](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5.  Po zakończeniu usuwania sieci, wybierz **OK**.

## <a name="about-the-mix-control"></a>Informacje o formancie mieszany

 Formant mieszanego pozwala dostosować procent obciążenia, które jest rozdzielona testy, typy przeglądarek lub typów sieci w scenariuszu testu obciążenia. Aby dostosować wartości procentowe, przesuń suwaki. Dopasowywanie różnych typów sieci określa prawdopodobieństwo wirtualny użytkownik korzystający z profilu sieciowego określonych w scenariuszu testu obciążenia.

 W przypadku przenoszenia suwaka, zmień wartości procentowe wszystkie dostępne elementy. Jeśli masz więcej niż dwa elementy wielkość Dodaj lub usuń jest równomiernie między innymi elementami. Istnieje możliwość zastąpienia tego zachowania. Zaznacz pole wyboru w kolumnie blokady dla danego elementu, należy zablokować określoną wartość procentową wartość dla tego elementu. Następnie gdy suwak wielkość Dodaj lub usuń jest stosowana tylko do wszystkie pozostałe elementy odblokowane.

 **Dystrybucji** przycisk umożliwia przydzielenie wartości procentowe równomiernie wszystkie elementy. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.

 Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny zamiast przy użyciu suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, innych elementów nie zostanie automatycznie dostosowana.

> [!NOTE]
> Suwaki są wyłączone, gdy łączna nie dodaje do 100% lub po wprowadzeniu wartości procentowe w **%** kolumny są miejsc dziesiętnych.

Po wprowadzeniu wartości procentowe ręcznie, należy upewnić się, że suma wszystkich elementów jest 100%. Po zapisaniu mieszane, jeśli nie jest sumą 100%, pojawi się monit zaakceptować wartości procentowe są one lub aby powrócić i dopasować je. Jeśli wybierzesz je zaakceptować, ponieważ są one, zostaną obliczone proporcjonalnie do 100%.  Na przykład jeśli dwa elementy i ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawiona do 66,67% (80 podzielona przez 120) i drugiego elementu zostanie ustawiona do 33,33% (40 podzielona przez 120).