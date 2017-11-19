---
title: "Wskazówki: Analizowanie zarządzanego kodu pod względem wad kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3dd0c93476e646895362b98c2f62b569d87ffe35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Wskazówki: analizowanie zarządzanego kodu pod względem wad kodu
W tym przewodniku można analizować zarządzanego projektu pod względem wad kodu za pomocą narzędzie do analizy kodu.  
  
 W tym przewodniku będzie kroków procesu do analizowania ponownie zestawy kod zarządzany .NET dla zgodności z wytycznymi dla programu Microsoft .NET Framework projektu za pomocą analizy kodu.  
  
 W tym przewodniku możesz:  
  
-   Analizowanie i popraw ostrzeżenia wad kodu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Tworzenie biblioteki klas  
  
#### <a name="to-create-a-class-library"></a>Do tworzenia biblioteki klas  
  
1.  Na **pliku** menu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], kliknij przycisk **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **typów projektów**, kliknij przycisk **Visual C#**.  
  
3.  W obszarze **szablony**, wybierz pozycję **biblioteki klas**.  
  
4.  W **nazwa** polu tekstowym **CodeAnalysisManagedDemo** , a następnie kliknij przycisk **OK**.  
  
5.  Po utworzeniu projektu, otwórz plik Class1.cs.  
  
6.  Zastąp istniejący tekst w Class1.cs następujący kod:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Zapisz plik Class1.cs.  
  
## <a name="analyze-the-project"></a>Analizowanie projektu  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Do analizowania zarządzanego projektu pod względem wad kodu  
  
1.  Wybierz projekt CodeAnalysisManagedDemo **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.  
  
3.  Kliknij przycisk **analizy kodu**.  
  
4.  Upewnij się, że **Włącz analizę kodu podczas kompilacji (definiuje stała CODE_ANALYSIS**) jest zaznaczone.  
  
5.  Z **Uruchom ten zestaw reguł** listy rozwijanej wybierz **Microsoft wszystkie reguły**.  
  
6.  Na **pliku** menu, kliknij przycisk **zapisać wybrane elementy**, a następnie zamknij ManagedDemo strony właściwości.  
  
7.  Na **kompilacji** menu, kliknij przycisk **kompilacji ManagedDemo**.  
  
     Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są raportowane w **analizy kodu** i **dane wyjściowe** systemu windows.  
  
     Jeśli **analizy kodu** okno nie ma, na **Analizuj** menu, wybierz **Windows** , a następnie **wybierz analizy kodu**.  
  
## <a name="correct-the-code-analysis-issues"></a>Rozwiąż problemy dotyczące analizy kodu  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Aby rozwiązać naruszeń reguł analizy kodu  
  
1.  Na **widoku** menu, kliknij przycisk **listy błędów**.  
  
     W zależności od wybranego profilu deweloper może być konieczne wskaż **inne okna** na **widoku** menu, a następnie kliknij przycisk **listy błędów**.  
  
2.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.  
  
3.  Następnie rozwiń węzeł właściwości, a następnie otwórz plik AssemblyInfo.cs.  
  
4.  Popraw ostrzeżenia, należy wykonać następujące kroki:  
  
-   [CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "pokaz" powinien być oznaczony atrybutem CLSCompliant, a jego wartość powinna mieć wartość true.  
  
    -   Dodaj kod `using``System;` w pliku AssemblyInfo.cs.  
  
         Następnie dodaj kod `[assembly: CLSCompliant(true)]` na końcu pliku AssemblyInfo.cs.  
  
         Skompiluj ponownie projekt.  
  
-   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: demo(String) publiczny  
  
    -   Dodaj Konstruktor `public demo (String s) : base(s) { }` do klasy `demo`.  
  
-   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: Pokaz publiczny (ciąg, wyjątków)  
  
    -   Dodaj Konstruktor `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.  
  
-   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: chronione pokaz (SerializationInfo, StreamingContext)  
  
    -   Dodaj kod `using System.Runtime.Serialization;` na początku pliku Class1.cs.  
  
         Następnie dodaj konstruktora`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Skompiluj ponownie projekt.  
  
-   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: demo() publiczny  
  
    -   Dodaj Konstruktor `public demo () : base() { }` do klasy `demo` **.**  
  
         Skompiluj ponownie projekt.  
  
-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w nazwie przestrzeni nazw "testCode" przez zmianę na "TestCode".  
  
    -   Zmień wielkość liter w przestrzeni nazw `testCode` do `TestCode`.  
  
-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie nazwy typu "pokaz" przez zmianę na "Pokaz".  
  
    -   Zmień nazwę elementu członkowskiego do `Demo`.  
  
-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w nazwie elementu członkowskiego "elementu" przez zmianę na "Item".  
  
    -   Zmień nazwę elementu członkowskiego do `Item`.  
  
-   [CA1710: Identyfikatory powinny mieć poprawny przyrostek](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Zmień nazwę "testCode.demo" do końca w "Wyjątek".  
  
    -   Zmień nazwę klasy i jej konstruktorów `DemoException`.  
  
-   [CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Podpisz "ManagedDemo" przy użyciu klucza silnej nazwy.  
  
    -   Na **projektu** menu, kliknij przycisk **ManagedDemo właściwości**.  
  
         Właściwości projektu są wyświetlane.  
  
         Kliknij przycisk **podpisywania**.  
  
         Wybierz **Podpisz zestaw** pole wyboru.  
  
         W **wybierz plik klucza o nazwie ciąg** listy, wybierz  **\<nowy... >**.  
  
         **Tworzenie silnej nazwy klucza** zostanie wyświetlone okno dialogowe.  
  
         W **nazwę pliku klucza**, wpisz TestKey.  
  
         Wprowadź hasło, a następnie kliknij przycisk **OK**.  
  
         Na **pliku** menu, kliknij przycisk **zapisać wybrane elementy**, a następnie zamknij strony właściwości.  
  
         Skompiluj ponownie projekt.  
  
-   [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Dodaj atrybut [Serializable] na typ "demonstracją", ponieważ ten typ implementuje interfejs ISerializable.  
  
    -   Dodaj `[Serializable ()]` do klasy atrybutu `demo`.  
  
         Skompiluj ponownie projekt.  
  
 Po zakończeniu zmiany pliku Class1.cs powinna wyglądać następująco:  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>Wyklucz ostrzeżenia analizy kodu  
  
#### <a name="to-exclude-code-defect-warnings"></a>Aby wyłączyć ostrzeżenia wad kodu  
  
1.  Dla każdego z pozostałych ostrzeżeń wykonaj następujące czynności:  
  
    1.  W oknie analizy kodu Wybierz ostrzeżenia.  
  
    2.  Wybierz **akcje**, a następnie wybierz **Pomiń komunikat**, a następnie wybierz pozycję **w pliku pominięć projektu**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: pomijanie ostrzeżeń przy użyciu elementu Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Skompiluj ponownie projekt.  
  
     Tworzy projekt bez żadnych ostrzeżeń ani błędów.