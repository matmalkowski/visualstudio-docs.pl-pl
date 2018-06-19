---
title: Strona Zdarzenia kompilacji, Projektant projektu (C#)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: fe83d3a387d2066965fe83145ddbda4e9648d36b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944846"
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)
Użyj **zdarzeń kompilacji** strony **projektanta projektu** do określenia instrukcji konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia postkompilacyjnego. Aby uzyskać więcej informacji, zobacz [porady: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)i [porady: Określ kompilacji zdarzenia (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Lista elementów UI
 **Konfiguracja** ten formant nie jest edytowalny na tej stronie. Opis tego formantu, zobacz [strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma** ten formant nie jest edytowalny na tej stronie. Opis tego formantu, zobacz [strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Wiersz polecenia zdarzenia prekompilacyjnego** określa żadnych poleceń do wykonania przed rozpoczęciem kompilacji. Wpisanie polecenia długie, kliknij przycisk **Edytuj prekompilacyjnego** do wyświetlenia [prekompilacyjnego zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Jeśli projekt jest aktualny i kompilacji nie zostanie wywołany, nie należy uruchamiać zdarzenia prekompilacyjnego.


 **Wiersz polecenia zdarzenia po kompilacji** określa żadnych poleceń do wykonania po zakończeniu kompilacji. Wpisanie polecenia długie, kliknij przycisk **Edytuj postkompilacyjnego** do wyświetlenia **prekompilacyjnego zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe**.

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkie postkompilacyjnego polecenia, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Uruchomić zdarzenie mające miejsce po kompilacji** określa następujące warunki dla zdarzenia postkompilacyjnego do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Zawsze**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony niezależnie od tego, czy kompilacja zakończy się pomyślnie.|
|**Pomyślnie kompilacji**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony, jeśli kompilacja zakończy się powodzeniem. W związku z tym zdarzeniem zostanie uruchomiony nawet w przypadku projektu, który jest aktualny, dopóki kompilacja zakończy się pomyślnie.|
|**Gdy kompilacja aktualizuje wyjście projektu**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony tylko wtedy, gdy plik wyjściowy przez kompilator (.exe lub .dll) różni się od poprzedniego pliku danych wyjściowych kompilatora. W związku z tym zdarzenie mające miejsce po kompilacji nie jest uruchamiane, gdy projekt jest aktualny.|

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Instrukcje: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)