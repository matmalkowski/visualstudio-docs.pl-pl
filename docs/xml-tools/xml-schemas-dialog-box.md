---
title: Okno dialogowe schematy XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aeea4b015cf728b2b6b40375ce87bcd3c1dd2b89
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-schemas-dialog-box"></a>Okno dialogowe schematy XML

**Schematów XML** okno dialogowe służy do wybierania który schematy XML schematu definition language (XSD) do skojarzenia z dokumentu XML. Wybierz schemat z pamięci podręcznej schematu lub określ schemat, który nie znajduje się w pamięci podręcznej. Wybrane schematy są traktowane jako część zestawu schematu. Zestaw schematu jest używany na potrzeby funkcji IntelliSense, a także sprawdzanie poprawności kodu XML dokumentu.

Dostęp można uzyskać **schematów XML** okno dialogowe albo klikając **schematy** przycisk w oknie właściwości dokumentu lub wybierając **schematy** z **XML** menu.

## <a name="uielement-list"></a>Lista elementów UI
 **Użyj**

 Wybierz, jak schemat XML ma być używany.

-   **Automatyczne**. Ten schemat nie jest używany przez bieżący dokument, ale jest dostępny na automatyczne kojarzenie. Jeśli dokument XML deklaruje przestrzeni nazw, która odpowiada `targetNamespace` tego schematu schemat zostanie automatycznie skojarzona i znajduje się w zestawie schematów.

-   **Używaj tego schematu**. Ten schemat jest używany przez bieżącego dokumentu. Użytkownik ma jawnie żądana, można użyć tego schematu, klikając tę kolumnę lub schemat został automatycznie skojarzone na podstawie zgodności `targetNamespace`.

-   **Nie używaj wybranych schematów**. Ten schemat nie jest używany przez bieżący dokument, nawet jeśli schemat ma pasujący `targetNamespace`. To ustawienie może być przydatne podczas rozwiązywania konfliktów, jeśli istnieje więcej niż jedną wersję tego samego schematu w pamięci podręcznej schematu lub rozwiązania.

**Namespace docelowego**

Wyświetla docelową przestrzeń nazw, skojarzone ze schematem XML.

**Nazwa pliku**

Wyświetla nazwę pliku schematu XML.

**Dodaj**

Otwiera **Otwórz schematu XSD** okno dialogowe, które można wybrać dodatkowe schematy do dodania do zestawu schematu. Po dodaniu schematu do schematu ustawiony **użyj** ma ustawioną wartość w kolumnie **używają tego schematu**.

**Usuń**

Usuwa obecnie wybrany schemat z zestawu schematów. Spowoduje to usunięcie schematu z pamięci podręcznej schematu w pamięci, ale nie z systemu plików.

## <a name="see-also"></a>Zobacz też

- [Składniki edytora XML](../xml-tools/xml-editor-components.md)
- [Instrukcje: Wybieranie schematów XML do użycia](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Pamięć podręczna schematów](../xml-tools/schema-cache.md)