---
title: Ostrzeżenia VSInstr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a306276e015d06fe3becf297d0bb5834f640a1a7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571649"
---
# <a name="vsinstr-warnings"></a>Ostrzeżenia VSInstr
W poniższej tabeli wymieniono ostrzeżenia *VSInstr.exe* narzędzia. NOWARN — opcja wraz z numerów ostrzeżeń, które umożliwia Pomiń wyświetlanie ostrzeżenia.  
  
|Numer ostrzeżenia|Opis|  
|--------------------|-----------------|  
|**VSP2000**|Błąd wewnętrzny. Nie można pobrać nazwy pliku modułu dla tego pliku wykonywalnego.|  
|**VSP2001**|\<Nazwa zestawu > jest zestaw o silnej nazwie. Należy ponownie podpisany, można było wykonać.<br /><br /> To ostrzeżenie występuje, gdy jest instrumentowany podpisanych zestawów. Można użyć *sn.exe* narzędzia rezygnacji z pliku binarnego lub tymczasowo wyłączyć wymaganie silnej nazwy. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool).|  
|**VSP2002**|Nie można znaleźć funkcji \<funcname > w pliku \<nazwa pliku ><br /><br /> To ostrzeżenie występuje, jeśli funkcja nie może znajdować się w określonym pliku.|  
|**VSP2003**|Nie można znaleźć żadnych skrzyżowanych skoków do funkcji \<funcname > w pliku \<nazwa_pliku >.<br /><br /> To ostrzeżenie występuje, gdy narzędzie VSInstr nie zniesienia przechodzi między. Skrzyżowany skok są używane do optymalizacji kodu.|  
|**VSP2004**|Funkcja \<funcname > został wykluczony, za pomocą przełącznika wiersza polecenia EXCLUDE, ale była wymagana, ponieważ zawiera on krzyżowego skoku.<br /><br /> To ostrzeżenie występuje, gdy funkcja została wykluczona przy użyciu opcji EXCLUDE, ale jest wymagany podczas procesu instrumentacji. Profiler automatycznie uwzględnia wymaganej funkcji.|  
|**VSP2005**|Wewnętrzny błąd Instrumentacji \<tekst błędu ><br /><br /> To ostrzeżenie, jeśli nie można przeprowadzić instrumentacji. Przejrzyj tekst błędu, aby określić, czy można go usunąć.|  
|**VSP2006**|Nie można zlokalizować pliku PDB dla \<name ><br /><br /> To ostrzeżenie występuje, gdy plik PDB nie istnieje w ścieżce wyszukiwania lub niezgodny plik binarny.|  
|**VSP2007**|\<Nazwa pliku > nie zawiera Instrumentacji kodu.<br /><br /> To ostrzeżenie zostanie wyświetlone, czy funkcje w pliku binarnym zostały wszystkie wykluczone, czy określony plik zawiera tylko zasoby.|  
|**VSP2008**|Nie można pobrać atrybutów zabezpieczeń z \<name >. Kod błędu \<kod ><br /><br /> To ostrzeżenie występuje, gdy użytkownik nie ma uprawnień READ_DAC. Podczas procesu Instrumentacji profilera próbuje zachować oryginalne DACL dla danych binarnych. Ponieważ oryginalnego pliku binarnego jest zastępowany nowego pliku binarnego, DACL z oryginalnego pliku binarnego musi być kopiowane i stosowane do nowych danych binarnych. Może się nie powieść, jeśli użytkownik nie ma dostępu READ_DAC na oryginalnego pliku binarnego.|  
|**VSP2009**|Nie można ustawić atrybutów zabezpieczeń na \<name >. Kod błędu \<numer błędu ><br /><br /> To ostrzeżenie występuje, gdy użytkownik nie ma uprawnień WRITE_DAC. Podczas procesu Instrumentacji profilera próbuje zachować oryginalne DACL dla danych binarnych. Ponieważ oryginalnego pliku binarnego jest zastępowany nowego pliku binarnego, DACL z oryginalnego pliku binarnego musi być kopiowane i stosowane do nowych danych binarnych. Może się nie powieść, jeśli użytkownik nie ma dostępu WRITE_DAC na nowe dane binarne.|  
|**VSP2010**|Funkcje nie są specjalnie wybranych do Instrumentacji z powodu — użyć opcji/WYKLUCZANIA|  
|**VSP2011**|Dołączania/wykluczania funcspec \<name > nie pasuje do żadnych funkcji|  
|**VSP2012**|Obraz nie zawiera kodu, który może być Instrumentacji pokrycia kodu.<br /><br /> Profiler nie Instrumentacja typ następującego kodu:<br /><br /> — Statyczne funkcje CRT<br />-Zarządzanych metody z NonUserCodeAttribute<br />-Zarządzanych metody z DebuggerHiddenAttribute<br />— MASM bloki<br /><br /> To ostrzeżenie jest generowany, gdy po powyższym filtrowaniu nie jest wykonywany kod po lewej.|  
|**VSP2013**|Zinstrumentowanie tego obrazu wymaga do uruchamiania jako proces 32-bitowy. Aby to odzwierciedlić flagi nagłówka CLR zostały zaktualizowane.<br /><br /> Profiler modyfikuje plik binarny, aby 64-bitowych systemów operacyjnych można otworzyć procesu 32-bitowej w emulatorze WOW64. Dla biblioteki dll to może się nie powieść, jeśli są załadowane w istniejących procesu 64-bitowego. To ostrzeżenie informuje użytkownika zależności.|  
|**VSP2014**|Wynikowy zinstrumentowany obraz jest nieprawidłowy i może nie działać.<br /><br /> Ten komunikat występuje, gdy końcowego instrumentowanego zestawu ma nieprawidłowy nagłówek PE.|  
  
## <a name="see-also"></a>Zobacz także  
 [VSInstr](../profiling/vsinstr.md)