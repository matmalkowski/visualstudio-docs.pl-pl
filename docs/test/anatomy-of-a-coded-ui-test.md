---
title: "Anatomia kodowanego testu interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: coded UI tests
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c449c0e23fa3effa693059ed6d0b6c4a61b8470c
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomia kodowanego testu interfejsu użytkownika

Podczas tworzenia kodowanego testu interfejsu użytkownika w projekcie kodowanego testu interfejsu użytkownika kilka pliki zostaną dodane do rozwiązania. W tym temacie użyjemy przykład kodowany Test interfejsu użytkownika do eksplorowania tych plików.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="contents-of-a-coded-ui-test"></a>Zawartość kodowanego testu interfejsu użytkownika  
 Podczas tworzenia kodowanego testu interfejsu użytkownika, **konstruktora testu kodowanego interfejsu użytkownika** tworzy mapę interfejsu użytkownika w obszarze testu i również metody testowe, parametrów i potwierdzenia dla wszystkich testów. Tworzy plik klasy dla każdego z testów.  
  
|Plik|Spis treści|Można edytować?|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Sekcja deklaracji](#UIMapDesignerFile)<br /><br /> [Klasa UIMap](#UIMapClass) (częściowe, generowane automatycznie)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Właściwości](#UIMapProperties)|Nie|  
|[UIMap.cs](#UIMapCS)|[Klasa UIMap](#UIMapCS) (częściowe)|Tak|  
|[CodedUITest1.cs](#CodedUITestCS)|[Klasa CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Właściwości](#CodedUITestProperties)|Tak|  
|[UIMap.uitest](#UIMapuitest)|Mapa XML interfejsu użytkownika dla testu.|Nie|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Ten plik zawiera kod, który jest automatycznie tworzony przez **konstruktora testu kodowanego interfejsu użytkownika** po utworzeniu testu. Ten plik ponownie jest tworzony zawsze zmienia testu, dzięki czemu nie jest plik, w którym można dodać lub zmodyfikować kod.  
  
#### <a name="declarations-section"></a>Sekcja deklaracji  
 Ta sekcja zawiera następujące deklaracje dla interfejsu użytkownika systemu Windows.  
  
```csharp  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> Przestrzeni nazw jest on dołączony do interfejsu użytkownika (UI) systemu Windows. Strony sieci Web interfejsu użytkownika będzie przestrzeń nazw <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; dla systemu Windows Presentation Foundation interfejsu użytkownika, będzie przestrzeń nazw <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.  
  
####  <a name="UIMapClass"></a>Klasa UIMap  
 W następnej sekcji pliku jest <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy.  
  
```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```
  
Kod klasy rozpoczyna się od <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> do klasy, która jest zadeklarowany jako częściowy klasy zastosowano. Można zauważyć, że atrybut jest również zastosowane do każdej klasy w tym pliku. Plik, który może zawierać więcej kodu dla tej klasy jest `UIMap.cs`, która została omówiona później.  

Wygenerowany `UIMap` klasy zawiera kod dla każdej metody, która została określona podczas testu została zarejestrowana.  

```csharp
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```

Ta część <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasa zawiera także wygenerowany kod dla każdej właściwości, który jest wymagany przez metody.

```csharp
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```
  
#####  <a name="UIMapMethods"></a>Metody do UIMap  
 Każda metoda ma podobną strukturę `AddItems()` metody. To jest szczegółowo w kodem, które są prezentowane wraz z podziały wierszy można dodać przejrzystości.

```csharp
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}
```

Podsumowanie komentarz dla każdej definicji metody informuje która klasa na potrzeby wartości parametrów dla tej metody. W takim przypadku jest `AddItemsParams` klasy, która jest zdefiniowana później w `UIMap.cs` plików i która jest również typ wartości, który jest zwracany przez `AddItemsParams` właściwości.  
  
 W górnej części metody kod jest `Variable Declarations` obiekty regionu, który definiuje zmienne lokalne interfejsu użytkownika, który będzie używany przez metodę.  
  
 W przypadku tej metody zarówno `UIItemWindow` i `UIItemEdit` właściwości, które są dostępne za pomocą `UICalculatorWindow` klasy, która jest zdefiniowana później w `UIMap.cs` pliku.  
  
 Następnie są wiersze, które wysyłanie tekstu z klawiatury do Kalkulatora aplikacji przy użyciu właściwości `AddItemsParams` obiektu.  
  
 `VerifyTotal()` Metoda ma bardzo podobne strukturę i zawiera następujący kod potwierdzenia.  

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```

 Nazwa pola tekstowego jest wymienione jako nieznane, ponieważ Deweloper aplikacji Kalkulator systemu Windows nie dostarczył nazwę publicznie dostępnych dla formantu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> Metody zakończy się niepowodzeniem, gdy rzeczywista wartość nie jest równa oczekiwanej wartości, które mogłyby spowodować niepowodzenie testu. Także zauważyć, że wartość oczekiwana zawiera dziesiętnym, w którym następuje spacja. Jeśli masz jakikolwiek modyfikowanie funkcji wdrażanych tego konkretnego testu, musisz zezwolić na dla tego punktu dziesiętnego i miejsce.  
  
#####  <a name="UIMapProperties"></a>Właściwości UIMap  
 Kod dla każdej właściwości jest również bardzo standardowe w klasie. Poniższy kod dla `AddItemsParams` właściwość jest używana w `AddItems()` metody.  
  
```csharp
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}
```

 Powiadomienie, że właściwość używa prywatnego zmiennej lokalnej o nazwie `mAddItemsParams` do przechowywania wartości przed zwraca go. Nazwa właściwości i nazwa klasy dla obiekt, który zwraca są takie same. Klasa jest zdefiniowana później w `UIMap.cs` pliku.  
  
 Każda klasa, która jest zwracana przez właściwość jest strukturę podobną. Poniżej przedstawiono `AddItemsParams` klasy.  

```csharp
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}
```

W przypadku wszystkich klas `UIMap.cs` pliku, ta klasa rozpoczyna się od <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. W tej klasie małych jest `Fields` region, który definiuje ciągi do użycia jako parametry <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> metodę, która jest używana w `UIMap.AddItems()` metodę, która została omówiona wcześniej. Można napisać kod, aby zastąpić wartości w polach ciąg przed wywołaniem metody, w którym są używane te parametry.  

###  <a name="UIMapCS"></a> UIMap.cs  
 Domyślnie ten plik zawiera częściowym `UIMap` klasy, która nie ma metody ani właściwości.  
  
#### <a name="uimap-class"></a>Klasa UIMap  
 Jest to, gdzie można utworzyć niestandardowy kod, aby rozszerzyć funkcjonalność programu <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy. Kod, który można utworzyć w tym pliku nie zostanie wygenerowana ponownie przez **konstruktora testu kodowanego interfejsu użytkownika** zawsze zmodyfikowanego testu.  
  
 Wszystkie części <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> można użyć metod i właściwości z inną część <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy.  
  
###  <a name="CodedUITestCS"></a>CodedUITest1.cs  
 Ten plik został wygenerowany przez **konstruktora testu kodowanego interfejsu użytkownika**, ale nie zostanie ponownie utworzony zawsze zmodyfikowanego testu, dzięki czemu można zmodyfikować kod w tym pliku. Nazwa pliku jest generowany na podstawie nazwy, określony dla testu podczas jego tworzenia.  
  
#### <a name="codeduitest1-class"></a>Klasa CodedUITest1

Domyślnie ten plik zawiera definicję tylko jedną klasę.

```csharp
[CodedUITest]  
public class CodedUITest1  
```

<xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute> Jest automatycznie stosowane do klasy, która umożliwia testowanie platformę, by go rozpoznać jako rozszerzenia testowania. Także zauważyć, że nie jest klasy częściowej. Cały kod klasy znajduje się w tym pliku.  
  
#####  <a name="CodedUITestProperties"></a>Właściwości CodedUITest1  
 Klasa zawiera dwie właściwości domyślne, które znajdują się w dolnej części pliku. Nie należy modyfikować.  
  
```csharp
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```
  
#####  <a name="CodedUITestMethods"></a>Metody CodedUITest1  
 Domyślnie klasa zawiera tylko jedna metoda.  

```csharp
public void CodedUITestMethod1()  
```

 Ta metoda wywołuje każdą `UIMap` metody określonej zostały zarejestrowane testu jest opisany w sekcji na [UIMap klasy](#UIMapClass).  
  
 Region, który jest zatytułowany `Additional test attributes`, jeśli odkomentowana, zawiera dwie metody opcjonalne.  
  
```csharp
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}
```

 `MyTestInitialize()` Metoda ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> zastosować dla niego, informujące framework testowych, aby wywołać tę metodę przed wszystkie inne metody. Podobnie `MyTestCleanup()` metoda ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> zastosować dla niego, która informuje framework testowych, aby wywołać tę metodę po wszystkich innych metod testu zostać wywołany. Korzystanie z tych metod jest opcjonalne. Dla tego testu `UIMap.LaunchCalculator()` metoda może być wywoływana z `MyTestInitialize()` i `UIMap.CloseCalculator()` metoda może być wywoływana z `MyTestCleanup()` zamiast z `CodedUITest1Method1()`.  
  
 Jeśli dodasz więcej metod do tej klasy za pomocą <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, testowania platforma wywoła każdej metody w ramach testu.  
  
###  <a name="UIMapuitest"></a> UIMap.uitest  
 Jest to plik XML, że reprezentuje strukturę kodowanego interfejsu użytkownika testu rejestrowania i jego części. Obejmują one akcje i klasy oprócz tych metod i właściwości tych klas. [UIMap.Designer.cs](#UIMapDesignerFile) plik zawiera kod, który został wygenerowany przez konstruktora kodowanego interfejsu użytkownika, aby odtworzyć struktury testu i udostępnia połączenie do testowania framework.  
  
 `UIMap.uitest` Plik nie jest bezpośrednio można edytować. Jednak można użyć konstruktora kodowanego interfejsu użytkownika można zmodyfikować test, który automatycznie zmienia `UIMap.uitest` pliku i [UIMap.Designer.cs](#UIMapDesignerFile) pliku.  
  
## <a name="see-also"></a>Zobacz także

<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
<xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
[Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)   
[Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)   
[Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)   
[Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
