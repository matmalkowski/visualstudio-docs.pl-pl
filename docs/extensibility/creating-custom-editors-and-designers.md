---
title: Tworzenie niestandardowych edytorów i projektantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0dbc0db9d5116e372d96b43059a393ac8f4b5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105294"
---
# <a name="creating-custom-editors-and-designers"></a>Tworzenie niestandardowych edytorów i projektantów
Visual Studio zintegrowane środowisko programistyczne (IDE) mogą obsługiwać różne rodzaje edytora:  
  
-   Edytor podstawowych programu Visual Studio  
  
-   Edytory niestandardowych  
  
-   Edytory zewnętrzne  
  
-   Projektanci  
  
 Następujące informacje pomogą wybierz typ edytora, które są potrzebne.  
  
## <a name="types-of-editor"></a>Typy edytora  
 Informacje o Edytorze podstawowych programu Visual Studio, zobacz [rozszerzanie edytora i usług języka](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Edytory niestandardowych  
 Niestandardowy Edytor to taki, który jest przeznaczony do pracy w specjalne okoliczności. Na przykład utworzyć edytor, którego zadaniem jest do odczytu i zapisu danych do określonego repozytorium, takich jak Microsoft Exchange server. Wybierz niestandardowego edytora, jeśli edytor, który współpracuje z danego typu projektu lub jeśli chcesz edytorze, który ma kilka określonych poleceń. Należy jednak pamiętać, że użytkownicy nie będą mogli używać niestandardowego edytora do edycji standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów.  
  
 Edytor niestandardowy można użyć fabryki edytora i dodać informacje o edytorze w rejestrze. Jednak typ projektu skojarzony z edytora niestandardowego można utworzyć wystąpienia niestandardowego edytora w inny sposób.  
  
 Edytor niestandardowy umożliwia Aktywacja w miejscu lub uproszczone osadzanie zaimplementować widoku.  
  
##### <a name="external-editors"></a>Edytory zewnętrzne  
 Edytory zewnętrzne są edytory, które nie są zintegrowane w programie Visual Studio, na przykład Microsoft Word, Notatnika lub programu Microsoft FrontPage. Takie edytora może wywołać, jeśli, na przykład tekst do niego z VSPackage. Edytory zewnętrzne rejestrować i może służyć poza programem Visual Studio. Po wywołań zewnętrznego edytora i można ją osadzić w oknie hosta, następnie wyświetlany w oknie w środowisku IDE. Jeśli nie, następnie IDE tworzy osobne okno dla niego.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Metoda ustawia priorytet dokumentu za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczenia. Jeśli `DP_External` jest określona, plik może otworzyć zewnętrznego edytora.  
  
## <a name="editor-design-decisions"></a>Decyzje dotyczące projektu edytora  
 Następujące pytania dotyczące projektu pomoże Ci wybrać typ edytora najlepiej nadaje się do aplikacji:  
  
-   Aplikacja zapisze dane w plikach lub nie? Jeśli jego danych zostanie zapisany w plikach, zostaną one w formacie niestandardowych lub standard?  
  
     Jeśli używasz standardowy format pliku innych typów projektów oprócz projektu będzie mogła otwierać i odczytu/zapisu danych do nich. Jeśli używasz formatu niestandardowego pliku, jednak tylko typ projektu będzie mogła otwierać i odczytu/zapisu danych do nich.  
  
     Jeśli projekt używa plików, należy dostosować standardowego edytora. Jeśli projekt nie korzystają z plików, ale raczej używa elementów w bazie danych lub inne repozytorium, należy utworzyć niestandardowego edytora.  
  
-   Czy edytor potrzebuje do hostowania kontrolki ActiveX?  
  
     Edytor obsługuje formantów ActiveX, następnie należy wdrożyć Edytor aktywacji w miejscu, w sposób opisany w [Aktywacja w miejscu](../extensibility/in-place-activation.md). Jeśli nie obsługuje formantów ActiveX, następnie za pomocą uproszczonego edytora osadzania albo dostosować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] domyślny edytor.  
  
-   Edytor będzie obsługiwać wiele widoków? Musi obsługiwać wiele widoków, jeśli chcesz, aby widoki edytora, aby były widoczne w tym samym czasie jako domyślny edytor.  
  
     Jeśli Edytor musi obsługiwać wiele widoków, dane dokumentu i obiekty widoku dokumentu edytora musi być oddzielnych obiektów. Aby uzyskać więcej informacji, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
     Jeśli Edytor obsługuje wiele widoków, czy zamierzasz używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podstawowego edytora tekstowego buforu implementacji (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu) dla obiekt danych dokumentu? Oznacza to, czy mają być obsługiwane z edytora widoku po stronie by-side z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor core? W tym celu jest podstawę Projektant formularzy.  
  
-   Jeśli potrzebujesz hosta zewnętrznego edytora, Edytor można osadzić wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Jeśli można ją osadzić, należy utworzyć okno hosta dla zewnętrznego edytora, a następnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> — metoda i zestaw <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wartości wyliczenia `DP_External`. Jeśli Edytor nie może zostać osadzony, IDE automatycznie utworzy oddzielne okno dla niego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik: tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Wyjaśnia sposób tworzenia niestandardowego edytora.  
  
 [Przewodnik: dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Opisano sposób dodawania funkcji do edytora niestandardowego.  
  
 [Inicjowanie projektanta i konfiguracja metadanych](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Wyjaśniono, jak zainicjować projektanta.  
  
 [Dostarczanie obsługi polecenia Cofnij do projektantów](../extensibility/supplying-undo-support-to-designers.md)  
 Wyjaśniono, jak zapewnić obsługę cofania dla projektantów.  
  
 [Kolorowania składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)  
 Objaśniono różnicę między kolorowania w edytorze rdzeni i edytory niestandardowych.  
  
 [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Opisuje sposób nadawania danych dokumentów i widoków dokumentu w edytorach niestandardowych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)  
 Wyjaśniono, jak uzyskać dostępu do edytora core za pomocą starszej wersji interfejsu API.  
  
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)  
 Opisuje sposób nadawania usługi języka.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Wyjaśniono, jak utworzyć elementy interfejsu użytkownika, zgodne z resztą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>