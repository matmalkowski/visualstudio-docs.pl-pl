---
title: "Włącz testowanie kodowanego interfejsu użytkownika dla Twoich formantów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 782a68e61786121095d3bf730dbd053564bad1cf
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz testowanie kodowanego interfejsu użytkownika dla Twoich kontrolek
Formantu można łatwiej przetestowane, jeśli implementuje obsługę framework testowanie kodowanego interfejsu użytkownika. Zwiększa poziom obsługi można dodać przyrostowo. Można uruchomić obsługi sprawdzania poprawności rekordu i odtwarzanie i właściwości. Tworzenie na tym, aby umożliwić Konstruktor kodowanego testu interfejsu użytkownika do rozpoznawania niestandardowych właściwości formantu i podaj klas niestandardowych dostęp do tych właściwości z wygenerowanego kodu. Może również pomóc kodowanego testu konstruktora przechwytywania działania Interfejsu w sposób zbliżonej do celem akcji rejestrowanych.

![CUIT &#95; Pełna](../test/media/cuit_full.png "CUIT_Full")  
  
##  <a name="recordandplayback"></a>Obsługuje rekordu i odtwarzanie i sprawdzanie poprawności właściwości zaimplementowanie ułatwień dostępu  
 Konstruktor kodowanego testu interfejsu użytkownika znajdują się informacje dotyczące formantów, że wystąpi podczas rejestracji, a następnie generuje kod powtarzania tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, kodowanego testu interfejsu użytkownika będzie przechwytywać akcji (np. kliknięcia myszą) za pomocą współrzędnych ekranu. Podczas odtwarzania testu wygenerowany kod będzie wystawiać tych kliknięć myszą w takich samych współrzędnych ekranu. Jeśli formant znajduje się w innym miejscu na ekranie podczas odtwarzania testu, wygenerowany kod zakończy się niepowodzeniem do wykonania tej akcji formantu. Może to spowodować błędy, jeśli test jest odtwarzany na inny ekran konfiguracji, w różnych środowiskach lub po zaszły zmiany w układzie interfejsu użytkownika.  
  
 ![CUIT &#95; RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT_RecordNoSupport")  
  
 Ułatwień dostępu w przypadku zastosowania, jednak kodowanego testu interfejsu użytkownika będą używać, aby zebrać informacje o formantu, kiedy rejestruje testu i generuje kod. Następnie po uruchomieniu testu wygenerowany kod zostanie będzie odtwarzana w tych zdarzeń z formantu, nawet jeśli jest ona gdzieś w interfejsie użytkownika. Autorzy testu będzie można utworzyć deklaracji rozkazujących przy użyciu podstawowe właściwości formantu.  
  
 ![CUIT &#95; Rekord](../test/media/cuit_record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Do obsługi rekordu i odtwarzania, sprawdzanie poprawności właściwości i nawigacji dla formantu formularzy systemu Windows  
 Implementowanie ułatwień dostępu dla formantu w sposób opisany w poniższej procedurze, a omówiona szczegółowo w artykule <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT &#95; Dostępne](../test/media/cuit_accessible.png "CUIT_Accessible")  
  
1.  Implementuje klasę, która jest pochodną <xref:System.Windows.Forms.Control.ControlAccessibleObject>i Zastąp <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwości, aby zwrócić obiekt klasy.  
  
    ```csharp  
    public partial class ChartControl : UserControl  
    {  
        // Overridden to return the custom AccessibleObject for the control.  
        protected override AccessibleObject CreateAccessibilityInstance()  
        {  
            return new ChartControlAccessibleObject(this);  
        }  
  
        // Inner class ChartControlAccessibleObject represents accessible information  
        // associated with the ChartControl and is used when recording tests.  
        public class ChartControlAccessibleObject : ControlAccessibleObject  
        {  
            ChartControl myControl;  
            public ChartControlAccessibleObject(ChartControl ctrl)  
                : base(ctrl)  
            {  
                myControl = ctrl;  
            }  
        }  
    }  
    ```  
  
2.  Zastąpienie dostępny obiekt <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> i <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> właściwości i metody.  
  
3.  Implementuje innego obiektu ułatwień dostępu dla formantu podrzędnego i Przesłoń formant podrzędny <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwości, aby powrócić do tego obiektu ułatwień dostępu.  
  
4.  Zastąpienie <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, i <xref:System.Windows.Forms.AccessibleObject.Select%2A> właściwości i metody dla obiektu ułatwień dostępu kontrolki podrzędnej.  
  
> [!NOTE]
>  W tym temacie, który rozpoczyna się od próbki ułatwień dostępu w <xref:System.Windows.Forms.AccessibleObject> w tej procedury, a następnie kompilacji na tej pozostałych procedur. Jeśli chcesz utworzyć działającą wersją próbki ułatwień dostępu, tworzenie aplikacji konsoli, a następnie Zastąp kod w pliku Program.cs przykładowy kod. Musisz dodać odwołanie do ułatwień dostępu, System.Drawing i System.Windows.Forms. Należy zmienić **Osadź typy międzyoperacyjne** ułatwień dostępu do **False** wyeliminować ostrzeżenie kompilacji. Możesz zmienić typ danych wyjściowych projektu do z **aplikacji konsoli** do **aplikacji systemu Windows** tak, aby nie zostanie wyświetlone okno konsoli po uruchomieniu aplikacji.  
  
##  <a name="customproprties"></a>Sprawdzanie poprawności właściwości niestandardowe pomocy technicznej dzięki implementacji dostawcy właściwości  
 Po podstawowej obsługi sprawdzania poprawności rekordu i odtwarzanie i właściwości zostały wdrożone, można udostępnić niestandardowe właściwości formantu do kodowane testy interfejsu użytkownika zaimplementowanie <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> wtyczki. Na przykład poniższa procedura dotyczy tworzenia dostawcy właściwości, który umożliwia kodowane testy interfejsu użytkownika do dostępu do właściwości stanu formantów podrzędnych CurveLegend formantu wykresu.  
  
 ![CUIT &#95; CustomProps](../test/media/cuit_customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>Do obsługi sprawdzania poprawności właściwości niestandardowej

![CUIT &#95; Właściwości](../test/media/cuit_props.png "CUIT_Props")

1. Zastąpienie krzywej legendy dostępny obiektu <xref:System.Windows.Forms.AccessibleObject.Description%2A> właściwości do przekazania wartości właściwości sformatowanego w ciągu opisu oddzielona od głównego opis (i wzajemnie w przypadku wdrażania wielu właściwości) należy rozdzielić średnikami (;).  
  
    ```csharp  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add ";" and the state value to the end  
                // of the curve legend's description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  

1. Utwórz pakiet rozszerzenia testów interfejsu użytkownika dla formantu przez utworzenie projektu biblioteki klas i dodaj odwołania do ułatwień dostępu, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common, i Microsoft.VisualStudio.TestTools.Extension. Zmień **Osadź typy współdziałania** ułatwień dostępu do **False**.

1. Dodaj klasę dostawcy właściwości, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Implementowanie dostawcy właściwości przez umieszczenie nazw właściwości i deskryptorów właściwości w <xref:System.Collections.Generic.Dictionary%602>.

1. Zastąpienie <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> aby wskazać, że używanemu zestawowi zapewnia obsługę specyficzne dla formantu dla formantu i jego elementów podrzędnych.

1. Zastępowanie pozostałe metody abstrakcyjne<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Dodaj klasę pakietu rozszerzenia, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Zdefiniuj `UITestExtensionPackage` atrybutu dla zestawu.

1. W klasie pakietu rozszerzenia, należy zastąpić <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> do zwrócenia klasy dostawcy właściwości, gdy wymagane jest Dostawca właściwości.

1. Zastąpienie pozostałe metody abstrakcyjne i właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Tworzenie Twoje pliki binarne i skopiuj je do **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.  

> [!NOTE]
> Ten pakiet rozszerzenia zostaną zastosowane do każdego formantu, który jest typu "Text". W przypadku testowania wielu formantów tego samego typu, należy je przetestować oddzielnie i zarządzanie nimi pakiety rozszerzeń, które są wdrażane po zarejestrowaniu testy.

##  <a name="codegeneration"></a>Obsługa generowania kodu przez implementującej klasy do dostępu do właściwości niestandardowe

Gdy kodowanego testu interfejsu użytkownika generuje kod z rejestrowania sesji, używa <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> klasę, aby dostęp do formantów.

Jeśli zostały zaimplementowane dostawcy właściwości w celu zapewnienia dostępu do właściwości niestandardowych formantu, można dodać specjalne klasy, która jest używana do dostępu do tych właściwości, aby została uproszczona w wygenerowanym kodzie.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać klas wyspecjalizowanych dostępu formantu do

![CUIT &#95; CodeGen](../test/media/cuit_codegen.png "CUIT_CodeGen")  

1. Implementuje klasę, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> i dodać do kolekcji właściwości wyszukiwania w Konstruktorze typu formantu.  

1. Implementowanie właściwości niestandardowych formantu jako właściwości klasy.  

1. Zastąpienie dostawcy właściwości <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodę, aby zwracany typ nową klasę dla krzywej formantów podrzędnych legendy.  

1. Zastąpienie dostawcy właściwości <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodę, aby zwracany typ metody PropertyNames nowej klasy.

##  <a name="intentawareactions"></a>Obsługuje akcje obsługujący zamiar zaimplementowanie filtr akcji  
 Visual Studio rejestruje testu, umożliwia przechwytywanie każdego zdarzenia myszy i klawiatury. Jednak w niektórych przypadkach celem akcji może zostać utracone w serie zdarzeń myszy i klawiatury. Na przykład jeśli formant obsługuje autouzupełniania, ten sam zestaw zdarzeń myszy i klawiatury może powodować innej wartości podczas testu odtwarzania w innym środowisku. Można dodać filtr akcji wtyczki zastępujący serie zdarzeń klawiatury i myszy z jednej akcji. W ten sposób można zastąpić serie zdarzeń myszy i klawiatury, co spowoduje zaznaczenie wartości z jednej akcji, która ustawia wartości. Które chroni kodowane testy interfejsu użytkownika z różnic w funkcji autocomplete z jednego środowiska do innego.  
  
### <a name="to-support-intent-aware-actions"></a>Do obsługi obsługujący celem akcji

![CUIT &#95; Akcje](../test/media/cuit_actions.png "CUIT_Actions")  

1. Implementuje klasę filtru akcji, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, zastępowanie właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> i <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>. 

1. Zastąpienie <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. Przykład tutaj realpces akcją kliknij dwukrotnie jeden kliknij akcję.

1. Dodaj filtr akcji do <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> metody pakietu rozszerzenia.

1. Skompiluj Twoje pliki binarne i skopiuj je do %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> Filtr akcji nie zależy od implementacji dostępności ani właściwości dostawcy.

## <a name="debug-your-property-provider-or-action-filter"></a>Debugowanie z usługodawcą właściwości lub filtr akcji

Filtr akcji i dostawcy właściwości są implementowane w pakiecie rozszerzenia ładowany i uruchamiane przez konstruktora kodowanego testu interfejsu użytkownika w procesie niezależnie od aplikacji.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować właściwości filtru akcji lub dostawcy  
  
1.  Tworzenie kopii pakietu rozszerzenia biblioteki DLL wersji do debugowania i .pdb, pliki do %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
2.  Uruchom aplikację (nie w debugerze).  
  
3.  Uruchamianie kodowanego testu interfejsu użytkownika.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Dołącz debuger do procesu codedUITestBuilder.  
  
5.  Ustaw punkty przerwania w kodzie.  
  
6.  W Konstruktorze kodowanego testu interfejsu użytkownika, należy utworzyć potwierdzeń wykonywania dostawcy właściwości i rejestrowanie akcji do wykonywania filtrów akcji.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
