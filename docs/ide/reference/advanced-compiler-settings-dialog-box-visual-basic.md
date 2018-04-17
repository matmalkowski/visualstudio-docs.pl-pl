---
title: Kompilator okno dialogowe Zaawansowane ustawienia (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8b89b140154b18ad2055beed059fe628b077752
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe

Użyj **ustawienia AdvancedCompiler** okna dialogowego **projektanta projektu** do określenia zaawansowane właściwości konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko projektów Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Dostęp do tego okna dialogowego
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** pojawia się, kliknij przycisk **skompilować** kartę.  
  
3.  Na [strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), wybierz pozycję **konfiguracji** i **platformy**. W konfiguracji kompilacji uproszczony **konfiguracji** i **platformy** list nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie debugowania i konfiguracje wydania](../../debugger/how-to-set-debug-and-release-configurations.md).
  
4.  Kliknij przycisk **zaawansowane opcje kompilacji**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="optimizations"></a>Optymalizacje  
 Następujące opcje Określ funkcje optymalizacji, które można w niektórych przypadkach zmniejszyć plik programu, Ustaw program szybsze i przyspieszyć proces kompilacji.  
  
 **Wyłącz sprawdzanie przepełnienia całkowitych**  
 Domyślnie to pole wyboru jest wyczyszczone włączać sprawdzanie przepełnienia liczby całkowitej. Zaznacz to pole wyboru, aby usunąć sprawdzanie przepełnienia liczby całkowitej. Jeśli to pole wyboru jest zaznaczone, obliczenia na liczbach całkowitych może przebiegać szybciej. Jednak po usunięciu przepełnienie sprawdzanie i dane typu możliwości przepełnienie niepoprawne wyniki mogą być przechowywane bez błędów zgłaszanych.  
  
 Jeśli warunki przepełnienie są sprawdzane i operacji na wartościach całkowitych zachodzi, <xref:System.OverflowException> wyjątku. Jeśli warunki przepełnienie nie jest zaznaczone, przepełnienia operacji całkowitą nie Zgłoś wyjątek.  
  
 **Włącz optymalizacje**  
 Domyślnie to pole wyboru jest wyczyszczone, aby wyłączyć optymalizacje kompilatora. Zaznacz to pole wyboru, aby włączyć optymalizacje kompilatora. Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora. Jednak ponieważ optymalizacje modyfikacji kodu w pliku wyjściowym, optymalizacje kompilatora może utrudnić debugowania.  
  
 **Adres podstawowy biblioteki DLL**  
 To pole tekstu Wyświetla domyślny adres podstawowy biblioteki DLL w formacie szesnastkowym. W projektach biblioteki klas i Biblioteka formantów tego pola tekstowego służy do określ adres podstawowy, który będzie używany podczas tworzenia biblioteki DLL.  
  
 **Generowanie informacji o debugowaniu**  
 Wybierz **Brak**, **pełne**, lub **tylko do pdb** z listy. **Brak** Określa, czy można wygenerować żadnych informacji debugowania. **Pełna** określa wygenerowania pełne informacje o debugowaniu, i **tylko do pdb** Określa, że jest generowany tylko informacje debugowania pliku PDB. Domyślnie ta opcja jest ustawiona na **pełne**.  
  
## <a name="compilation-constants"></a>Stałe kompilacji  
 Kompilacja warunkowa stałe obowiązują podobne do przy użyciu [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) plików dyrektywy preprocesora w źródle, z wyjątkiem tego, że stałe zdefiniowane są publiczne i dotyczą wszystkich plików w projekcie. Można użyć stałe kompilacja warunkowa razem z [#If... Then... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) dyrektywy warunkowo skompilować plików źródłowych. Zobacz [kompilacja warunkowa](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Zdefiniuj stała debugowania**  
 Domyślnie to pole wyboru jest zaznaczone, określając, że można ustawić stałą debugowania.  
  
 **Zdefiniuj stała śledzenia**  
 Domyślnie to pole wyboru jest zaznaczone, określając, że można ustawić stałą śledzenia.  
  
 **Stałe niestandardowych**  
 Wprowadź wszelkie stałe niestandardowych aplikacji w tym polu tekstowym. Wpisy powinny być rozdzielone przecinkami, za pomocą tego formularza: **Nazwa1 = "Wartość1," Nazwa2 = "Wartość2," nazwa3 = "Wartość3"**.  
  
## <a name="other-settings"></a>Inne ustawienia

 **Generowanie zestawów serializacji**  
 To ustawienie określa, czy kompilator utworzy zestawy serializacji XML. Zestawy serializacji może poprawić wydajność uruchamiania <xref:System.Xml.Serialization.XmlSerializer> przypadku użycia tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na **automatycznie**, który określa, że zestawy serializacji generowane tylko wtedy, gdy jest używanych <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie XML. **Wyłącz** Określa, czy zestawy serializacji nigdy nie można wygenerować, niezależnie od tego, czy używa Twój kod <xref:System.Xml.Serialization.XmlSerializer>. **Na** Określa, czy zestawy serializacji zawsze być generowany. Zestawy serializacji są nazywane `TypeName`. XmlSerializers.dll.  

## <a name="see-also"></a>Zobacz także

[Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)