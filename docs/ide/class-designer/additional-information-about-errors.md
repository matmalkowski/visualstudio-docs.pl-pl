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
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 014497d0b32df61412820468a8f3f7e0b177c14f
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33963636"
---
# <a name="class-designer-errors"></a>Błędy projektanta klas

**Projektant klas** nie śledzi lokalizację plików źródłowych, więc modyfikowania struktury projektu i przenoszenie plików źródłowych w projekcie może spowodować **Projektant klas** utratę informacji typu, na przykład jest wspólny dla Zmodyfikuj typ źródła jako element typedef, klas podstawowych i skojarzenia typów. Błąd może pojawić się takie jak **Projektant klas nie może wyświetlić tego typu**. Aby rozwiązać problem, przeciągnij kod źródłowy przeniesiono lub modyfikacji do diagramu klas ponownie, aby go wyświetlić.

## <a name="resources"></a>Zasoby

Pomoc w innych błędów i ostrzeżeń można znaleźć w następujących zasobach:

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md) zawiera informacje o wyświetlaniu C++ na diagramie klas dotyczące rozwiązywania problemów.
- [Visual Studio Projektant klas forum](http://go.microsoft.com/fwlink/?LinkId=160754) zawiera forum pytania na temat **Projektant klas**.

## <a name="see-also"></a>Zobacz także

- [Projektowanie i widoku klas i typów](designing-and-viewing-classes-and-types.md)
