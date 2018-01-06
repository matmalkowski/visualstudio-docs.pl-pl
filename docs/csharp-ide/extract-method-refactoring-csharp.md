---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "Wyodrębnij metodę Refaktoryzacja (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>Refaktoryzacja wyodrębniania metody (C#)
**Wyodrębnij metodę** jest operacja refaktoryzacji, która zapewnia prosty sposób na utworzenie nowej metody z fragmentu kodu w istniejącego elementu członkowskiego.  
  
 Przy użyciu **Wyodrębnij metodę**, można utworzyć nowej metody wyodrębniając wybór kodu z wewnątrz bloku kodu istniejącego elementu członkowskiego. Zaznaczony kod zawiera nowe, wyodrębnionego — metoda i zaznaczony kod w istniejących element członkowski jest zastępowany wywołanie do nowej metody. Włączanie fragment kodu do własnej metody umożliwia szybkie i dokładnie zmianę kodu dla lepszej czytelności i ponowne użycie.  
  
 **Wyodrębnij metodę** ma następujące zalety:  
  
-   Zachęca praktyk kodowania najlepiej przez akcentowania metody dyskretnych, wielokrotnego użytku.  
  
-   Zachęca własnym dokumentowanie kodu za pośrednictwem dobrej organizacji.  
  
     Gdy nazw są używane, wysokiego poziomu metod można Dowiedz się więcej, takich jak szereg komentarze.  
  
-   Zachęca do tworzenia bardziej precyzyjną dopasowanymi metod, które upraszczają zastępowanie.  
  
-   Zmniejsza zduplikowania kodu.  
  
### <a name="to-use-extract-method"></a>Aby użyć Wyodrębnij metodę  
  
1.  Utwórz aplikację konsoli o nazwie `ExtractMethod`, a następnie zastąp `Program` z Poniższy przykładowy kod.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Wybierz fragment kodu, które mają zostać wyodrębnione:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Na **Refaktoryzuj** menu, kliknij przycisk **Wyodrębnij metodę**.  
  
     **Wyodrębnij metodę** zostanie wyświetlone okno dialogowe.  
  
     Alternatywnie możesz także wpisać skrótu klawiaturowego CTRL + R, M, aby wyświetlić **Wyodrębnij metodę** okno dialogowe.  
  
     Można również prawym przyciskiem myszy wybrane kodu, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **Wyodrębnij metodę** do wyświetlenia **Wyodrębnij metodę** okno dialogowe.  
  
4.  Określ nazwę nowej metody, takie jak `CircleArea`w **nową nazwę metody** pole.  
  
     Wyświetla podgląd nowego podpisu metody w obszarze **podpis metody podglądu**.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz **Wyodrębnij metodę** polecenie dodaje się nowa metoda Członkowskim źródła w tej samej klasy.  
  
## <a name="partial-types"></a>Typy częściowe  
 Jeśli klasa jest typu częściowego, następnie **Wyodrębnij metodę** generuje nowej metody bezpośrednio po element członkowski źródła. **Wyodrębnij metodę** Określa podpis nowej metody, tworząc metody statycznej, gdy żadne dane wystąpienia odwołuje się do niego kod w nowej metody.  
  
## <a name="generic-type-parameters"></a>Parametry typu ogólnego  
 Podczas wyodrębniania metody, która ma parametr typu ogólnego nieograniczonego wygenerowanego kodu nie dodają `ref` modyfikator do tego parametru, chyba że wartość jest do niego przypisany. Jeśli wyodrębnionej metody będzie obsługiwać typy referencyjne jako argumentu typu ogólnego, należy ręcznie dodać `ref` modyfikator parametru w podpisie metody.  
  
## <a name="anonymous-methods"></a>Metody anonimowe  
 Jeśli spróbujesz wyodrębnić część metody anonimowej, która zawiera odwołanie do zmiennej lokalnej, która jest zadeklarowana lub odwołuje się do poza metodą anonimową, następnie Visual Studio ostrzeżenie o potencjalnych zmiany semantycznego.  
  
 Gdy metody anonimowej używa wartości zmiennej lokalnej, wartość jest uzyskiwana w momencie utworzenia metody anonimowej jest wykonywana. Gdy metody anonimowej zostanie wyodrębniony do innej metody, wartość zmiennej lokalnej jest uzyskiwana w momencie wywołania do wyodrębnionej metody.  
  
 Poniższy przykład przedstawia tę zmianę semantycznego. Jeśli ten kod jest wykonywane, następnie **11** będą wypisywane w konsoli. Jeśli używasz **Wyodrębnij metodę** do wyodrębniania region kodu, który został oznaczony przez komentarze w kodzie do własnej metody i następnie wykonać kod refactored, **10** będą wypisywane w konsoli.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Aby obejść ten problem, należy zmienne lokalne, które są używane w polach metody anonimowej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](refactoring-csharp.md)