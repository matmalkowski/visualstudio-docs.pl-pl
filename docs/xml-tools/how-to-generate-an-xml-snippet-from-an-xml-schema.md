---
title: 'Porady: generowanie fragment kodu XML na podstawie schematu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f598f01116d7ce2aec5759c411e456083f6932b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Porady: generowanie fragment kodu XML na podstawie schematu XML

Edytor XML ma możliwość Generowanie fragmentów kodu XML na podstawie schematu schematu XML definition language (XSD). Na przykład podczas tworzenia pliku XML, gdy znajduje się obok nazwy elementu, można naciśnij klawisz TAB, aby umieścić element w danych XML generowane na podstawie informacji o schemacie dla tego elementu.

Ta funkcja jest dostępna tylko w przypadku elementów. Również mają zastosowanie następujące reguły:

-   Element musi mieć typ schematu skojarzone; oznacza to, że element musi być prawidłowa zgodnie z niektórych skojarzony schemat. Typ schematu nie może być abstrakcyjny i typ musi zawierać wymaganych atrybutów i/lub wymaganych elementów podrzędnych.

-   Bieżący element w edytorze może być pusta bez atrybutów. Na przykład poniżej przedstawiono wszystkie ważne

    -   `<Account`

    -   `<Account>`

    -   `<Account></Account>`

-   Kursor musi znajdować się na prawo nazwy elementu.

Wygenerowany fragment kodu zawiera wszystkie wymagane atrybuty i elementy. Jeśli `minOccurs` jest większa niż jeden, minimalna wymagana liczba wystąpień tego elementu znajduje się we fragmencie, maksymalnie 100 wystąpień. Wszelkie stałe wartości znajdujące się w wyniku schematu w wartości stałe we fragmencie. `xsd:any` i `xsd:anyAttribute` elementy są ignorowane i spowodować konstrukcje nie dodatkowe fragmentu.

Wartości domyślne są generowane i oznaczane jako wartości można edytować. Jeśli schemat określa wartość domyślną, ta wartość domyślna jest używana. Jednak jeśli schemat wartość domyślna to ciąg pusty, Edytor generuje wartości domyślne w następujący sposób:

-   Jeśli typ schematu zawiera wszystkie aspekty wyliczenia bezpośrednio lub pośrednio przy użyciu żadnego z elementów członkowskich typu złożenia pierwsza wartość wyliczenia odnaleźć w modelu obiektu schematu jest używany jako domyślny.

-   Jeśli typ schematu jest typem niepodzielnym, Edytor pobiera atomic typu i wstawia nazwy typu atomic. Pochodne typu prostego używa podstawowy typ prosty. Typ listy jest typu atomic `itemType`. Dla Unii, atomic typ jest typem atomic pierwszego `memberType`.

## <a name="example"></a>Przykład

 Kroki opisane w tej sekcji pokazują, jak funkcja wygenerować schematu XML fragment kodu z edytora XML.

> [!NOTE]
> Przed rozpoczęciem tych procedur, Zapisz plik schematu na komputerze lokalnym.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go z schematu XML

1.  Na **pliku** menu wskaż **nowy**i kliknij przycisk **pliku**.

2.  Wybierz **pliku XML** w **szablony** okienko i kliknij przycisk **Otwórz**.

     Nowy plik jest otwarty w edytorze. Plik zawiera deklaracji XML domyślne `<?xml version="1.0" encoding="utf-8">`.

3.  W oknie właściwości dokumentu, kliknij przycisk Przeglądaj (**...** ) na **schematy** pola.

     **Schematów XSD** zostanie wyświetlone okno dialogowe.

4.  Kliknij przycisk **Dodaj**.

     **Otwórz schematu XSD** zostanie wyświetlone okno dialogowe.

5.  Wybierz plik schematu, a następnie kliknij przycisk **Otwórz**.

6.  Kliknij przycisk **OK**.

     Schemat XML jest obecnie powiązany z dokumentem XML.

### <a name="to-generate-an-xml-snippet"></a>Aby wygenerować fragment kodu XML

1.  Typ `<` w okienku edytora.

2.  Lista elementów członkowskich Wyświetla możliwych elementów:

     **!--** Aby dodać komentarz.

     **! DOCTYPE** można dodać typu dokumentu.

     **?** Aby dodać instrukcji przetwarzania.

     **Skontaktuj się z** można dodać elementu głównego.

3.  Wybierz **kontakt** z listy elementów członkowskich i naciśnij klawisz ENTER.

     Edytor dodaje tag początkowy `<Contact` i umieszcza kursor po nazwie elementu.

4.  Naciśnij klawisz TAB, aby wygenerować danych XML dla `Contact` element na podstawie jego schematu informacji.

## <a name="input"></a>Dane wejściowe

 Następujący plik schematu jest używany przez przewodnika.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>Dane wyjściowe

 Poniżej przedstawiono dane XML, które jest generowany na podstawie informacji schematu skojarzone z `Contact` elementu. Elementy oznaczone jako `bold` wyznaczyć edytowalnego pola we fragmencie kodu XML.

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu XML](../xml-tools/xml-snippets.md)
- [Instrukcje: Używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md)