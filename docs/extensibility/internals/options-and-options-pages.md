---
title: Opcje i opcje strony | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d85b900779a5df8af077b292b2e2f70b0592e35c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="options-and-options-pages"></a>Opcje i opcje strony
Kliknięcie przycisku **opcje** na **narzędzia** zostanie otwarte menu **opcje** okno dialogowe. Opcje w oknie dialogowym zbiorowo są określane jako strony opcji. Drzewie w okienku nawigacji zawiera opcje kategorie, a każda kategoria ma opcje strony. Po wybraniu stroną jego opcje są wyświetlane w okienku po prawej stronie. Te strony umożliwiają Zmień wartości opcji, które określają stan pakiet VSPackage.  
  
## <a name="support-for-options-pages"></a>Obsługa stron opcje  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasy zapewnia obsługę tworzenia strony opcji i opcje kategorii. <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasa implementuje stronę opcji.  
  
 Domyślna implementacja <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jego właściwości publiczne z kontem użytkownika w ogólne siatki właściwości. To zachowanie można dostosować przez zastąpienie różnych metod na stronie, aby utworzyć stronę opcji niestandardowej, która ma własny interfejs użytkownika (UI). Aby uzyskać więcej informacji, zobacz [tworzenie stron opcje](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasa implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, zapewniające trwałości dla stron opcje, a także dla ustawień użytkownika. Domyślne implementacje <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> i <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metody utrwalania zmian właściwości do sekcji rejestru użytkownika, jeśli właściwość można przekonwertować do i z ciągu.  
  
## <a name="options-page-registry-path"></a>Ścieżka rejestru strony opcji  
 Domyślnie, ścieżka rejestru właściwości zarządzane przez stronę opcji jest określany przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word typu DialogPage i nazwę typu klasy strony opcji. Klasa strony opcji może na przykład zdefiniowane w następujący sposób.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, a następnie pary nazw i wartości właściwości są podkluczy HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Ścieżka rejestru strony Opcje jest określany przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, słowo, ToolsOptionsPages i opcje strony kategorii i nazwę. Na przykład, jeśli strona Opcje niestandardowe zawiera kategorii, Moje stron opcji i <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> jest HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie strona Opcje zawiera klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom opcji.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Atrybuty strony narzędzia/Opcje i układu  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atrybut określa grupowanie niestandardowych opcji stron na kategorie w drzewie nawigacji **opcje** okno dialogowe. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atrybut kojarzy stronę opcji z pakiet VSPackage, który udostępnia interfejs. Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Deklaruje to, że MyPackage zawiera dwie strony Opcje OptionsPageGeneral i OptionsPageCustom. W **opcje** okno dialogowe, obie strony opcje są wyświetlane w **Moje strony opcji** kategorii jako **ogólne** i **niestandardowy**odpowiednio.  
  
## <a name="option-attributes-and-layout"></a>Opcja atrybuty i układu  
 Interfejs użytkownika (UI), które ta strona zawiera określa wygląd opcje na stronie Opcje niestandardowe. Układ, etykietowania i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Określa kategorię opcji.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Określa nazwę wyświetlaną opcji.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Określa opis opcji.  
  
    > [!NOTE]
    >  Odpowiednik atrybutów, SRCategory LocDisplayName i SRDescription, użyj zasoby ciągów dla lokalizacji i są zdefiniowane w [próbki zarządzanego projektu](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 Opcja OptionInteger pojawia się na stronie opcji jako **opcji całkowitą** w **Moje opcje** kategorii. Jeśli zaznaczona jest opcja, opis, **Moje opcja całkowitą**, zostanie wyświetlony w polu Opis.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Uzyskiwanie dostępu do strony opcji z innej pakiet VSPackage  
 Pakiet VSPackage, który obsługuje i zarządza nimi na stronie Opcje można programowo możliwy z innego pakiet VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie pakiet VSPackage jest zarejestrowany jako stanowiącego host strony opcji.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Poniższy fragment kodu pobiera wartość OptionInteger z MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Gdy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut rejestruje Opcje strony, strony jest zarejestrowany w przypadku klucza AutomationProperties `SupportsAutomation` argument atrybutu jest `true`. Automatyzacja sprawdza, czy ten wpis rejestru, aby znaleźć skojarzone pakiet VSPackage i automatyzacji, a następnie uzyskuje dostęp do właściwości za pośrednictwem strony hostowanej opcje, w tym przypadku Moje strony siatki.  
  
 Ścieżka rejestru właściwości automatyzacji jest określany przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, word, AutomationProperties i opcje strony kategorii i nazwę. Na przykład, jeśli strona Opcje zawiera kategorii Moje kategorii, nazwę Moje strony siatki i <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a następnie właściwości automatyzacji ma klucz rejestru, HKEY_LOCAL_MACHINE\SOFTWARE\ Strona siatki Category\My Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
>  Nazwa kanoniczna Moja strona siatki Category.My, jest to wartość podklucza nazwa tego klucza.