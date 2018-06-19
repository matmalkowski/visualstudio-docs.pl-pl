---
title: 'Wskazówki: Dostosowywanie widoku tekstu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fb4762a422102b91c44d755d387168ab0572f2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142085"
---
# <a name="walkthrough-customizing-the-text-view"></a>Wskazówki: Dostosowywanie widoku tekstu
Można dostosować widoku tekstu, zmieniając dowolne z następujących właściwości w jego format edytora mapy:  
  
-   Margines wskaźnika  
  
-   Daszek wstawiania  
  
-   Zastąp karetki  
  
-   Zaznaczony tekst  
  
-   Nieaktywnego zaznaczonego tekstu (to znaczy zaznaczonego tekstu, który utraciła fokus)  
  
-   Widoczne odstępu  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `ViewPropertyTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
## <a name="defining-the-content-type"></a>Definiowanie typu zawartości  
  
1.  Dodaj plik klasy i nadaj mu nazwę `ViewPropertyModifier`.  
  
2.  Dodaj następujące `using` dyrektywy:  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Deklarowanie klasy o nazwie `TestViewCreationListener` dziedziczący po <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Wyeksportuj tej klasy, z następującymi atrybutami:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Określanie typu zawartości, którego dotyczy ten odbiornika.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Aby określić roli tego odbiornika.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  W tej klasie zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Zmiana właściwości widoku  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metody, aby właściwości widoku są zmieniane po otwarciu widoku. Aby wprowadzić zmiany, Znajdź najpierw <xref:System.Windows.ResourceDictionary> odpowiadający aspekt widoku, który ma zostać znaleziony. Zmień odpowiednie właściwości w słowniku zasobów, a następnie ustaw właściwości. Partii wywołań <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody wywołując <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metoda przed ustawieniem właściwości, a następnie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po ustawieniu właściwości.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie.  
  
     Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
2.  Utwórz plik tekstowy i wpisz tekst.  
  
    -   Daszek Zastąp należy turkusowy i karetki wstawiania powinna być amarantowy.  
  
    -   Margines wskaźnika (do lewej strony widoku tekstu) powinna być jasny zielony.  
  
3.  Zaznacz tekst, który został wpisany. Kolor tekstu zaznaczonego powinien być jasny różowy.  
  
4.  Gdy tekst jest zaznaczony, kliknij w dowolnym miejscu poza oknem tekstu. Kolor tekstu zaznaczonego powinna być ciemnoróżowy.  
  
5.  Włącz widoczne odstępu. (Na **Edytuj** menu wskaż **zaawansowane** , a następnie kliknij przycisk **widoku biały znak**). Wpisz tekst niektóre karty. Czerwone strzałki, które reprezentują kartach powinien być wyświetlany.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)