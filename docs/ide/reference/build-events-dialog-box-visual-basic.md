---
title: Zdarzenia kompilacji (Visual Basic) — Okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38ef3b173643c7bff0e1417ffc9ecfb431b06685
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944138"
---
# <a name="build-events-dialog-box-visual-basic"></a>Zdarzenia kompilacji (Visual Basic) — Okno dialogowe
Użyj **zdarzeń kompilacji** okno dialogowe, aby określić instrukcje konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia prekompilacyjnego lub mające miejsce po kompilacji. Aby uzyskać więcej informacji, zobacz [porady: Określanie kompilacji zdarzenia (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Wiersz polecenia zdarzenia prekompilacyjnego** określa żadnych poleceń do wykonania przed rozpoczęciem kompilacji. Wpisanie polecenia długie, kliknij przycisk **Edytuj prekompilacyjnego** do wyświetlenia [prekompilacyjnego zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Jeśli projekt jest aktualny i kompilacji nie zostanie wywołany, nie należy uruchamiać zdarzenia prekompilacyjnego.


 **Wiersz polecenia zdarzenia po kompilacji** określa żadnych poleceń do wykonania po zakończeniu kompilacji. Wpisanie polecenia długie, kliknij przycisk **Edytuj postkompilacyjnego** do wyświetlenia **zdarzeń/po kompilacji — zdarzenia prekompilacyjnego d wiersza polecenia**ialog pole.

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkie postkompilacyjnego polecenia, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Uruchomić zdarzenie mające miejsce po kompilacji** określa warunki zdarzenia postkompilacyjnego do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Zawsze**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony, niezależnie od tego, czy kompilacja zakończy się pomyślnie.|
|**Pomyślnie kompilacji**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony, jeśli kompilacja zakończy się powodzeniem. Zdarzenie zostanie uruchomiony nawet w przypadku projektu, który jest aktualny, dopóki kompilacja zakończy się pomyślnie. To jest ustawienie domyślne.|
|**Gdy kompilacja aktualizuje wyjście projektu**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony tylko wtedy, gdy plik wyjściowy przez kompilator (.exe lub .dll) różni się od poprzedniego pliku danych wyjściowych kompilatora. Zdarzenie mające miejsce po kompilacji nie jest uruchamiane, gdy projekt jest aktualny.|

## <a name="see-also"></a>Zobacz też

- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Okno dialogowe wiersza polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)