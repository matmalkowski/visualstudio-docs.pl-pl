---
title: Tworzenie wystąpień Edytor Core przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a720126324faf1ab9a9a4e07086bc4ec711508f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132341"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Tworzenie wystąpień Edytor Core przy użyciu interfejsu API starsza wersja
Edytor jest odpowiedzialny za funkcji, takich jak wstawianie, usuwanie, kopiowanie i wklejanie edycji tekstu. Te funkcje łączy z udostępnianych przez usługi języka, takie jak tekstu kolorowania, wcięcia i uzupełniania IntelliSense.  
  
 Można utworzyć wystąpienia edytora rdzeni w jednym z trzech sposobów:  
  
-   Jawnie utworzyć wystąpienia podstawowego edytora w oknie.  
  
-   Podaj fabryki edytora, która zwraca wystąpienie klasy podstawowej edytora  
  
-   Otwórz plik z projektu hierarchii.  
  
 W poniższych sekcjach omówiono sposób używania starszej wersji interfejsu API można utworzyć wystąpienia edytora.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Jawnie otwierania wystąpienia Core edytora  
 Podczas uzyskiwania jawnie wystąpienie edytora rdzeni:  
  
-   Uzyskaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do przechowywania edytowanego obiektu danych dokumentu.  
  
-   Utwórz reprezentację wiersza zorientowane na obiekt danych dokumentu przez utworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejsu z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu.  
  
-   Ustaw <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> jako obiekt danych dokumentu dla wystąpienia Domyślna implementacja <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfejs, za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metody.  
  
     Host <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> wystąpienia w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsu za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metody.  
  
 W tym momencie wyświetlanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejs zawiera okno zawierające wystąpienie edytora core.  
  
 Jednak to nie jest wystąpieniem bardzo przydatne, ponieważ nie mają klawiszy skrótu lub dostęp do zaawansowanych funkcji. Aby uzyskać dostęp do klawiszy skrótów i zaawansowane funkcje:  
  
-   Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metoda powiązania usługi języka oraz obiekt danych dokumentu, który korzysta z edytora.  
  
-   Tworzenie własnych skrótów klawiaturowych, albo użyj domyślnego systemu przez ustawienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekty będą wyświetlane właściwości. Aby to zrobić, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> właściwości.  
  
     Aby uzyskiwał i wykorzystywał klawiszy skrótów niestandardowych, generowanie je za pomocą pliku vsct. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Jak używać fabryki edytora uzyskanie Edytor Core  
 Podczas implementowania edytorze core z fabryki edytora za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, wykonaj wszystkie kroki opisane w poprzedniej sekcji, aby jawnie obsługiwać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> obiektu danych dokumentu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektu.  
  
 Do wyświetlania tekstu, należy uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> obiekt i wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Aby zapewnić usługi języka dla edytora, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody w <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Można uzyskać domyślnego klawiszy skrótów, w przeciwieństwie do poprzedniej sekcji, użyj kontekst polecenia zwrócony przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody podczas uzyskiwania edytora core z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metoda zwraca tego samego polecenia identyfikatora GUID jako edytora tekstu, wystąpienie edytora core automatycznie uzyskuje wartość domyślna klawiszy skrótów.  
  
 Aby uzyskać ogólne informacje, zobacz [wskazówki: tworzenie edytora rdzeni i rejestrowania edytora plików typu](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze Core](../extensibility/inside-the-core-editor.md)   
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Wskazówki: Tworzenie edytora rdzeni i rejestrowania edytora typu pliku](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)