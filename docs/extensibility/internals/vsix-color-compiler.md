---
title: VSIX kolorem kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-color-compiler"></a>VSIX kolorem kompilatora
Narzędzie kompilatora kolor rozszerzeń programu Visual Studio jest aplikacja konsolowa, która przyjmuje plik .xml reprezentujący kolory istniejącego motywu programu Visual Studio i konwertuje go do .pkgdef plików w celu kolorów te mogą być używane w programie Visual Studio. Ponieważ jest to łatwa do porównania różnic między plikami XML to narzędzie jest przydatne do zarządzania kolorów niestandardowych w kontroli źródła. On również mogą być dołączane do środowiska kompilacji, aby dane wyjściowe kompilacji jest plikiem .pkgdef prawidłowe.  
  
 **Schemat XML motywu**  
  
 Plik XML motywu pełną wygląda następująco:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Motyw**  
  
 \<Motyw > element definiuje całego motywu. Motyw musi zawierać co najmniej jeden \<kategorii > elementu. Elementy kompozycja definiuje się następująco:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Nazwa|[Wymagane] Nazwa motywu|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID motywu (muszą pasować formatowanie identyfikatora GUID)|  
  
 Podczas tworzenia kolorów niestandardowych dla programu Visual Studio, kolorów te muszą być zdefiniowane dla następujących tematów. Jeśli nie istnieją żadne kolorów dla wybranego motywu, Visual Studio próbuje załadować brakujących kolorów z motywu jasny.  
  
|||  
|-|-|  
|**Nazwa motywu**|**Motyw identyfikator GUID**|  
|Jasny|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Ciemny|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|niebieski|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Duży kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategoria**  
  
 \<Kategorii > element definiuje kolekcji kolorów motywu. Nazwy kategorii Podaj logiczne grupy i powinien być zdefiniowany jako ściśle, jak to możliwe. Kategoria musi zawierać co najmniej jeden \<kolor > elementu. Elementy kategorii zdefiniowano następująco:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Nazwa|[Wymagane] Nazwa kategorii|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID kategorii (muszą pasować formatowanie identyfikatora GUID)|  
  
 **Kolor**  
  
 \<Kolor > element definiuje kolor składnika lub stan interfejsu użytkownika. Preferowany nazewnictwa kolor jest [typ interfejsu użytkownika] [Stan]. Nie należy używać słowa "color", ponieważ jest nadmiarowy. Kolor powinny wyraźnie wskazuje typ elementu i sytuacji lub "stanu", dla których zostaną zastosowane kolor. Kolor nie może być pusta i musi zawierać jedną lub obie \<tła > i \<pierwszego planu > elementu. Kolor elementów są zdefiniowane następująco:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Nazwa|[Wymagane] Nazwa koloru|  
  
 **Tło i/lub pierwszego planu**  
  
 \<Tła > i \<pierwszego planu > elementy zdefiniować wartość koloru i typ dla tła lub pierwszego planu elementu interfejsu użytkownika. Elementy te nie mają elementów podrzędnych.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Typ|[Wymagane] Typ koloru. Może być jedną z następujących czynności:<br /><br /> *CT_INVALID:* kolor jest nieprawidłowy lub nie została ustawiona.<br /><br /> *CT_RAW:* nieprzetworzonej wartości ARGB.<br /><br /> *CT_COLORINDEX:* NIE UŻYWAJ.<br /><br /> *CT_SYSCOLOR:* kolor systemu Windows z SysColor.<br /><br /> *CT_VSCOLOR:* kolor Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* kolorowi automatycznemu.<br /><br /> *CT_TRACK_FOREGROUND:* NIE UŻYWAJ.<br /><br /> *CT_TRACK_BACKGROUND:* NIE UŻYWAJ.|  
|Źródło|[Wymagane] Wartość koloru reprezentowane w formacie szesnastkowym|  
  
 Wszystkie wartości wyliczenia __VSCOLORTYPE są obsługiwane przez schemat w atrybucie typu. Jednak zaleca się, że można używać tylko CT_RAW i CT_SYSCOLOR.  
  
 **Wszystko w jednym**  
  
 Jest to prosty przykład pliku .xml prawidłowy motywu:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 **Składnia**  
  
 VsixColorCompiler \<pliku XML > \<pliku PkgDef > \<opcjonalnych argumentów >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Nazwa przełącznika**|**Uwagi**|**Wymagany lub opcjonalny**|  
|Nienazwane (plik .xml)|Jest to pierwszy parametr nienazwany, ścieżka do pliku XML do konwersji.|Wymagane|  
|Nienazwane (plik .pkgdef)|Jest to drugi parametr nienazwany, ścieżka wyjściowa .pkgdef wygenerowanego pliku.<br /><br /> Wartość domyślna: \<nazwę pliku XML > .pkgdef|Optional|  
|/ nologo|Ustawienie tej flagi zatrzymuje produktu i prawa autorskie informacje z drukowania.|Optional|  
|/?|Wydrukuj informacji pomocy.|Optional|  
|/help|Wydrukuj informacji pomocy.|Optional|  
  
 **Przykłady**  
  
-   D:\pkgdef\colors.pkgdef VsixColorCompiler D:\xml\colors.xml  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Uwagi  
  
-   To narzędzie wymaga zainstalowania najnowszej wersji środowiska uruchomieniowego VC ++.  
  
-   Obsługiwane są tylko pojedynczych plików. Konwersja zbiorcza za pośrednictwem ścieżki folderu nie jest obsługiwana.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 Plik .pkgdef generowany przez narzędzie będą podobne do poniższych kluczy:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```