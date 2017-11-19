---
title: "Szybkie informacje w usłudze języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 692884d31e55921489aad0fbbea32ca1c094c6c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="quick-info-in-a-legacy-language-service"></a>Szybkie informacje w starsza wersja usługi języka
Szybkie informacje funkcji IntelliSense zawiera informacje o identyfikator źródła, gdy użytkownik umieszcza w identyfikatorze karetki i wybiera **szybka podpowiedź** z **IntelliSense** menu lub posiada myszy kursor nad identyfikatorem. Powoduje to etykietka narzędzia, która się z informacjami o tym identyfikatorze. Te informacje zazwyczaj składa się z typ identyfikatora. Gdy aparat debugowania jest aktywne, te informacje mogą obejmować bieżącą wartość. Aparat debugowania udostępnia wartości wyrażenia, podczas gdy usługa języka obsługuje tylko identyfikatory.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [wskazówki: wyświetlanie podpowiedzi QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
 Klasy usługi języka framework (MPF) zarządzanego pakietu zapewniają pełną obsługę wyświetlania etykietka narzędzia Szybkie informacje funkcji IntelliSense. To wszystko, co należy zrobić, podaj tekst, który można wyświetlić i włączyć funkcję Szybkie informacje.  
  
 Tekst, który ma być wyświetlane są uzyskiwane przez wywołanie metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora składni metody o wartości Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Z tego powodu informuje analizatora składni, aby uzyskać informacje o typie (lub niezależnie od jest odpowiednia, który będzie wyświetlany w etykietce narzędzia Szybkie informacje) dla identyfikatora w lokalizacji określonej w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu. <xref:Microsoft.VisualStudio.Package.ParseRequest> Obiekt jest co został przekazany do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody.  
  
 Analizator należy przeanalizować wszystko do pozycji w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt, aby określić typy wszystkie identyfikatory. Następnie analizator musi pobrać identyfikator w lokalizacji żądanie analizy. Na koniec analizator należy przekazać dane Porada narzędzia skojarzone z danym identyfikatorem do <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektów, ten obiekt może zwrócić tekst ze <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.  
  
## <a name="enabling-the-quick-info-feature"></a>Włączenie funkcji Szybkie informacje  
 Aby włączyć funkcję Szybkie informacje, należy ustawić `CodeSense` i `QuickInfo` nazwane parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Ustaw następujące atrybuty <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> i <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> właściwości.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementowanie funkcji Szybkie informacje  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasa obsługuje operację szybkie informacje funkcji IntelliSense. Podczas <xref:Microsoft.VisualStudio.Package.ViewFilter> odbiera klasy <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenia, wywołania klasy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody parse przyczynę <xref:Microsoft.VisualStudio.Package.ParseReason> i lokalizacji karetki w czasie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Wysłano polecenie. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analizatora składni metody musi następnie przeanalizować źródła do danej lokalizacji, a następnie analizować identyfikator w podanej lokalizacji w celu określenia, jakie można wyświetlić w etykietce narzędzia Szybkie informacje.  
  
 Większość analizatory składni nie początkowej analizy całego pliku źródłowego i zapisane wyniki w drzewie analizy. Pełną analizę odbywa się podczas <xref:Microsoft.VisualStudio.Package.ParseReason> jest przekazywana do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Inne rodzaje analizowania następnie można użyć w drzewie analizy uzyskać odpowiednie informacje.  
  
 Na przykład analizy przyczyny wartość <xref:Microsoft.VisualStudio.Package.ParseReason> można znaleźć identyfikatora w lokalizacji źródłowej i wyszukiwanie w drzewie analizy w celu uzyskania informacji o typie. Informacje o tym typie są następnie przekazywane do <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy, a zwracany przez <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.