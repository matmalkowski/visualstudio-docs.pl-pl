---
title: Błędy projektanta klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0af8686af556ca24cdbc9e0a51206f4f0728206
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="additional-information-about-class-designer-errors"></a>Dodatkowe informacje o błędach Projektant klas

**Projektant klas** nie śledzi lokalizację plików źródłowych, więc modyfikowania struktury projektu i przenoszenie plików źródłowych w projekcie może spowodować **Projektant klas** utratę informacji o typie (szczególnie typ źródła element typedef, klas podstawowych lub skojarzenia typów). Błąd może pojawić się takie jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij kod źródłowy zmodyfikowany lub przeniesiono do diagramu klas, aby ją wyświetlić go ponownie.

## <a name="resources"></a>Zasoby

Pomoc w innych błędów i ostrzeżeń można znaleźć w następujących zasobach:

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md) zawiera informacje o wyświetlaniu C++ na diagramie klas dotyczące rozwiązywania problemów.
- [Visual Studio Projektant klas forum](http://go.microsoft.com/fwlink/?LinkId=160754) zawiera forum pytania na temat **Projektant klas**.

## <a name="see-also"></a>Zobacz także

- [Projektowanie i tworzenie klas i typów](designing-and-viewing-classes-and-types.md)
