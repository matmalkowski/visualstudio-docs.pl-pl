---
title: 'BOOKMARK, formant: | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
ms.assetid: 940bf165-18c9-4db8-a46c-aad786b8bbad
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a946c190197b40dbc51fe2ddbcff434a21d84c11
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bookmark-control"></a>Formant zakładki
  <xref:Microsoft.Office.Tools.Word.Bookmark> Formant jest zakładki, która ma unikatową nazwę, opisuje zdarzenia i może być powiązany z danymi. Zakładki można służyć jako symbol zastępczy można oznaczyć elementu lub lokalizacji w dokumencie programu Microsoft Office Word. <xref:Microsoft.Office.Tools.Word.Bookmark> Formant jest kombinacją <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu i <xref:Microsoft.Office.Interop.Word.Range> obiektu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formanty do dokumentu w czasie projektowania lub w czasie wykonywania. W dodatku VSTO projektów, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 A <xref:Microsoft.Office.Tools.Word.Bookmark> sterowanie obsługuje proste powiązanie danych. Zakładka powinny być powiązane z źródła danych przy użyciu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości. Domyślna właściwość powiązania danych zakładki jest <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości.  
  
 Jeśli dane w zestawie danych powiązane są aktualizowane, <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli odzwierciedla zmiany.  
  
 W projektach na poziomie dokumentu, można także powiązać dane zakładki przy użyciu **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [porady: wypełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Word.Bookmark> można zastosować do <xref:Microsoft.Office.Tools.Word.Bookmark> formantu. W tym czcionek, wcięć, odstępy, numerowanie i style.  
  
## <a name="assigning-text-to-the-bookmark"></a>Przypisywanie tekstu do zakładki  
 Dodatkowe różnica między <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu i <xref:Microsoft.Office.Tools.Word.Bookmark> formant jest jego zachowania podczas tekst jest przypisany do zakładki. Jeśli tekst jest przypisane do zerowej długości <xref:Microsoft.Office.Interop.Word.Bookmark>, tekst jest dołączany do prawej zakładki i Zakładka pozostanie o zerowej długości. Jednak jeśli tekst jest przypisane do zerowej długości <xref:Microsoft.Office.Tools.Word.Bookmark>, wstawiony do zakładki, a długość zakładki rozszerza całkowitą liczbę znaków wstawiony.  
  
 <xref:Microsoft.Office.Tools.Word.Bookmark> Formantu ma również <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości. Różni się to od <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość, która jest dostępna w <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli lub <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> właściwość <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu.  
  
|Właściwość tekstu|Opis|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|Ta właściwość służy do wyświetlania tekstu w zakładce i pozostawić zakładki w dokumencie. Przypisywanie tekstu do zakładki rozszerza zakresu zakładek i nie powoduje usunięcia zakładki.<br /><br /> Na przykład `Bookmark1.Text = "Hello world"` wstawia tekst do zakładki i pozostawienie zakładki bez zmian.|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|Ta właściwość służy do wyświetlania tekstu w lokalizacji zakładek i automatycznie usunąć zakładki. Na przykład `Bookmark1.Range.Text = "Hello world"` wstawia tekst do zakładki i usuwa zakładki.|  
  
## <a name="renaming-the-control-at-design-time"></a>Zmiana nazwy formantu w czasie projektowania  
 W przypadku projektów na poziomie dokumentu, podczas przeciągania <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolować z **przybornika** do dokumentu, Visual Studio automatycznie generuje nazwę dla formantu. Można zmienić nazwę formantu w **właściwości** okna.  
  
## <a name="overlapping-controls"></a>Nakładanie się kontrolek  
 Formantów zakładki mogą nakładać się na siebie; oznacza to ten sam tekst może być współużytkowane przez więcej niż jeden zakładki. Po przypisaniu nowy tekst do jednego z nakładającymi się zakładki będzie zawierać nowego tekstu i zakładki już będzie nakłada się na. Inne zakładki teraz będzie zawierać tylko tekst, który nie został udostępniony między oryginalnego nakładające się zakładki.  
  
 W poniższej tabeli przedstawiono sposób zdania "Jest przykładowy tekst". jest współużytkowana przez dwie nakładające się zakładki.  
  
|Zakładka|Tekst|  
|--------------|----------|  
|Nakładające się zakładki|[to jest przykładowy {] tekstu.}|  
|Bookmark1|To jest przykładowy|  
|Bookmark2|Przykładowy tekst.|  
  
 Jeśli przypisany nowy tekst "Jest zastąpienie". Aby Bookmark1 już nie nakładają się na zakładek i Bookmark2 zachowuje tekst, który nie był pierwotnie część Bookmark1.  
  
|Zakładka|Tekst|  
|--------------|----------|  
|Dwa oddzielne zakładki|[to jest zastąpienie] {tekst}.|  
|Bookmark1|Zastępuje|  
|Bookmark2|tekst.|  
  
 Po zmianie tekstu zakładki zewnętrzne jeden zakładki pełni jest zawarty w innym zakładki, wewnętrzny zakładki nie są usuwane. Jednak zakładki wewnętrzne staje się puste zakładki, która została przeniesiona do końca zewnętrzne zakładki. W poniższej tabeli przedstawiono sposób zdania "Jest przykładowy tekst". jest współużytkowany przez zakładki, która jest zawarty w innym zakładki.  
  
|Zakładka|Tekst|  
|--------------|----------|  
|Nakładające się zakładki|[to jest tekst {próbki}].|  
|Bookmark1|To jest przykładowy tekst.|  
|Bookmark2|przykład|  
  
 Jeśli przypisany nowy tekst "Jest zastąpienie". Aby Bookmark1 już nie nakładają się na zakładek i Bookmark2 staje się puste zakładki, która znajduje się na końcu Bookmark1.  
  
|Zakładka|Tekst|  
|--------------|----------|  
|Dwa oddzielne zakładki|[to jest zastąpienie]. {}|  
|Bookmark1|To zastąpienie.|  
|Bookmark2|*\<pusty >*|  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Word.Bookmark> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Wskazówki: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  