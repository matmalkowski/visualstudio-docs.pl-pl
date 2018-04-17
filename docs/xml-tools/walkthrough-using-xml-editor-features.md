---
title: 'Wskazówki: Korzystanie z funkcji edytora XML | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb7fee9546ecebfed2f5f95fb430f8d2026175c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-xml-editor-features"></a>Wskazówki: Korzystanie z funkcji edytora XML
Kroki opisane w tym przewodniku opisano sposób tworzenia nowego dokumentu XML. Instruktaż używa niektóre funkcje edytora XML wchodzące przydatne do tworzenia XML.  
  
> [!NOTE]
>  Przed rozpoczęciem przewodnika, Zapisz plik hireDate.xsd (przedstawionym poniżej w tym temacie) na komputerze lokalnym.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go z schematu XML  
  
1.  Na **pliku** menu wskaż **nowy**i kliknij przycisk **pliku**.  
  
2.  Wybierz **pliku XML** w **szablony** okienko i kliknij przycisk **Otwórz**.  
  
     Nowy plik jest otwarty w edytorze. Plik zawiera deklaracji XML domyślne `<?xml version="1.0" encoding="utf-8">`.  
  
3.  W oknie właściwości dokumentu, kliknij przycisk Przeglądaj (**...** ) na **schematy** pola.  
  
     **Schematów XSD** zostanie wyświetlone okno dialogowe.  
  
4.  Kliknij przycisk **Dodaj**.  
  
     **Otwórz schematu XSD** zostanie wyświetlone okno dialogowe.  
  
5.  Wybierz plik hireDate.xsd, a następnie kliknij przycisk **Otwórz**.  
  
6.  Kliknij przycisk **OK**.  
  
     Schemat XML jest obecnie powiązany z dokumentem XML. Schemat XML jest używany do walidacji dokumentu. Również jest używany przez funkcję IntelliSense w do wypełnienia listy Członkowskie elementów prawidłową.  
  
### <a name="to-add-data"></a>Aby dodać dane  
  
1.  Typ `<` w okienku edytora.  
  
     Lista elementów członkowskich Wyświetla możliwych elementów:  
  
    -   **!--** Aby dodać komentarz.  
  
    -   **! DOCTYPE** można dodać typu dokumentu.  
  
    -   **?** Aby dodać instrukcji przetwarzania.  
  
    -   **Pracownik** można dodać elementu głównego.  
  
2.  Wybierz **<!--** Dodaj węzeł komentarz, a następnie naciśnij klawisz ENTER.  
  
     Edytor wstawia tagu końcowego komentarz i umieszcza kursor między tagiem początkowym i końcowym w komentarz.  
  
3.  Wpisz w **pliku XML testu**.  
  
4.  W nowym wierszu, wpisz `<`i wybierz **pracownika** z listy elementów członkowskich.  
  
     Edytor dodaje początek elementu XML `<employee`. W tym momencie można dodawać atrybuty do elementu lub tagu początkowego można zamknąć, wpisując `>`.  
  
5.  Typ `>` zamknięcia tagu.  
  
6.  Edytor dodaje do tagu końcowego. Tag końcowy zostanie dodany z faliste podkreślenie wskazujące błąd sprawdzania poprawności. Etykietki narzędzia wyświetlany jest komunikat: element "pracownik" ma niekompletną zawartość. Oczekiwano 'ID'.  
  
7.  Typ `<` i wybierz **identyfikator** z listy elementów członkowskich. Następnie wpisz `>`.  
  
     Edytor dodaje XML element `<ID></ID>`i umieszcza kursor po tag początkowy identyfikator.  
  
8.  Typ **abc**.  
  
     **Abc** tekst ma faliste podkreślenie. Etykietki narzędzia wyświetlany jest komunikat: element 'ID' ma nieprawidłową wartość przy uwzględnieniu jego typu danych.  
  
9. Kliknij prawym przyciskiem myszy elementu ID, a następnie wybierz **przejdź do definicji**.  
  
     Edytor otwiera plik hireDate.xsd w nowym oknie dokumentu i umieszcza kursor w definicji elementu Identyfikatora schematu.  
  
10. Wróć do pliku XML i Zastąp **abc** tekst z **123**.  
  
     Faliste podkreślenie i etykietek narzędzi są usuwane w wartości elementu Identyfikatora. Etykietka narzędzia dla tagu końcowego pracownika teraz wyświetli komunikat: element "pracownik" ma niekompletną zawartość. Oczekiwano "zatrudnienia data".  
  
11. Umieść kursor po tagu końcowego identyfikator, wpisz w `<`, wybierz datę zatrudnienia z listy elementów członkowskich, a następnie wpisz w `>`.  
  
     Edytor dodaje XML element `<hire-date></hire-date>`i umieszcza kursor po Data zatrudnienia tag początkowy.  
  
12. Wpisz w **2003-01-10** zatrudnienia daty.  
  
### <a name="to-format-the-xml-document"></a>Format dokumentu XML  
  
- Wybierz **dokumentu w formacie** przycisku paska narzędzi edytora XML.
  
    Dokument XML jest ponownie sformatowany.  
  
### <a name="to-save-the-xml-document"></a>Aby zapisać dokument XML  
  
1.  Z **pliku** menu, wybierz opcję **Zapisz jako**.  
  
     **Zapisz plik jako** zostanie wyświetlone okno dialogowe. Domyślna nazwa pliku jest "XMLFile1".  
  
2.  Wprowadź nazwę pliku i lokalizację dokument XML, a następnie kliknij przycisk **zapisać**.  
  
## <a name="hiredatexsd-file"></a>hireDate.xsd pliku  
 Następujący plik schematu jest używany przez przewodnika.  
  
```xml
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)