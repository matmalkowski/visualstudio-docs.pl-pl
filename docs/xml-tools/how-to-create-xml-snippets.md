---
title: 'Porady: tworzenie fragmentów kodu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b820820a42814eb7169287408200bedd73435ff7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-xml-snippets"></a>Porady: tworzenie fragmentów kodu XML

Edytor XML może służyć do tworzenia nowych fragmentów kodu XML. Edytor zawiera fragment kodu XML, o nazwie "Fragment", czyli fragment standardowy do tworzenia nowych fragmentów kodu XML.

## <a name="to-create-a-new-xml-snippet"></a>Aby utworzyć nowy fragment kodu XML

 Aby utworzyć nowy kod XML fragment Utwórz nowy plik XML i użyj **wstawić fragment** funkcji.

1.  Na **pliku** menu, kliknij przycisk **nowy** , a następnie kliknij przycisk **pliku**.

2.  Kliknij przycisk **pliku XML** , a następnie kliknij przycisk **Otwórz**.

3.  Kliknij prawym przyciskiem myszy w okienku Edytora i wybierz **wstawić fragment**.

4.  Wybierz **fragment** z listy i naciśnij klawisz ENTER.

5.  Wprowadź wszelkie zmiany do nowego fragmentu.

6.  Z **pliku** menu wybierz opcję **zapisać XMLFile.xml**.

     **Zapisz plik jako** zostanie wyświetlone okno dialogowe.

7.  Wprowadź nazwę dla nowego fragmentu i wybierz **pliki fragmentu kodu** z **Zapisz jako typ** okno listy rozwijanej.

8.  Użyj **zapisać w** listy rozwijanej, aby zmienić lokalizację pliku do folderu Moje Documents\Visual Studio 2005\Code Snippets\XML\My fragmentów kodu XML, a następnie naciśnij klawisz **zapisać**.

## <a name="snippet-description"></a>Opis elementu fragment kodu

 W tej sekcji opisano niektóre z kluczowych elementów we fragmencie standardowego. Aby uzyskać więcej informacji o elementach schematu używanego przez fragmentów kodu XML, zobacz [fragmenty kodu — odwołanie do schematu](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>Element SnippetType

 Edytor obsługuje dwa typy fragment kodu:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 `Expansion` Typ Określa, czy fragment pojawia się po wywołaniu **wstawić fragment** polecenia. `SurroundsWith` Typ Określa, czy fragment pojawia się po wywołaniu **obudowy z** polecenia.

### <a name="code-element"></a>Element Code

 `Code` Element definiuje tekstu XML, który zostanie wstawiony po wywołaniu fragment kodu.

> [!NOTE]
> Tekst fragment kodu XML musi być ujęta w `<![CDATA[...]]>` sekcji.


 Poniżej przedstawiono `Code` element, który jest tworzony przez fragment standardowego.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 `Code` Element zawiera trzy zmienne.

-   $name$ jest zmiennej zdefiniowanej przez użytkownika. Tworzy `name` element, który ma wartość można edytować, który domyślnie "name". Zmienne zdefiniowane przez użytkownika są definiowane przy użyciu `Literal` elementu.

-   $ $zaznaczone to uprzednio zdefiniowanej zmiennej. Reprezentuje tekst, który wybrano w edytorze XML przed wywołaniem fragment kodu. Umieszczenia tej zmiennej określa, gdzie zaznaczonego tekstu pojawi się we fragmencie kodu wokół tego zaznaczenia.

-   $end$ to uprzednio zdefiniowanej zmiennej. Gdy użytkownik naciśnie ENTER, aby zakończyć edytowanie pól fragment kodu, ta zmienna Określa, gdzie daszek (^) zostanie przeniesiony do.

 Powyższe `Code` element wstawia następujący tekst XML:

```xml
<test>
  <name>name</name>
</test>
```

 Wartość elementu name jest oznaczona jako edytowalny region.

### <a name="literal-element"></a>Element Literal

 `Literal` Element służy do identyfikowania tekst zastępczy, który można dostosować po wstawieniu do pliku. Na przykład ciągi literału, wartości liczbowe oraz niektóre nazwy zmiennych mogą być deklarowane jako literały. Można określić dowolną liczbę literałów w Twojej fragment kodu XML i mogą odwoływać się do nich wiele razy w obrębie fragmentu. Poniżej przedstawiono przykład `Literal` element, który definiuje zmienną $ $name, którego wartość domyślna to "name".

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 Literały znajdują się funkcje. Edytor XML zawiera funkcji o nazwie **LookupPrefix**. **LookupPrefix** funkcja wyszukuje dany identyfikator URI przestrzeni nazw z lokalizacji w dokumencie XML ta Wstawka kodu jest wywoływany z i zwraca prefiks przestrzeni nazw, który jest zdefiniowany dla tej przestrzeni nazw, jeśli istnieje i zawiera dwukropek (:) w tej nazwie. Poniżej przedstawiono przykład `Literal` element, który używa **LookupPrefix** funkcji.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 Zmienna $ $prefix następnie może być używana w innym miejscu w Twojej fragment kodu XML.

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu XML](../xml-tools/xml-snippets.md)
- [Instrukcje: Używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md)
- [Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)