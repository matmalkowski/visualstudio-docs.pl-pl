---
title: Implementowanie kolorowanie składni | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131858"
---
# <a name="implementing-syntax-coloring"></a>Implementowanie kolorowanie składni
Kiedy usługa języka udostępnia kolorowanie składni, analizator konwertuje wiersza tekstu na tablicę elementów colorable i zwraca odpowiadający te elementy colorable typy tokenów. Analizator powinien zwrócić token typy, które należą do listy elementów colorable. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Wyświetla każdy element colorable w oknie Kod zgodnie z atrybutów przypisane przez obiekt colorizer do odpowiedniego typu tokenu.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie określono interfejsu analizatora, oraz implementacji analizator całkowicie od użytkownika. Jednak domyślna implementacja analizatora składni znajduje się w projekcie pakiet językowy programu Visual Studio. Dla zarządzanego kodu zarządzanego pakietu framework (MPF) zapewnia obsługę pełną Kolorowanie tekstu.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej na temat nowych sposób implementowania kolorowania składni, zobacz [wskazówki: wyróżnianie tekstu](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroki następuje edytora w celu Kolorowanie tekstu  
  
1.  Edytor pobiera colorizer przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiektu.  
  
2.  Wywołania edytor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodę, aby określić, czy colorizer potrzebuje stan każdego wiersza, aby zachować poza colorizer.  
  
3.  Jeśli colorizer wymaga stanu, aby zachować poza colorizer, Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodę, aby pobrać stan pierwszego wiersza.  
  
4.  Dla każdego wiersza w buforze wywołuje edytor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, która wykonuje następujące czynności:  
  
    1.  Wiersz tekstu jest przekazywany do skanera, aby dokonać konwersji tekstu na tokeny. Każdy token Określa tekst tokenu i typ tokenu.  
  
    2.  Typ tokenu jest konwertowany na indeks do listy elementów colorable.  
  
    3.  Dane tokenu jest używany do wypełniania w tablicy, tak, aby każdy element tablicy odpowiada znaku w wierszu. Wartości przechowywane w tablicy są indeksów do listy elementów colorable.  
  
    4.  Stan na końcu wiersza jest zwracany dla każdego wiersza.  
  
5.  Jeśli colorizer wymaga, aby zachować stan, Edytor buforuje stan dla tej linii.  
  
6.  Edytor renderuje wiersza tekstu przy użyciu informacje zwrócone z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody. To wymaga wykonania następujących czynności:  
  
    1.  Dla każdego znaku w wierszu uzyskać wartość indeksu elementu colorable.  
  
    2.  Jeśli przy użyciu elementów colorable domyślne, dostęp do listy elementów colorable edytora.  
  
    3.  W przeciwnym razie wywołania usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody można uzyskać elementu colorable.  
  
    4.  Skorzystaj z informacji w elemencie colorable do renderowania tekstu do wyświetlenia.  
  
## <a name="managed-package-framework-colorizer"></a>Colorizer Framework zarządzanego pakietu  
 Framework zarządzanego pakietu (MPF) zawiera wszystkie klasy, które są wymagane do zaimplementowania colorizer. Klasy usługi języka powinny dziedziczyć <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i wdrożenie wymaganych metod. Należy podać skanera i analizatora zaimplementowanie <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu i zwrócić wystąpienia interfejsu z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> — metoda (jednej z metod, które muszą zostać zaimplementowane w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy). Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: używanie wbudowanych elementów Colorable](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Niestandardowe elementy Colorable](../../extensibility/internals/custom-colorable-items.md)   
 [Tworzenie usługi języka starsza wersja](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)