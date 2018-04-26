---
title: Wskazówki analizowanie zarządzanego kodu pod względem wad kodu | Dokumentacja firmy Microsoft
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bb13e88e07741327088e8d138dfcf8b92a9075a6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Wskazówki: Analizowanie zarządzanego kodu dla kodu usterki

W tym przewodniku będziesz analizowanie zarządzanego projektu pod względem wad kodu za pomocą narzędzie do analizy kodu.

Ten przewodnik zawiera kroki procesu za pomocą analizy kodu do analizowania ponownie zestawy kod zarządzany .NET dla zgodności z wytycznymi projektowania Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Tworzenie biblioteki klas

### <a name="to-create-a-class-library"></a>Do tworzenia biblioteki klas

1. Na **pliku** menu, wybierz **nowy** > **projektu...** .

1. W **nowy projekt** okna dialogowego rozwiń **zainstalowana** > **Visual C#**, a następnie wybierz pozycję **klasycznego pulpitu systemu Windows**.

1. Wybierz **biblioteki klas (.NET Framework)** szablonu.

1. W **nazwa** polu tekstowym **CodeAnalysisManagedDemo** , a następnie kliknij przycisk **OK**.

1. Po utworzeniu projektu otwórz *Class1.cs* pliku.

1. Zastąp istniejący tekst w Class1.cs następujący kod:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Zapisz plik Class1.cs.

## <a name="analyze-the-project"></a>Analizowanie projektu

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Do analizowania zarządzanego projektu pod względem wad kodu

1. Wybierz projekt CodeAnalysisManagedDemo **Eksploratora rozwiązań**.

1. Na **projektu** menu, kliknij przycisk **właściwości**.

     Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.

1. Wybierz **analizy kodu** kartę.

1. Upewnij się, że **Włącz analizę kodu podczas kompilacji** jest zaznaczony.

1. Z **Uruchom ten zestaw reguł** listy rozwijanej wybierz **Microsoft wszystkie reguły**.

1. Na **pliku** menu, kliknij przycisk **zapisać wybrane elementy**, a następnie zamknij na stronach właściwości.

1. Na **kompilacji** menu, kliknij przycisk **kompilacji CodeAnalysisManagedDemo**.

    Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są wyświetlane w **listy błędów** i **dane wyjściowe** systemu windows.

## <a name="correct-the-code-analysis-issues"></a>Rozwiąż problemy dotyczące analizy kodu

### <a name="to-correct-code-analysis-rule-violations"></a>Aby rozwiązać naruszeń reguł analizy kodu

1. Na **widoku** menu, wybierz **listy błędów**.

    W zależności od wybranego profilu deweloper może być konieczne wskaż **inne okna** na **widoku** menu, a następnie wybierz pozycję **listy błędów**.

1. W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**.

1. Rozwiń węzeł właściwości, a następnie otwórz *AssemblyInfo.cs* pliku.

1. Użyj następujących wskazówek, aby naprawić ostrzeżenia:

   [CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "pokaz" powinien być oznaczony atrybutem CLSCompliant, a jego wartość powinna mieć wartość true.

   1. Dodaj kod `using System;` w pliku AssemblyInfo.cs.

   1. Następnie dodaj kod `[assembly: CLSCompliant(true)]` na końcu pliku AssemblyInfo.cs.

   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: demo(String) publiczny

   1. Dodaj Konstruktor `public demo (String s) : base(s) { }` do klasy `demo`.

   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: Pokaz publiczny (ciąg, wyjątków)

   1. Dodaj Konstruktor `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.

   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: chronione pokaz (SerializationInfo, StreamingContext)

   1. Dodaj kod `using System.Runtime.Serialization;` na początku pliku Class1.cs.

   1. Następnie dodaj konstruktora `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementowanie standardowych konstruktorów wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: demo() publiczny

   1. Dodaj Konstruktor `public demo () : base() { }` do klasy `demo` **.**

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w nazwie przestrzeni nazw "testCode" przez zmianę na "TestCode".

   1. Zmień wielkość liter w przestrzeni nazw `testCode` do `TestCode`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie nazwy typu "pokaz" przez zmianę na "Pokaz".

   1. Zmień nazwę elementu członkowskiego do `Demo`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w nazwie elementu członkowskiego "elementu" przez zmianę na "Item".

   1. Zmień nazwę elementu członkowskiego do `Item`.

   [CA1710: Identyfikatory powinny mieć poprawny przyrostek](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Zmień nazwę "testCode.demo" do końca w "Wyjątek".

   1. Zmień nazwę klasy i jej konstruktorów `DemoException`.

   [CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Podpisz "CodeAnalysisManagedDemo" przy użyciu klucza silnej nazwy.

   1. Na **projektu** menu, wybierz **CodeAnalysisManagedDemo właściwości**.

      Właściwości projektu są wyświetlane.

   1. Wybierz **podpisywanie** kartę.

   1. Wybierz **Podpisz zestaw** pole wyboru.

   1. W **wybierz plik klucza o nazwie ciąg** listy, wybierz  **\<nowy... >**.

      **Tworzenie silnej nazwy klucza** zostanie wyświetlone okno dialogowe.

   1. W **nazwę pliku klucza**, wpisz TestKey.

   1. Wprowadź hasło, a następnie wybierz pozycję **OK**.

   1. Na **pliku** menu, wybierz **zapisać wybrane elementy**, a następnie zamknij strony właściwości.

   [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Dodaj atrybut [Serializable] na typ "demonstracją", ponieważ ten typ implementuje interfejs ISerializable.

   1. Dodaj `[Serializable ()]` do klasy atrybutu `demo`.

   Po zakończeniu zmiany pliku Class1.cs powinna wyglądać następująco:

   ```csharp
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

1. Skompiluj ponownie projekt.

## <a name="exclude-code-analysis-warnings"></a>Wyklucz ostrzeżenia analizy kodu

### <a name="to-exclude-code-defect-warnings"></a>Aby wyłączyć ostrzeżenia wad kodu

1. Dla każdego z pozostałych ostrzeżeń wykonaj następujące czynności:

    1. Wybrać ostrzeżenie w **listy błędów**.

    1. Z menu kliknij prawym przyciskiem myszy lub kontekstu wybierz **Pomiń** > **w pliku pominięć**.

1. Skompiluj ponownie projekt.

     Tworzy projekt bez żadnych ostrzeżeń ani błędów.

## <a name="see-also"></a>Zobacz także

[Analiza kodu dla zarządzanego kodu](../code-quality/code-analysis-for-managed-code-overview.md)