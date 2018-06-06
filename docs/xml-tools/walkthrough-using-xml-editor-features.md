---
title: 'Przewodnik: korzystanie z funkcji edytora XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afda2968ece2a18b7abdc2c4c35e4353206cbe42
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693828"
---
# <a name="walkthrough-use-xml-editor-features"></a>Wskazówki: Użyj funkcji edytora XML

Kroki opisane w tym przewodniku opisano sposób tworzenia nowego dokumentu XML. Instruktaż używa niektóre funkcje edytora XML wchodzące przydatne do tworzenia XML.

> [!NOTE]
> Przed rozpoczęciem przewodnika, Zapisz *hireDate.xsd* pliku (przedstawionym poniżej w tym temacie) na komputerze lokalnym.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go z schematu XML

1.  Na **pliku** menu wskaż **nowy**i kliknij przycisk **pliku**.

2.  Wybierz **pliku XML** w **szablony** okienko i kliknij przycisk **Otwórz**.

     Nowy plik jest otwarty w edytorze. Plik zawiera deklaracji XML domyślne `<?xml version="1.0" encoding="utf-8">`.

3.  W oknie właściwości dokumentu, kliknij przycisk Przeglądaj (**...** ) na **schematy** pola.

     **Schematów XSD** zostanie wyświetlone okno dialogowe.

4.  Kliknij przycisk **Dodaj**.

     **Otwórz schematu XSD** zostanie wyświetlone okno dialogowe.

5.  Wybierz *hireDate.xsd* plik i kliknij przycisk **Otwórz**.

6.  Kliknij przycisk **OK**.

     Schemat XML jest obecnie powiązany z dokumentem XML. Schemat XML jest używany do walidacji dokumentu. Również jest używany przez funkcję IntelliSense w do wypełnienia listy Członkowskie elementów prawidłową.

## <a name="to-add-data"></a>Aby dodać dane

1.  Typ `<` w okienku edytora.

     Lista elementów członkowskich Wyświetla możliwych elementów:

    -   **!--** Aby dodać komentarz.

    -   **! DOCTYPE** można dodać typu dokumentu.

    -   **?** Aby dodać instrukcji przetwarzania.

    -   **Pracownik** można dodać elementu głównego.

2.  Wybierz **<!--** , aby dodać węzeł komentarzy i naciśnij klawisz **Enter**.

     Edytor wstawia tagu końcowego komentarz i umieszcza kursor między tagiem początkowym i końcowym w komentarz.

3.  Wpisz w **pliku XML testu**.

4.  W nowym wierszu, wpisz `<`i wybierz **pracownika** z listy elementów członkowskich.

     Edytor dodaje początek elementu XML `<employee`. W tym momencie można dodawać atrybuty do elementu lub tagu początkowego można zamknąć, wpisując `>`.

5.  Typ `>` zamknięcia tagu.

6.  Edytor dodaje do tagu końcowego. Tag końcowy zostanie dodany z faliste podkreślenie wskazujące błąd sprawdzania poprawności. **ToolTip** wyświetli komunikat: **elementu "pracownik" ma niekompletną zawartość. Oczekiwano 'ID'**.

7.  Typ `<` i wybierz **identyfikator** z listy elementów członkowskich. Następnie wpisz `>`.

     Edytor dodaje XML element `<ID></ID>`i umieszcza kursor po tag początkowy identyfikator.

8.  Typ **abc**.

     **Abc** tekst ma faliste podkreślenie. **ToolTip** wyświetli komunikat: **element 'ID' ma nieprawidłową wartość przy uwzględnieniu jego typu danych**.

9. Kliknij prawym przyciskiem myszy na elementu ID, a następnie wybierz **przejdź do definicji**.

     Otwiera edytora *hireDate.xsd* plik w nowym oknie dokumentu i umieszcza kursor w definicji elementu Identyfikatora schematu.

10. Wróć do pliku XML i Zastąp **abc** tekst z **123**.

     Faliste podkreślenie i **ToolTip** zostały wyczyszczone w wartości elementu Identyfikatora. **ToolTip** dla elementu end pracownika tag teraz wyświetlany jest komunikat: **elementu "pracownik" ma niekompletną zawartość. Oczekiwano "Data zatrudnienia"**.

11. Umieść kursor po tagu końcowego identyfikator, wpisz w `<`, wybierz pozycję **Data zatrudnienia** z listy elementów członkowskich, a następnie wpisz w `>`.

     Edytor dodaje XML element `<hire-date></hire-date>`i umieszcza kursor po Data zatrudnienia tag początkowy.

12. Wpisz w **2003-01-10** zatrudnienia daty.

## <a name="to-format-the-xml-document"></a>Format dokumentu XML

- Wybierz **dokumentu w formacie** przycisku paska narzędzi edytora XML.

    Dokument XML jest ponownie sformatowany.

## <a name="to-save-the-xml-document"></a>Aby zapisać dokument XML

1.  Z **pliku** menu, wybierz opcję **Zapisz jako**.

     **Zapisz plik jako** zostanie wyświetlone okno dialogowe. Domyślna nazwa pliku jest *"XMLFile1"*.

2.  Wprowadź nazwę pliku i lokalizację dokument XML, a następnie kliknij przycisk **zapisać**.

## <a name="hiredatexsd-file"></a>Plik hireDate.xsd
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

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)