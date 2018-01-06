---
title: "W usłudze języka starsza wersja programu Word ukończenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a4ab4bd29c753fc03787fbbadbe106d2d8862b10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>Zakończenie programu Word w starsza wersja usługi języka
Uzupełnianie Word wypełnia brakujących znaków na częściowo typu wyrazu. Jeśli istnieje tylko jeden ukończenia możliwe, wyraz zostało zakończone, po wprowadzeniu znak zakończenia. Jeśli częściowe word odpowiada więcej niż jedną z możliwości, jest wyświetlona lista możliwe uzupełnienia. Znak zakończenia może być dowolny znak, który nie jest używany dla identyfikatorów.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="implementation-steps"></a>Kroki implementacji  
  
1.  Gdy użytkownik wybierze **całe słowo** z **IntelliSense** menu <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenia są wysyłane do usługi języka.  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasy połowy polecenia i wywołania <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> Klasy następnie wywołania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę, aby uzyskać listę zakończeń możliwości programu word, a następnie wyświetla listę słów w etykietce narzędzia przy użyciu <xref:Microsoft.VisualStudio.Package.CompletionSet> klasy.  
  
     Jeśli istnieje tylko jedno słowo dopasowania, <xref:Microsoft.VisualStudio.Package.Source> klasy zakończeniu słowo.  
  
 Alternatywnie Jeśli skaner zwraca wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> po wpisaniu pierwszy znak identyfikatora <xref:Microsoft.VisualStudio.Package.Source> klasy wykryje to i wywołuje <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. W takim przypadku analizator musi wykrywania obecności znaku wyboru elementu członkowskiego i zawierają listę elementów członkowskich.  
  
## <a name="enabling-support-for-the-complete-word"></a>Włączanie obsługi całe słowo  
 Aby włączyć obsługę programu word zakończenia zestawu `CodeSense` nazwany parametr przekazany do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybut użytkownika skojarzonego z pakietem języka. To ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
 Twoje analizator musi zwracać listę deklaracje w odpowiedzi na wartość przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason>, na zakończenie programu word do działania.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementowanie całe słowo w metodzie ParseSource  
 Na zakończenie word <xref:Microsoft.VisualStudio.Package.Source> klasy wywołania <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metody w <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy do uzyskiwania listy dopasowań możliwości programu word. Lista musi implementować w klasie pochodzącej z <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Zobacz <xref:Microsoft.VisualStudio.Package.Declarations> klasy, aby uzyskać więcej informacji na temat metod musi implementować.  
  
 Jeśli lista zawiera tylko pojedynczego wyrazu, a następnie <xref:Microsoft.VisualStudio.Package.Source> klasy automatycznie wstawia wyrazie zamiast częściowe programu word. Jeśli lista zawiera więcej niż jedno słowo <xref:Microsoft.VisualStudio.Package.Source> klasa przedstawia listę Porada narzędzia, z którego użytkownik może wybrać właściwy wybór.  
  
 Wyglądać na przykładzie <xref:Microsoft.VisualStudio.Package.Declarations> Implementacja klasy [zakończenia elementu członkowskiego w starsza wersja usługi języka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).