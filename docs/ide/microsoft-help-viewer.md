---
title: Visual Studio w dokumentacji pomocy w trybie offline
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb2c375aebd327d3d56b8f720b1b3619fab9b256
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117163"
---
# <a name="microsoft-help-viewer"></a>Podgląd Pomocy firmy Microsoft

Można zainstalować i wyświetlić zawartość różne produkty i technologie, na komputerze lokalnym przy użyciu Podglądu pomocy firmy Microsoft. Produkty te obejmują Visual Studio, .NET Framework, dokumentację języka, SQL Server i systemu Windows dla deweloperów. Podgląd Pomocy umożliwia:

- Pobierz zestawy zawartości, które także są nazywane książek. Może to być przydatne, jeśli potrzebujesz do pracy w "trybie offline" i nadal mieć dostęp do dokumentacji.

- Znajdowanie tematów przez tytuł przeglądania i wyszukując spisu treści.

- Wyszukiwanie tematów w indeksie.

- Informacje można znaleźć przy użyciu wyszukiwania pełnotekstowego.

- Widok, zakładki i drukowanie tematów.

Aby zainstalować podglądu pomocy, zobacz [instalacja podglądu pomocy firmy Microsoft](../ide/microsoft-help-viewer-installation.md). Aby rozpocząć odczyt tematów pomocy w Podglądzie pomocy, a nie w trybie online, przejdź do **pomocy** menu programu Visual Studio, a następnie wybierz **Ustaw preferencje pomocy** > **Uruchom w Podglądzie pomocy** .

> [!TIP]
> Innym sposobem na pobieranie zawartości lokalnie, aby mogły go wyświetlać, gdy nie ma połączenia internetowego jest pobrać wersję plików PDF z niego. Wiele zestawów dokumentacji w witrynie docs.microsoft.com zawiera łącza w dolnej części spisu treści (TOC), aby pobrać plik PDF, który zawiera wszystkie artykuły dla tego spisu treści.
>
> ![Pobierz plik PDF dokumentacji programu Visual Studio](media/download-pdf.png)

## <a name="help-viewer-tour"></a>Samouczek podglądu pomocy

Informacje można znaleźć w treści zainstalowanych przy użyciu karty nawigacji, Wyświetl zainstalowane zawartości w temacie karty lub kart i zarządzania zawartością za pomocą **Zarządzaj zawartością** kartę. Można również wykonanie dodatkowych zadań, za pomocą przycisków na pasku narzędzi i dodatkowe informacje można znaleźć w prawym dolnym rogu okna.

### <a name="navigation-tabs"></a>Karty nawigacji

|Tab|Opis|
|---|-----------|
|Spis treści|Wyświetla zainstalowane zawartości jako hierarchię (spis treści). Możesz określić kryteria filtrowania tytułów, które są wyświetlane.|
|Indeks|Wyświetla alfabetyczną listę indeksowanego warunki. Można w indeksie, określ kryteria filtrowania wpisy i wymagają tego indeksu wpisy zawierają lub rozpoczynać się od tekstu, który określisz.|
|Ulubione|Można "Ulubione" Tematy, wybierając **Dodaj do ulubionych** przycisk i tematy są wyświetlane na tej karcie. **Historii** sekcja Wyświetla listę tematów, które zostały ostatnio wyświetlane.|
|Wyszukaj|Zawiera pole tekstowe, w której można wyszukiwać warunków w dowolnym miejscu zawartości, w tym tytuły kodu i tematu.|

### <a name="view-topics"></a>Widok — tematy

Każdy temat znajduje się w osobnej karcie i możesz otworzyć wiele tematów w tym samym czasie.

### <a name="manage-content"></a>Zarządzanie zawartością

Można zainstalować, zaktualizować, przenieść i usunąć zawartość przy użyciu **Zarządzaj zawartością** kartę. U góry karty, można użyć **źródła instalacji** sterowania, aby określić, czy zainstalować książek z lokalizacji sieciowej lub z dysku lub identyfikatora URI. **Ścieżki w lokalnym magazynie** polu wskazują, gdzie książek są zainstalowane na komputerze lokalnym i przenieść do innej lokalizacji, wybierając **Przenieś** przycisku.

Na liście zawartości pokazano książki można zainstalować lub został już zainstalowany, czy jest dostępna aktualizacja, i każda książka rozmiar, jaki jest. Można zainstalować lub usunąć jedną lub większą liczbę pozycji, wybierając odpowiednie **Dodaj** lub **Usuń** łącza, a następnie wybierając **aktualizacji** przycisku w obszarze **oczekujące zmiany** okienka. Jeśli aktualizacje są dostępne dla dowolnego książek, które zostały już zainstalowane, można odświeżyć zawartości, wybierając **kliknij tutaj, aby pobrać teraz** łącze umieszczone u dołu okna. Ponadto wszystkich zainstalowanych książek są odświeżane, jeśli aktualizacje są dostępne po zainstalowaniu dodatkowych książek.

> [!NOTE]
> Funkcje **zarządzania zawartością** kartę mogą się różnić, jeśli te funkcje dezaktywuje administratora podglądu pomocy lub Brak dostępu do Internetu.

### <a name="toolbar-buttons"></a>Przyciski paska narzędzi

Pasek narzędzi w **podglądu pomocy** okna zawiera następujące przyciski:

- **Pokaż temat w spisie treści** przycisk wyświetlana jest lokalizacja tematu w **zawartość** kartę.

- **Dodaj do ulubionych** przycisk Dodaje temat active **ulubione** kartę.

- **Znaleźć w temacie** przycisk wyróżnia wyszukiwanie tekstu w aktywny temat.

- **Drukowania** przycisku drukuje lub Podgląd aktywny temat.

- **Opcje aplikacji Viewer** przycisk wyświetla ustawienia, takie jak rozmiar, jaki jest wyświetlany tekst, liczbę wyników wyszukiwania do zwrócenia, jak wiele tematów do wyświetlenia w historii i czy do sprawdzania aktualizacji w trybie online.

- **Zarządzania zawartością** sprawia, że przycisk **zarządzania zawartością** kartę aktywne.

- Mały trójkąt po prawej stronie otwiera listy kart, w tym temacie kart i **zarządzania zawartością** kartę. Można wybrać nazwę karty dokonanie aktywnej karty.

## <a name="see-also"></a>Zobacz także

- [Instalacja podglądu pomocy firmy Microsoft](../ide/microsoft-help-viewer-installation.md)
- [Przewodnik administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md)
- [Zainstaluj i Zarządzaj zawartości lokalnej](../ide/install-and-manage-local-content.md)
