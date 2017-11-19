---
title: "Ułatwienia dostępu | Dokumentacja firmy Microsoft"
description: 
author: asb3993
ms.author: amburns
ms.date: 08/15/2017
ms.topic: article
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 13c69a1c13507a0f856bc652f7ffa0e5ab233081
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="accessibility"></a>Ułatwienia dostępu

Oprócz funkcji i narzędzi macOS programu Visual Studio for Mac zawiera następujące funkcje, dzięki czemu bardziej dostępny dla osób niepełnosprawnych:

- Rozszerzenia tekstu w rozwiązaniu i tablety edytora
- Opcje rozmiaru tekstu w edytorach
- Dostosowywanie kolorów w edytorach
- Dostosowywanie skrótów klawiaturowych
- Uzupełnianie kodu dla metody i parametry 

Aby uzyskać więcej informacji dotyczących funkcji ułatwień dostępu w macOS, zobacz [witryny sieci Web firmy Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Korzystanie z funkcji ułatwień dostępu w programie Visual Studio dla komputerów Mac

Funkcje ułatwień dostępu w programie Visual Studio for Mac są domyślnie wyłączone. Aby je włączyć, wykonaj następujące czynności:

1. Przejdź do **programu Visual Studio > Preferencje > Inne > ułatwień dostępu**.

2. Wybierz **włączyć ułatwień dostępu** pole wyboru, jak pokazano na poniższym diagramie:

    ![Włącz wyboru ułatwień dostępu](media/accessibility-image1.png)

3. Naciśnij klawisz **Uruchom ponownie program Visual Studio** przycisk, aby umożliwić funkcji ułatwień dostępu zaczęły obowiązywać.


Alternatywnie można użyć wiersza polecenia, aby włączyć funkcje ułatwień dostępu. Aby to zrobić, wprowadź następujące polecenie w terminalu: 

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1 
```

Po włączeniu ułatwień dostępu, należy uruchomić ponownie program Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Porady: użyj nawigacji klawiatury

Nawigacji klawiatury może być włączona opcja pełny dostęp klawiatury **preferencjach systemowych > klawiatury > Skróty** do **wszystkie formanty**:

  ![Systemy panelu Preferencje macos](media/accessibility-image2.png)

Ustawienia dostępu do klawiatury pełne włącza prostokąt fokusu. Następnie możesz wybrać formantów za pomocą:
- TAB, aby przejść do przodu, za pomocą formantów
- Shift-Tab, aby przejść wstecz za pomocą formantów
- Klawisze strzałek można przenieść między formantami w kierunku strzałki. 

Naciskając klawisz spacji aktywuje ukierunkowanych formantu.

## <a name="how-to-enable-and-use-voice-over"></a>Porady: Włączanie i używanie głosu za pośrednictwem

Włącz VoiceOver lub wyłącz naciśnij **Cmd + F5**

Aby poruszać się za pomocą interfejsu użytkownika, VoiceOver poleceń, użyj następujących poleceń:

- Przesuń kursor VoiceOver między formantami: **Ctrl + Alt + lewej Strzałka / Strzałka w prawo**

Odczytuje voiceOver limit nazwy formantów, niektóre szczegóły i co można zrobić z nim. 

- Wprowadź grup i (takie jak konsola rozwiązania, przybornika i pozostałe): **Ctrl + Alt + Shift + Strzałka w dół**

Gdy w formancie, można użyć **Ctrl + Alt + strzałki** Aby poruszać się po niej. 
 
Ogólne informacje na temat używania VoiceOver w macOS można znaleźć w następujących przewodnikach:

- [Wprowadzenie do korzystania z VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [System macOS voiceOver poleceń](http://lab.dotjay.com/notes/voiceover-commands/)
