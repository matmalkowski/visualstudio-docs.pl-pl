---
title: Dodawanie parametrów kontekstu do ustawień testu obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: dd19f945dec052ad2c90784252c0c85eba6889ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Porady: dodawanie parametrów kontekstu do ustawień testu obciążenia

Po utworzeniu testu obciążenia za pomocą **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

Można utworzyć parametrów kontekstu do użycia w teście obciążenia, w ustawieniach testu za pomocą edytora testu obciążenia. Parametry kontekstu umożliwiają parametryzacja ciąg.

Załóżmy, że test obciążenia zawiera testu wydajności sieci Web, które już używa sparametryzowane adres URL serwera sieci Web za pomocą parametru kontekstu. Można dodać parametr kontekstowy do ustawienia, które korzysta z tej samej wartości Nazwa, która jest używana podczas testów wydajności sieci Web uruchomienia testu obciążenia. Będzie to mapować testu wydajności sieci Web na innym serwerze, po uruchomieniu testu obciążenia. Na przykład jeśli test obciążenia zawiera testu wydajności sieci Web, która używa parametru kontekstu o nazwie Serwer_sieci_web_1 dla nazwy serwera sieci Web w adresie URL. Jeśli następnie określisz parametru kontekstu testu obciążenia ustawienie o nazwie Serwer_sieci_web_1, test obciążenia zostanie użyty parametr kontekstowy przypisana w teście obciążenia, w ustawieniach testu. Wyjaśnienie, jeśli testu wydajności sieci Web w teście obciążenia używa tej samej nazwy parametru kontekstu jako parametru kontekstu w teście obciążenia, parametru kontekstowego w teście obciążenia spowoduje zastąpienie parametru kontekstowego, który jest używany podczas testu wydajności sieci Web.

> [!WARNING]
> Nie można więc przypadkowo zastąpienie parametru kontekstowego testu wydajności sieci Web, korzystając z parametrów kontekstu w ustawieniach testu. Unikaj używania takie same nazwy parametrów kontekstu, chyba że w tym celowo.

Jeśli można przypisać wartość parametru kontekstowego serwer_sieci_Web_1 do `http://CorporateStagingWebServer`, można użyć `WebServer1` w całym obciążenia testowania i tym samym łatwo Zmień wartość na inny serwer sieci Web w dowolnej chwili.

Ponadto przypisując różne wartości do parametru kontekstu przy użyciu tej samej nazwie w ustawieniach testu różnym obciążeniem, można uruchomić testu obciążenia za pomocą różnych środowiskach:

-   Ustawienia uruchamiania firmowy serwer sieci Web przemieszczania: parametr kontekstowy o nazwie Serwer_sieci_web_1 =http://CorporateStagingWebServer

-   Ustawienia uruchamiania firmowy serwer sieci Web produkcji: parametr kontekstu, o nazwie Serwer_sieci_web_1 =http://CorporateProductionWebServer

 **Zmiana ustawień z poziomu wiersza polecenia**

 Jeśli chcesz używać różnych ustawień wykonywania w wierszu polecenia przeprowadzać strategii parametru kontekstu, użyj następujących poleceń:

 **Set Test.UseRunSetting= CorporateStagingWebServer**

 - i -

 **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Aby dodać parametr kontekstu do ustawień

1.  Otwórz testu obciążenia.

2.  Rozwiń węzeł **parametrów uruchomieniowych** folderu w drzewie testu obciążenia w edytorze testu obciążenia.

3.  Kliknij prawym przyciskiem myszy konkretnych ustawień, do której chcesz dodać parametr kontekstu, a następnie wybierz pozycję **Dodaj parametr kontekstowy**.

     Nowy parametr kontekstu jest dodawany do **parametrów kontekstu** folderu w **parametrów uruchomieniowych** folderu w drzewie testu obciążenia.

     —lub—

     Jeśli uruchomienie ustawienie już zawiera **parametrów kontekstu** folderu, możesz kliknij go prawym przyciskiem myszy i wybierz **Dodaj parametr kontekstowy**.

4.  W oknie Właściwości zmień wartość atrybutu **nazwa** odpowiednio (na przykład Serwer_sieci_web_1). W oknie Właściwości zmień **wartość** do parametru, który chcesz użyć (na przykład http://CorporateStagingWebServer).

5.  (Opcjonalnie) Powtórz kroki od 3 do 5 i użyj innego ciągu dla **wartość** właściwości (na przykład http://CorporateProductionWebServer).

6.  Wybierz opcję uruchamiania ustawień, które mają być aktywne. Otwórz menu skrótów w ustawieniach uruchamiania i wybierz polecenie **Ustaw jako aktywny**.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)