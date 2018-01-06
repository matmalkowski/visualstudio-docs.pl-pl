---
title: "Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: "25"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: f5cb41ab9a68e567d7c6b64243c6cec017835088
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności
Ten temat dotyczy niektóre problemy, które mogą wystąpić podczas tworzenia rozszerzenia modelu warstwy.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Po naciśnięciu klawisza klawisz F5, aby debugować Moje rozszerzenia, poleceń, procedury obsługi gestów, sprawdzania poprawności rozszerzenia lub właściwości niestandardowe nie są wyświetlane na wykresach zależności w eksperymentalne wystąpienie programu[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Otwórz rozwiązanie rozszerzenia w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]i na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.  
  
2.  Naciśnij klawisz **F5** lub **CTRL + F5** do Uruchom eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Otwórz diagram zależności i przetestować rozszerzenia.  
  
 Przejdź do następnej procedury w razie potrzeby.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Działa starsza wersja programu Moje rozszerzenie.  
  
1.  Upewnij się, że żadne wystąpienie eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest uruchomiona.  
  
2.  Usuń następujący folder: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [wersja]  
  
    > [!NOTE]
    >  % LocalAppData % jest zwykle *DriveName*: \Users\\*UserName*\AppData\Local.  
  
 Przejdź do następnej procedury w razie potrzeby.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Stara wersja wyniki sprawdzania poprawności pojawia się lub Moje metoda sprawdzania poprawności nie jest wywoływana.  
  
1.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**. Powoduje wyczyszczenie pamięci podręcznej wyniki poprzedniego analizy sprawdzania poprawności.  
  
2.  Upewnij się, że warstwy modelu są skojarzone z elementy kodu i że istnieje co najmniej jedno łącze zależności w modelu. Sprawdzanie poprawności nie jest wywoływana, jeśli nie ma nic do zweryfikowania.  
  
3.  Regularne punktów przerwania może nie działać w metodę sprawdzania poprawności, ponieważ jest uruchamiana w oddzielnych procesach. Wstaw wywołanie `System.Diagnostics.Debugger.Launch()` Aby krokowo metodę.  
  
4.  W **source.extension.vsixmanifest** w projekcie weryfikacji warstwy, upewnij się, że dodano zarówno **składników MEF** elementu i **niestandardowe rozszerzenia typu** elementu w obszarze **Zawartości**.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)
