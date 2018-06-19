---
title: Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b56ccd587df4a830eab5bee000cafcc02b0031e8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949374"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności

Ten temat dotyczy niektóre problemy, które mogą wystąpić podczas tworzenia rozszerzenia modelu warstwy.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Po naciśnięciu klawisza klawisz F5, aby debugować Moje rozszerzenia, poleceń, procedury obsługi gestów, sprawdzania poprawności rozszerzenia lub właściwości niestandardowe nie są wyświetlane na wykresach zależności w eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

1.  Otwórz rozwiązanie rozszerzenia w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]i na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.

2.  Naciśnij klawisz **F5** lub **CTRL + F5** do Uruchom eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Otwórz diagram zależności i przetestować rozszerzenia.

 Przejdź do następnej procedury w razie potrzeby.

## <a name="an-old-version-of-my-extension-runs"></a>Działa starsza wersja programu Moje rozszerzenie.

1.  Upewnij się, że żadne wystąpienie eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest uruchomiona.

2.  Usuń następujący folder: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [wersja]

    > [!NOTE]
    > % LocalAppData % jest zwykle *DriveName*: \Users\\*UserName*\AppData\Local.

 Przejdź do następnej procedury w razie potrzeby.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Stara wersja wyniki sprawdzania poprawności pojawia się lub Moje metoda sprawdzania poprawności nie jest wywoływana.

1.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**. Powoduje wyczyszczenie pamięci podręcznej wyniki poprzedniego analizy sprawdzania poprawności.

2.  Upewnij się, że warstwy modelu są skojarzone z elementy kodu i że istnieje co najmniej jedno łącze zależności w modelu. Sprawdzanie poprawności nie jest wywoływana, jeśli nie ma nic do zweryfikowania.

3.  Regularne punktów przerwania może nie działać w metodę sprawdzania poprawności, ponieważ jest uruchamiana w oddzielnych procesach. Wstaw wywołanie `System.Diagnostics.Debugger.Launch()` Aby krokowo metodę.

4.  W **source.extension.vsixmanifest** w projekcie weryfikacji warstwy, upewnij się, że dodano zarówno **składników MEF** elementu i **niestandardowe rozszerzenia typu** elementu w obszarze **Zawartości**.

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)
