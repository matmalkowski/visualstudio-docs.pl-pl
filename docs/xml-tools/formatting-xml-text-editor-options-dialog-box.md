---
title: Formatowanie, XML, Edytor tekstu, opcje — Okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f92ced5ca5ac007969a06cec7f253617ee293e3
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548794"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatowanie, XML, Edytor tekstu, okno dialogowe Opcje

To okno dialogowe służy do określenia ustawienia formatowania edytora XML. Dostęp można uzyskać **opcje** okno dialogowe z **narzędzia** menu.

> [!NOTE]
> Te ustawienia są dostępne po wybraniu **Edytor tekstu** folderu, **XML** folder, a następnie **formatowanie** opcję **opcje** okno dialogowe.

## <a name="attributes"></a>Atrybuty
 **Zachowaj ręczne formatowanie atrybutów**

 Atrybuty nie są ponownie sformatowany. Domyślnie włączone.

> [!NOTE]
> W przypadku atrybutów w wielu wierszach, Edytor wcięcie każdego wiersza atrybutów, aby dopasować wcięcie elementu nadrzędnego.

 **Dopasuj atrybutów na ich własnych wiersza**

 Wyrównuje druga i kolejna atrybutów w pionie, tak aby dopasować wcięcia pierwszego atrybutu. Przykładem czy wyrównanie atrybutów jest następujący tekst XML.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatycznego ponownego formatowania
 **Po wklejeniu ze Schowka**

 Formatuje tekstu XML wklejonych ze Schowka.

 **Po zakończeniu tagu końcowego**

 Formatuje element po zakończeniu tagu końcowego.

## <a name="mixed-content"></a>Zawartość mieszaną
 **Zachowaj zawartość mieszaną domyślnie**

 Określa, czy edytor formatuje zawartość mieszana. Domyślnie próbuje ponownie Formatuj zawartość mieszaną, z wyjątkiem przypadków, gdy zawartość znajduje się w edytorze `xml:space="preserve"` zakresu.

 Jeśli element zawiera tekst i znacznik, zawartość są traktowane jako mieszanie zawartości. Oto przykład elementu z zawartością mieszaną.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz także

- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Składniki edytora XML](../xml-tools/xml-editor-components.md)