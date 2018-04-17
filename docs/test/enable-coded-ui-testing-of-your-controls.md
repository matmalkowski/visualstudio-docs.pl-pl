---
title: Włącz testowanie kodowanego interfejsu użytkownika dla Twoich formantów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7c3906b84995716072d4df0a1b518930a521cdb6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz testowanie kodowanego interfejsu użytkownika dla Twoich formantów

Implementuje obsługę kodowanego interfejsu użytkownika testowania framework dokonanie więcej testować formantu. Zwiększa poziom obsługi można dodać przyrostowo. Rozpocznij od obsługi sprawdzania poprawności rekordu i odtwarzanie i właściwości. Następnie kompilacji na tym, aby włączyć Konstruktor kodowanego testu interfejsu użytkownika do rozpoznawania niestandardowych właściwości formantu. Podaj klas niestandardowych dostęp do tych właściwości z wygenerowanego kodu. Może również pomóc kodowanego testu konstruktora przechwytywania działania Interfejsu w sposób zbliżonej do celem akcji rejestrowanych.

![CUIT&#95;Full](../test/media/cuit_full.png "CUIT_Full")

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Obsługuje sprawdzania rekordu i odtwarzanie i właściwości zaimplementowanie ułatwień dostępu

Konstruktor kodowanego testu interfejsu użytkownika znajdują się informacje dotyczące formantów, że wystąpi podczas rejestracji, a następnie generuje kod powtarzania tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, kodowanego testu interfejsu użytkownika przechwytuje akcji (np. kliknięcia myszą) za pomocą współrzędnych ekranu. Podczas odtwarzania testu wygenerowany kod wystawia akcje w takich samych współrzędnych ekranu. Jeśli formant znajduje się w innym miejscu na ekranie podczas odtwarzania testu, wygenerowany kod zakończy się niepowodzeniem do wykonania akcji. Implementując nie ułatwień dostępu dla formantu, można napotkać test niepowodzenia testu jest odtwarzany na inny ekran konfiguracji, w różnych środowiskach, albo jeśli zmieni się układ interfejsu użytkownika.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT_RecordNoSupport")

 W przypadku zastosowania ułatwień dostępu, kodowanego testu interfejsu użytkownika użyty do przechwycenia informacji na temat formantu, gdy rejestruje testu. Następnie po uruchomieniu testu wygenerowany kod zostanie będzie odtwarzana w tych zdarzeń z formantu, nawet jeśli jest ona gdzieś w interfejsie użytkownika. Autorzy testów można również utworzyć potwierdzeń przy użyciu podstawowe właściwości formantu.

 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Do obsługi rekordu i odtwarzania, sprawdzanie poprawności właściwości i nawigacji dla formantu formularzy systemu Windows
 Implementowanie ułatwień dostępu dla formantu w sposób opisany w poniższej procedurze, a omówiona szczegółowo w artykule <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT_Accessible")

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

3.  Implementuje innego obiektu ułatwień dostępu dla formantu podrzędnego i Przesłoń formant podrzędny <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwość, aby przywrócić obiektu ułatwień dostępu.

4.  Zastąpienie <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, i <xref:System.Windows.Forms.AccessibleObject.Select%2A> właściwości i metody dla obiektu ułatwień dostępu kontrolki podrzędnej.

> [!NOTE]
> W tym temacie, który rozpoczyna się od próbki ułatwień dostępu w <xref:System.Windows.Forms.AccessibleObject>, a potem kompiluje dla tej próbki pozostałych procedur. Jeśli chcesz utworzyć działającą wersją próbki ułatwień dostępu, tworzenie aplikacji konsoli, a następnie Zastąp kod w pliku Program.cs przykładowy kod. Dodaj odwołania do ułatwień dostępu, System.Drawing i System.Windows.Forms. Zmień **Osadź typy międzyoperacyjne** ułatwień dostępu do **False** wyeliminować ostrzeżenie kompilacji. Możesz zmienić typ danych wyjściowych projektu z **aplikacji konsoli** do **aplikacji systemu Windows** tak, aby nie zostanie wyświetlone okno konsoli po uruchomieniu aplikacji.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Obsługa weryfikacji właściwości niestandardowej przez implementowanie dostawcy właściwości

Po wdrożeniu podstawowej obsługi sprawdzania poprawności rekordu i odtwarzanie i właściwości można udostępnić niestandardowe właściwości formantu do kodowane testy interfejsu użytkownika zaimplementowanie <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> wtyczki. Na przykład poniższa procedura dotyczy tworzenia dostawcy właściwości, który umożliwia kodowane testy interfejsu użytkownika do dostępu do właściwości stanu formantów podrzędnych formantu wykresu CurveLegend:

 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Do obsługi sprawdzania poprawności właściwości niestandardowej

![CUIT&#95;Props](../test/media/cuit_props.png "CUIT_Props")

1. Zastąpienie krzywej legendy dostępny obiektu <xref:System.Windows.Forms.AccessibleObject.Description%2A> właściwości do przekazania wartości właściwości sformatowanego w ciągu opisu. Wiele wartości należy rozdzielić średnikami (;).

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

1. Utwórz pakiet rozszerzenia testów interfejsu użytkownika dla formantu przez utworzenie projektu biblioteki klas. Dodaj odwołania do ułatwień dostępu, Microsoft.VisualStudio.TestTools.UITesting Microsoft.VisualStudio.TestTools.UITest.Common i Microsoft.VisualStudio.TestTools.Extension. Zmień **Osadź typy współdziałania** ułatwień dostępu do **False**.

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

1. Zastępowanie pozostałe metody abstrakcyjne <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Dodaj klasę pakietu rozszerzenia, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Zdefiniuj `UITestExtensionPackage` atrybutu dla zestawu.

1. W klasie pakietu rozszerzenia, należy zastąpić <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> do zwrócenia klasy dostawcy właściwości, gdy wymagane jest Dostawca właściwości.

1. Zastąpienie pozostałe metody abstrakcyjne i właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Tworzenie Twoje pliki binarne i skopiuj je do **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Ten pakiet rozszerzenia jest stosowany do żadnego formantu, który jest typu "Text". Jeśli testujesz wielu formantów tego samego typu testowane oddzielnie, można zarządzać, które pakiety rozszerzenia są wdrażane po zarejestrowaniu testy.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Obsługa generowania kodu zaimplementowanie klasę, aby uzyskać dostęp do właściwości niestandardowych

Gdy kodowanego testu interfejsu użytkownika generuje kod z rejestrowania sesji, używa <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> klasę, aby dostęp do formantów.

Jeśli zostały zaimplementowane dostawcy właściwości w celu zapewnienia dostępu do właściwości niestandardowych formantu, można dodać specjalne klasy, która umożliwia dostęp do tych właściwości. Dodawanie klas wyspecjalizowanych upraszcza wygenerowanego kodu.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać klas wyspecjalizowanych dostępu formantu do

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT_CodeGen")

1. Implementuje klasę, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> i dodać do kolekcji właściwości wyszukiwania w Konstruktorze typu formantu.

1. Implementowanie właściwości niestandardowych formantu jako właściwości klasy.

1. Zastąpienie dostawcy właściwości <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodę, aby zwracany typ nową klasę dla krzywej formantów podrzędnych legendy.

1. Zastąpienie dostawcy właściwości <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodę, aby zwracany typ metody PropertyNames nowej klasy.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Obsługuje akcje obsługujący zamiar zaimplementowanie filtr akcji

 Visual Studio rejestruje testu, umożliwia przechwytywanie każdego zdarzenia myszy i klawiatury. Jednak w niektórych przypadkach celem akcji może zostać utracone w serie zdarzeń myszy i klawiatury. Na przykład jeśli formant obsługuje autouzupełniania, ten sam zestaw zdarzeń myszy i klawiatury może powodować innej wartości podczas testu odtwarzania w innym środowisku. Można dodać filtr akcji wtyczki zastępujący serie zdarzeń klawiatury i myszy z jednej akcji. W ten sposób można zastąpić serie zdarzeń myszy i klawiatury, które wybierz wartość z jednej akcji, która ustawia wartości. Które chroni kodowane testy interfejsu użytkownika z różnic w funkcji autocomplete z jednego środowiska do innego.

### <a name="to-support-intent-aware-actions"></a>Do obsługi obsługujący celem akcji

![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT_Actions")

1. Implementuje klasę filtru akcji, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, zastępowanie właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> i <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.

1. Zastąpienie <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. W tym przykładzie zastępuje akcji kliknij dwukrotnie działanie jednego kliknięcia.

1. Dodaj filtr akcji do <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> metody pakietu rozszerzenia.

1. Skompiluj Twoje pliki binarne i skopiuj je do %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> Filtr akcji nie zależy od implementacji dostępności ani właściwości dostawcy.

## <a name="debug-your-property-provider-or-action-filter"></a>Filtr akcji lub dostawcy właściwości debugowania

Filtr akcji i dostawcy właściwości są implementowane w pakiecie rozszerzenia. Konstruktor testu uruchamia pakiet rozszerzenia w oddzielnych procesach z aplikacji.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować właściwości filtru akcji lub dostawcy

1.  Tworzenie kopii pakietu rozszerzenia biblioteki DLL wersji do debugowania i .pdb, pliki do %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

2.  Uruchom aplikację (nie w debugerze).

3.  Uruchamianie kodowanego testu interfejsu użytkownika.

     `codedUITestBuilder.exe  /standalone`

4.  Dołącz debuger do procesu codedUITestBuilder.

5.  Ustaw punkty przerwania w kodzie.

6.  W Konstruktorze kodowanego testu interfejsu użytkownika, należy utworzyć potwierdzeń wykonywania dostawcy właściwości i rejestrowanie akcji do wykonywania filtrów akcji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.AccessibleObject>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)