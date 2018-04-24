---
title: 'CA2000: Usuwanie obiektów przed utratą zakresu'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 436dec37598aac31d0de2e7cb495f49b2a0bf41e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Usuwanie obiektów przed utratą zakresu
|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Obiekt lokalnego <xref:System.IDisposable> typ jest tworzony, ale obiekt nie jest usunięty, zanim wszystkie odwołania do obiektu będą poza zakresem.

## <a name="rule-description"></a>Opis reguły
 Jeśli możliwy do likwidacji obiekt nie zostanie jawnie zlikwidowany, zanim wszystkie odwołania do niego będą poza zakresem, obiekt zostanie zlikwidowany w nieokreślonym czasie gdy moduł garbage collector uruchomi finalizatora obiektu. Ponieważ może wystąpić zdarzenie wyjątku która uniemożliwi finalizatora obiektu z pracy, obiekt powinien zostać jawnie zlikwidowany zamiast tego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, należy wywołać <xref:System.IDisposable.Dispose%2A> na obiekcie, zanim wszystkie odwołania do niego będą poza zakresem.

 Należy pamiętać, że można użyć `using` instrukcji (`Using` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) do opakowywania obiektów implementujących `IDisposable`. Obiekty, które są ujęte w ten sposób zostanie usunięta automatycznie z końcem `using` bloku.

 Poniżej przedstawiono niektóre sytuacji, w którym za pomocą instrukcji nie wystarcza do ochrony IDisposable obiektów i może spowodować CA2000 występuje.

-   Zwracanie likwidacji obiekt wymaga konstruowania obiektu w bloku try/finally poza przy użyciu bloku.

-   Inicjowanie członkami likwidacji obiekt nie należy wykonywać w Konstruktorze przy użyciu instrukcji.

-   Zagnieżdżania konstruktorów, które są chronione tylko przez program obsługi wyjątku jeden. Na przykład

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     powoduje, że CA2000 występuje z powodu błędu w konstrukcji obiektu StreamReader może powodować obiektu FileStream nigdy nie zamknięte.

-   Obiekty dynamiczne powinien użyć obiektu cienia w celu implementować wzorzec Dispose interfejsu IDisposable obiektów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenie od tej reguły, chyba że wywołano metodę na nazwę obiektu, który wywołuje `Dispose`, takich jak <xref:System.IO.Stream.Close%2A>, lub metody wywoływane ostrzeżenia zwraca obiekt interfejsu IDisposable opakowuje obiektu.

## <a name="related-rules"></a>Powiązanych reguł
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Nie likwiduj obiektów wiele razy](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Przykład
 W przypadku wdrażania metodę, która zwraca obiekt jednorazowe umożliwia bloku try/finally bez bloku catch upewnij się, że obiekt jest usunięty. Za pomocą bloku try/finally, musisz zezwolić na wyjątki, aby być zgłaszany w momencie błędu i upewnij się, że dany obiekt jest usunięty.

 W metodzie OpenPort1 wywołania do otwarcia portu SerialPort obiektu ISerializable lub wywołanie SomeMethod może zakończyć się niepowodzeniem. Ostrzeżenie CA2000 jest wywoływane w tej implementacji.

 W metodzie OpenPort2 dwa obiekty portu SerialPort są zadeklarowane i należy ustawić wartość null:

-   `tempPort`, które używany do sprawdzania, czy operacje metody powiodło się.

-   `port`, który jest używany dla wartości zwracanej metody.

 `tempPort` Jest tworzony i otwierany `try` bloku oraz wszelkie inne wymagane praca jest wykonywana w tym samym `try` bloku. Na koniec `try` bloku otwartego portu jest przypisany do `port` obiektu, który zostanie zwrócony i `tempPort` obiektu ma ustawioną wartość `null`.

 `finally` Bloku sprawdza wartość `tempPort`. Jeśli nie jest zerowa, operacja w metodzie zakończyła się niepowodzeniem, i `tempPort` jest zamknięty, aby upewnić się, że wszystkie zasoby są wydawane. Obiekt zwrócony portu będzie zawierać otwarty obiekt portu SerialPort operacji metody zakończyło się powodzeniem, czy będzie ona mieć wartość null, jeśli operacja nie powiodła się.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>Przykład
 Domyślnie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora ma operatory arytmetyczne wszystkie sprawdzaj przepełnienie. W związku z tym może zgłosić żadnych operacji arytmetycznej Visual Basic <xref:System.OverflowException>. Może to prowadzić do nieoczekiwanych naruszeń w zasadach, takie jak CA2000. Na przykład następująca funkcja CreateReader1 spowoduje naruszenie CA2000, ponieważ kompilator Visual Basic jest emitowanie przepełnienie sprawdzanie instrukcji dodatku, który może wywoływać wyjątek spowodowałoby TextWriter nie można usunąć.

 Aby rozwiązać ten problem, można wyłączyć emitowanie sprawdzanie nadmiaru dla operacji przez kompilator Visual Basic w projekcie, lub zmodyfikować kod w następujących funkcji CreateReader2.

 Aby wyłączyć emitowanie sprawdzanie nadmiaru dla operacji, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **skompilować**, kliknij przycisk **zaawansowane opcje kompilacji**, a następnie sprawdź, **Wyłącz sprawdzanie przepełnienia całkowitych**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable> [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)