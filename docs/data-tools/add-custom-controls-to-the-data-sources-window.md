---
title: Dodawanie formantów niestandardowych do okna źródeł danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d00e818c0cfaa2659f55e5eb8bb8e4e4a87e8abc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Dodawanie formantów niestandardowych do okna źródeł danych
Gdy przeciągnąć element z **źródeł danych** okna do powierzchni projektu, można utworzyć formantu powiązanego z danymi, można wybrać typ formantu, który można utworzyć. Każdy element w oknie ma listy wyświetla formantów, które są dostępne. Zbiór kontrolki skojarzone z każdym elementem zależy od typu danych elementu. Jeśli formant, który ma zostać utworzony, nie ma na liście, można postępuj zgodnie z instrukcjami w tym temacie, aby dodać kontrolki do listy.  
  
 Aby uzyskać więcej informacji o wybieraniu formanty powiązane z danymi można utworzyć dla elementów w **źródeł danych** okna, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, na **narzędzia** menu, wybierz opcję **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
##  <a name="customizinglist"></a> Dostosowywanie na liście można powiązać formantów dla typu danych  
 Aby dodać lub usunąć formantów z listy dostępnych formantów dla elementów w **źródeł danych** okna, które ma typ danych, wykonaj następujące kroki.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Aby wybrać formantów był wyświetlany dla typu danych  
  
1.  Upewnij się, że projektant WPF lub Projektant formularzy systemu Windows jest otwarty.  
  
2.  W **źródeł danych** okna, kliknij element, który jest częścią źródła danych został dodany do okna, a następnie kliknij menu rozwijane elementu.  
  
3.  W menu rozwijanym kliknij **Dostosuj**. Jedną z następujących okien dialogowych otwiera:  
  
    -   Jeśli projektant formularzy systemu Windows jest otwarty, **dostosowywania interfejsu użytkownika danych** strony **opcje** zostanie otwarte okno dialogowe.  
  
    -   Jeśli projektant WPF jest otwarty, **Dostosuj powiązania kontrolki** zostanie otwarte okno dialogowe.  
  
4.  W oknie dialogowym Wybierz typ danych z **— typ danych** listy rozwijanej.  
  
    -   Aby dostosować listę formantów dla tabeli lub obiektu, wybierz **[lista]**.  
  
    -   Aby dostosować listę formantów dla kolumny tabeli lub właściwości obiektu, wybierz typ danych kolumny lub właściwości w odpowiedni magazyn danych.  
  
    -   Aby dostosować listę formantów na wyświetlanie obiektów danych, które mają kształtów zdefiniowane przez użytkownika, zaznacz **[innych]**. Na przykład wybierz **[innych]** Jeśli aplikacja ma kontrolki niestandardowej, która zawiera dane z więcej niż jedną właściwość określonego obiektu.  
  
5.  W **skojarzonych formantów** wybierz każdego formantu, który ma być dostępna dla wybranego typu danych lub wyczyść zaznaczenie wszystkich formantów, które chcesz usunąć z listy.  
  
    > [!NOTE]
    >  Jeśli formant, który ma zostać wybrana, nie jest widoczna w **skojarzonych formantów** pole, należy dodać kontrolki do listy. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do listy z skojarzonych formantów dla typu danych](#addingcontrols).  
  
6.  Kliknij przycisk **OK**.  
  
7.  W **źródeł danych** , kliknij element danych wpisz tylko skojarzona jeden lub kilka formantów, a następnie kliknij menu rozwijane elementu.  
  
     Formanty wybranym **skojarzonych formantów** pola wyświetlone w menu rozwijanym elementu.  
  
##  <a name="addingcontrols"></a> Dodawanie formantów do listy skojarzonych formantów dla typu danych  
 Jeśli chcesz skojarzyć z typem danych formantu, ale nie ma formantu **skojarzonych formantów** okno, należy dodać kontrolki do listy. Formant musi znajdować się w bieżącym rozwiązaniu lub w przywoływanym zestawie. Musi być także dostępna w **przybornika**, i mieć atrybut, który określa zachowanie wiązania danych formantu.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Aby dodać kontrolki do listy skojarzonych formantów  
  
1.  Dodaj formant żądanego **przybornika** przez kliknięcie prawym przyciskiem myszy **przybornika** i wybierając **wybierz elementy**.  
  
     Kontrolka musi mieć jedną z następujących atrybutów.  
  
    |Atrybut|Opis|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Wdrożenie tego atrybutu na prosty formanty, które wyświetlają pojedyncza kolumna (lub właściwości) dane, takie jak <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Wdrożenie tego atrybutu w formantach, które wyświetlania list lub tabele danych, takich jak <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Wdrożenie tego atrybutu w formantach, które wyświetlania list lub tabel danych, ale także przedstawiania pojedyncza kolumna lub właściwości, takie jak <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Dla formularzy systemu Windows na **opcje** po otwarciu okna dialogowego **dostosowywania interfejsu użytkownika danych** strony. WPF, można otworzyć **Dostosuj powiązania kontrolki** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dostosowywanie listy możliwej do wiązania kontrolki typu danych](#customizinglist).  
  
3.  W **skojarzonych formantów** polu formantu, który właśnie został dodany do **przybornika** powinien zostać wyświetlony.  
  
    > [!NOTE]
    >  Lista skojarzonych formantów można dodać tylko formanty, które znajdują się w bieżącym rozwiązaniu lub przywoływanego zestawu. (Formantów musi także implementować jeden z atrybutów powiązanie danych w poprzedniej tabeli.) Wiązanie danych do kontrolki niestandardowej, która nie jest dostępna w **źródeł danych** okna, przeciągnij formant z **przybornika** na powierzchni projektu, a następnie przeciągnij element, aby powiązać z **danych Źródeł** okna w formancie.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)