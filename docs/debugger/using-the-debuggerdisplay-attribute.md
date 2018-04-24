---
title: Za pomocą atrybutu DebuggerDisplay | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06a41f0843b33e1f73d9a2449fe954d8673350fc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="using-the-debuggerdisplay-attribute"></a>Za pomocą atrybutu DebuggerDisplay
[Debuggerdisplayattribute — klasa](/dotnet/api/system.diagnostics.debuggerdisplayattribute) Określa, jak obiekt, właściwość lub pole jest wyświetlany w oknach zmiennych debugera. Ten atrybut można stosować do typów delegatów, właściwości, pól i zestawów.  
  
 `DebuggerDisplay` Atrybut ma jeden argument jest ciąg mają być wyświetlane w kolumnie wartość dla wystąpienia typu. Ten ciąg może zawierać nawiasy klamrowe (`{` i `}`). Tekst w parę nawiasów klamrowych jest szacowana jako pola, właściwości lub metody.  
  
 Jeśli klasa została zastąpiona `ToString()` metoda, debuger używa przeciążonej zamiast domyślnej `{<typeName>}`. W związku z tym jeśli ma być zastąpiona `ToString()` metoda, debuger używa przeciążonej zamiast domyślnej`{<typeName>}`, i nie trzeba używać `DebuggerDisplay`. Jeśli używasz zarówno `DebuggerDisplay` atrybut ma pierwszeństwo przed przesłoniętych `ToString()` — metoda.  
  
 Określa, czy debuger ocenia tym niejawne `ToString()` wywołania zależy od ustawienia użytkownika w **narzędzia / Opcje / Debugowanie** okno dialogowe. Visual Basic nie implementuje tym niejawne `ToString()` oceny.  
  
> [!IMPORTANT]
>  Jeśli **Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych** jest zaznaczone pole wyboru w **narzędzia/Opcje / Debugowanie** okno dialogowe, a następnie `DebuggerDisplay` atrybut jest ignorowany.  
  
 W poniższej tabeli przedstawiono niektóre możliwości wykorzystania `DebuggerDisplay` atrybutu i przykładowe dane wyjściowe.  
  
|Atrybut|Dane wyjściowe w kolumnie wartość|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Na typu z polami `x` i `y`.|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`Składnia parametru może się różnić między językami. Dlatego należy używać go z rozwagą.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` można także zaakceptować parametrów nazwanych.  
  
|Parametry|Cel|  
|----------------|-------------|  
|`Name`, `Type`|Parametry te mają wpływ na **nazwa** i **typu** kolumny zmiennych systemu windows. (One można ustawić na ciągi, przy użyciu takiej samej składni co konstruktor.) Nadużywania parametrów lub ich użycie nieprawidłowo, może spowodować mylące danych wyjściowych.|  
|`Target`, `TargetTypeName`|Określa typ docelowy, gdy atrybut jest stosowany na poziomie zestawu.|  
  
 Plik autoexp.cs korzysta z atrybutu DebuggerDisplay na poziomie zestawu. Plik autoexp.cs Określa rozszerzenia domyślne używane przez program Visual Studio dla obiektów platformy .NET. Można przejrzeć plik autoexp.cs przykłady sposobu korzystania z atrybutu DebuggerDisplay lub można modyfikować i skompiluj plik autoexp.cs, aby zmienić domyślne rozszerzenia. Pamiętaj utworzyć kopię zapasową pliku autoexp.cs przed próbą zmodyfikowania.  
  
 Aby utworzyć autoexp.cs, otwórz wiersz polecenia zapasowej Developer dla VS2015 i uruchom następujące polecenia  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Zmiany autoexp.dll zostanie pobrana w następnej sesji debugowania.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Za pomocą wyrażeń w DebuggerDisplay  
 Mimo że można ogólne wyrażenia w nawiasach klamrowych atrybutu DebuggerDisplay takie rozwiązanie nie jest zalecane.  
  
 Ogólne wyrażenia w DebuggerDisplay ma niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typ docelowy. Wyrażenie nie ma dostępu do aliasy, zmienne lokalne lub wskaźników. Jeśli wyrażenie odwołuje się do właściwości, atrybuty te właściwości nie są przetwarzane. Na przykład kod C# `[DebuggerDisplay("Object {count - 2}")]` wyświetli `Object 6` Jeśli pole `count` został 8.  
  
 Używanie wyrażeń w DebuggerDisplay może spowodować następujące problemy:  
  
-   Ocena wyrażeń jest najbardziej kosztowna operacja w debugerze i wyrażenie jest obliczane w każdym razem, gdy jest on wyświetlany. Może to powodować problemy z wydajnością w krokowe wykonywanie kodu. Na przykład wyrażenie złożone, który służy do wyświetlania wartości z kolekcji lub listy może być bardzo wolno po dużej liczby elementów.  
  
-   Wyrażenia są oceniane przez Ewaluator wyrażeń języka bieżącej ramki stosu, a nie przez ewaluatora języka, w którym zapisano wyrażenie. Może to spowodować nieprzewidywalne skutki, jeśli języki są różne.  
  
-   Obliczenia wyrażenia można zmienić stanu aplikacji. Na przykład wyrażenie, która ustawia wartości właściwości mutuje wartości właściwości w wykonywanie kodu.  
  
 Jest jednym ze sposobów zmniejszyć możliwe problemy z wyrażenia przez utworzenie właściwości prywatnej, która wykonuje operację i zwraca wartość typu ciąg. Atrybutu DebuggerDisplay można następnie wyświetlić wartość tej właściwości prywatnej. Poniższy przykład zawiera implementację tego wzorca:  
  
```csharp  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób użycia `DebuggerDisplay`, wraz z `DebuggerBrowseable` i `DebuggerTypeProxy`. Podczas wyświetlania w oknie zmienne debugera, takie jak **czujki** okna, tworzy ekspansja, która wygląda następująco:  
  
|**Nazwa**|**Wartość**|**Typ**|  
|--------------|---------------|--------------|  
|Key|"3"|Obiekt {ciąg}|  
|Wartość|3|Obiekt {int}|  
  
```csharp  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }
    
    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Specyfikatory formatu w C#](../debugger/format-specifiers-in-csharp.md)   
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
