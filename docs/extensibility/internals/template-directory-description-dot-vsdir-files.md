---
title: Opis katalogu szablonu (. Pliki Vsdir) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14ea2e0bcc11324e6529c70c04c11874ec4a3399
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="template-directory-description-vsdir-files"></a>Opis katalogu szablonu (. Pliki Vsdir)
Szablon pliku opisu katalogu (.vsdir) to plik tekstowy, który umożliwia zintegrowane środowisko programistyczne (IDE), aby wyświetlić folderów, plików kreatora .vsz i plików szablonów, które są skojarzone z projektu w oknach dialogowych. Zawierać jeden rekord dla każdego pliku lub folderu. Wszystkie pliki .vsdir w lokalizacji, do którego istnieje odwołanie są scalane, mimo że .vsdir tylko jeden plik jest zazwyczaj podawana do opisywania wiele folderów, pliki szablonów lub kreatorów.  
  
 Foldery (w podkatalogach), plików, które są wymienione w pliku .vsdir i w samym pliku .vsdir znajdują się w tym samym katalogu. Gdy IDE uruchamia Kreator lub wyświetla folderu lub pliku w **nowy projekt** lub **Dodaj nowy element** okien dialogowych katalog, który zawiera wykonanego pliki, aby sprawdzić, czy plik .vsdir jest sprawdza IDE obecny. Jeśli zostanie znaleziony plik .vsdir, IDE odczytuje go, aby ustalić, czy zawiera on wpis pliku lub folderu wykonywane lub wyświetlane. Jeśli wpis zostanie znaleziony, IDE używa tych informacji w wykonanie kreatora lub wyświetlanie zawartości.  
  
 Poniższy przykładowy kod jest z pliku SourceFiles.vsdir w \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files klucz rejestru:  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 W takim przypadku dwa rekordy są w jednym pliku. Nowy wiersz (znak powrotu karetki) oddziela każdego rekordu. Każdy wiersz zawiera inny typ pliku. Potok (&#124;) rozdziela pól w każdym rekordzie. Jednego katalogu może zawierać wiele plików .vsdir, które mają różne nazwy plików lub może mieć jeden plik .vsdir dla każdego typu pliku.  
  
## <a name="fields"></a>Pola  
 W poniższej tabeli wymieniono pola określone dla każdego rekordu.  
  
|Pole|Opis|  
|-----------|-----------------|  
|Nazwa ścieżki względnej (RelPathName)|Nazwa folderu, w szablonie lub .vsz pliku, na przykład HeaderFile.h lub MyWizard.vsz. To pole może być również nazwa używana do reprezentowania folderu.|  
|{clsidPackage}|Identyfikator GUID pakiet VSPackage, który umożliwia dostęp do zlokalizowanych ciągów, takich jak LocalizedName, opis, IconResourceId i SuggestedBaseName, w pakiecie VSPackage satelity dołączana dynamicznie biblioteka (DLL) zasobów. IconResourceId ma zastosowanie, jeśli nie podano ścieżka dll. **Uwaga:** to pole jest opcjonalne, chyba że przynajmniej jedna z poprzednich pola jest identyfikatorem zasobu. To pole jest zwykle puste w przypadku .vsdir pliki, które odpowiadają z kreatorami innych firm, które nie jest lokalizowany tekstu.|  
|LocalizedName|Zlokalizowana nazwa pliku szablonu lub kreatora. To pole może być ciągiem lub identyfikatorem zasobu w postaci "#ResID". Ta nazwa będzie wyświetlana w **Dodaj nowy element** okno dialogowe. **Uwaga:** Jeśli LocalizedName jest identyfikatorem zasobu, a następnie {clsidPackage} jest wymagane.|  
|SortPriority|Liczba całkowita reprezentująca względny priorytet tego pliku szablonu lub kreatora. Na przykład jeśli ten element ma wartość 1, ten element jest wyświetlany obok inne elementy o wartości 1 i wcześniejsze wszystkie elementy z wartością sortowania 2 lub większą.<br /><br /> Priorytet sortowania jest określana względem elementów w tym samym katalogu. W tym samym katalogu może istnieć więcej niż jeden plik .vsdir. W takim przypadku elementów ze wszystkich *.* vsdir pliki w tym katalogu zostały scalone. Elementy z takim samym priorytecie są wyświetlane według lexicographic bez uwzględniania wielkości liter nazwę wyświetlaną. `_wcsicmp` Służy funkcja porządkowania elementów.<br /><br /> Elementy nie zostały opisane w plikach .vsdir zawierają wiele priorytet większych niż wymienione w plikach .vsdir najwyższy priorytet. Wynik jest, że te elementy znajdują się na końcu wyświetlonej listy niezależnie od ich nazwy.|  
|Opis|Zlokalizowany opis pliku szablonu lub kreatora. To pole może być ciągiem lub identyfikatorem zasobu w postaci "#ResID". Ten ciąg jest wyświetlana w **nowy projekt** lub **Dodaj nowy element** okno dialogowe, gdy element jest zaznaczony.|  
|Ścieżka dll lub {clsidPackage}|Pozwala załadować ikony dla kreatora lub pliku szablonu. Ikona jest ładowany jako zasób poza plik .dll lub .exe przy użyciu IconResourceId. Ten plik .dll lub .exe można zidentyfikować przy użyciu pełną ścieżkę lub przy użyciu identyfikatora GUID pakiet VSPackage. Implementacja DLL pakiet VSPackage jest używana w celu załadowania ikona (nie satelitarnej biblioteki DLL).|  
|IconResourceId|Identyfikator zasobu w implementacji biblioteki DLL lub pakiet VSPackage DLL, która określa ikonę do wyświetlenia.|  
|Flagi (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|Pozwala włączyć lub wyłączyć **nazwa** i **lokalizacji** pól na **Dodaj nowy element** okno dialogowe. Wartość **flagi** pole jest dziesiętną kombinacji flag bitowych wymagane.<br /><br /> Gdy użytkownik wybierze element na **nowy** karcie projektu określa, czy pola nazwy i lokalizacji są wyświetlane podczas **Dodaj nowy element** najpierw zostanie wyświetlone okno dialogowe. Element, za pomocą pliku .vsdir, można kontrolować tylko czy pola są włączone lub wyłączone, gdy element jest zaznaczony.|  
|SuggestedBaseName|Reprezentuje domyślną nazwę pliku, Kreator lub szablonu. To pole jest ciągiem lub identyfikatorem zasobu w postaci "#ResID". IDE używa tej wartości, aby podać nazwę domyślnej dla elementu. Tej wartości podstawowej jest dołączany z wartością całkowitą można utworzyć nazwy są unikatowe, takich jak MyFile21.asp.<br /><br /> Na poprzedniej liście opis, ścieżka dll IconResourceId, flag i SuggestedBaseNumber dotyczą tylko pliki kreatora i szablonu. Foldery nie dotyczą tych pól. Ten fakt przedstawiono na kod w pliku BscPrjProjectItems w \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems klucza rejestru. Ten plik zawiera trzy (po jednej dla każdego folderu) rekordy z czterech pól dla każdego rekordu: RelPathName, {clsidPackage} LocalizedName i SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Podczas tworzenia pliku kreatora, należy również rozważyć następujące kwestie.  
  
-   Pole nie jest wymagane dla której nie ma żadnych istotnych danych powinien zawierać 0 (zero) jako symbol zastępczy.  
  
-   Jeśli zostanie podana żadna zlokalizowana nazwa, nazwa ścieżki względnej jest używana w pliku kreatora.  
  
-   Ścieżka dll przesłania clsidPackage ikonę lokalizacji.  
  
-   Jeśli ikona nie jest zdefiniowany, IDE zastępuje domyślną ikonę pliku, który ma tego rozszerzenia.  
  
-   W przypadku nie sugerowane nazwy podstawowej 'Projekt' jest używana.  
  
-   Jeśli usuniesz .vsz — pliki, foldery lub pliki szablonów, należy także usunąć ich skojarzonych rekordów z pliku .vsdir.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)