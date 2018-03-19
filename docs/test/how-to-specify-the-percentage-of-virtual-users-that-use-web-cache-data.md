---
title: "Określ wartość procentową z wirtualnych użytkowników sprawdzający dane pamięci podręcznej sieci Web użycia dla obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: c1aa64c0ecee9f214d1bd892c62ba79090d2ce15
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Porady: określanie wartości procentowej użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można zmienić właściwości scenariuszy, aby spełnić potrzeby i celów testowania przy użyciu **edytorze testu obciążenia**. Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

**Procent nowych użytkowników** właściwość jest ustawiona w oknie właściwości. Edytowanie właściwości scenariusza testów obciążenia w edytorze testu obciążenia.

**Procent nowych użytkowników** właściwość ma wpływ na sposób, w którym testu obciążenia symuluje buforowanie zostałoby przeprowadzone przez przeglądarkę sieci Web. Domyślnie **procent nowych użytkowników** właściwość jest ustawiona na 0%. Jeśli wartość **procent nowych użytkowników** właściwość jest ustawiona na 100%, każdego testu wydajności sieci Web uruchomione w teście obciążenia jest traktowany jak pierwszego użytkownika w czasie do witryny sieci Web, który nie ma żadnej zawartości z witryny sieci Web w swojej pamięci podręcznej przeglądarki z previ odwiedza jednostek organizacyjnych. W związku z tym wszystkie żądania w teście sieci Web, w tym wszystkich zależnych żądań, takich jak obrazy, zostaną pobrane.

> [!NOTE]
> Po zażądaniu tego samego zasobu buforowalnej w więcej niż raz w teście sieci web żądania nie zostaną pobrane.

Jeśli jesteś witryny sieci Web, która ma znaczących zwracany użytkowników, którzy mogą mieć obrazów do testowania obciążenia i innych buforowalnej zawartości buforowane lokalnie, następnie ustawienie 100% **procent nowych użytkowników** wygeneruje więcej właściwości żądań pobierania nie może mieć miejsce w rzeczywistych użycia. W takim przypadku należy oszacować procentową wizyt do witryny sieci Web, które pochodzą z pierwszym uruchomieniu witryny sieci web i ustaw **procent nowych użytkowników** właściwości odpowiednio.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Aby określić agentów na potrzeby scenariusza

1.  Otwórz testu obciążenia.

     **Edytora testu obciążenia** pojawi się. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia test drzew **scenariusze** folderu, wybierz węzła scenariusza, aby określić agentów na potrzeby.

3.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w oknie właściwości.

4.  Ustaw wartość **procent nowych użytkowników** właściwości, wprowadzając numer procent nowych użytkowników.

5.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowego **procent nowych użytkowników** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Wskazówki: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelowania aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)