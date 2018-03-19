---
title: "Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9f31916a15bb65a4278382e5d661fdc398138451
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych

Niestandardowa wtyczka używa kodu, który napiszesz i dołączysz to testu obciążeniowego lub testu wydajności sieci Web. Interfejsu API testu obciążeniowego lub testu wydajności sieci Web można użyć do utworzenia niestandardowej wtyczki dla testów, aby rozszerzyć wbudowaną funkcjonalność. Można dodać wielu wtyczek do testów obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Tworzenie niestandardowego wtyczki podczas testu obciążenia**: interfejs API testu obciążenia umożliwia utworzenie niestandardowego wtyczki, aby dodać funkcje bardziej testowych do testów obciążenia.|-   [Porady: Korzystanie z API testu obciążenia](../test/how-to-use-the-load-test-api.md)<br />-   [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)|
|**Tworzenie niestandardowego wtyczki dla testu wydajności sieci Web:** interfejsu API testu wydajności sieci Web umożliwia utworzenie niestandardowego wtyczki, aby dodać więcej funkcji testowych do Twojej testu wydajności sieci Web, w tym na poziomie żądania. Można również utworzyć test usługi sieci Web.<br /><br /> Dodatkowo można utworzyć wtyczkę rejestratora sieci Web, która może modyfikować test wydajności sieci Web, po jego rejestracji, ale przed pojawieniem się w Podglądzie wyników testu wydajności sieci Web|-   [Porady: Korzystanie z API testu wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Porady: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Porady: Tworzenie nowego testu usług sieci Web](../test/how-to-create-a-web-service-test.md)<br />-   [Porady: tworzenie wtyczki rejestratora](../test/how-to-create-a-recorder-plug-in.md)|
|**Dodawanie funkcji interfejsu użytkownika do przeglądarka wyników testu wydajności sieci Web:** więcej funkcji interfejsu użytkownika można dodać do przeglądarka wyników testu wydajności sieci Web przy użyciu dodatku programu Visual Studio.|-   [Porady: Tworzenie dodatku Visual Studio dla przeglądarki wyników testu wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Tworzenie edytora niestandardowego ciała dokumentu HTTP:** można utworzyć niestandardowego edytora do edycji pliku binarnego lub ciąg XML odpowiedzi http usługi sieci web.|-   [Porady: Tworzenie niestandardowego edytora HTTP dla edytora testów wydajności sieci Web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Tematy pomocy

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md)