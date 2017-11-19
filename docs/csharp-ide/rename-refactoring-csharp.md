---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: Refaktoryzacja zmiany nazwy (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eba5a9f55e5d3d08eee48dc083a7e2f848118162
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="rename-refactoring-c"></a>Refaktoryzacja zmiany nazwy (C#)
**Zmień nazwę** jest funkcją refaktoryzacji w Visual Studio zintegrowane środowisko programistyczne (IDE), która zapewnia łatwy sposób można zmienić nazwy identyfikatory symboli kodu, takich jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typów. **Zmień nazwę** może służyć do zmiany nazwy w komentarze i ciągi i zmienić deklaracje i wywołania identyfikatora.  
  
> [!NOTE]
>  Korzystając z kontroli źródła dla programu Visual Studio, należy pobrać najnowszą wersję źródeł przed podjęciem próby wykonania Refaktoryzacja zmiany nazwy.  
  
 Refaktoryzacja zmiany nazwy jest dostępne następujące funkcje programu Visual Studio:  
  
|Funkcja|Zachowanie refaktoryzacji w środowisku IDE|  
|-------------|----------------------------------------|  
|Edytor kodu|Refaktoryzacja zmiany nazwy jest dostępna w edytorze kodu, po umieszczeniu kursora na niektóre rodzaje symboli kodu. Gdy kursor znajduje się w tym miejscu, można wywołać **zmienić** polecenia, wpisując skrót klawiaturowy (Ctrl + R, Ctrl + R) lub wybierając **zmienić** szybkie akcje, w menu skrótów polecenie lub **Refaktoryzuj** menu.|  
|Widok klas|Po wybraniu identyfikatora w widoku klas Refaktoryzacja zmiany nazwy jest dostępne w menu skrótów i **Refaktoryzuj** menu.|  
|Przeglądarka obiektów|Po wybraniu identyfikatora w przeglądarce obiektów Refaktoryzacja zmiany nazwy jest dostępna wyłącznie z **Refaktoryzuj** menu.|  
|Siatki właściwości projektanta formularzy systemu Windows|W **siatki właściwości** projektanta formularzy systemu Windows, zmiana nazwy formantu zostanie zainicjowana operacja zmiany nazwy dla tego formantu. **Zmienić** nie zostanie wyświetlone okno dialogowe.|  
|Eksplorator rozwiązań|W **Eksploratora rozwiązań**, **zmienić** polecenie jest dostępne w menu skrótów. Jeśli plik wybrane źródło zawiera klasy, których nazwa klasy jest taka sama jak nazwa pliku, możesz użyć tego polecenia, jednocześnie zmienić nazwę pliku źródłowego i wykonać Refaktoryzacja zmiany nazwy.<br /><br /> Na przykład jeśli tworzenia domyślnej aplikacji opartych na systemie Windows, a następnie zmień nazwę pliku Form1.cs na TestForm.cs, nazwa pliku źródłowego pliku Form1.cs zostanie zmieniony na TestForm.cs i klasa Form1 i wszystkie odwołania do czy klasa zostanie zmieniona na TestForm. **Uwaga:** **Cofnij** polecenia (CTRL + Z) będziesz tylko cofnąć Refaktoryzacja zmiany nazwy w kodzie, a nie Zmień nazwę pliku z powrotem do oryginalnej nazwy. <br /><br /> Jeśli plik wybrane źródło nie zawiera klasy, których nazwa jest taka sama jak nazwa pliku **zmienić** w **Eksploratora rozwiązań** tylko spowoduje zmianę nazwy pliku źródłowego i nie zostanie wykonany, Zmień nazwę refaktoryzacji.|  
  
## <a name="rename-operations"></a>Zmień nazwę operacji  
 Podczas wykonywania **zmienić**, aparat refaktoryzacji wykonuje określonej operacji zmiany nazwy dla każdego symbolu kodu, zgodnie z opisem w poniższej tabeli.  
  
|Symbol w kodzie|Zmień nazwę operacji|  
|-----------------|----------------------|  
|Pole|Zmienia deklaracji i użycia pola na nową nazwę.|  
|Zmienna lokalna|Zmienia deklaracji i użycia zmiennej na nową nazwę.|  
|Metoda|Zmienia nazwę metody i wszystkie odwołania do tej metody na nową nazwę. **Uwaga:** podczas zmiany nazwy metody rozszerzenia operacji zmiany nazwy propaguje do wszystkich wystąpień metody, które znajdują się w zakresie, niezależnie od tego, czy metoda rozszerzenia jest używany jako metodą statyczną lub metodą wystąpienia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Przestrzeń nazw|Zmienia nazwę przestrzeni nazw na nową nazwę w deklaracji, wszystkie `using` instrukcje i w pełni kwalifikowane nazwy. **Uwaga:** przy zmianie nazwy przestrzeni nazw, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aktualizuje również **domyślne Namespace** właściwość **aplikacji** strony **projektanta projektu**. Nie można zresetować tej właściwości, wybierając **Cofnij** z **Edytuj** menu. Aby zresetować **domyślne Namespace** wartość właściwości, należy zmodyfikować właściwości w **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [strony aplikacji](../ide/reference/application-page-project-designer-csharp.md).|  
|Właściwość|Zmienia deklaracji i użycia właściwości na nową nazwę.|  
|Typ|Zmienia wszystkie deklaracje i wszystkie ich użycia typu na nową nazwę, w tym konstruktory i destruktory. Dla typów częściowych operacji zmiany nazwy zostaną przeniesione na wszystkie części.|  
  
#### <a name="to-rename-an-identifier"></a>Aby zmienić nazwę identyfikatora  
  
1.  Utwórz aplikację konsoli o nazwie `RenameIdentifier`, a następnie zastąp `Program` z Poniższy przykładowy kod.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Umieść kursor na `MethodB`, albo w deklaracji metody lub wywołanie metody.  
  
3.  Z **Refaktoryzuj** menu, wybierz opcję **zmienić**. **Zmienić** zostanie wyświetlone okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy kursora, wskaż polecenie **Refaktoryzuj** w menu kontekstowym, a następnie kliknij przycisk **Zmień nazwę** do wyświetlenia **zmienić** okno dialogowe.  
  
4.  W **nową nazwę** wpisz `MethodC`.  
  
5.  Wybierz **wyszukiwania w komentarzach** pole wyboru.  
  
6.  Kliknij przycisk **OK**.  
  
7.  W **podgląd zmian** okno dialogowe, kliknij przycisk **Zastosuj**.  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>Aby zmienić nazwę identyfikatora przy użyciu szybkie akcje  
  
1.  Utwórz aplikację konsoli o nazwie `RenameIdentifier`, a następnie zastąp `Program` z Poniższy przykładowy kod.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  W deklaracji `MethodB`, wpisz lub backspace przez identyfikator metody. Szybkie akcje żarówka pojawi się na marginesie.  
  
    > [!NOTE]
    >  Można tylko wywołać Refaktoryzacja zmiany nazwy przy użyciu szybkie akcje w deklaracji identyfikatora.  
  
3.  Wpisz skrót klawiaturowy **Shift + Alt + F10** do wyświetlenia menu Szybkie akcje.  
  
     —lub—  
  
     Kliknij czarny trójkąt obok żarówkę, aby wyświetlić menu Szybkie akcje.  
  
4.  Wybierz **Zmień nazwę "\<identifer1 >" do "\<identifier2 >"** element menu do wywołania Refaktoryzacja zmiany nazwy. Wszystkie odwołania do  **\<identifer1 >** zostaną automatycznie zaktualizowane do  **\<identifier2 >**.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="renaming-implemented-or-overridden-members"></a>Zmiana nazwy zaimplementowana lub przesłoniętych elementów członkowskich  
 Gdy możesz **Zmień nazwę** elementu członkowskiego, który implementuje/zastąpienia lub jest zaimplementowana/zastąpione elementów członkowskich w innych typach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Wyświetla okno dialogowe z informacją kaskadowych aktualizacji spowoduje, że operacja zmiany nazwy. Jeśli klikniesz przycisk **Kontynuuj**, refaktoryzacji rekursywnie aparat wyszukuje i zmienia jego nazwę, wszystkie elementy członkowskie w podstawowym i typów pochodnych, które mają implementuje/zastąpień relacje z elementem członkowskim zmieniana.  
  
 Poniższy przykład kodu zawiera elementy członkowskie z relacjami implementuje/zastąpień.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 W poprzednim przykładzie zmiana nazwy `C.Method()` również zmienia nazwę `Ibase.Method()` ponieważ `C.Method()` implementuje `Ibase.Method()`. Następnie rekursywnie aparat zrefaktoryzuj widzi, że `Ibase.Method()` jest implementowany przez `Derived.Method()` i zmienia nazwę `Derived.Method()`. Aparat refaktoryzacji nie zmienia nazwy `Base.Method()`, ponieważ `Derived.Method()` nie przesłania `Base.Method()`. Aparat refaktoryzacji zatrzymuje tutaj w przypadku braku **zmienić przeciążenia** zaewidencjonowany **zmienić** okno dialogowe.  
  
 Jeśli **zmienić przeciążenia** zaznaczono zmienia nazwę aparat zrefaktoryzuj `Derived.Method(int i)` ponieważ przeciąża `Derived.Method()`, `Base.Method(int i)` , ponieważ jest on przesłaniany przez `Derived.Method(int i)`, i `Base.Method()` ponieważ jest on przeciążenia `Base.Method(int i)`.  
  
> [!NOTE]
>  Podczas zmiany nazwy elementu członkowskiego, który został zdefiniowany w zestawie, okno dialogowe wyjaśniono, że zmiana nazwy spowoduje błędy kompilacji.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Zmiana nazwy właściwości typy anonimowe  
 Podczas zmiany nazwy właściwości typów anonimowych operacji zmiany nazwy zostaną przeniesione na właściwości innych typów anonimowych, które mają takie same właściwości. Poniższe przykłady przedstawiają to zachowanie.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 W poprzednim kodzie zmiana nazwy `ID` ulegnie zmianie `ID` w obu instrukcji "", ponieważ mają one ten sam typ anonimowy podstawowy.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 W powyższym kodzie zmiana nazwy `ID` tylko Zmień nazwę jednego wystąpienia `ID` ponieważ `companyIDs` i `orderIDs` nie mają tej samej właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](refactoring-csharp.md)   
 [Typy anonimowe](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)