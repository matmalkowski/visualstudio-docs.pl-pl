---
title: 'Lista kontrolna: Tworzenie usługi języka starszych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad407d85213bf640b8631e9fbcb12b681ac87406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="checklist-creating-a-legacy-language-service"></a>Lista kontrolna: Tworzenie starsza wersja usługi języka
Poniższa lista kontrolna zawiera podsumowanie podstawowe kroki, które należy wykonać, aby utworzyć usługę języka [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] core edytora. Integracja usługi języka do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], należy utworzyć ewaluatora wyrażeń debugowania. Aby uzyskać więcej informacji, zobacz [zapisywania ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) w [programu Visual Studio Extensibility debugera](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Procedura tworzenia usługi języka  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfejsu.  
  
    -   W pakiecie VSPackage, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs do obsługi language.  
  
    -   Udostępnia zintegrowane środowisko programistyczne (IDE) w usłudze języka programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji.  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu w klasie usługi główny język.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Interfejsu jest punktem początkowym interakcji między Edytor rdzeni i usługi języka.  
  
### <a name="optional-features"></a>Funkcje opcjonalne  
 Następujące funkcje są opcjonalne i można zaimplementować w dowolnej kolejności. Te funkcje zwiększenia funkcjonalności usługi języka.  
  
-   Kolorowanie składni  
  
     Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu. Implementacji tego interfejsu powinny informacji analizatora do zwracania informacji odpowiednie kolorów.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Metoda zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu. Wystąpienie oddzielnych colorizer jest tworzone dla każdej buforu tekstu należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu oddzielnie. Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   W oknie kodu  
  
     Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejsu, aby włączyć usługę języka otrzymać powiadomienie o podczas tworzenia nowego okna kodu.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Metoda zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejsu. Usługa języka można następnie dodać specjalne interfejsu użytkownika do okna Kod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Usługa języka można też wykonać wszelkie specjalnego przetwarzania, takie jak dodanie filtru widoku tekstu w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Filtr widoku tekstu  
  
     Zapewnienie instrukcji IntelliSense w usłudze języka przechwycić niektórych poleceń, które w przeciwnym razie będzie obsługiwać widoku tekstu. Aby przechwycić tych poleceń, wykonaj następujące kroki:  
  
    -   Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> brać udziału w poleceń edytora łańcucha i dojście polecenia.  
  
    -   Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> — metoda i przekazać w Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji.  
  
    -   Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metody po odłączeniu z widoku tak, że te polecenia są już przekazywane.  
  
     Polecenia, które muszą być obsługiwane są zależne od usług, które są udostępniane. Aby uzyskać więcej informacji, zobacz [ważne poleceń dla filtrów usługi języka](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Interfejs musi zostać wdrożone na tym samym obiekcie jako <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu.  
  
-   Uzupełnianie składni  
  
     Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu.  
  
     Obsługuje polecenie uzupełniania instrukcji (oznacza to, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) i Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu przekazywanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu. Aby uzyskać więcej informacji, zobacz [uzupełniania w starsza wersja usługi języka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Porady — metoda  
  
     Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu dostarczający dane dla okna Porada — metoda.  
  
     Filtr widoku tekstu do obsługi poleceń, należy zainstalować, aby wiedzieć, kiedy mają zostać wyświetlone okno Porada danych metody. Aby uzyskać więcej informacji, zobacz [informacje o parametrach w starsza wersja usługi języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Znaczniki błędów  
  
     Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu.  
  
     Błąd podczas tworzenia obiektów znacznika, które implementują <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu i wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> jest metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs obiektu znacznika błędu.  
  
     Zazwyczaj każdy znacznik błąd zarządza elementu w oknie Lista zadań.  
  
-   Elementy listy zadań  
  
     Wdrożenia, zapewniając klasy elementu zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfejsu.  
  
     Wdrożenia, zapewniając klasa dostawcy zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfejsu.  
  
     Wdrożenia, zapewniając klasy modułu wyliczającego zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfejsu.  
  
     Zarejestruj dostawcę zadań z listy zadań <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> metody.  
  
     Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejsu, wywołując usługi języka dostawcy usług w usłudze GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Tworzenie obiektów element zadania i wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metody w <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfejs, gdy istnieją nowe lub zaktualizowane zadania.  
  
-   Komentarz elementów zadań  
  
     Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejsu można uzyskać zadań tokeny komentarza.  
  
     Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfejsu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> usługi.  
  
     Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfejsu z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.  
  
     Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfejs do nasłuchiwania zmian na liście tokenu.  
  
-   Tworzenie konspektu  
  
     Dostępnych jest kilka opcji obsługi obramowanie. Na przykład można obsługiwać **Zwiń definicji** poleceń, podaj konspektu kontrolowane przez Edytor regionów lub obsługuje regionów kontrolowane przez klienta. Aby uzyskać więcej informacji, zobacz [porady: Podaj rozwinięty określająca zakres obsługi w starsza wersja usługi języka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Rejestracja usługi języka  
  
     Aby uzyskać więcej informacji o sposobie rejestrowania usługi języka, zobacz [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service2.md) i [Zarządzanie VSPackages](../../extensibility/managing-vspackages.md).  
  
-   Kontekstowa pomoc  
  
     Dostarcza kontekst do edytora w jednym z następujących sposobów:  
  
    -   Przewidują kontekstu znacznikach tekstu zaimplementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejsu.  
  
 Podaj wszystkie kontekstu użytkownika zaimplementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usługi języka starsza wersja](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)