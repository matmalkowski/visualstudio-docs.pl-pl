---
title: 'Porady: wykluczanie projektów z kompilacji'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e203fd9f1515e212591afe11c246cdeb78201b8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-exclude-projects-from-a-build"></a>Porady: wykluczanie projektów z kompilacji

Można tworzyć rozwiązania bez tworzenia wszystkie projekty, które zawiera. Może na przykład wykluczyć projektu, który dzieli kompilacji. Można następnie zbudować projekt po możesz zbadać i adres problemy.

Projekt można wykluczyć, wykonując następujących metod:

-   Usunięcie go tymczasowo z aktywnej konfiguracji rozwiązania.

-   Tworzenie konfiguracji rozwiązania, która nie zawiera projektu.

Aby uzyskać więcej informacji, zobacz [konfiguracje kompilacji omówienie](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunąć projekt z aktywnej konfiguracji rozwiązania

1.  Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.

2.  W **projektu kontekstów** tabeli, Znajdź projektu, które chcesz wykluczyć z kompilacji.

3.  W **kompilacji** kolumny dla projektu, usuń zaznaczenie pola wyboru.

4.  Wybierz **Zamknij** przycisk, a następnie ponownie skompiluj rozwiązanie.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Aby utworzyć konfigurację rozwiązania, która nie obejmuje projektu

1.  Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.

2.  W **aktywnej konfiguracji rozwiązania** wybierz  **\<nowy >**.

3.  W **nazwa** wprowadź nazwę dla konfiguracji rozwiązania.

4.  W **Kopiuj ustawienia** wybierz konfigurację rozwiązania, na którym chcesz utworzyć nową konfigurację (na przykład **debugowania**), a następnie wybierz pozycję **OK** przycisku .

5.  W **programu Configuration Manager** okno dialogowe, wyczyść pole wyboru w **kompilacji** kolumny dla projektu, który chcesz wykluczyć, a następnie wybierz pozycję **Zamknij** przycisku.

6.  Na **standardowe** narzędzi, sprawdź, czy nowa konfiguracja rozwiązania jest aktywna konfiguracja w **konfiguracje rozwiązania** pole.

7.  Na pasku menu wybierz **kompilacji** > **Kompiluj ponownie rozwiązanie**.

## <a name="see-also"></a>Zobacz także

- [Zrozumienie konfiguracje kompilacji](../ide/understanding-build-configurations.md)
- [Porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Porady: równoczesne kompilowanie wielu konfiguracji](../ide/how-to-build-multiple-configurations-simultaneously.md)