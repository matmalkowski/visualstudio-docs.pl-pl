---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: Hermetyzuj pole Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d587edebcea443e0bfff52004b128c70923470d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Refaktoryzacja hermetyzowania pola (C#)
**Hermetyzuj pole** operacja refaktoryzacji umożliwia szybkie tworzenie właściwości z istniejącego pola, a następnie bezproblemowo zaktualizuj swój kod z odwołaniami do nowej właściwości.  
  
 Gdy [pola](/dotnet/csharp/programming-guide/classes-and-structs/fields) jest [publicznych](/dotnet/csharp/language-reference/keywords/public), inne obiekty ma bezpośredni dostęp do tego pola i można ją zmodyfikować, niewykryte przez obiekt, który jest właścicielem tego pola. Za pomocą [właściwości](/dotnet/csharp/programming-guide/classes-and-structs/properties) celu hermetyzacji tego pola, można uniemożliwić bezpośredni dostęp do pola.  
  
 Aby utworzyć nową właściwość **Hermetyzuj pole** operację zmiany modyfikator dostępu do pola, które chcesz Hermetyzowanie do [prywatnej](/dotnet/csharp/language-reference/keywords/private), a następnie generuje [uzyskać](/dotnet/csharp/language-reference/keywords/get)i [ustawić](/dotnet/csharp/language-reference/keywords/set) metody dostępu dla tego pola. W niektórych przypadkach tylko `get` metody dostępu jest generowany, np. Jeśli pole jest zadeklarowany jako tylko do odczytu.  
  
 Aparat refaktoryzacji aktualizuje kodu z odwołaniami do nowej właściwości w obszarów określona w **odwołuje się do aktualizacji** sekcji **Hermetyzuj pole** okno dialogowe.  
  
### <a name="to-create-a-property-from-a-field"></a>Aby utworzyć właściwość z polem  
  
1.  Utwórz aplikację konsoli o nazwie `EncapsulateFieldExample`, a następnie zastąp `Program` z Poniższy przykładowy kod.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  W [edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md), umieść kursor w deklaracji, nazwy pola, które chcesz Hermetyzuj. W poniższym przykładzie, umieść kursor na wyraz `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Na **Refaktoryzuj** menu, kliknij przycisk **Hermetyzuj pole**.  
  
     **Hermetyzuj pole** zostanie wyświetlone okno dialogowe.  
  
     Możesz także wpisać skrótu klawiaturowego CTRL + R, E, aby wyświetlić **Hermetyzuj pole** okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy kursora, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **Hermetyzuj pole** do wyświetlenia **Hermetyzuj pole** okno dialogowe.  
  
4.  Określ ustawienia.  
  
5.  Naciśnij klawisz ENTER lub kliknij przycisk **OK** przycisku.  
  
6.  W przypadku wybrania **podgląd zmian odwołanie** opcji, a następnie **podgląd zmian odwołanie** zostanie otwarte okno. Kliknij przycisk **Zastosuj** przycisku.  
  
     Następujące `get` i `set` kod dostępu jest wyświetlany w pliku źródłowego:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Kod w `Main` dodano także do nowej metody `Width` nazwy właściwości.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Uwagi  
 **Hermetyzuj pole** operacja jest możliwe tylko wtedy, gdy kursor znajduje się na tym samym wierszu co deklaracja pola.  
  
 Dla deklaracji, które deklaruje wielu pól **Hermetyzuj pole** używa przecinek jako granicę między polami i inicjuje refaktoryzacji na pole najbliższego kursor i na tym samym wierszu co kursora. Można również określić pole, które chcesz Hermetyzowanie wybierając nazwę tego pola w deklaracji.  
  
 Kod, który jest generowany przez tę operację refaktoryzacji jest formowana przez funkcję wstawki kodu hermetyzowania pola. Wstawki kodu są można modyfikować. Aby uzyskać więcej informacji, zobacz [wstawki kodu](../ide/visual-csharp-code-snippets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](refactoring-csharp.md)   
 [Fragmenty kodu Visual C#](../ide/visual-csharp-code-snippets.md)