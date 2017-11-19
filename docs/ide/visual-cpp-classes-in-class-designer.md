---
title: Klasy Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdesigner.inheritancelinelabel
helpviewer_keywords: Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b4ba110a67604a24517cac90c4645f118a33e722
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-classes-in-class-designer"></a>Klasy Visual C++ w Projektancie klas
Projektant klas obsługuje klas C++ i wizualizuje macierzystych klas C++ w taki sam sposób jak kształty klas języka Visual Basic i Visual C#, z wyjątkiem klasy C++ może mieć wiele relacji dziedziczenia. Można rozwinąć kształtu klasy do wyświetlenia więcej pól i metod w klasie lub zwinąć do oszczędzania przestrzeni dyskowej.  
  
> [!NOTE]
>  Projektant klas nie obsługuje unie (specjalny typ klasy, w którym przydzielić pamięć jest niezbędne dla elementu Członkowskiego Unii największy danych Kwota).  
  
## <a name="simple-inheritance"></a>Proste dziedziczenie  
 Gdy przeciągnięcie więcej niż jedną klasę do diagramu klas i klasy mają relację dziedziczenia klasy, Strzałka łączy je. Punkty strzałki w kierunku klasy podstawowej. Na przykład podczas następujących klas są wyświetlane na diagramie klas, Strzałka łączy, wskazujący z B A:  
  
```  
class A {};  
class B : A {};  
```  
  
 Możesz także przeciągnąć klasy B do diagramu klas, kliknij prawym przyciskiem myszy kształtu klasy B, a następnie kliknij **Pokaż klasy podstawowej**. Spowoduje to wyświetlenie jej klasa podstawowa: A.  
  
## <a name="multiple-inheritance"></a>Dziedziczenie wielokrotne  
 Projektant klas obsługuje wizualizację relacji dziedziczenia wielu klas. *Dziedziczenie wielokrotne* jest używany, gdy klasa pochodna atrybutami więcej niż jedną klasę podstawową. Poniżej przedstawiono przykład dziedziczenie wielokrotne:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Gdy przeciągnięcie więcej niż jedną klasę do diagramu klas i klasy mają relację dziedziczenia wielu klas, Strzałka łączy je. Punkty strzałki w kierunku klas podstawowych.  
  
 Prawym przyciskiem myszy kształt klasy, a następnie klikając pozycję **Pokaż klas podstawowych** zawiera klasy podstawowe dla wybranej klasy.  
  
> [!NOTE]
>  **Pokaż klas pochodnych** polecenie nie jest obsługiwane dla kodu C++. Klasy pochodne można wyświetlić, przechodząc do widoku klasy, rozwijając węzeł typu, rozszerzanie **typów pochodnych** podfolder, a następnie przeciągając tych typów do diagramu klas.  
  
 Aby uzyskać więcej informacji na temat dziedziczenia klas wielu zobacz [dziedziczenie wielokrotne](https://msdn.microsoft.com/en-us/library/6td5yws2.aspx) i [wielu klas Base](/cpp/cpp/multiple-base-classes).  
  
## <a name="abstract-classes"></a>Klasy abstrakcyjne  
 Projektant klas obsługuje klasy abstrakcyjne (o nazwie "abstrakcyjnych klas podstawowych"). Są to klasy, który nigdy nie wystąpienia, ale z którego mogą pochodzić innych klas. W przykładzie z "Dziedziczenie wielokrotne" we wcześniejszej części tego dokumentu, użytkownik może utworzyć wystąpienia `Bird` klasy pojedyncze obiekty w następujący sposób:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Jednak może nie zamierzasz utworzyć wystąpienia `Swimmer` klasy jako pojedyncze obiekty. Zamierzasz tylko do innych typów klas zwierząt od niej pochodzić, na przykład `Penguin`, `Whale`, i `Fish`. W takim przypadku może zadeklarować `Swimmer` klasą abstrakcyjną klasę podstawową.  
  
 Aby zadeklarować klasy jako abstrakcyjny, można użyć `abstract` — słowo kluczowe. Elementy członkowskie oznaczone jako abstrakcyjny lub zawarte w klasie abstrakcyjnej wirtualne i musi być implementowana przez klasy, które pochodzi z klasy abstrakcyjnej.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 Klasa może deklarować także jako abstrakcyjny, umieszczając w niej co najmniej jeden czystej funkcji wirtualnej:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Po wyświetleniu tych deklaracji na diagramie klas, nazwa klasy `Swimmer` i jego czystej funkcji wirtualnej `swim` w są wyświetlane kursywą kształtu Klasa abstrakcyjna, wraz z notacji **klasy abstrakcyjnej**. Zauważ, że kształtu typu klasy abstrakcyjnej jest takie samo jak w przypadku zwykłej klasy, z wyjątkiem tego, że obramowanie jest przerywana linia.  
  
 Klasy pochodnej z klasy abstrakcyjnej podstawowej przesłonięcie poszczególnych czystej funkcji wirtualnej w klasie podstawowej lub nie można utworzyć wystąpienia klasy pochodnej. Tak, na przykład, jeśli wyprowadzona `Fish` klasę z `Swimmer` klasy, `Fish` przesłonięcie `swim` metody:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Podczas wyświetlania tego kodu na diagramie klas, Projektant klas rysuje dziedziczenia z `Fish` do `Swimmer`.  
  
## <a name="anonymous-classes"></a>Klasy anonimowe  
 Projektant klas obsługuje klasy anonimowy. *Anonimowe typy klas* są klasy zadeklarowana bez identyfikatora. One nie może mieć Konstruktor ani destruktor nie mogą być przekazywane jako argumenty do funkcji i nie może być zwracany jako wartości zwracane z funkcji. Klasa anonimowe umożliwia Zastąp nazwą klasy nazwy typu typedef, jak w poniższym przykładzie:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Można też anonimowe struktury. Projektant klas Wyświetla anonimowe klasy i struktury taki sam, jak jest wyświetlana odpowiedniego typu. Mimo że można zadeklarować i wyświetlić anonimowe klas i struktur, Projektant klas nie będzie używać nazwa tagu, który określisz. Nazwa, która generuje widoku klasy zostanie użyty. Klasy lub struktury pojawia się w widoku klas i Projektant klas jako elementu o nazwie **__unnamed**.  
  
 Aby uzyskać więcej informacji o klasach anonimowe, zobacz [anonimowe typy klas](/cpp/cpp/anonymous-class-types).  
  
## <a name="template-classes"></a>Klasy szablonów  
 Projektant klas obsługuje wizualizację klasy szablonu. Zagnieżdżone deklaracje są obsługiwane. W poniższej tabeli przedstawiono niektóre typowe deklaracji.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Klasy szablonów|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasy szablonów|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Klasy szablonów|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasy szablonów|  
  
 W poniższej tabeli przedstawiono przykłady z częściowa specjalizacja.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasy szablonów|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Klasy szablonów|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Klasy szablonów|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Klasy szablonów|  
  
 W poniższej tabeli przedstawiono kilka przykładów dziedziczenia w specjalizacji częściowej.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Klasy szablonów<br /><br /> `B`<br /><br /> Class<br /><br /> (wskazuje klasy A)<br /><br /> `C`<br /><br /> Class<br /><br /> (wskazuje klasy A)|  
  
 W poniższej tabeli przedstawiono przykłady z częściowa specjalizacja szablonu funkcji.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> FUNC\<T, U > (+ 1 przeciążenia)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Klasy szablonów<br /><br /> `B<T2>`<br /><br /> Klasy szablonów<br /><br /> (B znajduje się w obrębie klasy A **zagnieżdżone typy**)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Class<br /><br /> -> C\<int ><br /><br /> `C<T>`<br /><br /> Klasy szablonów|  
  
 W poniższej tabeli przedstawiono kilka przykładów dziedziczenia szablonu.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Class<br /><br /> -> B<br /><br /> `C<int>`<br /><br /> Class<br /><br /> (B znajduje się w obrębie klasy C w obszarze **zagnieżdżone typy**)<br /><br /> `C<T>`<br /><br /> Klasy szablonów|  
  
 W poniższej tabeli przedstawiono kilka przykładów canonical klas wyspecjalizowanych połączenia.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Class<br /><br /> -> C\<int ><br /><br /> `C<int>`<br /><br /> Class<br /><br /> `C<T>`<br /><br /> Klasy szablonów<br /><br /> `D`<br /><br /> Class<br /><br /> -> C\<float >|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T >|  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z kodem Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)   
 [Anonimowe typy klas](/cpp/cpp/anonymous-class-types)   
 [Dziedziczenie wielokrotne](https://msdn.microsoft.com/en-us/library/6td5yws2.aspx)   
 [Wiele klas podstawowych](/cpp/cpp/multiple-base-classes)   
 [Szablony](/cpp/cpp/templates-cpp)