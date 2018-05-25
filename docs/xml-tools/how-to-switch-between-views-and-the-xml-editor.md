---
title: 'Porady: przełączać się między widokami edytora XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b0eb90f2ead313ce94d609d71385b595f3e964b
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Porady: przełączać się między widokami edytora XML

W tym temacie pokazano, jak przełączać się między widokami Projektant schematu XML (XSD Projektant) i Edytor XML. W tym przykładzie użyto [schematu zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Aby przełączyć między widoki i edytora XML

1.  Można tworzyć i edytować plik schematu XML, postępuj zgodnie z instrukcjami [porady: tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Aby przełączyć się do projektanta schematu XML w edytorze XML, kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz **Widok projektanta**.

3.  Aby przełączyć do widoku wykresu przy użyciu znaku wodnego, kliknij przycisk **użyj widoku wykresu, aby wyświetlić relacji między węzłami** łącza w widoku startowego.

4.  Przeciągnij `USAddress` węzła z **Eksploratora schematu XML** na widok wykresu. Kliknij prawym przyciskiem myszy `USAddress` węzeł w widoku wykresu i wybierz **Pokaż w widoku modelu zawartości** w menu kontekstowym.

     Widok modelu zawartości ze szczegółami dotyczącymi `USAddress` węzeł jest dostępny.

5.  Aby przełączyć do widoku startowego z widoku modelu zawartości za pomocą paska narzędzi, kliknij przycisk **widoku startowego** przycisk na pasku narzędzi XSD.

6.  Aby przełączyć się między widokami za pomocą klawiszy dostępu, naciśnij klawisz **Ctrl**+**1** dla widoku startowego **Ctrl**+**2** w widoku wykresu i **Ctrl**+**3** widoku modelu zawartości.

7.  Aby przejść do edytora XML z widoku modelu zawartości, kliknij węzeł prawym przyciskiem myszy i wybierz **kod widoku** w menu kontekstowym.