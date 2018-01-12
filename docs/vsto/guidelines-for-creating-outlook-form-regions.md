---
title: "Wytyczne dotyczące tworzenia Outlook tworzą regionów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e82a4428dde7aa25c7e9a3d7d74017b9f2a874f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="guidelines-for-creating-outlook-form-regions"></a>Wytyczne dotyczące tworzenia regionów formularzy w programie Outlook
  Poniższe informacje mogą pomóc w optymalizacji sieci regionów formularzy i uniknąć ewentualnych problemów:  
  
-   [Przy użyciu nazwy regionów formularza](#UsingFormRegions).  
  
-   [Wyłączając dziedziczenie regionu formularza](#DisablingInheritance).  
  
-   [Opis typów i komunikat klasy nazwy](#ClassNames).  
  
-   [Projektowanie sąsiadujących regionów formularzy w okienku odczytu](#ReadingPane).  
  
-   [Przy użyciu rozmiary optymalne ikona](#UsingOptimal).  
  
 Aby uzyskać więcej informacji na temat regionów formularzy, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a>Przy użyciu nazwy regionów formularza  
 Istnieje kilka nazw używany do opisania regionu formularza. Należy zrozumieć różnicę między te nazwy i ich wpływ na regionu formularza. W poniższej tabeli opisano każdej nazwy.  
  
|Nazwa regionu formularza|Opis|  
|----------------------|-----------------|  
|Nazwa elementu regionu formularza|Nazwa określona dla **regionów formularzy programu Outlook** elementu **Dodaj nowy element** okno dialogowe. Jest to nazwa pliku kodu regionu formularza, który jest wyświetlany w **Eksploratora rozwiązań**.|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>Właściwość|Określ nazwę tego w **Podaj opis, a następnie wybierz preferencje wyświetlania** strony **nowych regionów formularzy programu Outlook** kreatora. Ta nazwa jest wyświetlana jako **FormRegionName** właściwości w **właściwości** okna.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości w celu określenia etykietę, która identyfikuje regionów formularzy w interfejsie użytkownika (UI) programu Outlook. Formularz oddzielnych regionach nazwa ta zostanie wyświetlona jako przycisk na Wstążce elementu programu Outlook.<br /><br /> Sąsiadujących regionów formularzy ta nazwa pojawia się jako tekst nagłówka powyżej regionu formularza.|  
|Atrybut Microsoft.Office.Tools.Outlook.FormRegionName|Po dodaniu **regionów formularzy programu Outlook** elementu do projektu programu Visual Studio ustawia tę właściwość, aby w pełni kwalifikowana nazwa regionu formularza. Jest w pełni kwalifikowana nazwa domyślna nazwa dodatku VSTO połączona nazwę regionu formularza za pomocą pojedynczego znaku kropki — na przykład `OutlookAddIn1.FormRegion1`.<br /><br /> To w pełni kwalifikowana nazwa pojawia się również jako atrybut u góry klasy fabryki regionu formularza.<br /><br /> Użyj atrybutu Microsoft.Office.Tools.Outlook.FormRegionName do unikatowego identyfikowania regionu formularza we wszystkich dodatków VSTO programu Outlook. Nie można zmienić wartości atrybutu Microsoft.Office.Tools.Outlook.FormRegionName, zmieniając element regionu formularza lub zmieniając <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości. Aby zmienić tę nazwę, należy zmodyfikować atrybutu Microsoft.Office.Tools.Outlook.FormRegionName w pliku kodu regionu formularza.|  
  
##  <a name="DisablingInheritance"></a>Wyłączając dziedziczenie regionu formularza  
 Domyślnie klasa niestandardowy komunikat dziedziczy wszystkie skojarzenia regionu formularza klasy podstawowej wiadomości. Na przykład o nazwie klasy wiadomości `IPM.Task.Contoso` pochodną IPM. Zadanie. W związku z tym `IPM.Task.Contoso` dziedziczy skojarzenia regionu formularza IPM. Zadanie.  
  
 Jeśli nie chcesz, aby regionu formularza, który ma zostać skojarzony z dowolnej klasy pochodnej wiadomości, ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> właściwości regionu formularza do **true**. Na przykład, jeśli należy powiązać z IPM sąsiadujących regionu formularza. Zadania i ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> właściwości **true**, regionu formularza zostanie dołączona tylko do dolnej części formularza zadania standardowego. Region formularza nie zostaną dodane na końcu wszystkie niestandardowe wersje formularza zadania standardowego.  
  
##  <a name="ClassNames"></a>Opis typów i nazw klasy wiadomości  
 Nazwa typu elementu programu Outlook różni się od nazwy klasy wiadomości, elementu programu Outlook. Na przykład nazwa typu elementu RSS jest Microsoft.Office.Interop.Outlook.PostItem. Nazwa klasy wiadomości elementu RSS jest IPM. Post.RSS.  
  
 Użyj nazwy typu do odwołania elementu programu Outlook w kodzie. Aby uzyskać listę nazw typów, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Użyj nazwy klasy wiadomości elementów programu Outlook w **nowych regionów formularzy programu Outlook** kreatora, aby skojarzyć element z regionu formularza. Lista nazw klas prawidłowego elementu message, [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a>Projektowanie regionów formularzy sąsiadujących okienka odczytu  
 Okienko odczytu programu Outlook umożliwia podgląd elementu programu Outlook bez otwierania elementu. Okienko odczytu jest przeznaczony do czytania tylko. W związku z tym kontrolki wejściowe, które dodajesz do sąsiadujących regionu formularza, takich jak pole tekstowe, może nie działać zgodnie z oczekiwaniami, gdy region elementu i formularza są otwarte w okienku odczytu.  
  
 Na przykład jeśli element sąsiadujących region formularza jest otwarty w okienku odczytu, możliwe jest następujących sytuacji:  
  
1.  Wybierz dowolny tekst w polu tekstowym, który znajduje się na regionu formularza.  
  
2.  Naciśnij klawisz DELETE.  
  
3.  Element całej poczty jest usuwany zamiast tekstu w polu tekstowym.  
  
 W przypadku projektowania sąsiadujących regionu formularza, który zawiera kontrolki wejściowe, należy przetestować formantów w okienku odczytu, aby upewnić się, że działają one prawidłowo. Rozważ dodanie kodu niestandardowego, który powoduje wyłączenie formantów, które nie działają zgodnie z oczekiwaniami.  
  
 Alternatywnie, można ustawić <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> właściwości regionu formularza do **False**. Nie można użyć w ten sposób regionów formularzy w okienku odczytu.  
  
##  <a name="UsingOptimal"></a>Przy użyciu rozmiary optymalne ikony  
 Można określić, które ikony mają regionu formularza do wyświetlenia za pomocą właściwości ikony w **ikony** grupy właściwości **właściwości** okna. Aby osiągnąć najwyższą jakość wizualną, skorzystaj z poniższych wskazówek:  
  
-   Dla **strony** ikonę, użyj pliku Portable Network Graphics (PNG).  
  
-   **Okno** ikony powinny być 32 pikseli na 32 pikseli.  
  
-   Wszystkie inne ikony powinna być 16 x pikseli 16.  
  
 **Strony** pojawi się ikona na Wstążce inspektora dla elementów, które mają oddzielne, wymiana albo regionów formularzy Zamień wszystkie.  
  
 **Okna** ikona jest wyświetlana w obszarze powiadomień, jak i w oknie dialogowym ALT + TAB otwarte elementy zawierające zastąpienia lub regionów formularzy Zastąp wszystkie.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Porady: dodawanie regionu formularza na projekt dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  