---
title: 'Porady: Wybieranie schematów XML do użycia'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d835a8592108b549a109f7bb7e128a8ae5b01611
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549106"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Porady: Wybieranie schematów XML do użycia

Edytor XML zawiera znajduje się w pamięci podręcznej schematu *%InstallDir%\Xml\Schemas* katalogu. Pamięci podręcznej schematu obejmuje dobrze znanych schematów XML, które są używane do walidacji dokumentu IntelliSense i XML.

**Schematy** właściwości dokumentu jest używana do wybierania co najmniej jeden schemat definition language (XSD) schematy XML do użycia. Można wybrać schematów z pamięci podręcznej schematu lub określ schemat, który nie znajduje się w pamięci podręcznej.

Schematy należy określić są zapisywane w ukrytym pliku opcji użytkownika rozwiązania (. *suo*), właściwości oraz wszystkich innych XML dokumentu. W związku z tym nie trzeba ponownie wprowadzić te wartości przy następnym otwarciu rozwiązania.

> [!NOTE]
> Edytor można sprawdzić za pomocą wbudowanego schematu lub schemat odwołuje się `xsd:schemaLocation` atrybutu. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności kodu XML dokumentu](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Aby wybrać schematu XML z pamięci podręcznej schematu

1.  Otwórz plik w edytorze XML.

2.  W oknie właściwości dokumentu, kliknij przycisk **schematy** pola.

     **Schematów XML** zostanie wyświetlone okno dialogowe. Okno dialogowe zawiera listę wszystkich schematów z. *xsd* rozszerzenia w pamięci podręcznej schematu (w tym schematów, do którego odwołuje się *catalog.xml* pliku) i również żadnego schematu, która jest w bieżącym rozwiązaniu, Otwórz w programie Visual Studio, do której odwołuje się `xsd:schemaLocation` atrybut lub do których odwołuje się **schematy** właściwości.

3.  Wybierz schematy do użycia w celu weryfikacji, wykonując jedną z następujących czynności:

    -   Wybierz na liście schemat **schematów XML** okna dialogowego, kliknij przycisk **użyj** kolumny, a następnie wybierz **używają tego schematu**.

     —lub—

    -   Wybierz wiele schematów na liście **schematów XML** okna dialogowego, kliknij prawym przyciskiem myszy i wybierz **używają tego schematu**.

4.  Kliknij przycisk **OK**.

     Lista wybranych schematów jest kopiowany do **schematy** właściwości dokumentu.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Aby dodać schematu XML do pamięci podręcznej schematu

1.  W oknie właściwości dokumentu, kliknij przycisk **schematy** pola.

2.  Kliknij przycisk **Dodaj**.

     Spowoduje to otwarcie **Otwórz schematu XSD** okna dialogowego.

3.  Wyszukaj i wybierz schematy do dodania do pamięci podręcznej schematu.

4.  Kliknij przycisk **Otwórz**.

     Schematy dodane do schematu pamięci podręcznej i jest **użyj** ma ustawioną wartość w kolumnie **używają tego schematu**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Aby usunąć z pamięci podręcznej schematu schematu XML

1.  W oknie właściwości dokumentu, kliknij przycisk **schematy** pola.

2.  Wybierz schemat, Usuń, a następnie kliknij przycisk **Usuń**.

     Schemat zostanie usunięty z pamięci podręcznej schematu w pamięci, ale nie zostanie usunięta z systemu plików.

    > [!NOTE]
    > Jeśli nadal masz odwołanie do schematu za pomocą `schemaLocation` atrybutu lub odpowiadającego mu `targetNamespace` następnie **Usuń** nie będzie działać w tej sytuacji z powodu skojarzenia automatycznie. W takim przypadku zalecane jest, aby oznaczyć schematu jako **nie używaj wybranych schematów** w **użyj** kolumny.

## <a name="see-also"></a>Zobacz także

- [Pamięci podręcznej schematów](../xml-tools/schema-cache.md)
- [Okno dialogowe schematy XML](../xml-tools/xml-schemas-dialog-box.md)
- [Edytor XML](../xml-tools/xml-editor.md)