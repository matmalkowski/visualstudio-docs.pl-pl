---
title: Importy Edytor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f01567efa411187bede4f6daf15012da81c2331f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132737"
---
# <a name="editor-imports"></a>Importy edytora
Liczba usług edytora, fabryki i brokerów, które dostarczają rozszerzenie różnego rodzaju dostępu do edytora core można zaimportować. Na przykład możesz zaimportować <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> umożliwia z <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> dla danego typu zawartości. (Tego nawigatora pozwala na bufor tekstowy wykonywać różnego rodzaju wyszukiwania).  
  
 Aby użyć edytora importu, zaimportować jako pole lub właściwość klasy, które eksportuje część Managed Extensibility Framework.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat Managed Extensibility Framework, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
## <a name="import-syntax"></a>Składnia importu  
 Poniższy przykład pokazuje, jak zaimportować Edytor opcje fabryki usługi.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Jeśli chcesz zaimportować usługi jako pola i właściwości nie powinien być skonfigurowany `null` w deklaracji, aby uniknąć ostrzeżenia kompilatora, aby nie przypisywać do zmiennej:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Więcej przykładów dotyczących przy użyciu Importy zobacz następujące wskazówki:  
  
 [Przewodnik: tworzenie symbolu na marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Przewodnik: dostosowywanie widoku tekstu](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Przewodnik: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)  
  
 [Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Przewodnik: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Przewodnik: wyświetlanie sugestii „żarówka”](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## <a name="importing-the-service-provider"></a>Importowanie dostawcy usług  
 Możesz również zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (znaleziony w zestawie Microsoft.VisualStudio.Shell.Immutable.10.0) w taki sam sposób, aby uzyskać dostęp do usługi Visual Studio:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Zobacz [wskazówki: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) Aby uzyskać więcej informacji.  
  
## <a name="services"></a>Usługi  
 Edytor usługi są zazwyczaj pojedynczych jednostek, które świadczenia usługi i są współdzielone przez wiele składników.  
  
|{1&gt;Importuj&lt;1}|Udostępnia|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relacja między rozszerzeniami plików i <xref:Microsoft.VisualStudio.Utilities.IContentType> obiektów.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekcja <xref:Microsoft.VisualStudio.Utilities.IContentType> obiektów.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Obiekty|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Wiele obiektów karta edytora:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> Obiektu podany tekst w widoku.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> Różnic.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> Różnic.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Lub <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Zbiór <xref:Microsoft.VisualStudio.Text.ITextBuffer> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Dla <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Zapewnia zbiór <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Dla bufora tekstowego.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Dla widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> Dla określonego zakresu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> Dla widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Pobiera automatyczne wcięcia za pośrednictwem <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Zarządza <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> dla <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje tekstu w formacie RTF z zestawu obejmuje migawki.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> formatowania wierszy tekstu w widoku.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> obiekt do <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Wyszukuje migawki tekstu.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> Dla <xref:Microsoft.VisualStudio.Text.ITextBuffer> przez <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> Dla widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardowy zestaw symboli.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Śledzi klawiatury obsługi.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardowe <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Przechowuje relacje między buforów tekstu i <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> obiektów.|  
  
## <a name="other-imports"></a>Inne importów  
 Fabryki dostawców i brokerów są zwykle jednostek, które mogą mieć wiele wystąpień w wielu składników.  
  
|{1&gt;Importuj&lt;1}|Udostępnia|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> Typu <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) dla podanego buforu.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Modułu znakowania tekstu znacznika ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> Dla danego <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)