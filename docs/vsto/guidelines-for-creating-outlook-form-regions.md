---
title: Wytyczne dotyczące tworzenia regionów formularzy programu Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dfbe02c652c53f0b7e5b2322ce76e7c022487d2e
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548170"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Wytyczne tworzenia regionów formularzy programu Outlook
  Poniższe informacje mogą pomóc w optymalizacji sieci regionów formularzy i uniknąć ewentualnych problemów:  
  
-   [Użyj nazwy regionów formularza](#UsingFormRegions).  
  
-   [Wyłącz dziedziczenie regionu formularza](#DisablingInheritance).  
  
-   [Zrozumienie typów i komunikatów nazwy klas](#ClassNames).  
  
-   [Projekt sąsiadujące regionów formularzy w okienku odczytu](#ReadingPane).  
  
-   [Użyj rozmiarów optymalne ikona](#UsingOptimal).  
  
 Aby uzyskać więcej informacji na temat regionów formularzy, zobacz [regionów formularzy Outlook utwórz](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Użyj nazwy regionów formularza  
 Istnieje kilka nazw używany do opisania regionu formularza. Należy zrozumieć różnicę między te nazwy i ich wpływ na regionu formularza. W poniższej tabeli opisano każdej nazwy.  
  
|Nazwa regionu formularza|Opis|  
|----------------------|-----------------|  
|Nazwa elementu regionu formularza|Nazwa określona dla **regionów formularzy programu Outlook** elementu **Dodaj nowy element** okno dialogowe. Jest to nazwa pliku kodu regionu formularza, który jest wyświetlany w **Eksploratora rozwiązań**.|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Właściwość|Określ nazwę tego w **Podaj opis, a następnie wybierz preferencje wyświetlania** strony **nowych regionów formularzy programu Outlook** kreatora. Ta nazwa jest wyświetlana jako **FormRegionName** właściwości w **właściwości** okna.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości w celu określenia etykietę, która identyfikuje regionów formularzy w interfejsie użytkownika (UI) programu Outlook. Formularz oddzielnych regionach nazwa ta zostanie wyświetlona jako przycisk na Wstążce elementu programu Outlook.<br /><br /> Sąsiadujących regionów formularzy ta nazwa pojawia się jako tekst nagłówka powyżej regionu formularza.|  
|`Microsoft.Office.Tools.Outlook.FormRegionName` Atrybut|Po dodaniu **regionów formularzy programu Outlook** elementu do projektu programu Visual Studio ustawia tę właściwość, aby w pełni kwalifikowana nazwa regionu formularza. Jest w pełni kwalifikowana nazwa domyślna nazwa dodatku VSTO połączona nazwę regionu formularza za pomocą pojedynczego znaku kropki — na przykład `OutlookAddIn1.FormRegion1`.<br /><br /> To w pełni kwalifikowana nazwa pojawia się również jako atrybut u góry klasy fabryki regionu formularza.<br /><br /> Użyj `Microsoft.Office.Tools.Outlook.FormRegionName` atrybut do unikatowego identyfikowania regionu formularza we wszystkich dodatków VSTO programu Outlook. Nie można zmienić wartości `Microsoft.Office.Tools.Outlook.FormRegionName` atrybut zmieniając element regionu formularza lub zmieniając <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości. Aby zmienić tę nazwę, należy zmodyfikować `Microsoft.Office.Tools.Outlook.FormRegionName` atrybutu w pliku kodu regionu formularza.|  
  
##  <a name="DisablingInheritance"></a> Wyłącz dziedziczenie regionów formularzy  
 Domyślnie klasa niestandardowy komunikat dziedziczy wszystkie skojarzenia regionu formularza klasy podstawowej wiadomości. Na przykład o nazwie klasy wiadomości `IPM.Task.Contoso` pochodną `IPM.Task`. W związku z tym `IPM.Task.Contoso` dziedziczy formularz skojarzenia region `IPM.Task`.  
  
 Jeśli nie chcesz, aby regionu formularza, który ma zostać skojarzony z dowolnej klasy pochodnej wiadomości, ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> właściwości regionu formularza do **true**. Na przykład, jeśli skojarzone sąsiadujących regionu formularza z `IPM.Task` i ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> właściwości **true**, regionu formularza zostanie dołączona tylko do dolnej części formularza zadania standardowego. Region formularza nie zostaną dodane na końcu wszystkie niestandardowe wersje formularza zadania standardowego.  
  
##  <a name="ClassNames"></a> Typy i nazwy klas wiadomości  
 Nazwa typu elementu programu Outlook różni się od nazwy klasy wiadomości, elementu programu Outlook. Na przykład nazwa typu elementu RSS jest `Microsoft.Office.Interop.Outlook.PostItem`. Nazwa klasy wiadomości elementu RSS jest `IPM.Post.RSS`.  
  
 Użyj nazwy typu do odwołania elementu programu Outlook w kodzie. Aby uzyskać listę nazw typów, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Użyj nazwy klasy wiadomości elementów programu Outlook w **nowych regionów formularzy programu Outlook** kreatora, aby skojarzyć element z regionu formularza. Lista nazw klas prawidłowego elementu message, [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Projektowanie regionów formularzy w sąsiadujących okienka odczytu  
 Okienko odczytu programu Outlook umożliwia podgląd elementu programu Outlook bez otwierania elementu. Okienko odczytu jest przeznaczony do czytania tylko. W związku z tym kontrolki wejściowe, które dodajesz do sąsiadujących regionu formularza, takich jak pole tekstowe, może nie działać zgodnie z oczekiwaniami, gdy region elementu i formularza są otwarte w okienku odczytu.  
  
 Na przykład jeśli element sąsiadujących region formularza jest otwarty w okienku odczytu, możliwe jest następujących sytuacji:  
  
1.  Wybierz dowolny tekst w polu tekstowym, który znajduje się na regionu formularza.  
  
2.  Naciśnij klawisz **usunąć**.  
  
3.  Element całej poczty jest usuwany zamiast tekstu w polu tekstowym.  
  
 W przypadku projektowania sąsiadujących regionu formularza, który zawiera kontrolki wejściowe, należy przetestować formantów w okienku odczytu, aby upewnić się, że działają one prawidłowo. Rozważ dodanie kodu niestandardowego, który powoduje wyłączenie formantów, które nie działają zgodnie z oczekiwaniami.  
  
 Alternatywnie, można ustawić <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> właściwości regionu formularza do **False**. Nie można użyć w ten sposób regionów formularzy w okienku odczytu.  
  
##  <a name="UsingOptimal"></a> Ikona optymalny rozmiar używany  
 Można określić, które ikony mają regionu formularza do wyświetlenia za pomocą właściwości ikony w **ikony** grupy właściwości **właściwości** okna. Aby osiągnąć najwyższą jakość wizualną, skorzystaj z poniższych wskazówek:  
  
-   Dla **strony** ikonę, użyj pliku Portable Network Graphics (PNG).  
  
-   **Okno** ikony powinny być 32 pikseli na 32 pikseli.  
  
-   Wszystkie inne ikony powinna być 16 x pikseli 16.  
  
 **Strony** pojawi się ikona na Wstążce inspektora dla elementów, które mają oddzielne, wymiana albo regionów formularzy Zamień wszystkie.  
  
 **Okna** ikona jest wyświetlana w obszarze powiadomień, a w **Alt**+**kartę** okno dialogowe otwarte elementy tego wyświetlania zastąpienia lub Zastąp wszystkie formularza regiony.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Porady: dodawanie regionu formularza do projektu dodatek programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  